#1. What's the difference between `include` and `extend`?
	Include give the instance access to the module's method  while extend gives the class access to the module's method

	example:

	For extend
	module ModuleA
	  def example_method
	    "abcd"
	  end
	end

	class ClassA
	  extend ModuleA
	end

	test = ClassA.example_method
	puts test
	For include
	module ModuleA
	  def example_method
	    "abcd"
	  end
	end

	class ClassA
	  include ModuleA
	end

	test = ClassA.new.example_method
	puts test

#2. What's the difference between `clone` and `dup`?

	2.1) While using clone the frozen state of object remains same bur for dup frozen state changes
	 data = 'kajal'.freeze
	  => "kajal"
	 data.clone.frozen?
	  => true
	 data.dup.frozen?
	  => false 
	2.2)Dup creates a new object without setting the id while clone creates the object with same id

#3. What's the difference between `Proc` and `lambda`?
	Lamda check for the no. of argumnent and throws an error if the argument doensn't match while proc doesn't care for the no. of arguments also both lamda and proc treats return key was in different manner

	example:
	data = lambda { |x| puts x }    # creates a lambda that takes 1 argument
	lam.call("hi")                    # prints out hi
	lam.call                       # ArgumentError: wrong number of arguments (0 for 1)


	data = Proc.new { |x| puts x } # creates a proc that takes 1 argument
	data.call(x)                   # prints out x
	data.call                      # returns nil
	data.call(x,y,z)               # prints out x and forgets about the extra arguments

#4. What's a good example for using `yield` in ruby?

	Yeild basically allows a chunck of code to inject during method invokation.

	Below is the example that I usually use for the metatags in my application

	Example:
	in application helper

	def yield_meta_tag(tag, default_text='')
	   content_for?(:"meta_#{tag}") ? content_for(:"meta_#{tag}") : default_text
	end

	in application layout:
	<meta name='keywords' content='<%= yield_meta_tag(:keywords, 'xyz') %>' />

#5. You need to integrate with several REST APIs that often change over time. What design pattern would you use so that it limits  the effect of these changes on your code base?
  
  For acheiving this we should make reusable apis with Custom business logic and end points.

#6. If you were to give a junior dev 3 programming books, what would they be?
  
  The Ruby Programming Language
  Learning From Jquery
  W3 school html tutorial


#7. You've been tasked with adding a new screen that shows an index page of Recent Articles, briefly describe the steps you would take when adding this new feature

  Following are the steps that needs to be followed for achceiving the requirement:

	We will create a route for the index action with "get" method.
	We will create a method for index action.
	we will performs a left outer join on article and author.
	we will create a scope in article model to get all the recent articles ordered in the most recent published_at column.
	We will get a array based upon the scope
	We will create a view page for the index action
	We will iterate a loop on the array we got from action to display thedata in the array.

  Example: Same as in articles#index of our articles controller

