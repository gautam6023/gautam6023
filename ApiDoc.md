# Integrate your Web Applicatication with Ai.Mas platform

## Terminology

- VI_API_URL => Server end point of VI Platform


### `1. Signup / Register at vi.masaischool.com:`
   
   - Ensure that you register at vi.masaischool.com using your organization's email address.
     
   ##### `Existing User`
   - If you are already a user within the same organization, you will be automatically added to the organization.
   - After signing up, have your account verified by the organization's admin.
     
   ##### `New User`
   - If you are a new user, register and verify both your personal and organizational accounts with the Ai.Mas team.
     
   - A new organization will be automatically created at vi.masaischool.com based on your business email address If you are an new user.

### `2.  Generate an API Key for the Organization:`

 - Once your organization and account are verified, you can generate an API key.
   
 - Obtain API keys from the admin or Ai.Mas team as of now.
   
 - After obtaining the API key, include it as a token in the headers of all API requests to access the Ai.Mas platform..
   
   ```js
      headers:{
         `x-auth-token`: YOUR_API_KEY
      }
   ```

### `3. Set Up a Webhook for the Organization:`

   - To establish a webhook, use the following endpoint and ensure that you pass the API key in the request headers.
     
   - `POST : VI_API_URL/webhook/create` : Make a POST request on this endpoint.
     
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

   ### Get Assessments :
   
   - Use  `GET : VI_API_URL/virtual-interview-template/assessments` endpoint to get All assessments.
     
   ### Create an Assessments :

   - Utilize the `GET : VI_API_URL/virtual-interview-template/assessments` endpoint to retrieve all assessments.
   - You need to include following things in the body of this POST request.
   - `title` : Title of the Assessment
   - `questions` : Question Id's.
        - As of now create the Question on the vi platfomrm.
        - Get Id's of the question you want to add in the assessments.
   - `intro_message` : Introduction message.
   - `voice_code` : You can use following voice codes.
       
        ```
              const voices = [
                   { voice_code: 'en-US-JennyMultilingualNeural3', gender: 'Female', name: 'Jenny' },
                   { voice_code: 'en-US-JennyNeural', gender: 'Female', name: 'Jenny' },
                   { voice_code: 'en-US-GuyNeural', gender: 'Male', name: 'Guy' },
                   { voice_code: 'en-US-AriaNeural', gender: 'Female', name: 'Aria' },
                   { voice_code: 'en-US-DavisNeural', gender: 'Male', name: 'Davis' },
                   { voice_code: 'en-US-AmberNeural', gender: 'Female', name: 'Amber' },
                   { voice_code: 'en-US-AnaNeural', gender: 'Female', name: 'Ana' },
                   { voice_code: 'en-US-AshleyNeural', gender: 'Female', name: 'Ashley' },
                   { voice_code: 'en-US-BrandonNeural', gender: 'Male', name: 'Brandon' },
                   { voice_code: 'en-US-ChristopherNeural', gender: 'Male', name: 'Christopher' },
                   { voice_code: 'en-US-CoraNeural', gender: 'Female', name: 'Cora' },
                   { voice_code: 'en-US-ElizabethNeural', gender: 'Female', name: 'Elizabeth' },
                   { voice_code: 'en-US-EricNeural', gender: 'Male', name: 'Eric' },
                   { voice_code: 'en-US-JacobNeural', gender: 'Male', name: 'Jacob' },
                   { voice_code: 'en-US-JaneNeural', gender: 'Female', name: 'Jane' },
                   { voice_code: 'en-US-JasonNeural', gender: 'Male', name: 'Jason' },
                   { voice_code: 'en-US-MichelleNeural', gender: 'Female', name: 'Michelle' },
                   { voice_code: 'en-US-MonicaNeural', gender: 'Female', name: 'Monica' },
                   { voice_code: 'en-US-NancyNeural', gender: 'Female', name: 'Nancy' },
                   { voice_code: 'en-US-RogerNeural', gender: 'Male', name: 'Roger' },
                   { voice_code: 'en-US-SaraNeural', gender: 'Female', name: 'Sara' },
                   { voice_code: 'en-US-SteffanNeural', gender: 'Male', name: 'Steffan' },
                   { voice_code: 'en-US-TonyNeural', gender: 'Male', name: 'Tony' },
                   { voice_code: 'en-US-AIGenerate1Neural1', gender: 'Male', name: 'AI Generate 1' },
                   { voice_code: 'en-US-AIGenerate2Neural1', gender: 'Female', name: 'AI Generate 2' },
                   { voice_code: 'en-US-BlueNeural1', gender: 'Neutral', name: 'Blue' },
                   { voice_code: 'en-US-JennyMultilingualV2Neural1,3', gender: 'Female', name: 'Jenny Multilingual V2' },
                   { voice_code: 'en-US-RyanMultilingualNeural1,3', gender: 'Male', name: 'Ryan Multilingual' },
                   { voice_code: 'en-IN-NeerjaNeural', gender: 'Female', name: 'Neerja' },
                   { voice_code: 'en-IN-PrabhatNeural', gender: 'Male', name: 'Prabhat' },
                   { voice_code: 'hi-IN-SwaraNeural', gender: 'Female', name: 'Swara' },
                   { voice_code: 'hi-IN-MadhurNeural', gender: 'Male', name: 'Madhur' },
                  ]
        ```
   - `redirect_url` : When assessment get's over you will be redirect to following Url.
   - `schedule_start_time` : Start time of the assessment.
   - `schedule_end_time` : End time of the assessment.
   - `max_duration_minutes` : Max duration of interview in minutes.
   - `lock_assessment_after_end_time` : Lock assessment after end time.
   - `model` : You can use following models as of now.
     ```js
                   GPT4 = 'gpt-4',
                   GPT4June = 'gpt-4-0613',
                   GPT4March = 'gpt-4-0314',
                   GPT35Turbo16kJune = 'gpt-3.5-turbo-16k-0613',
                   GPT35Turbo16k = 'gpt-3.5-turbo-16k',
                   GPT35TurboJune = 'gpt-3.5-turbo-0613',
                   GPT35TurboMarch = 'gpt-3.5-turbo-0301',
                   GPT35Turbo = 'gpt-3.5-turbo
     ```
   - `webhooks` : Add an Ids of your ogranisation's webhooks
   - Body :
     ```js
                 {
                   "title": "Title",
                   "questions": ["Questin ID"],
                   "intro_message": "Hi, There",
                   "interviewer_name": "Ai.Mas",
                   "voice_code": "en-US-GuyNeural",
                   "redirect_url": "https://example.com",
                   "schedule_start_time": "2023-08-28T01:25",
                   "schedule_end_time": "2023-08-28T03:28",
                   "max_duration_minutes": "10",
                   "lock_assessment_after_end_time": false, 
                   "model": "gpt-3.5-turbo"
                   "webhooks":["Webhook Ids"] 
                }
     ```
     
   ### Get Assessment By Id
   
   - Retrieve a specific assessment using `GET VI_API_URL/virtual-interview-template/assessments/:id`.


   ### Get Submissions for an Assessment: 

   - Obtain submissions for an assessment using `GET VI_API_URL/vi-assessment/submissions/?assessment_id=:id`.


   ### Create Interview / Add Users to Assessment :

   - Use `POST VI_API_URL/vi-assessment/submission/create` to add users, they will be appearing for the Interview / Asssessment.
     
   - Include the following in the request body:
     
   - `email` : User's Email address.
     
   - `code` : Unique code.
     
   - `assessment_id` : Id of the Assessment.
     
   - `meta` : Addition details of the user.
     ```js
          {
           "assessment_id": "ASSESSMENT_ID",
           "code": "EXAMPLE_123",
           "email": "example@gmail.com",
           "meta": "{}",
           "variables": []
          }
     ```
      
         


  

   

