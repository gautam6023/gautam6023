# Integrate your Web Applicatication with Ai.Mas platform

## Terminology

- VI_SERVER_URL => Server end point of VI Platform


### `1. Signup / Register at vi.masaischool.com:`
   
   - Make sure to use your organisation's email address to register at vi.masaischool.com.
     
   ##### `Existing User`
   - If you are an existing user for the same organisation then you will be added to the organisation automatically.
   - After signup get your account verified from the admin of the organisation.
     
   ##### `New User`
   - In can you are a new user then after registering, get verified your own account and organisation account with the admin / contact     
     Ai.Mas team.
   - New organisation will be created automatically at vi.masaischool.com with respect your business email address. 

### `2. Create API Key for the organisation:`

 - After getting verified your organisation and your account you can generate your API key.
 - Sigin at vi.masaschool.com platform. get 
 - Use following end point to generate API key for the organisation.
 - 
 - `POST - /organisations/api-keys/create`
 - Body
     - name of the API key required.
     ```json
       { "name":"test2_api_key" }
     ```
  

   

