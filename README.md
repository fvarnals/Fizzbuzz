# Fizzbuzz

## Concept

Use Test Driven Development (TDD) to create and test a program which, when given an integer, returns the following:

* 'Fizz' if the integer is divisible by 3
* 'Buzz' if the integer is divisible by 5
* 'Fizzbuzz' if the integer is divisible by both 3 and 5
* The input integer if none of the above

===================================================================

## Process

1. First set up RSpec.

Install the gem using:
    install rspec
Then initialise the project using:
  rspec --init

2. Create a new Ruby file for our spec tests

  touch spec/fizzbuzz_spec.rb
Then run RSpec to check that there are no errors (since there are currently 0 tests, there should be no failures)

3. Create the first test.

The first test is that the program fizzbuzz will return 'fizz' when passed the integer 3 as an input:
  require 'fizzbuzz'
  describe 'fizzbuzz' do
    it 'returns "fizz" when passed 3' do
      expect(fizzbuzz(3)).to eq 'fizz'
    end

We first wrote a method which will always return 'fizz':
  def fizzbuzz(number)
    'fizz'
  end

This works initially because we're only looking for a 3 to return 'fizz', however the program will also return 'fizz' for any number whatsoever! What about the other inputs?

4. Create a new test to include 5 as an input integer.

For this we used the same format as before, but altered for our new test:

  it 'returns "buzz" when passed 5' do
    expect(fizzbuzz(5)).to eq 'buzz'
  end

5. Now we need to change our fizzbuzz method to deal with mutliples of 5, and also all multiples of 3, rather than just 3 itself!

  def fizzbuzz(number)
  	if number % 3 == 0
  		return 'fizz'
  	elsif number % 5 == 0
  		return 'buzz'
  	end
  end

6. Now we add a test for an integer that is a multiple of both 3 and 5. Let's start with 15.

We add the following new test to our fizzbuzz_spec.rb file:

  it 'returns "fizzbuzz" when passed 15' do
    expect(fizzbuzz(15)).to eq 'fizzbuzz'
  end

We also need to update our method to address this. We'll have to put the case where the integer (number) is a multiple of both 3 and 5 first in the control flow loop, since of course otherwise it would return the first result, since it meets the requirements of each test!

  def fizzbuzz(number)
  	if number % 3 == 0 && number % 5 == 0
  		return 'fizzbuzz'
  	elsif number % 3 == 0
  		return 'fizz'
  	elsif number % 5 == 0
  		return 'buzz'
  	end
  end

  7. Finally, we need to address the case where the input integer is not a multiple of either 3 or 5. So lets add a test for that, choosing an input number that meets the criterion; we'll use 7:

    it 'returns 7 when passed 7' do
      expect(fizzbuzz(7)).to eq 7
    end

  And again, add this functionality to the fizzbuzz method. We add this on at the end of the flow control loop as:

    else
  		return number

  i.e if none of the other criteria are met (input integer is not divisible by both 3 and 5, or just 3, or just 5) then we return the input integer.
