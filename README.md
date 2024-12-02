OpenRefine extension for Google Sheets and Google Drive
=======================================================

by Tom Morris <tfmorris@gmail.com> and other OpenRefine contributors

This extension provides OpenRefine with the ability to read Google spreadsheets
directly so you don't have to export them as CSV files first. It also lets you export
OpenRefine projects to Google Drive.

Download it from [the Releases pages](https://github.com/OpenRefine/refine-gdata-extension/releases).

Unpack the contents of this archive (jar, zip, etc) into the extensions folder
of OpenRefine.

## Steps to obtain OAuth credentials:

To obtain data from [Google Drive](https://www.google.com/drive/) or [Google Sheets](https://www.google.com/sheets/about/) for OpenRefine requires OAuth credentials. For obtaining the OAuth credentials follow these steps:

* Go to the [Google API Console](https://console.developers.google.com/)
* Click on **Create Project**.
* Pick a project name such as **My OpenRefine Dev Project**.
* Fill the required fields.
* Hit **Create** for creating the project. 
* Pick **Enable APIs and Services**.

**Enable the following services:**
* Google Sheets API
* Google Drive API

**OAuth consent screen pane:**
- Go to the **OAuth consent screen pane**.
- As user type, pick **External**. 
- Fill the form for the OAuth credentials. 
- For the OAuth scopes, pick ../auth/drive/ which will give you write access to your Google Drive.
- For the domain (and other URLs), you can pick anything (since the localhost will be allowed anyway). 
- Hit **Save** to save the consent screen.

**Credentials pane:**
- Go to the **Credentials pane**.
- Create new OAuth credentials, adding as allowed origin `http://127.0.0.1:3333`, and as allowed callback URL: `http://127.0.0.1:3333/extension/gdata/authorized`
- Copy your **client id**, **client secret key**
- Go back to the **Credentials Pane**, and create a new **API key**. Copy its value.
- Save them in a file outside your git clone of OpenRefine.
- Add Java property definitions for your client id and secret key by adding `-Dext.gdata.clientid=<yourid>` `-Dext.gdata.clientsecret=...` `-Dext.gdata.apikey=...` to your JVM arguments. This can be done by editing the `refine.ini` file at the root of the code base.

# Usage

After installing the extension and restarting OpenRefine, you'll be able to create a project from a Google Sheets document alongside other import sources.

If you end up with a project full of HTML tags and an RSS feed, the extension
isn't installed properly.  A properly installed extension should have an About
page available at http://127.0.0.1:3333/extension/gdata/ (the trailing
slash is significant).

