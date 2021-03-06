---
swagger: "2.0"
x-collection-name: Box
x-complete: 0
info:
  title: Box Delete Comment
  description: Permanently deletes a comment.
  version: 1.0.0
host: api.box.com
basePath: /2.0
schemes:
- http
produces:
- application/json
consumes:
- application/json
paths:
  /files/content:
    options:
      summary: File upload preflight check
      description: The Pre-flight check API will verify that a file will be accepted
        by Box before you send all the bytes over the wire.
      operationId: fileUploadPreflightCheck
      x-api-path-slug: filescontent-options
      parameters:
      - in: body
        name: body
        schema:
          $ref: '#/definitions/holder'
      responses:
        200:
          description: OK
      tags:
      - Documents
      - Files
      - Content
  /files/{FILE_ID}:
    get:
      summary: Get File's Info, Get Embed Link
      description: Used to retrieve the metadata about a file.
      operationId: getFile
      x-api-path-slug: filesfile-id-get
      parameters:
      - in: query
        name: fields
        description: Attribute(s) to include in the response
      - in: path
        name: FILE_ID
      responses:
        200:
          description: OK
      tags:
      - Documents
      - Files
      - File
    put:
      summary: Update File Info, Lock and Unlock, Create Shared Link
      description: |-
        Used to update individual or multiple fields in the file object, including renaming the file, changing its description, and creating a shared link for the file. To move a file, change the ID of its parent folder. An optional If-Match header can be included to prevent race conditions.

        To lock and unlock files, you execute a PUT operation on the /files/{file id} endpoint and set or clear the lock properties on the file.

        Used to create a shared link for this particular file. Please see here for more information on the permissions available for shared links. In order to get default shared link status, set it to an empty access level, i.e. {"shared_link": {}}. In order to disable a shared link, send this same type of PUT request with the value of shared_link set to null, i.e. {"shared_link": null}
      operationId: updateFileInfo
      x-api-path-slug: filesfile-id-put
      parameters:
      - in: body
        name: body
        schema:
          $ref: '#/definitions/holder'
      - in: path
        name: FILE_ID
      - in: header
        name: If-Match
        description: The etag of the file can be included as an ???If-Match??? header
          to prevent race conditions
      responses:
        200:
          description: OK
      tags:
      - Documents
      - Files
      - File
    delete:
      summary: Delete File
      description: Discards a file to the trash. The etag of the file can be included
        as an ???If-Match??? header to prevent race conditions.
      operationId: deleteFile
      x-api-path-slug: filesfile-id-delete
      parameters:
      - in: path
        name: FILE_ID
      - in: header
        name: If-Match
        description: The etag of the file
      responses:
        200:
          description: OK
      tags:
      - Documents
      - Files
      - File
    post:
      summary: Restore Item
      description: Restores an item that has been moved to the trash. Default behavior
        is to restore the item to the folder it was in before it was moved to the
        trash. If that parent folder no longer exists or if there is now an item with
        the same name in that parent folder, the new parent folder and/or new name
        will need to be included in the request.
      operationId: restoreTrashedFile
      x-api-path-slug: filesfile-id-post
      parameters:
      - in: body
        name: body
        schema:
          $ref: '#/definitions/holder'
      - in: path
        name: FILE_ID
      responses:
        200:
          description: OK
      tags:
      - Documents
      - Files
      - File
  /files/{FILE_ID}/content:
    get:
      summary: Download File
      description: Retrieves the actual data of the file. An optional version parameter
        can be set to download a previous version of the file.
      operationId: getFileContent
      x-api-path-slug: filesfile-idcontent-get
      parameters:
      - in: header
        name: BoxApi
        description: The shared link for this item
      - in: path
        name: FILE_ID
      - in: header
        name: Range
        description: The range value in bytes
      - in: query
        name: version
        description: The ID specific version of this file to download
      responses:
        200:
          description: OK
      tags:
      - Documents
      - Files
      - File
      - ""
      - Content
  /files/{FILE_ID}/versions:
    get:
      summary: View Versions
      description: If there are previous versions of this file, this method can be
        used to retrieve information about the older versions. (Versions are only
        tracked for Box users with premium accounts.)
      operationId: getFileVersions
      x-api-path-slug: filesfile-idversions-get
      parameters:
      - in: query
        name: fields
        description: Attribute(s) to include in the response
      - in: path
        name: FILE_ID
      responses:
        200:
          description: OK
      tags:
      - Documents
      - Files
      - File
      - ""
      - Versions
  /files/{FILE_ID}/versions/current:
    post:
      summary: Promote Version
      description: If there are previous versions of this file, this method can be
        used to promote one of the older versions to the top of the stack. This actually
        mints a copy of the old version and puts it on the top of the versions stack.
        The file will have the exact same contents, the same SHA1/etag, and the same
        name as the original. Other properties such as comments do not get updated
        to their former values.
      operationId: promotoeFileVersion
      x-api-path-slug: filesfile-idversionscurrent-post
      parameters:
      - in: body
        name: body
        schema:
          $ref: '#/definitions/holder'
      - in: path
        name: FILE_ID
      responses:
        200:
          description: OK
      tags:
      - Documents
      - Files
      - File
      - ""
      - Versions
      - Current
  /files/{FILE_ID}/versions/{VERSION_ID}:
    delete:
      summary: Delete Old Version
      description: Discards a specific file version to the trash. (Depending on the
        enterprise settings for this user, the item will either be actually deleted
        from Box or moved to the trash.)
      operationId: deleteFileVersion
      x-api-path-slug: filesfile-idversionsversion-id-delete
      parameters:
      - in: path
        name: FILE_ID
      - in: header
        name: If-Match
        description: The etag of the file
      - in: path
        name: VERSION_ID
      responses:
        200:
          description: OK
      tags:
      - Documents
      - Files
      - File
      - ""
      - Versions
      - Version
  /files/{FILE_ID}/copy:
    post:
      summary: Copy File
      description: Used to create a copy of a file in another folder. The original
        version of the file will not be altered.
      operationId: copyFile
      x-api-path-slug: filesfile-idcopy-post
      parameters:
      - in: body
        name: body
        schema:
          $ref: '#/definitions/holder'
      - in: path
        name: FILE_ID
      responses:
        200:
          description: OK
      tags:
      - Documents
      - Files
      - File
      - ""
      - Copy
  /files/{FILE_ID}/thumbnail.{EXTENSION}:
    get:
      summary: Get Thumbnail
      description: Retrieves a thumbnail, or smaller image representation, of this
        file. Sizes of 32x32,64x64, 128x128, and 256x256 can be returned in the .png
        format and sizes of 32x32, 94x94, 160x160, and 320x320 can be returned in
        the .jpg format. Thumbnails can be generated for the image and video file
        formats listed here.
      operationId: getFileThumbnail
      x-api-path-slug: filesfile-idthumbnail-extension-get
      parameters:
      - in: path
        name: EXTENSION
        description: The preview format, e
      - in: path
        name: FILE_ID
      - in: query
        name: max_height
        description: The maximum height of the thumbnail
      - in: query
        name: max_width
        description: The maximum width of the thumbnail
      - in: query
        name: min_height
        description: The minimum height of the thumbnail
      - in: query
        name: min_width
        description: The minimum width of the thumbnail
      responses:
        200:
          description: OK
      tags:
      - Documents
      - Files
      - File
      - ""
      - Thumbnail.
      - Extension
  /files/{FILE_ID}/trash:
    get:
      summary: Get Trashed File
      description: Retrieves an item that has been moved to the trash.
      operationId: getTrashedFile
      x-api-path-slug: filesfile-idtrash-get
      parameters:
      - in: path
        name: FILE_ID
      responses:
        200:
          description: OK
      tags:
      - Documents
      - Files
      - File
      - ""
      - Trash
    delete:
      summary: Permanently Delete
      description: Permanently deletes an item that is in the trash. The item will
        no longer exist in Box. This action cannot be undone.
      operationId: deleteTrashedFile
      x-api-path-slug: filesfile-idtrash-delete
      parameters:
      - in: path
        name: FILE_ID
      responses:
        200:
          description: OK
      tags:
      - Documents
      - Files
      - File
      - ""
      - Trash
  /files/{FILE_ID}/comments:
    get:
      summary: Get File's Comments
      description: Retrieves the comments on a particular file, if any exist.
      operationId: getFileComments
      x-api-path-slug: filesfile-idcomments-get
      parameters:
      - in: query
        name: fields
        description: Attribute(s) to include in the response
      - in: path
        name: FILE_ID
      responses:
        200:
          description: OK
      tags:
      - Documents
      - Files
      - File
      - ""
      - Comments
  /files/{FILE_ID}/collaborations:
    get:
      summary: Get File's Collaborations
      description: Use this to get a list of all the collaborations on a file
      operationId: getFileCollaborations
      x-api-path-slug: filesfile-idcollaborations-get
      parameters:
      - in: query
        name: fields
        description: Attribute(s) to include in the response
      - in: path
        name: FILE_ID
      - in: query
        name: limit
        description: The maximum number of items to return in a page
      - in: query
        name: offset
        description: The item at which to begin the response
      responses:
        200:
          description: OK
      tags:
      - Documents
      - Files
      - File
      - ""
      - Collaborations
  /files/{FILE_ID}/tasks:
    get:
      summary: Get File's Tasks
      description: Retrieves all of the tasks for given file.
      operationId: getFileTasks
      x-api-path-slug: filesfile-idtasks-get
      parameters:
      - in: query
        name: fields
        description: Attribute(s) to include in the response
      - in: path
        name: FILE_ID
      responses:
        200:
          description: OK
      tags:
      - Documents
      - Files
      - File
      - ""
      - Tasks
  /folders:
    post:
      summary: Create Folder
      description: Used to create a new empty folder. The new folder will be created
        inside of the specified parent folder
      operationId: createFolder
      x-api-path-slug: folders-post
      parameters:
      - in: body
        name: body
        schema:
          $ref: '#/definitions/holder'
      - in: query
        name: fields
        description: Attribute(s) to include in the response
      responses:
        200:
          description: OK
      tags:
      - Documents
      - Folders
  /folders/{FOLDER_ID}:
    get:
      summary: Get Folder's Info
      description: Retrieves the full metadata about a folder, including information
        about when it was last updated as well as the files and folders contained
        in it. The root folder of a Box account is always represented by the id ???0???.
      operationId: getFolder
      x-api-path-slug: foldersfolder-id-get
      parameters:
      - in: query
        name: fields
        description: Attribute(s) to include in the response
      - in: path
        name: FOLDER_ID
      responses:
        200:
          description: OK
      tags:
      - Documents
      - Folders
      - Folder
    put:
      summary: Update Folder, Create Shared Link, Create or Delete
      description: |-
        Used to update information about the folder. To move a folder, update the ID of its parent. To enable an email address that can be used to upload files to this folder, update the folder_upload_email attribute. An optional If-Match header can be included to ensure that client only updates the folder if it knows about the latest version.

        Used to create a shared link for this particular folder. Please see here for more information on the permissions available for shared links. In order to get default shared link status, set it to an empty access level, i.e. {"shared_link": {}}. In order to disable a shared link, send this same type of PUT request with the value of shared_link set to null, i.e. {"shared_link": null}

        To add or remove an item from a collection, you do a PUT on that item and change the list of collections it belongs to. Philosophically, this is similar to the way ???move??? operations work on files and folders: you do a PUT on the item and change its parent. It???s the same idea with collections, except you???re changing which collection(s) the item belongs to instead of the folder it belongs to. Currently the only collection available is the favorites collection, and you???ll need to know it???s ID for the user that is making the API call, since every user has a different favorites collection_id.
        The Add/Remove API handling will check all ids passed in before performing any add/removal operations. If any collection ids are malformed or do not exist in the user???s account, the API call will throw a 400. Only if all of the collection ids are valid will the adds and removals be carried out.
      operationId: updateFolder
      x-api-path-slug: foldersfolder-id-put
      parameters:
      - in: body
        name: body
        schema:
          $ref: '#/definitions/holder'
      - in: query
        name: fields
        description: Attribute(s) to include in the response
      - in: path
        name: FOLDER_ID
      - in: header
        name: If-Match
        description: This is in the ???etag??? field of the folder object
      responses:
        200:
          description: OK
      tags:
      - Documents
      - Folders
      - Folder
    delete:
      summary: Delete Folder
      description: Used to delete a folder. A recursive parameter must be included
        in order to delete folders that have items inside of them. An optional If-Match
        header can be included to ensure that client only deletes the folder if it
        knows about the latest version.
      operationId: deleteFolder
      x-api-path-slug: foldersfolder-id-delete
      parameters:
      - in: path
        name: FOLDER_ID
      - in: header
        name: If-Match
        description: This is in the ???etag??? field of the folder object
      - in: query
        name: recursive
      responses:
        200:
          description: OK
      tags:
      - Documents
      - Folders
      - Folder
    post:
      summary: Restore Folder
      description: Restores an item that has been moved to the trash. Default behavior
        is to restore the item to the folder it was in before it was moved to the
        trash. If that parent folder no longer exists or if there is now an item with
        the same name in that parent folder, the new parent folder and/or new name
        will need to be included in the request.
      operationId: restoreTrashedFolder
      x-api-path-slug: foldersfolder-id-post
      parameters:
      - in: body
        name: body
        schema:
          $ref: '#/definitions/holder'
      - in: query
        name: fields
        description: Attribute(s) to include in the response
      - in: path
        name: FOLDER_ID
      responses:
        200:
          description: OK
      tags:
      - Documents
      - Folders
      - Folder
  /folders/{FOLDER_ID}/items:
    get:
      summary: Get Folder???s Items
      description: Retrieves the files and/or folders contained within this folder
        without any other metadata about the folder. Any attribute in the full files
        or folders objects can be passed in with the fields parameter to get specific
        attributes, and only those specific attributes back; otherwise, the mini format
        is returned for each item by default. Multiple attributes can be passed in
        separated by commas e.g. fields=name,created_at. Paginated results can be
        retrieved using the limit and offset parameters.
      operationId: getFolderItems
      x-api-path-slug: foldersfolder-iditems-get
      parameters:
      - in: query
        name: fields
        description: Attribute(s) to include in the response
      - in: path
        name: FOLDER_ID
      - in: query
        name: limit
        description: The maximum number of items to return in a page
      - in: query
        name: offset
        description: The offset at which to begin the response
      responses:
        200:
          description: OK
      tags:
      - Documents
      - Folders
      - Folder
      - ""
      - Items
  /folders/{FOLDER_ID}/copy:
    post:
      summary: Copy Folder
      description: Used to create a copy of a folder in another folder. The original
        version of the folder will not be altered.
      operationId: copyFolder
      x-api-path-slug: foldersfolder-idcopy-post
      parameters:
      - in: body
        name: body
        schema:
          $ref: '#/definitions/holder'
      - in: query
        name: fields
        description: Attribute(s) to include in the response
      - in: path
        name: FOLDER_ID
      responses:
        200:
          description: OK
      tags:
      - Documents
      - Folders
      - Folder
      - ""
      - Copy
  /folders/{FOLDER_ID}/collaborations:
    get:
      summary: Get Folder Collaborations
      description: Use this to get a list of all the collaborations on a folder i.e.
        all of the users that have access to that folder.
      operationId: getFolderCollaborations
      x-api-path-slug: foldersfolder-idcollaborations-get
      parameters:
      - in: query
        name: fields
        description: Attribute(s) to include in the response
      - in: path
        name: FOLDER_ID
      - in: query
        name: limit
        description: The maximum number of items to return in a page
      - in: query
        name: offset
        description: The item at which to begin the response
      responses:
        200:
          description: OK
      tags:
      - Documents
      - Folders
      - Folder
      - ""
      - Collaborations
  /folders/{FOLDER_ID}/trash:
    get:
      summary: Get Trashed Folder
      description: Retrieves an folder that has been moved to the trash.
      operationId: getTrashedFolder
      x-api-path-slug: foldersfolder-idtrash-get
      parameters:
      - in: query
        name: fields
        description: Attribute(s) to include in the response
      - in: path
        name: FOLDER_ID
      responses:
        200:
          description: OK
      tags:
      - Documents
      - Folders
      - Folder
      - ""
      - Trash
    delete:
      summary: Permanently Delete
      description: Permanently deletes an folder that is in the trash. The item will
        no longer exist in Box. This action cannot be undone.
      operationId: deleteTrashedFolder
      x-api-path-slug: foldersfolder-idtrash-delete
      parameters:
      - in: path
        name: FOLDER_ID
      responses:
        200:
          description: OK
      tags:
      - Documents
      - Folders
      - Folder
      - ""
      - Trash
  /folders/trash/items:
    get:
      summary: Get Trashed Items
      description: Retrieves the files and/or folders that have been moved to the
        trash. Any attribute in the full files or folders objects can be passed in
        with the fields parameter to get specific attributes, and only those specific
        attributes back; otherwise, the mini format is returned for each item by default.
        Multiple attributes can be passed in separated by commas e.g. fields=name,created_at.
        Paginated results can be retrieved using the limit and offset parameters.
      operationId: getTrashedItems
      x-api-path-slug: folderstrashitems-get
      parameters:
      - in: query
        name: fields
        description: Attribute(s) to include in the response
      - in: query
        name: limit
        description: The maximum number of items to return
      - in: query
        name: offset
        description: The item at which to begin the response
      responses:
        200:
          description: OK
      tags:
      - Documents
      - Folders
      - Trash
      - Items
  /files/{FILE_ID}/watermark:
    get:
      summary: Get Watermark on File
      description: Used to retrieve the watermark for a corresponding Box file.
      operationId: getFileWatermark
      x-api-path-slug: filesfile-idwatermark-get
      parameters:
      - in: path
        name: FILE_ID
      responses:
        200:
          description: OK
      tags:
      - Documents
      - Files
      - File
      - ""
      - Watermark
    put:
      summary: Apply Watermark on File
      description: Used to apply or update the watermark for a corresponding Box file.
        The endpoint accepts a JSON body describing the watermark to apply.
      operationId: updateFileWatermark
      x-api-path-slug: filesfile-idwatermark-put
      parameters:
      - in: body
        name: body
        schema:
          $ref: '#/definitions/holder'
      - in: path
        name: FILE_ID
      responses:
        200:
          description: OK
      tags:
      - Documents
      - Files
      - File
      - ""
      - Watermark
    delete:
      summary: Remove Watermark on File
      description: Used to remove the watermark for a corresponding Box file.
      operationId: deleteFileWatermark
      x-api-path-slug: filesfile-idwatermark-delete
      parameters:
      - in: path
        name: FILE_ID
      responses:
        200:
          description: OK
      tags:
      - Documents
      - Files
      - File
      - ""
      - Watermark
  /folders/{FOLDER_ID}/watermark:
    get:
      summary: Get Watermark on Folder
      description: Used to retrieve the watermark for a corresponding Box folder.
      operationId: getFolderWatermark
      x-api-path-slug: foldersfolder-idwatermark-get
      parameters:
      - in: path
        name: FOLDER_ID
      responses:
        200:
          description: OK
      tags:
      - Documents
      - Folders
      - Folder
      - ""
      - Watermark
    put:
      summary: Apply Watermark on Folder
      description: Used to apply or update the watermark for a corresponding Box folder.
        The endpoints accepts a JSON body describing the watermark to apply.
      operationId: updateFolderWatermark
      x-api-path-slug: foldersfolder-idwatermark-put
      parameters:
      - in: body
        name: body
        schema:
          $ref: '#/definitions/holder'
      - in: path
        name: FOLDER_ID
      responses:
        200:
          description: OK
      tags:
      - Documents
      - Folders
      - Folder
      - ""
      - Watermark
    delete:
      summary: Remove Watermark on Folder
      description: Used to remove the watermark for a corresponding Box Folder.
      operationId: deleteFolderWatermark
      x-api-path-slug: foldersfolder-idwatermark-delete
      parameters:
      - in: path
        name: FOLDER_ID
      responses:
        200:
          description: OK
      tags:
      - Documents
      - Folders
      - Folder
      - ""
      - Watermark
  /web_links:
    post:
      summary: Create Web Link
      description: Creates a web link object within a given folder.
      operationId: createWebLink
      x-api-path-slug: web-links-post
      parameters:
      - in: body
        name: body
        schema:
          $ref: '#/definitions/holder'
      responses:
        200:
          description: OK
      tags:
      - Documents
      - Web
      - Links
  /web_links/{WEB_LINK_ID}:
    get:
      summary: Get Web Link
      description: Use to get information about the web link.
      operationId: getWebLink
      x-api-path-slug: web-linksweb-link-id-get
      parameters:
      - in: query
        name: fields
        description: Attribute(s) to include in the response
      - in: path
        name: WEB_LINK_ID
      responses:
        200:
          description: OK
      tags:
      - Documents
      - Web
      - Links
      - Web
      - Link
    put:
      summary: Update Web Link
      description: Updates information for a web link.
      operationId: updateWebLink
      x-api-path-slug: web-linksweb-link-id-put
      parameters:
      - in: body
        name: body
        schema:
          $ref: '#/definitions/holder'
      - in: query
        name: fields
        description: Attribute(s) to include in the response
      - in: path
        name: WEB_LINK_ID
      responses:
        200:
          description: OK
      tags:
      - Documents
      - Web
      - Links
      - Web
      - Link
    delete:
      summary: Delete Web Link
      description: Deletes a web link and moves it to the trash
      operationId: deleteWebLink
      x-api-path-slug: web-linksweb-link-id-delete
      parameters:
      - in: path
        name: WEB_LINK_ID
      responses:
        200:
          description: OK
      tags:
      - Documents
      - Web
      - Links
      - Web
      - Link
  /metadata_templates/schema:
    post:
      summary: Create Metadata Template
      description: Used to create a new metadata template with the specified schema.
      operationId: createMetadataTemplate
      x-api-path-slug: metadata-templatesschema-post
      parameters:
      - in: body
        name: body
        schema:
          $ref: '#/definitions/holder'
      responses:
        200:
          description: OK
      tags:
      - Documents
      - Metadata
      - Templates
      - Schema
  /metadata_templates/{SCOPE}:
    get:
      summary: Get Enterprise Metadata
      description: Used to retrieve all metadata templates within a user's enterprise.
        Currently only the enterprise scope is supported.
      operationId: getEnterpriseMetadataTemplates
      x-api-path-slug: metadata-templatesscope-get
      parameters:
      - in: path
        name: SCOPE
      responses:
        200:
          description: OK
      tags:
      - Documents
      - Metadata
      - Templates
      - Scope
  /metadata_templates/{SCOPE}/{TEMPLATE}/schema:
    get:
      summary: Get Metadata Template
      description: Used to retrieve the schema for a given metadata template.
      operationId: getMetadataTemplate
      x-api-path-slug: metadata-templatesscopetemplateschema-get
      parameters:
      - in: path
        name: SCOPE
      - in: path
        name: TEMPLATE
      responses:
        200:
          description: OK
      tags:
      - Documents
      - Metadata
      - Templates
      - Scope
      - Template
      - Schema
    put:
      summary: Update Metadata Template
      description: Used to update the schema of an existing template.
      operationId: updateMetadataTemplate
      x-api-path-slug: metadata-templatesscopetemplateschema-put
      parameters:
      - in: body
        name: body
        schema:
          $ref: '#/definitions/holder'
      - in: path
        name: SCOPE
      - in: path
        name: TEMPLATE
      responses:
        200:
          description: OK
      tags:
      - Documents
      - Metadata
      - Templates
      - Scope
      - Template
      - Schema
  /files/{FILE_ID}/metadata:
    get:
      summary: Get all Metadata on File
      description: Used to retrieve all metadata associated with a given file
      operationId: getAllFileMetadata
      x-api-path-slug: filesfile-idmetadata-get
      parameters:
      - in: path
        name: FILE_ID
      responses:
        200:
          description: OK
      tags:
      - Documents
      - Files
      - File
      - ""
      - Metadata
  /files/{FILE_ID}/metadata/{SCOPE}/{TEMPLATE}:
    post:
      summary: Create Metadata on File
      description: Used to create the metadata template instance for a corresponding
        Box file. When creating metadata, only values that adhere to the metadata
        template schema will be accepted.
      operationId: createFileMetadata
      x-api-path-slug: filesfile-idmetadatascopetemplate-post
      parameters:
      - in: body
        name: body
        schema:
          $ref: '#/definitions/holder'
      - in: path
        name: FILE_ID
      - in: path
        name: SCOPE
      - in: path
        name: TEMPLATE
      responses:
        200:
          description: OK
      tags:
      - Documents
      - Files
      - File
      - ""
      - Metadata
      - Scope
      - Template
    get:
      summary: Get Metadata on File
      description: Used to retrieve the metadata template instance for a corresponding
        Box file.
      operationId: getFileMetadata
      x-api-path-slug: filesfile-idmetadatascopetemplate-get
      parameters:
      - in: path
        name: FILE_ID
      - in: path
        name: SCOPE
      - in: path
        name: TEMPLATE
      responses:
        200:
          description: OK
      tags:
      - Documents
      - Files
      - File
      - ""
      - Metadata
      - Scope
      - Template
    put:
      summary: Update Metadata on File
      description: |-
        Used to update the template instance. The request body must follow the JSON-Patch specification, which is represented as a JSON array of operation objects (see examples for more details). Updates can be either add, replace, remove , test, move, or copy. The template instance can only be updated if the template instance already exists. When editing metadata, only values that adhere to the metadata template schema will be accepted.
        The update is applied atomically. If any errors occur during the application of the update operations, the metadata instance remains unchanged.
      operationId: updateFileMetadata
      x-api-path-slug: filesfile-idmetadatascopetemplate-put
      parameters:
      - in: body
        name: body
        schema:
          $ref: '#/definitions/holder'
      - in: path
        name: FILE_ID
      - in: path
        name: SCOPE
      - in: path
        name: TEMPLATE
      responses:
        200:
          description: OK
      tags:
      - Documents
      - Files
      - File
      - ""
      - Metadata
      - Scope
      - Template
    delete:
      summary: Delete Metadata on File
      description: Used to delete the template instance. To delete custom key:value
        pairs within a template instance, you should refer to the updating metadata
        section.
      operationId: deleteFileMetadata
      x-api-path-slug: filesfile-idmetadatascopetemplate-delete
      parameters:
      - in: path
        name: FILE_ID
      - in: path
        name: SCOPE
      - in: path
        name: TEMPLATE
      responses:
        200:
          description: OK
      tags:
      - Documents
      - Files
      - File
      - ""
      - Metadata
      - Scope
      - Template
  /folders/{FOLDER_ID}/metadata:
    get:
      summary: Get All Metadata on Folder
      description: Used to retrieve all metadata associated with a given folder
      operationId: getAllFolderMetadata
      x-api-path-slug: foldersfolder-idmetadata-get
      parameters:
      - in: path
        name: FOLDER_ID
      responses:
        200:
          description: OK
      tags:
      - Documents
      - Folders
      - Folder
      - ""
      - Metadata
  /folders/{FOLDER_ID}/metadata/{SCOPE}/{TEMPLATE}:
    post:
      summary: Create Metadata on Folder
      description: Used to create the metadata template instance for a corresponding
        Box folder. When creating metadata, only values that adhere to the metadata
        template schema will be accepted.
      operationId: createFolderMetadata
      x-api-path-slug: foldersfolder-idmetadatascopetemplate-post
      parameters:
      - in: body
        name: body
        schema:
          $ref: '#/definitions/holder'
      - in: path
        name: FOLDER_ID
      - in: path
        name: SCOPE
      - in: path
        name: TEMPLATE
      responses:
        200:
          description: OK
      tags:
      - Documents
      - Folders
      - Folder
      - ""
      - Metadata
      - Scope
      - Template
    get:
      summary: Get Metadata on Folder
      description: Used to retrieve the metadata template instance for a corresponding
        Box folder.
      operationId: getFolderMetadata
      x-api-path-slug: foldersfolder-idmetadatascopetemplate-get
      parameters:
      - in: path
        name: FOLDER_ID
      - in: path
        name: SCOPE
      - in: path
        name: TEMPLATE
      responses:
        200:
          description: OK
      tags:
      - Documents
      - Folders
      - Folder
      - ""
      - Metadata
      - Scope
      - Template
    put:
      summary: Update Metadata on Folder
      description: Used to update the template instance. Updates can be either add,
        replace, remove , or test. The template instance can only be updated if the
        template instance already exists. When editing metadata, only values that
        adhere to the metadata template schema will be accepted.
      operationId: updateFolderMetadata
      x-api-path-slug: foldersfolder-idmetadatascopetemplate-put
      parameters:
      - in: body
        name: body
        schema:
          $ref: '#/definitions/holder'
      - in: path
        name: FOLDER_ID
      - in: path
        name: SCOPE
      - in: path
        name: TEMPLATE
      responses:
        200:
          description: OK
      tags:
      - Documents
      - Folders
      - Folder
      - ""
      - Metadata
      - Scope
      - Template
    delete:
      summary: Delete Metadata on Folder
      description: Used to delete the template instance. To delete custom key:value
        pairs within a template instance, you should refer to the updating metadata
        section.
      operationId: deleteFolderMetadata
      x-api-path-slug: foldersfolder-idmetadatascopetemplate-delete
      parameters:
      - in: path
        name: FOLDER_ID
      - in: path
        name: SCOPE
      - in: path
        name: TEMPLATE
      responses:
        200:
          description: OK
      tags:
      - Documents
      - Folders
      - Folder
      - ""
      - Metadata
      - Scope
      - Template
  /collaborations:
    get:
      summary: Pending Collaborations
      description: Used to retrieve all pending collaboration invites for this user.
      operationId: getPendingCollaborations
      x-api-path-slug: collaborations-get
      parameters:
      - in: query
        name: fields
        description: Attribute(s) to include in the response
      - in: query
        name: status
        description: Must be pending
      responses:
        200:
          description: OK
      tags:
      - Documents
      - Collaborations
    post:
      summary: Create Collaboration
      description: Used to add a collaboration for a single user or a single group
        to a folder. Either an email address, a user ID, or a group id can be used
        to create the collaboration. If the collaboration is being created with a
        group, access to this endpoint is granted based on the group's invitability_level.
      operationId: createCollaboration
      x-api-path-slug: collaborations-post
      parameters:
      - in: body
        name: body
        schema:
          $ref: '#/definitions/holder'
      responses:
        200:
          description: OK
      tags:
      - Documents
      - Collaborations
  /collaborations/{COLLAB_ID}:
    get:
      summary: Get Collaboration
      description: Used to get information about a single collaboration. All collaborations
        for a single folder can be retrieved through GET /folders/{id}/collaborations.
        A complete list of the user???s pending collaborations can also be retrieved.
      operationId: getCollaboration
      x-api-path-slug: collaborationscollab-id-get
      parameters:
      - in: path
        name: COLLAB_ID
      - in: query
        name: fields
        description: Attribute(s) to include in the response
      - in: query
        name: status
        description: Can only be pending
      responses:
        200:
          description: OK
      tags:
      - Documents
      - Collaborations
      - Collab
    put:
      summary: Update Collaboration
      description: Used to edit an existing collaboration. Descriptions of the various
        roles can be found here.
      operationId: updateCollaboation
      x-api-path-slug: collaborationscollab-id-put
      parameters:
      - in: body
        name: body
        schema:
          $ref: '#/definitions/holder'
      - in: path
        name: COLLAB_ID
      responses:
        200:
          description: OK
      tags:
      - Documents
      - Collaborations
      - Collab
    delete:
      summary: Delete Collaboration
      description: Used to delete a single collaboration.
      operationId: deleteCollaboration
      x-api-path-slug: collaborationscollab-id-delete
      parameters:
      - in: path
        name: COLLAB_ID
      responses:
        200:
          description: OK
      tags:
      - Documents
      - Collaborations
      - Collab
  /search:
    get:
      summary: Searching for Content
      description: The search endpoint provides a powerful way of finding items that
        are accessible by a single user or an entire enterprise. Leverage the parameters
        listed below to generate targeted advanced searches.
      operationId: search
      x-api-path-slug: search-get
      parameters:
      - in: query
        name: ancestor_folder_ids
        description: Limit searches to specific parent folders
      - in: query
        name: content_types
        description: Limit searches to specific Box designated content types
      - in: query
        name: created_at_range
        description: The date for when the item was created
      - in: query
        name: file_extensions
        description: Limit searches to specific file extensions like pdf,png,doc
      - in: query
        name: limit
        description: Number of search results to return
      - in: query
        name: mdfilters
        description: Filters for a specific metadata template for files with metadata
          object associations
      - in: query
        name: offset
        description: The search result at which to start the response
      - in: query
        name: owner_user_ids
        description: Search by item owners
      - in: query
        name: query
        description: The string to search for; can be matched against item names,
          descriptions, text content of a file, and other fields of the different
          item types
      - in: query
        name: scope
        description: The scope for which you want to limit your search to
      - in: query
        name: size_range
        description: Filter by a file size range
      - in: query
        name: trash_content
        description: Allows you to search within the trash
      - in: query
        name: type
        description: The type you want to return in your search
      - in: query
        name: updated_at_range
        description: The date for when the item was last updated
      responses:
        200:
          description: OK
      tags:
      - Documents
      - Search
  /shared_items:
    get:
      summary: Shared Items
      description: |-
        Shared items are any files or folders that are represented by a shared link. Shared items are different from other API resources in that a shared resource doesn???t necessarily have to be in the account of the user accessing it. The actual shared link itself is used along with a normal access token.
        Used to retrieve the metadata about a shared item when only given a shared link. Because of varying permission for shared links, a password may be required to retrieve the shared item. Once the item has been retrieved, you can make API requests against the actual resource /files/{id} or /folders/{id} as long as the shared link and optional password are in the header.
      operationId: getSharedItems
      x-api-path-slug: shared-items-get
      parameters:
      - in: header
        name: BoxApi
        description: 'The usage is BoxApi: shared_link=SHARED_LINK&shared_link_password=SHARED_LINK_PASSWORD'
      responses:
        200:
          description: OK
      tags:
      - Documents
      - Shared
      - Items
  /collections:
    get:
      summary: Get Collections
      description: Retrieves the collections for the given user. Currently, only the
        favorites collection is supported.
      operationId: getCollections
      x-api-path-slug: collections-get
      responses:
        200:
          description: OK
      tags:
      - Documents
      - Collections
  /collections/{COLLECTION_ID}/items:
    get:
      summary: Get Collection Items
      description: |-
        Retrieves the files and/or folders contained within this collection. Collection item lists behave a lot like getting a folder???s items.
        Paginated results can be retrieved using the limit and offset parameters.
        Sub-object fields can be requested via the ?fields parameter
      operationId: getCollectionItems
      x-api-path-slug: collectionscollection-iditems-get
      parameters:
      - in: path
        name: COLLECTION_ID
      - in: query
        name: fields
        description: Attribute(s) to include in the response
      - in: query
        name: limit
        description: The maximum number of items to return in a page
      - in: query
        name: offset
        description: The offset at which to begin the response
      responses:
        200:
          description: OK
      tags:
      - Documents
      - Collections
      - Collection
      - ""
      - Items
  /comments:
    post:
      summary: Create Comment
      description: Used to add a comment by the user to a specific file or comment
        (i.e. as a reply comment).
      operationId: createComment
      x-api-path-slug: comments-post
      parameters:
      - in: body
        name: body
        schema:
          $ref: '#/definitions/holder'
      - in: query
        name: fields
        description: Attribute(s) to include in the response
      responses:
        200:
          description: OK
      tags:
      - Documents
      - Comments
  /comments/{COMMENT_ID}:
    get:
      summary: Get Comment
      description: Used to retrieve the message and metadata about a specific comment.
        Information about the user who created the comment is also included.
      operationId: getComment
      x-api-path-slug: commentscomment-id-get
      parameters:
      - in: path
        name: COMMENT_ID
      - in: query
        name: fields
        description: Attribute(s) to include in the response
      responses:
        200:
          description: OK
      tags:
      - Documents
      - Comments
      - Comment
    put:
      summary: Update Comment
      description: Used to update the message of the comment.
      operationId: updateComment
      x-api-path-slug: commentscomment-id-put
      parameters:
      - in: body
        name: body
        schema:
          $ref: '#/definitions/holder'
      - in: path
        name: COMMENT_ID
      - in: query
        name: fields
        description: Attribute(s) to include in the response
      responses:
        200:
          description: OK
      tags:
      - Documents
      - Comments
      - Comment
    delete:
      summary: Delete Comment
      description: Permanently deletes a comment.
      operationId: deleteComment
      x-api-path-slug: commentscomment-id-delete
      parameters:
      - in: path
        name: COMMENT_ID
      responses:
        200:
          description: OK
      tags:
      - Documents
      - Comments
      - Comment
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