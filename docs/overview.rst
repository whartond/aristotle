Application Overview
====================

Aristotle takes in a ruleset and can provide statistics on the included
metadata keys. If a filter string is provided, it will also be applied
against the ruleset and the filtered ruleset outputted.

.. note::
    By default Aristotle does *not* modify the contents of rules, it
    simply includes or excludes rules based on the given Boolean filter string.
    However, if the :ref:`Update Metadata option <target Update Metadata>` is set, then
    the ``metadata`` keyword value will be replaced as documented.

Aristotle is compatible with Python 2.7 and Python 3.x.

Background
==========

Suricata and Snort support the ``metadata`` keyword that allows for
non-functional (in terms of detection), arbitrary information to be
included in a rule. By defining key-value pairs and including them in
the metadata keyword, ruleset providers can embed rich teleological and
taxonomic information. This information can be used to filter a ruleset
– essentially enabling and disabling rules in a ruleset based on the
metadata key-value pairs.  Aristotle allows for the easy leveraging of
the metadata key-value pairs to "slice-and-dice" Suricata and Snort
rulesets that implement metadata key-value pairs.

Metadata Key-Value Pairs
========================

.. important:: In order for Aristotle to be useful, it must be provided a ruleset that
    has rules with the metadata keyword populated with appropriate key-value
    pairs. Aristotle assumes that the provided ruleset conforms to the
    `BETTER Schema <https://better-schema.readthedocs.io/>`__.

