# Changelog

## 0.3.0

Updates to support the quote escaping sections of the CSV standard (see: https://tools.ietf.org/html/rfc4180 sections 2.5-2.7):

    supports using escape quotes to escape commas
    supports using escape quotes to escape double quotes
    supports using escape quotes to escape newlines

BREAKING CHANGE TO THE DF PACKAGE. Here are the breaking changes, with examples:

    Double quotes around a field are now consumed
    example csv input row: a,"b",c\n
    current df output values: {'a', '"b"', 'c'}
    df output values after PR: {'a', 'b', 'c'}
    An un-escaped double quote or an escaping double quote without a closing escape quote will throw an exception
    example csv input row: a,b"c,d\n
    current df output: {'a', 'b"c', 'd'}
    df output values after PR: FormatException('A field contained an escape...') <- explanatory error message is included
    Numeric records accompanied by whitespace will be inferred as Strings with whitespace
    example csv input row: a, 1 \n
    current df output values: {'a', 1} <--- parsed as int
    df output values after PR: {'a', ' 1 '} <---- remains a string


## 0.2.1

- Improve the tests
- Improve the docs

## 0.2.0

- Add support for timestamp formats
- Update dependencies

## 0.1.0

Initial