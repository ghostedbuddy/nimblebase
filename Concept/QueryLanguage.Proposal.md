# NimbleBase Query Language Proposal

## FOREWORD
The main goal of this project is to try to provide a new innovative approach to what a database is and how i can provide value to a project. This implies that even though it might sound all thought entirely thought through and professional it probably and most likely isn't. This whole project might turn out as a big learning lesson but still maybe it is a worthy approach to research and put time into while collaborating with more intelligent people :-P.

## Overview
This document outlines the design for a simplified, token-based database system implemented as a JavaScript library for front-end applications. The goal is to create a new innovative database system which does not require a dedicated server to be run and maintained if it is not absolutely necessary or wanted. Meanwhile the additional goals are the creation of an intuitive, human-readable query language and tokenizer to manage and query data efficiently on client-side web applications.

### Goals
- Validate the concept of a simplified query language.
- Implement a basic tokenizer for indexing values.
- Facilitate CRUD operations in a user-friendly manner.

### Non-Goals
- Backend persistence.
- Distributed scalability.
- Advanced security measures.

## System Architecture
### Tokenizer
Responsible for converting indexable values into tokens for efficient searching.

### In-Memory Data Storage
Simulates a database by storing records in memory.

### Query Processor
Interprets and executes commands based on the simplified query language.

### API Interface
Provides methods for external interaction with the database system.

## Toughts on a potential Query Language
Based on the underlying aimed simplicity of this whole project, it could make sense to introduce a more straightforward and simplistic query language.

Following we have a few rough ideas about how such query language could look like and how it makes sense from the current point of view to envision such a language.

### Components
A Query consists of several lines. Each line consists of a few components which are roughly illustrated within the following:

	`ACTION(entity|field|flag)`

An action can be distinct operations onto the entity collection or onto the entity itself.
Possible actions could be:

- `add` - add a value or entity
- `set` - sets the current context to a specific entity
- `delete` - delete a value or entity
- `update` - updates a value
- `lookup` - performs a search
- `commit` - validates and executes the transation (consisting of all previous lines)

#### Example
```
ADD(user) # defines the entity to work with
UPDATE(name) John Doe # automatically interpreted as user.name
UPDATE(email) johndoe@example.com # automatically interpreted as user.email
COMMIT # evaluates the transaction and throws either an error or returns the result
```

### Tokenizer Application
each line needs to be tokenized by the integrated tokenizer which allows to be properly store and query the data. the index of each data needs to be stored within the entity collection itself while the tokenizer consists of the real data within its token bag.
