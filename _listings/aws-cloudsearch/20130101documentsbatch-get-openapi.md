---
swagger: "2.0"
x-collection-name: AWS CloudSearch
x-complete: 0
info:
  title: AWS CloudSearch Search Documents
  version: 1.0.0
  description: You use the document service API to add, replace, or delete documents
    in your Amazon CloudSearch domain. For more information managing the documents
    in your search domain, see Uploading Data to an Amazon CloudSearch Domain.
schemes:
- http
produces:
- application/json
consumes:
- application/json
paths:
  /2013-01-01/documents/batch:
    get:
      summary: Search Documents
      description: You use the document service API to add, replace, or delete documents
        in your Amazon CloudSearch domain. For more information managing the documents
        in your search domain, see Uploading Data to an Amazon CloudSearch Domain.
      operationId: search
      x-api-path-slug: 20130101documentsbatch-get
      parameters:
      - in: body
        name: fields
        description: A collection of one or more field_name properties that define
          the fields the document contains
        schema:
          $ref: '#/definitions/holder'
      - in: body
        name: field_name
        description: Specifies a field within the document being added
        schema:
          $ref: '#/definitions/holder'
      - in: body
        name: id
        description: An alphanumeric string
        schema:
          $ref: '#/definitions/holder'
      - in: body
        name: type
        description: The operation type, add or delete
        schema:
          $ref: '#/definitions/holder'
      responses:
        200:
          description: OK
      tags:
      - Search
  /?Action=IndexDocuments:
    get:
      summary: Index Documents
      description: Tells the search domain to start indexing its documents using the
        latest indexing options.
      operationId: IndexDocuments
      x-api-path-slug: actionindexdocuments-get
      parameters:
      - in: query
        name: DomainName
        description: A string that represents the name of a domain
        type: string
      responses:
        200:
          description: OK
      tags:
      - Index Documents
x-streamrank:
  polling_total_time_average: 0
  polling_size_download_average: 0
  streaming_total_time_average: 0
  streaming_size_download_average: 0
  change_yes: 0
  change_no: 0
  time_percentage: 0
  size_percentage: 0
  change_percentage: 0
  last_run: ""
  days_run: 0
  minute_run: 0
---