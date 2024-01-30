### Write a rest API to pass employee id and get employee detail.
```java
paths:
  /employees/{id}:
    get:
      summary: Get employee by ID
      parameters:
        - in: path
          name: id
          required: true
          schema:
            type: integer
      responses:
        '200':
          description: Successful response
          content:
            application/json:
              schema:
                type: object
                properties:
                  id:
                    type: integer
                  name:
                    type: string
                  position:
                    type: string
        '404':
          description: Employee not found
```
### Write a rest API to get all employee detail.
```java
  /employees:
    get:
      summary: Get all employees
      responses:
        '200':
          description: Successful response
          content:
            application/json:
              schema:
                type: array
                items:
                  type: object
                  properties:
                    id:
                      type: integer
                    name:
                      type: string
                    position:
                      type: string
```


### Write a rest API to post a employee detail.
```java
  /employees:
    post:
      summary: Create a new employee
      requestBody:
        description: Employee data
        required: true
        content:
          application/json:
            schema:
              type: object
              properties:
                id:
                  type: integer
                name:
                  type: string
                position:
                  type: string
      responses:
        '201':
          description: Employee created successfully
``` 
