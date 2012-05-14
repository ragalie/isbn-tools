== Not Maintained

I originally pulled this project into GitHub from its 
[original home](http://rubyforge.org/projects/isbn-tools/). I do not
believe it is currently maintained.

You may be interested in my [Lisbn](https://github.com/ragalie/lisbn)
project which performs many of the same functions and is backed by
a more modern test suite.

== ISBN-Tools for Ruby

This library provides the ability to manipulate ISBN numbers.
It knows about ISBN-10 and ISBN-13 numbers, has the ability to
check if they are valid and convert from one format to the other.
It can, of course, compute the check digit of both formats.

Finally, it has the ability to hyphenate ISBN numbers for the
following group identifiers: 0, 1 and 2.  Note that only hyphenation
methods need to know about ranges, so all others methods (validity, 
checksum computations and number conversions) can be used with ISBN 
numbers from any group.

Other ranges could be added on request but I would need samples
ISBN to check the result.

== Usage

  require 'rubygems'
  require 'isbn/tools'

  isbn_good = "2800107766"
  isbn_bad = "2810107766"

  def check_and_hyphenate(isbn)
    if ISBN_Tools.is_valid?(isbn)
      puts ISBN_Tools.hyphenate(isbn)
    else
      cksum = ISBN_Tools.compute_check_digit(isbn)
      puts "Invalid ISBN number [#{isbn}]. Checksum should be #{cksum}"
    end
  end

  check_and_hyphenate isbn_good # => 2-8001-0776-6
  check_and_hyphenate isbn_bad  # => Invalid ISBN number [2810107766]. Checksum should be 9

== Copyright

Copyright:: 2006, Thierry Godfroid

The following sources were used in order to understand ISBN numbers and
how to manipulate them. No books were harmed in the process.
- http://www.isbn-international.org
- "Are You Ready for ISBN-13?" http://www.isbn.org/standards/home/isbn/transition.asp. Note that at the bottom of this page, you can find a link towards a small book "ISBN-13 for Dummies", available as PDF (http://www.bisg.org/isbn-13/ISBN13_For_Dummies.pdf)
- Structure of an ISBN number http://www.isbn.org/standards/home/isbn/international/html/usm4.htm

Ranges information was found at http://www.isbn-international.org/en/identifiers.html.

== LICENCE NOTE

MIT-Style license. See LICENCE file in this distribution.

== Requirements

ISBN-Tools requires Ruby 1.8.2 or better.

== Known bugs/Limitations

- This release code only allows for one-digit groups.
- See also the TODO file in this distribution
