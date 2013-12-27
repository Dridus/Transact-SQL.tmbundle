Transact-SQL.tmbundle
=====================

This is a separate syntax mode for Sublime Text (and maybe TextMate?) to support Transact-SQL specifically.

The pre-packed SQL mode that comes with ST doesn't do a very good job with Transact-SQL, especially when you get into some of the gnarlier or more unique syntax thereof, such as `[Quoted Identifiers]` or `#temporary_tables`.

(Un)supported Syntax
====================

It is (as all such things are, probably) a work in progress. It supports great swaths of common SQL but probably omits many things.

I intend to actively maintain it, so if you find a problem or missing syntax, let me know and I'll try to work it in. Pull requests appreciated.

What is supported so far:
- all the various identifier forms in SQL Server (even `[server]."database".schema.[lulz]`)
- most operators
- many built-in forms that are Weird, like `CAST`, `CONVERT`, and `EXISTS`
- sub-selects, sub-sub-selects, selects inside `EXISTS`, scalar selects, and so on
- function application forms, including the oddball `UPDATE blah SET foo.modify(...)` (that example is for XML)
- #tables!
- @tables!
- `OPTION (...)` and `WITH (...)` clauses
- `BEGIN TRY` / `BEGIN CATCH`
- `GOTO` and labels
- `CROSS APPLY`, `CROSS JOIN`, all `OUTER JOIN`s

What's known missing:
- `ALTER TABLE`
- `CREATE INDEX` and `DROP INDEX`
- `OVER` and `WITH ROLLUP`

Again, send me a message if there's a gap in the syntax that you'd like closed.

How to use
==========

I don't know how to configure Sublime to prefer this mode for `.sql` files over the built-in one, other than to override the built-in one with a dummy version.

To do that:

1. Create a `SQL` directory in your `Packages` directory, located on OSX in `~/Library/Application Support/Sublime Text 3/Packages` and on Windows in `C:\Users\you\AppData\Roaming\Sublime Text 3\Packages`
2. Create a file `SQL.tmLanguage` in that directory with:

    <?xml version="1.0" encoding="UTF-8"?> <!DOCTYPE plist PUBLIC "-//Apple Computer//DTD PLIST 1.0//EN""http://www.apple.com/DTDs/PropertyList-1.0.dtd">
    <plist version="1.0">
    <dict>
        <key>fileTypes</key>
        <array><!--
            <string>sql</string>
            <string>ddl</string>
            <string>dml</string>
      --></array>
        <key>foldingStartMarker</key>
        <string>\s*\(\s*$</string>
        <key>foldingStopMarker</key>
        <string>^\s*\)</string>
        <key>keyEquivalent</key>
        <string>^~S</string>
        <key>name</key>
        <string>SQL</string>
        <key>patterns</key>
        <array>
          </array>
          <key>repository</key>
          <dict>
          </dict>
        <key>scopeName</key>
        <string>source.sql</string>
        <key>uuid</key>
        <string>C49120AC-6ECC-11D9-ACC8-000D93589AF6</string>
    </dict>
    </plist>

3. Close and re-open any files.

Closing
=======

Share and enjoy.

-Ross