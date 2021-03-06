---
swagger: "2.0"
x-collection-name: SAP
x-complete: 0
info:
  title: SAP Manufacturing Network Partner APIs Retrieves a document
  description: Retrieves the information of a document by its ID.
  version: 1.0.0
host: hostname
basePath: /dim/api
schemes:
- http
produces:
- application/json
consumes:
- application/json
paths:
  /collaborationRooms/{collaborationRoomId}/documents:
    get:
      summary: Retrieves documents in a collaboration room
      description: Retrieves the information of all documents in a collaboration room,
        such as design files and specifications.
      operationId: retrieves-the-information-of-all-documents-in-a-collaboration-room-such-as-design-files-and-specific
      x-api-path-slug: collaborationroomscollaborationroomiddocuments-get
      parameters:
      - in: path
        name: collaborationRoomId
        description: The ID of a collaboration room
      responses:
        200:
          description: Successful response
      tags:
      - Retrieves
      - Documents
      - In
      - Collaboration
      - Room
  /collaborationRooms/{collaborationRoomId}/documents/{fileId}:
    get:
      summary: Retrieves a document
      description: Retrieves the information of a document by its ID.
      operationId: retrieves-the-information-of-a-document-by-its-id
      x-api-path-slug: collaborationroomscollaborationroomiddocumentsfileid-get
      parameters:
      - in: path
        name: collaborationRoomId
        description: The ID of a collaboration room
      - in: path
        name: fileId
        description: The ID of a file
      responses:
        200:
          description: Successful response
      tags:
      - Retrieves
      - Document
    delete:
      summary: Deletes a document
      description: "Deletes a document.  \nThe login technical user must be the one
        who uploaded the document."
      operationId: deletes-a-document--the-login-technical-user-must-be-the-one-who-uploaded-the-document
      x-api-path-slug: collaborationroomscollaborationroomiddocumentsfileid-delete
      parameters:
      - in: path
        name: collaborationRoomId
        description: The ID of a collaboration room
      - in: path
        name: fileId
        description: The ID of a file
      responses:
        200:
          description: Successful response
      tags:
      - S
      - Document
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