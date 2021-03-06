---
swagger: "2.0"
info:
  title: AWS WorkDocs API Get Document Path
  version: 1.0.0
  description: Retrieves the path information (the hierarchy from the root folder)
    for the requested document.
schemes:
- http
produces:
- application/json
consumes:
- application/json
paths:
  /?Action=GetDocumentPath:
    get:
      summary: ' Get Document Path '
      description: Retrieves the path information (the hierarchy from the root folder)
        for the requested document
      operationId: getDocumentPath
      parameters:
      - in: query
        name: DocumentId
        description: The ID of the document
        type: string
      - in: query
        name: Fields
        description: A comma-separated list of values
        type: string
      - in: query
        name: Limit
        description: The maximum number of levels in the hierarchy to return
        type: string
      responses:
        200:
          description: OK
      tags:
      - documents
definitions: []
x-collection-name: AWS WorkDocs
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