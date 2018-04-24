[![Issues on deck](https://badge.waffle.io/mivok/markdownlint.png?label=on%20deck&title=On%20Deck)](https://waffle.io/mivok/markdownlint)
[![Travis build status](http://api.travis-ci.org/mivok/markdownlint.svg)](https://travis-ci.org/mivok/markdownlint)
[![Gem Version](https://badge.fury.io/rb/mdl.svg)](http://badge.fury.io/rb/mdl)

# Markdown lint tool

A tool to check markdown files and flag style issues.

## Installation

Markdownlint is written in ruby and is distributed as a rubygem. As long as
you have a relatively up to date ruby on your system, markdownlint will be
simple to install and use. You have 2 options to install it:

To install from rubygems, run:

    gem install mdl

To install the latest development version from github:

    git clone https://github.com/markdownlint/markdownlint
    cd markdownlint
    rake install


Note that you will need [rake](https://github.com/ruby/rake)
(`gem install rake`) and [bundler](https://github.com/bundler/bundler)
(`gem install bundler`) in order to build from source.

If you got error messages like:

    rake aborted!
    Couldn't install gem, run `gem install
    /root/markdownlint/pkg/mdl-0.4.0.gem' for more detailed output

    Tasks: TOP => install
    (See full trace by running task with --trace)

Please install the following packages with specific version by yourself

- bundler (default: 1.16.0)
- coderay (1.1.2)
- kramdown (1.14.0)
- method_source (0.9.0)
- mixlib-cli (1.7.0)
- mixlib-config (2.2.4)
- pry (0.11.3)
- rake (12.2.1)

## Usage

To have markdownlint check your markdown files, simply run `mdl` with the
filenames as a parameter:

    mdl README.md

Markdownlint can also take a directory, and it will scan all markdown files
within the directory (and nested directories):

    mdl docs/

If you don't specify a filename, markdownlint will use stdin:

    cat foo.md | mdl

Markdownlint will output a list of issues it finds, and the line number where
the issue is. See [RULES.md](docs/RULES.md) for information on each issue, as
well as how to correct it:

    README.md:1: MD013 Line length
    README.md:70: MD029 Ordered list item prefix
    README.md:71: MD029 Ordered list item prefix
    README.md:72: MD029 Ordered list item prefix
    README.md:73: MD029 Ordered list item prefix

Markdownlint has many more options you can pass on the command line, run
`mdl --help` to see what they are, or see the documentation on
[configuring markdownlint](docs/configuration.md).

### Styles

Not everyone writes markdown in the same way, and there are multiple flavors
and styles, each of which are valid. While markdownlint's default settings
will result in markdown files that reflect the author's preferred markdown
authoring preferences, your project may have different guidelines.

It's not markdownlint's intention to dictate any one specific style, and in
order to support these differing styles and/or preferences, markdownlint
supports what are called 'style files'. A style file is a file describing
which rules markdownlint should enable, and also what settings to apply to
individual rules. For example, rule [MD013](docs/RULES.md#md013---line-length)
checks for long lines, and by default will report an issue for any line longer
than 80 characters. If your project has a different maximum line length limit,
or if you don't want to enforce a line limit at all, then this can be
configured in a style file.

For more information on creating style files, see the
[creating styles](docs/creating_styles.md) document.

## Contributing

1. Fork it ( <http://github.com/markdownlint/markdownlint/fork> )
1. Create your feature branch (`git checkout -b my-new-feature`)
1. Commit your changes (`git commit -am 'Add some feature'`)
1. Push to the branch (`git push origin my-new-feature`)
1. Create new Pull Request
