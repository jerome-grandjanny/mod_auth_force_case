mod_auth_force_case
===================

An Apache 2.0 module for allowing users to type their login name in any case

Problem:

        Very often, users are complaining about refused connexion just
        because their login name must be typed in upper case letters or
        in lower case letters and they typed it the wrong way.

        In some situations, it is acceptable to allow users to type their
        username in any case and to be able to recognize any combination
        of upper case letters and lower case letters as the same user.

        The Apache's core Basic authentication module doesn't offer a
        mechanism to flexibly allow users to type their name in any case.

Solution:

        This module will re-write the Basic authorization header that comes
        from clients so that no matter how the user typed his login name,
        it will be recognized as all upper case letters or as all lower
        case letters.

        It would have been possible to hack the Apache's core mod_auth_basic
        module to achieve this behavior but with the pain to have a non
        standard configuration and the need to recompile Apache at each new
        version. Doing this with a module makes it totally independant from
        standard installation.

Configuration:

        Version 0.1 only has one configuration parameter:
        AuthForceCase Upper|Lower|Off

        Setting AuthForceCase to Upper will let you configure all usernames
        in uppercase letters despite of how the users types in their login
        names. In the example below, the user can type John, JOHN, john,
        JoHn ... and the authentication will work OK.

        Setting AuthForceCase to Lower will let you configure all usernames
        in lowercase letters despite of how the users types in their login
        names.

        Setting AuthForceCase to Off could be usefull to switch off the
        feature in a sub-directory of a directory where it was Upper or Lower.

Example:

        To configure a directory to use the login force case, you will need
        to put something like this in your httpd.conf:

        <Location /path/to/resource>
           AuthName YourAuthName
           AuthType Basic
           AuthForceCase Upper
           require user JOHN
        </Location>

Contents:

        README      - this file
        INSTALL     - installation instructions
        makefile    - the makefile
        mod_auth_force_case.c - source for the module
        mod_auth_force_case.html - This file in HTML format

Distribution:

        This software is distributed under the GNU License (GPL).
        You may redistribute or modify it under this license - and
        as it says you must include the author's name and copyright.

        No warranty is implied or expressed.

        If you find this helpful, good. If you find it a godsend you
        need to get out more. May be to buy me a beer or send me a
        postcard.