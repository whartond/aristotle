=========
Aristotle
=========

Aristotle is a simple Python program that allows for the filtering of
Suricata and Snort rulesets based on interpreted key-value pairs present
in the metadata keyword within each rule. It can be run as a standalone
script or utilized as a module.

Documentation
=============

`<https://aristotle-py.readthedocs.io/>`__

Application Overview
====================

Aristotle takes in a ruleset and can provide statistics on the included
metadata keys. If a filter string is provided, it will also be applied
against the ruleset and the filtered ruleset outputted.

Aristotle is compatible with Python 2.7 and Python 3.x.

+------------------------------------------------------------------------------------+
| In order for Aristotle to be useful, it must be provided a ruleset that            |
| has rules with the metadata keyword populated with appropriate key-value           |
| pairs. Aristotle assumes that the provided ruleset conforms to the                 |
| `BETTER Schema <https://better-schema.readthedocs.io/>`__.                         |
+------------------------------------------------------------------------------------+

Setup
=====

Install dependencies:

``pip install -r requirements.txt``

Or if using as a module:

``pip install aristotle``

And refer to `Aristotle as a Module <https://aristotle-py.readthedocs.io/en/latest/module.html>`__.

Usage
=====

.. code:: text

    usage: aristotle.py [-h] -r RULES [-f METADATA_FILTER] [--summary] [-o OUTFILE] [-s [STATS [STATS ...]]] [-i] [-n] [-e] [-t] [-g] [-m] [-q] [-d]

    Filter Suricata and Snort rulesets based on metadata keyword values.

    optional arguments:
      -h, --help            show this help message and exit
      -r RULES, --rules RULES, --ruleset RULES
                            path to a rules file, a directory containing '.rules' file(s), or string containing the ruleset
      -f METADATA_FILTER, --filter METADATA_FILTER
                            Boolean filter string or path to a file containing it
      --summary             output a summary of the filtered ruleset to stdout; if an output file is given, the full, filtered ruleset will still be written to it.
      -o OUTFILE, --output OUTFILE
                            output file to write filtered ruleset to
      -s [STATS [STATS ...]], --stats [STATS [STATS ...]]
                            display ruleset statistics about specified key(s). If no key(s) supplied, then summary statistics for all keys will be displayed.
      -i, --include-disabled
                            include (effectively enable) disabled rules when applying the filter
      -n, --normalize, --better, --iso8601
                            try to convert date and cve related metadata values to conform to the BETTER schema for filtering and statistics. Dates are normalized to the format YYY>
                            MM-DD and CVEs to YYYY-<num>.
      -e, --enhance         enhance metadata by adding additional key-value pairs based on the rules.
      -t, --ignore-classtype, --ignore-classtype-keyword
                            don't ignore_filenameincorporate the 'classtype' keyword and value from the rule into the metadata structure for filtering and reporting.
      -g, --ignore-filename
                            don't incorporate the filename of the rules file into the metadata structure for filtering and reporting.
      -m, --modify-metadata
                           modify the rule metadata keyword value on output to contain the internally tracked and normalized metadata data.
      -q, --quiet, --suppress_warnings
                            quiet; suppress warning logging
      -d, --debug           turn on debug logging

    A filter string defines the desired outcome based on Boolean logic, and uses
    the metadata key-value pairs as values in a (concrete) Boolean algebra.
    The key-value pair specifications must be surrounded by double quotes.
    Example:

    python3 aristotle/aristotle.py -r examples/example.rules --summary -n
    -f '(("priority high" AND "malware <ALL>") AND "created_at >= 2018-01-01")
    AND NOT ("protocols smtp" OR "protocols pop" OR "protocols imap") OR "sid 80181444"'

License
=======

Aristotle is licensed under the `Apache License, Version 2.0 <https://github.com/secureworks/aristotle/blob/master/LICENSE>`__.

Authors
=======

-  David Wharton
