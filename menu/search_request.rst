Search Request
======================

Web Service URL
-------------------

Send a GET/POST request to the following URL:

**http://servicedomain/acx/api/register/search.action**



Service Authentication
------------------------

To access the service the user need to be authenticated.

The request must be sent using the following header field::

	Authorization: Basic QWxhZGRpbjpvcGVuIHNlc2FtZQ==

The Authorization field is constructed as follows:

- The username and password are combined with a single colon.
- The resulting string is encoded using Base64.
- The authorization method and a space i.e. "Basic " is then put before the encoded string.

.. note:: For a user ``Aladdin`` having password ``open sesame`` the combined string would be:
   ``Aladdin`` + ``:`` + ``open sesame`` 
   and then encoded using Base64 the result will be ``QWxhZGRpbjpvcGVuIHNlc2FtZQ==``.

An example of request header with Basic Authentication:

.. code-block:: none
    :linenos:
    :emphasize-lines: 5

    POST /acx/api/register/search.action HTTP/1.1
    ...
    Origin: http://localhost:8003
    User-Agent: Mozilla/5.0 (Windows NT 6.1; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/53.0.2785.143 Safari/537.36
    Authorization: Basic ZGNvbnRyb2xsZXI6QXV0aDNudDFj
    Content-Type: application/x-www-form-urlencoded
    Referer: http://localhost:8003/acx/index.jsp
    ...

---------------




Required Request Parameters
------------------------------

login_type
    Must contain the string ``aconex`` required for authentication.

project
    The aconex project ID where to search the documents (you can find the ID of the project using the web service UI).

report_date (format: ``yyyy-MM-dd``)
    Report Date is required in order to calculate some of the date values to retrieve.
    If the report_date is not sent, these values will be null.


Optional Parameters
----------------------------

show_all
	Show all the revisions/version of one Document

paged
	The result will be limited in size to ``200`` items per request and the parameter ``page`` can be used to go though all the result items.

page (default: ``1``)
	Define the page number to retrieve incase the ``paged`` parameter is used.

docno
	Search a document by his document number. Is possible to search part of the number appending the suffix ``*``. 

trackingid
	Search a document by his tracking id.

status
	Search a document by his status.

type
	Search a document by his type.

revision
    Search a document by his revision.

from (format: ``yyyy-MM-dd``)
	Search documents created or modified starting from this date.

to (format: ``yyyy-MM-dd``)
	Search documents created or modified until this date.

output (default: ``json``)
	Define the type of response you will receive. You can choose between ``xml`` or ``json`` or ``excel`` response type.

with_file
    The document's file is downloaded on the server and a link is provided in order to download it.
    A new field named ``fileLink`` will contains the link to use to download the file.


.. important:: If ``with_file`` parameter is sent, the result will be limited to ``200`` documents to prevent too many requests to the Aconex server,
    and reduce server workload. 

.. note:: There is a limit to ``1000`` items if the ``paged`` parameter is not used for the same reason stated above.

HTTP Request Examples
^^^^^^^^^^^^^^^^^^^^^^^^^

Retrieve all the documents registered for the selected project (json response):

.. code-block:: bash

    $ curl \
    --data "login_type=aconex&project=1879048452&report_date=20161027" \
    --user username:password \
    http://dev.sangah.com:8063/acx/api/register/search.action

Retrieve all the documents and the response is in xml format:

.. code-block:: bash

    $ curl \
    --data "login_type=aconex&project=1879048452&report_date=20161027&output=xml" \
    --user username:password \
    http://dev.sangah.com:8063/acx/api/register/search.action

Retrieve all the documents and the file associated in xml format:

.. code-block:: bash

    $ curl \
    --data "login_type=aconex&project=1879048452&report_date=20161027&output=xml&with_file" \
    --user username:password \
    http://dev.sangah.com:8063/acx/api/register/search.action

Retrieve the second page of the pagined result (50 documents per page):

.. code-block:: bash

    $ curl \
    --data "login_type=aconex&project=1879048452&report_date=20161027&output=xml&paged&page=2" \
    --user username:password \
    http://dev.sangah.com:8063/acx/api/register/search.action

Retrieve all the revisions of the document having number D134:

.. code-block:: bash

    $ curl \
    --data "login_type=aconex&project=1879048452&report_date=20161027&output=xml&docno=D134&show_all" \
    --user username:password \
    http://dev.sangah.com:8063/acx/api/register/search.action

.. note:: The samples below make use of ``curl`` command on linux, and they should be translated according to the language you want to use.

.. note:: For **.NET** users, reference and examples about sending requests through .NET applications 
   are availables at the following websites: 
   
   * https://msdn.microsoft.com/en-us/library/debx8sh9(v=vs.110).aspx
   * https://msdn.microsoft.com/en-us/library/system.net.httpwebrequest(v=vs.110).aspx
   * https://msdn.microsoft.com/en-us/library/system.net.httpwebrequest.headers(v=vs.110).aspx
   * https://msdn.microsoft.com/en-us/library/system.web.httprequest.inputstream.aspx
   * https://msdn.microsoft.com/en-us/library/system.web.script.serialization.javascriptserializer.aspx

Response Type
---------------

JSON Output
^^^^^^^^^^^^^^

If the response is in ``json`` the result might be similar to the response below:

.. code-block:: json

    {
        "result": {
            "currentPage": 1,
            "list": [
                {
                    "CPYAnswerDueDate": null,
                    "HSSJVConsolidator": "",
                    "PMCReviewCategory": "Attribute 4",
                    "VDIssuePurpose": "Construction and Piling",
                    "asBuilt": "",
                    "commentFromPMC": null,
                    "createdBy": "Majestic Builders",
                    "fileId": "aconex_file_271341877549074476.acx",
                    "fileLink": "http://localhost:8003/acx/api/download.action?fileId=aconex_file_271341877549074476.acx&fileName=aconex_logo_topnav1.gif",
                    "fileName": "aconex_logo_topnav1.gif",
                    "fileType": "gif"
                }
            ],
            "pageSize": 50,
            "totalPages": 0,
            "totalResults": 0,
            "totalResultsOnPage": 0
        }
    }


XML Output
^^^^^^^^^^^^^

If the response is in ``xml`` the result will be similar to the sample below:

.. code-block:: xml

    <?xml version="1.0" encoding="UTF-8"?>
    <Response>
        <TotalPages>1</TotalPages>
        <PageSize>50</PageSize>
        <CurrentPage>1</CurrentPage>
        <TotalResults>1</TotalResults>
        <TotalResultsOnPage>1</TotalResultsOnPage>
        <List>
            <DocDetail>
                <docSeq>271341877549074476</docSeq>
                <docNumber>D134</docNumber>
                <docType>Photograph</docType>
                <title><![CDATA[fhyjfyui]]></title>
                <revision>34</revision>
                <version>3</version>
                <modified>2016-01-27</modified>
                <fileId>aconex_file_271341877549074476.acx</fileId>
                <fileName>aconex_logo_topnav1.gif</fileName>
                <fileType>gif</fileType>
                <trackingId>271341877549073091</trackingId>
                <fileLink><![CDATA[http://localhost:8003/acx/api/download.action?fileId=aconex_file_271341877549074476.acx&fileName=aconex_logo_topnav1.gif]]></fileLink>
            </DocDetail>
        </List>
    </Response>

Excel Output
^^^^^^^^^^^^^^

If the response output is ``excel``, the response will not return the file, 
instead the result will be similar to the following:

.. code-block:: json

    {
        "link": "/Common/TemporaryFile/download.action?fileId=abb2f8-785fcf-bf7548-e370c5-23f542-d6bf2f5126981184879558725.xlsx&fileName=result.xlsx",
        "fileName": "result.xlsx",
        "fileSize": 11476,
        "contentType": "application/vnd.ms-excel"
    }

After received the json response you can request the actual excel file using the link property.

link
    Is the URL to the excel file created on the server, so you can use it for retrieving the actual file in binary format.


Error Responses
---------------------

In case the request fail for some reason, a JSON response will be sent explaining the cause of the problem::

    {
        "error": {
            "type": "java.lang.RuntimeException",
            "message": "The request parameter page_number contains an incorrect or unknown value : 2"
        }
    }


In case a date sent with the request has an invalid format::

    {
        "error": {
            "type": "java.text.ParseException",
            "message": "Unparseable date: \"20162001\""
        }
    }


In case the authentication credentials have not been sent::

    {
        "error": {
            "message": "Unauthorized operation."
        }
    }


In case a valid project id has not been sent with the request::

    {
        "error": {
            "type": "java.lang.RuntimeException",
            "message": "The request parameter projectid contains an incorrect or unknown value : null"
        }
    }


In case the credentials are not valid the authentication will fail with the following response::

    {
        "error": {
            "type": "org.springframework.security.BadCredentialsException",
            "message": "Login failed - username or password incorrect; nested exception is java.lang.RuntimeException: Login failed - username or password incorrect"
        }
    }


This is an internal Aconex error caused probably to an invalid request::

    {
        "error": {
            "type": "java.lang.RuntimeException",
            "message": "An internal error has occurred, please contact Aconex for support on this matter"
        }
    }