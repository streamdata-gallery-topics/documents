---
swagger: "2.0"
x-collection-name: Dezrez
x-complete: 0
info:
  title: Dezrez Get a list of documents belonging to a role
  version: 1.0.0
  description: Get a list of documents belonging to a role.
host: api.dezrez.com
basePath: /
schemes:
- http
produces:
- application/json
consumes:
- application/json
paths:
  /api/Document:
    get:
      summary: Get documents by their ids
      description: Get documents by their ids.
      operationId: Document_GetByids
      x-api-path-slug: apidocument-get
      parameters:
      - in: query
        name: ids
      - in: header
        name: Rezi-Api-Version
        description: Specifies which version of the API to call
      responses:
        200:
          description: OK
      tags:
      - Documents
      - By
      - Their
      - Ids
  /api/group/{id}/documents:
    get:
      summary: Get a list of documents belonging to a group
      description: Get a list of documents belonging to a group.
      operationId: Group_DocumentsByidBysubTypesBypageSizeBypageNumberBytypeByorderDesc
      x-api-path-slug: apigroupiddocuments-get
      parameters:
      - in: path
        name: id
        description: The id of the group to get the documents for
      - in: query
        name: orderDesc
        description: Order by created date descending (true by default)
      - in: query
        name: pageNumber
      - in: query
        name: pageSize
      - in: header
        name: Rezi-Api-Version
        description: Specifies which version of the API to call
      - in: query
        name: subTypes
      - in: query
        name: type
      responses:
        200:
          description: OK
      tags:
      - List
      - Of
      - Documents
      - Belonging
      - To
      - Group
  /api/group/{id}/offers/made:
    get:
      summary: Get a list of documents belonging to a group
      description: Get a list of documents belonging to a group.
      operationId: Group_OffersMadeByidBypageSizeBypageNumber
      x-api-path-slug: apigroupidoffersmade-get
      parameters:
      - in: path
        name: id
        description: The id of the group to get the documents for
      - in: query
        name: pageNumber
      - in: query
        name: pageSize
      - in: header
        name: Rezi-Api-Version
        description: Specifies which version of the API to call
      responses:
        200:
          description: OK
      tags:
      - List
      - Of
      - Documents
      - Belonging
      - To
      - Group
  /api/group/{id}/offers/received:
    get:
      summary: Get a list of documents belonging to a group
      description: Get a list of documents belonging to a group.
      operationId: Group_OffersReceivedByidBypageSizeBypageNumber
      x-api-path-slug: apigroupidoffersreceived-get
      parameters:
      - in: path
        name: id
        description: The id of the group to get the documents for
      - in: query
        name: pageNumber
      - in: query
        name: pageSize
      - in: header
        name: Rezi-Api-Version
        description: Specifies which version of the API to call
      responses:
        200:
          description: OK
      tags:
      - List
      - Of
      - Documents
      - Belonging
      - To
      - Group
  /api/property/{id}/documents:
    get:
      summary: Get the documents of a property by the property Id
      description: Get the documents of a property by the property id.
      operationId: Property_DocumentsByidBysubTypesBypageSizeBypageNumberBytype
      x-api-path-slug: apipropertyiddocuments-get
      parameters:
      - in: path
        name: id
        description: The id of the property to get the documents for
      - in: query
        name: pageNumber
      - in: query
        name: pageSize
      - in: header
        name: Rezi-Api-Version
        description: Specifies which version of the API to call
      - in: query
        name: subTypes
      - in: query
        name: type
      responses:
        200:
          description: OK
      tags:
      - Documents
      - Of
      - Property
      - By
      - Property
      - Id
  /api/role/{id}/documents:
    get:
      summary: Get a list of documents belonging to a role
      description: Get a list of documents belonging to a role.
      operationId: Role_DocumentsByidBysubTypesBypageSizeBypageNumberBytypeByorderDesc
      x-api-path-slug: apiroleiddocuments-get
      parameters:
      - in: path
        name: id
        description: The id of the role to get the documents for
      - in: query
        name: orderDesc
      - in: query
        name: pageNumber
      - in: query
        name: pageSize
      - in: header
        name: Rezi-Api-Version
        description: Specifies which version of the API to call
      - in: query
        name: subTypes
      - in: query
        name: type
      responses:
        200:
          description: OK
      tags:
      - List
      - Of
      - Documents
      - Belonging
      - To
      - Role
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