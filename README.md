EasyCommentGenerator
====================

The best way to generate Documentation.

Use is really simple, comment your code as in the following example and run the program.

```
usage: DocGenerator.py [-h] [-m MARKER] [-d DIRECTORY] [-e EXTENSION]

Generate documentation from a very and easy-to-use syntax.

optional arguments:
  -h, --help            show this help message and exit
  -m MARKER, --marker MARKER
                        Specify the comment marker to use. This depends on the
                        language your are using. Default is defined for
                        python.
  -d DIRECTORY, --directory DIRECTORY
                        Specify the directory from which the source files will
                        be retrieved to parse documentation. Default is the
                        current working directory.
  -e EXTENSION, --extension EXTENSION
                        Specify the extension of your files. Default is `py`.
  -v VERBOSE, --verbose VERBOSE
                        Specify the verbose level. Possible verbose level are :
						DEBUG, INFO, WARNING, ERROR.
  -l LOG, --log LOG
                        Active and specify the output file for log.

```

Every comment must begin with the selected comment character followed by the type of comment and a colon.
the type can be written :

	#t:
	#type:
	#Type:


Available types are :

	- Variables : #v: or #var: or #Var:
	- Functions : #f: or #function: or #Function:
	- Parameters : #p: or #parameter: or #Parameter:
	- Returns : #r: or #return: or #Return:
	- Classes : #cl: or #class: or #Class:
	- Attributes : #a: or #attributes: or #Attributes:
	- Methods : #m: or #method: or #Method:
	- Additional comment : #c: or #comment: or #Comment:


Different styles for a comment line :

		-  #v: name : comment

		-  #v: name
		   #c: comment

		-  #v: name : comment
		   #c: comment

		-  #var: name : comment
		   #comment: comment

	if you use a comment just after the name you must use colon between the name and the comment.


Position of comment :
	you can position any comments as you want. Just follow the basic rules of programming :

		- parameters declarations must follow a function or method declaration.
		- return declarations must follow a function or method declaration.
		- attributes declarations must follow a class declaration.
		- methods declarations must follow a class declaration.
		- Additional comment declarations must follow anyone declaration.


Use of additional comments :
	An additional comment add comment to the last comment declaration (var or function or parameter...)


Some additional explanations :
	If you open a function comment, every parameter comments and every return comments link them with the last function declaration
	until you open an another function comment.
	If you open a class comment, every attributes comments and every methods comments link them with the last class declaration
	until you open an another class comment.
	Functions comment and method comments work in the same way.

Examples:
	We use python for the example but you can comment every languages (#).

	Comment a variable outside of any function :

		#v: name : comment

		#v: MAX_VERBOSE_LEVEL : the verbose level
		MAX_VERBOSE_LEVEL = 5

	Another style :

		#var: name
		#comment: comment

		#var: MAX_VERBOSE_LEVEL
		#comment: the verbose level
		MAX_VERBOSE_LEVEL = 5


	Comment a function :

		#f: name
		#c: comment
		#p: name : comment
		#r: name : comment
		#c: comment

		#f: myinit
		#c: Initialise Project Object
		#p: opts : Options given by user
		#r: test : comment
		#c: comment
		def myinit(opts) :
				self.options = Options(opts)
				self.verbose = Verbose(self.options.verboseLevel)
				self.verbose.printer(4, 'Init Class Project')
				return 2

	Another style :

		#Function: name : comment
		#p: name : comment
		#c: comment
		#r: name
		#c: comment

		#Function: myinit : Initialise Project Object
		#p: opts : Options given by user
		#c: comment
		#r: test :
		#c: comment
		def myinit(opts) :
				self.options = Options(opts)
				self.verbose = Verbose(self.options.verboseLevel)
				self.verbose.printer(4, 'Init Class Project')
				return 2

	Another style :

		#Function: name : comment
		#p: name : comment
		#r: name
		#c: comment

		#Function: myinit : Initialise Project Object
		def myinit(opts) :
			#p: opts : Options given by user
			self.options = Options(opts)
			self.verbose = Verbose(self.options.verboseLevel)
			self.verbose.printer(4, 'Init Class Project')
			#r: test :
			#c: comment
			return 2


	Comment a class :

		#Class: name : comment.
		#c: comment.
		#a: name : comment.
		#a: name : comment.
		#a: name : comment.
		#m: name : comment.
		#m: name : comment.


		#Class: OptionsExeption : OptionsExeption Object.
		#c: Inherit form Exception Object.
		#a: errorMessage : Message for the exception.
		#a: options : Options which have an error.
		#a: formatMessage : Option correctly formatted.
		class OptionsExeption(Exception):

		#m: init : Initialyse OptionsExeption Object.
		#p: errorMessage : Message for the exception.
		#p: options : Options which have an error.
		#p: formatMessage : Option correctly formatted.
		#r: None
		def __init__(self, errorMessage, options, formatMessage):
			self.errorMessage = errorMessage
			self.options = options
			self.formatMessage = formatMessage

		#m: str : Initialyse OptionsExeption Object.
		#r: Message : String which will be printed for the exception.
		def __str__(self):
			return '\n' + self.errorMessage + ': ' + str(self.options) + '\n' + self.formatMessage

	Another style :

		#cl: name : comment.
		#c: comment.
		#a: name : comment.
		#a: name : comment.
		#a: name : comment.
		#m: name : comment.
		#m: name.
		#c: comment


		#cl: OptionsExeption : OptionsExeption Object.
		#c: Inherit form Exception Object.
		class OptionsExeption(Exception):
			#a: errorMessage : Message for the exception.
			#a: options : Options which have an error.
			#a: formatMessage : Option correctly formatted.


		#m: init : Initialyse OptionsExeption Object.
		def __init__(self, errorMessage, options, formatMessage):
			#p: errorMessage : Message for the exception.
			self.errorMessage = errorMessage
			#p: options : Options which have an error.
			self.options = options
			#p: formatMessage : Option correctly formatted.
			self.formatMessage = formatMessage
			#r: None

		#m: str.
		#c: Initialyse OptionsExeption Object.
		def __str__(self):
			return '\n' + self.errorMessage + ': ' + str(self.options) + '\n' + self.formatMessage
			#r: Message : String which will be printed for the exception.



