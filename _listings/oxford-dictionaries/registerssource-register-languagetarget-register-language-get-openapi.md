---
swagger: "2.0"
x-collection-name: Oxford Dictionaries
x-complete: 0
info:
  title: Oxford Dictionaries Lists available registers in a bilingual dataset
  description: Returns a list of the available [registers](documentation/glossary?term=registers)
    for a given bilingual language dataset.
  termsOfService: http://helloreverb.com/terms/
  version: 1.8.0
host: od-api-demo.oxforddictionaries.com:443
basePath: /api/v1
schemes:
- http
produces:
- application/json
consumes:
- application/json
paths:
  /registers/{source_register_language}/{target_register_language}:
    get:
      summary: Lists available registers in a bilingual dataset
      description: Returns a list of the available [registers](documentation/glossary?term=registers)
        for a given bilingual language dataset.
      operationId: getRegistersSourceRegisterLanguageTargetRegisterLanguage
      x-api-path-slug: registerssource-register-languagetarget-register-language-get
      parameters:
      - in: query
        name: No Name
      - in: path
        name: source_register_language
        description: IANA language code
      - in: path
        name: target_register_language
        description: IANA language code
      responses:
        200:
          description: OK
      tags:
      - Registers
      - Source
      - Register
      - Language
      - Target
      - Register
      - Language
  /registers/{source_language}:
    get:
      summary: Lists available registers in a  monolingual dataset
      description: Returns a list of the available [registers](documentation/glossary?term=registers)
        for a given monolingual language dataset.
      operationId: getRegistersSourceLanguage
      x-api-path-slug: registerssource-language-get
      parameters:
      - in: query
        name: No Name
      - in: path
        name: source_language
        description: IANA language code
      responses:
        200:
          description: OK
      tags:
      - Registers
      - Source
      - Language
  /registers/{source_language}/{target_language}:
    get:
      summary: Lists available registers in a given bilingual language dataset.
      description: Returns a list of the available [registers](/glossary?tag=#registers&expand)
        for a given bilingual language dataset.
      operationId: getRegistersSourceLanguageTargetLanguage
      x-api-path-slug: registerssource-languagetarget-language-get
      parameters:
      - in: query
        name: No Name
      responses:
        200:
          description: OK
      tags:
      - Registers
      - Source
      - Language
      - Target
      - Language
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