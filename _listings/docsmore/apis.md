---
name: Docsmore
x-slug: docsmore
description: FORM.FILL.SIGN - With Docsmore, the process of setting up a form and
  sending to users to complete or sign is simplified.  Use our platform to easily
  upload a document, specify form fields/signage, and send to users for completion.  Present
  forms to you...
image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/28946-api-docsmore-com.jpg
x-kinRank: "7"
x-alexaRank: "7238418"
tags: Documents
created: "2018-08-27"
modified: "2018-08-27"
url: https://raw.githubusercontent.com/streamdata-gallery-topics/documents/master/_listings/docsmore/apis.md
specificationVersion: "0.14"
apis:
- name: Docsmore API 2.1 - Fetch All Documents from Your Team Catalogue
  x-api-slug: apidmcatalogue-post
  description: By design, the authenticated user can only view the files that are
    either created by them or shared with them. Make sure user has at least read permission
    to view the catalogue.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/28946-api-docsmore-com.jpg
  humanURL: http://api.docsmore.com
  baseURL: https://api.docsmore.com//
  tags: SaaS, Technology, Documents, Forms
  properties:
  - type: x-postman-collection
    url: https://raw.githubusercontent.com/streamdata-gallery-topics/documents/master/_listings/docsmore/apidmcatalogue-post-postman.md
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-topics/documents/master/_listings/docsmore/apidmcatalogue-post-openapi.md
- name: Docsmore API 2.1 - Get Raw Data For A Given Document
  x-api-slug: apiclientdocsgetrawdataauthtokendocumentkey-get
  description: |-
    This API call gets you underlying raw data of the document. All you need to do is supply Auth token and Document Key as part of the call.

    Document Key can be obtained from "Document Gallery" Page and Clicking on the sub-menu of the desired document.

    As a response object, jsondata and metadata information is passed. Jsondata is basically raw data and metadata is data columns information.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/28946-api-docsmore-com.jpg
  humanURL: http://api.docsmore.com
  baseURL: https://api.docsmore.com//
  tags: SaaS, Technology, Documents, Forms
  properties:
  - type: x-postman-collection
    url: https://raw.githubusercontent.com/streamdata-gallery-topics/documents/master/_listings/docsmore/apiclientdocsgetrawdataauthtokendocumentkey-get-postman.md
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-topics/documents/master/_listings/docsmore/apiclientdocsgetrawdataauthtokendocumentkey-get-openapi.md
- name: Docsmore API 2.1 - Fetch All Documents from Your Team Catalogue
  x-api-slug: apidmcatalogue-post
  description: By design, the authenticated user can only view the files that are
    either created by them or shared with them. Make sure user has at least read permission
    to view the catalogue.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/28946-api-docsmore-com.jpg
  humanURL: http://api.docsmore.com
  baseURL: https://api.docsmore.com//
  tags: SaaS, Technology, Documents, Forms
  properties:
  - type: x-postman-collection
    url: https://raw.githubusercontent.com/streamdata-gallery-topics/documents/master/_listings/docsmore/apidmcatalogue-post-postman.md
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-topics/documents/master/_listings/docsmore/apidmcatalogue-post-openapi.md
- name: Docsmore API 2.1 - Fetch Single Document
  x-api-slug: apidmcatalogueid-post
  description: Fetch single document.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/28946-api-docsmore-com.jpg
  humanURL: http://api.docsmore.com
  baseURL: https://api.docsmore.com//
  tags: SaaS, Technology, Documents, Forms
  properties:
  - type: x-postman-collection
    url: https://raw.githubusercontent.com/streamdata-gallery-topics/documents/master/_listings/docsmore/apidmcatalogueid-post-postman.md
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-topics/documents/master/_listings/docsmore/apidmcatalogueid-post-openapi.md
- name: Docsmore API 2.1 - Get All Document Flows
  x-api-slug: apidocflowgetdocflows-get
  description: Get all document flows.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/28946-api-docsmore-com.jpg
  humanURL: http://api.docsmore.com
  baseURL: https://api.docsmore.com//
  tags: SaaS, Technology, Documents, Forms
  properties:
  - type: x-postman-collection
    url: https://raw.githubusercontent.com/streamdata-gallery-topics/documents/master/_listings/docsmore/apidocflowgetdocflows-get-postman.md
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-topics/documents/master/_listings/docsmore/apidocflowgetdocflows-get-openapi.md
- name: Docsmore API 2.1 - Get Workflow Link For Flow Track
  x-api-slug: apidocflowtracksflowtrackviaapi-post
  description: |-
    In Docsmore space, Flow Track means all the client documents generated using one of the Document Flow. In other words, it is an instance of Document FLow. The other thing to notice here is payload information is remarkably similar to general "Workflow" of a Single Document.

    When you initiate this API call, you are basically setting up a new instance of Workflow and in turn getting workflow link of the starting document in the workflow.

    If "flowtrackid" value is "new", then new flowtrack will be created. If flowtrackid has a value of actual flowtrackid then link will be provided to access read-only view of document flowtrack
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/28946-api-docsmore-com.jpg
  humanURL: http://api.docsmore.com
  baseURL: https://api.docsmore.com//
  tags: SaaS, Technology, Documents, Forms
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-topics/documents/master/_listings/docsmore/apidocflowtracksflowtrackviaapi-post-openapi.md
- name: Docsmore API 2.1 - Get List of Client Documents By Document ID
  x-api-slug: getclientdocs-post
  description: In order to export as PDf, you will need to have client document ID
    available for that specific document you are looking to download.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/28946-api-docsmore-com.jpg
  humanURL: http://api.docsmore.com
  baseURL: https://api.docsmore.com//
  tags: SaaS, Technology, Documents, Forms
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-topics/documents/master/_listings/docsmore/getclientdocs-post-openapi.md
- name: Docsmore API 2.1 - Get List of Client Documents By Document ID
  x-api-slug: getclientdocs-post
  description: In order to export as PDf, you will need to have client document ID
    available for that specific document you are looking to download.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/28946-api-docsmore-com.jpg
  humanURL: http://api.docsmore.com
  baseURL: https://api.docsmore.com//
  tags: SaaS, Technology, Documents, Forms
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-topics/documents/master/_listings/docsmore/getclientdocs-post-openapi.md
- name: Docsmore API 2.1 - Get Raw Data For A Given Document
  x-api-slug: apiclientdocsgetrawdataauthtokendocumentkey-get
  description: |-
    This API call gets you underlying raw data of the document. All you need to do is supply Auth token and Document Key as part of the call.

    Document Key can be obtained from "Document Gallery" Page and Clicking on the sub-menu of the desired document.

    As a response object, jsondata and metadata information is passed. Jsondata is basically raw data and metadata is data columns information.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/28946-api-docsmore-com.jpg
  humanURL: http://api.docsmore.com
  baseURL: https://api.docsmore.com//
  tags: SaaS, Technology, Documents, Forms
  properties:
  - type: x-postman-collection
    url: https://raw.githubusercontent.com/streamdata-gallery-topics/documents/master/_listings/docsmore/apiclientdocsgetrawdataauthtokendocumentkey-get-postman.md
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-topics/documents/master/_listings/docsmore/apiclientdocsgetrawdataauthtokendocumentkey-get-openapi.md
- name: Docsmore API 2.1 - Get All Document Flows
  x-api-slug: apidocflowgetdocflows-get
  description: Get all document flows.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/28946-api-docsmore-com.jpg
  humanURL: http://api.docsmore.com
  baseURL: https://api.docsmore.com//
  tags: SaaS, Technology, Documents, Forms
  properties:
  - type: x-postman-collection
    url: https://raw.githubusercontent.com/streamdata-gallery-topics/documents/master/_listings/docsmore/apidocflowgetdocflows-get-postman.md
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-topics/documents/master/_listings/docsmore/apidocflowgetdocflows-get-openapi.md
- name: Docsmore API 2.1 - Fetch Single Document
  x-api-slug: apidmcatalogueid-post
  description: Fetch single document.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/28946-api-docsmore-com.jpg
  humanURL: http://api.docsmore.com
  baseURL: https://api.docsmore.com//
  tags: SaaS, Technology, Documents, Forms
  properties:
  - type: x-postman-collection
    url: https://raw.githubusercontent.com/streamdata-gallery-topics/documents/master/_listings/docsmore/apidmcatalogueid-post-postman.md
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-topics/documents/master/_listings/docsmore/apidmcatalogueid-post-openapi.md
x-common:
- type: x-api-gallery
  url: http://digitalocean.api.gallery.streamdata.io
- type: x-email
  url: contact@docsmore.com
- type: x-twitter
  url: https://twitter.com/docsmore
- type: x-website
  url: http://api.docsmore.com
include: []
maintainers:
- FN: Kin Lane
  x-twitter: apievangelist
  email: info@apievangelist.com
---