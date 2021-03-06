# DocumentDBPSModule
PowerShell Module for Azure Document DB
Author: Jason van der Paal
http://vanderpaal.com.au

TOPIC
    about_DocumentDB

SHORT DESCRIPTION
 This module will hep with looking up DBs, Collections and to query documents in Azure DocumentDB as well as create/update them.

LONG DESCRIPTION
 The purpose of this module is to provide a few simple commands to allow you to quickly query or upload/update documents in Azure DocumentDB.
 It is recommended to plan how to structure your documents as at the wirting of this module Azure DocumentDB does not support field updates so instead an entire document must be senmt for each update.
 The module utilises the native RestAPI

EXAMPLES
 The following will list all the databases in an account:
 Get-DocDBDatabases -accountName "TestDocDB" -key "23123-df233eas-34was3-aw3a3"

 The following will list allt hec ollections within the specified DB:
 Get-DocDBCollections -DBName "UserDetails" -accountName "TestDocDB" -key "23123-df233eas-34was3-aw3a3"

 The following will pass a JSON formatted query string and return the result, this is cleaned by default to return on the necesary output, the -NoClean switch will return the raw output.
 New-DocDBQuery -collection "DeletedUsers" -DBName "UserDetails" -accountName "TestDocDB" -key "23123-df233eas-34was3-aw3a3" -JSONQuery $JsonStringQuery

 The following will either create a new or update an existing document depending on wether the ID already exists, you can pass a JSON formatted document (with -JSONdocument) 
 or a powershell object that will attempt to be converted to JSON (with -PSdocument):
 Set-DocDBDocument -collection "DeletedUsers" -DBName "UserDetails" -accountName "TestDocDB" -key "23123-df233eas-34was3-aw3a3" -JSONdocument $JsonStringDocument
 Set-DocDBDocument -collection "DeletedUsers" -DBName "UserDetails" -accountName "TestDocDB" -key "23123-df233eas-34was3-aw3a3" -PSdocument $PSCustomObject

KEYWORDS
 DocumentDB, Collection, Database

