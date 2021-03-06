---
swagger: "2.0"
x-collection-name: Open Science Framework
x-complete: 0
info:
  title: Open Science Framework List all registrations
  description: |-
    List of all registrations of the given node.
    ####Returns

    Returns a JSON object containing `data` and `links` keys.

    The `data` key contains an array of up to 10 registrations. Each resource in the array is a separate registrations object.

    The `links` key contains a dictionary of links that can be used for [pagination](#Introduction_pagination).
    ####Filtering

    You can optionally request that the response only include registrations that match your filters by utilizing the filter query parameter, e.g. https://api.osf.io/v2/registrations/?filter[title]=open.

    Registrations may be filtered by their `id`, `title`, `category`, `description`, `public`, `tags`, `date_created`, `date_modified`, `root`, `parent`, and `contributors`.
  contact:
    name: OSF
    url: https://osf.io/support
    email: support@osf.io
  version: "2.0"
host: test-api.osf.io
basePath: /v2
schemes:
- http
produces:
- application/json
consumes:
- application/json
paths:
  /institutions/{institution_id}/registrations/:
    get:
      summary: List all affiliated registrations
      description: |-
        A paginated list of all registrations affiliated with an institution.
        #### Returns
        Returns a JSON object containing `data` and `links` keys.

        The `data` key contains an array of 10 registrations. Each resource in the array is a separate users object.

        The `links` key contains a dictionary of links that can be used for [pagination](#Introduction_pagination).

        If the request is unsuccessful, an `errors` key containing information about the failure will be returned. Refer to the [list of error codes](#Introduction_error_codes) to understand why this request may have failed.
        #### Filtering
        You can optionally request that the response only include registrations that match your filters by utilizing the `filter` query parameter, e.g. https://api.osf.io/v2/institutions/cos/registrations?filter[title]=science.

        Registrations may be filtered by their  `id`, `title`, `description`, `public`, `tags`, `category`, `date_created`, `date_modified`, `root`, `parent`, `contributors`, and `preprint`
      operationId: institutions_registration_list
      x-api-path-slug: institutionsinstitution-idregistrations-get
      parameters:
      - in: path
        name: institution_id
        description: The unique identifier of the institution you wish to retrieve
      responses:
        200:
          description: OK
      tags:
      - Institutions
      - Institution
      - Registrations
  /nodes/{node_id}/draft_registrations/:
    get:
      summary: List all draft registrations
      description: |-
        A paginated list of all of the draft registrations of a given node.

        Draft registrations contain the supplemental registration questions that accompany a registration. A registration is a frozen version of the project that can never be edited or deleted, but can be withdrawn.

        Your original project remains editable but will now have the draft registration linked to it.
        #### Permissions
        Only project administrators may view draft registrations.
        #### Returns
        Returns a JSON object containing `data` and `links` keys.

        The `data` key contains an array of 10 draft registrations. Each resource in the array is a separate draft registration object and contains the full representation of the draft registration, meaning additional requests to a draft registration's detail view are not necessary.

        The `links` key contains a dictionary of links that can be used for [pagination](#Introduction_pagination).
      operationId: nodes_draft_registrations_list
      x-api-path-slug: nodesnode-iddraft-registrations-get
      parameters:
      - in: path
        name: node_id
        description: The unique identifier of the node
      responses:
        200:
          description: OK
      tags:
      - Nodes
      - Node
      - Draft
      - Registrations
    post:
      summary: Create a draft registration
      description: |-
        Initiate a draft registration of the current node.
        Draft registrations contain the supplemental registration questions that accompany a registration. A registration is a frozen version of the project that can never be edited or deleted, but can be withdrawn.

        Your original project remains editable but will now have the draft registration linked to it.
        #### Permissions
        Only project administrators may view create registrations.
        #### Required
        Required fields for creating a draft registration include:

        &nbsp;&nbsp;&nbsp;&nbsp`registration_supplement`
        #### Returns
        Returns a JSON object with a `data` key containing the representation of the created draft registration, if the request is successful.

        If the request is unsuccessful, an `errors` key containing information about the failure will be returned. Refer to the [list of error codes](#Introduction_error_codes) to understand why this request may have failed.
      operationId: nodes_draft_registrations_create
      x-api-path-slug: nodesnode-iddraft-registrations-post
      parameters:
      - in: body
        name: body
        schema:
          $ref: '#/definitions/holder'
      - in: path
        name: node_id
        description: The unique identifier of the node
      responses:
        200:
          description: OK
      tags:
      - Nodes
      - Node
      - Draft
      - Registrations
  /nodes/{node_id}/draft_registrations/{draft_id}/:
    delete:
      summary: Delete a draft registration
      description: |-
        Permanently deletes a draft registration. A draft that has already been registered cannot be deleted.
        #### Permissions
        Only project administrators may delete draft registrations.
        #### Returns
        If the request is successful, no content is returned.

        If the request is unsuccessful, a JSON object with an `errors` key containing information about the failure will be returned. Refer to the [list of error codes]() to understand why this request may have failed.
      operationId: nodes_draft_registrations_delete
      x-api-path-slug: nodesnode-iddraft-registrationsdraft-id-delete
      parameters:
      - in: path
        name: draft_id
        description: The unique identifier of the draft registration
      - in: path
        name: node_id
        description: The unique identifier of the node
      responses:
        200:
          description: OK
      tags:
      - Nodes
      - Node
      - Draft
      - Registrations
      - Draft
    get:
      summary: Retrieve a draft registration
      description: |-
        Retrieve the details of a given draft registration.
        Draft registrations contain the supplemental registration questions that accompany a registration. A registration is a frozen version of the project that can never be edited or deleted, but can be withdrawn.

        Your original project remains editable but will now have the draft registration linked to it.
        #### Permissions
        Only project administrators may view draft registrations.
        #### Returns
        Returns a JSON object with a `data` key containing the representation of the requested draft registration, if the request is successful.

        If the request is unsuccessful, an `errors` key containing information about the failure will be returned. Refer to the [list of error codes](#Introduction_error_codes) to understand why this request may have failed.
      operationId: nodes_draft_registrations_read
      x-api-path-slug: nodesnode-iddraft-registrationsdraft-id-get
      parameters:
      - in: path
        name: draft_id
        description: The unique identifier of the draft registration
      - in: path
        name: node_id
        description: The unique identifier of the node
      responses:
        200:
          description: OK
      tags:
      - Nodes
      - Node
      - Draft
      - Registrations
      - Draft
    patch:
      summary: Update a draft registration
      description: |-
        Updates a draft registration by setting the values of the attributes specified in the request body. Any unspecified attributes will be left unchanged.

        Draft registrations contain the supplemental registration questions that accompany a registration. Answer the questions in the draft registration supplement by sending update requests until you are ready to submit the draft.

        The registration supplement of a draft registration cannot be updated after the draft has been created.

        When updating a draft registration, `registration_metadata` is required. It must be a dictionary with keys as question ids in the registration form, and values as nested dictionaries matching the specific format in the [registration schema](TODO: link me pls).

        If a question is multiple-choice, the question response must exactly match one of the possible choices.
        #### Permissions
        Only project administrators may update draft registrations.
        #### Returns
        Returns a JSON object with a `data` key containing the new representation of the updated draft registration, if the request is successful.

        If the request is unsuccessful, an `errors` key containing information about the failure will be returned. Refer to the [list of error codes](#Introduction_error_codes) to understand why this request may have failed.
      operationId: nodes_draft_registrations_partial_update
      x-api-path-slug: nodesnode-iddraft-registrationsdraft-id-patch
      parameters:
      - in: body
        name: body
        schema:
          $ref: '#/definitions/holder'
      - in: path
        name: draft_id
        description: The unique identifier of the draft registration
      - in: path
        name: node_id
        description: The unique identifier of the node
      responses:
        200:
          description: OK
      tags:
      - Nodes
      - Node
      - Draft
      - Registrations
      - Draft
  /nodes/{node_id}/registrations/:
    get:
      summary: List all registrations
      description: |-
        List of all registrations of the given node.
        ####Returns

        Returns a JSON object containing `data` and `links` keys.

        The `data` key contains an array of up to 10 registrations. Each resource in the array is a separate registrations object.

        The `links` key contains a dictionary of links that can be used for [pagination](#Introduction_pagination).
        ####Filtering

        You can optionally request that the response only include registrations that match your filters by utilizing the filter query parameter, e.g. https://api.osf.io/v2/registrations/?filter[title]=open.

        Registrations may be filtered by their `id`, `title`, `category`, `description`, `public`, `tags`, `date_created`, `date_modified`, `root`, `parent`, and `contributors`.
      operationId: nodes_registrations_list
      x-api-path-slug: nodesnode-idregistrations-get
      parameters:
      - in: path
        name: node_id
        description: The unique identifier of the node
      responses:
        200:
          description: OK
      tags:
      - Nodes
      - Node
      - Registrations
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