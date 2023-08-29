# Integrate your Web Applicatication with Ai.Mas platform

## Terminology

- VI_API_URL => Server end point of VI Platform


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

 - After getting verified your organisation and your account you can get your API key.
   
 - Get API keys from the admin / Ai.Mas team as of now.
   
 - After getting the API key, To access the API's of the Ai.Mas platform you need to pass API key as a token in the headers of the all       requests.
   
   ```js
      headers:{
         `x-auth-token`: YOUR_API_KEY
      }
   ```

### `3. Create Webhook for the organisation`

   - To create a webhook use following endpoint and make sure you pass apikey in the headers of the request.
     
   - `VI_API_URL/webhook/create` : Make a POST request on this endpoint.
     
   - Make sure you are sending `name` and `targetUrl` in the body of the request.
     
   - `name` : Webhook name
     
   - `targetUrl` : This is the URL where you will be recieving updates when some events get triggered on Ai.Mas platform.
     
     ```js
      {
         name:"my_org_webhook",
         targetUrl:"https://my_org_api/webhook/callback"
      }
       
     ```
### `4. Assessments`

   #### `create assessment`


  

   

