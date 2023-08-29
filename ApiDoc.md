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

   ### Get an Assessments :
   
   - Use  `GET : VI_API_URL/virtual-interview-template/assessments` endpoint to get All assessments.
     
   ### Create an Assessments :

   - Use `POST : VI_API_URL/virtual-interview-template/assessments/create` to create an assessment.
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
   - `webhooks` : Add an Id of your ogranisation's webhooks
   - Body :
     ```js
                 {
                   "title": "Test2 ",
                   "questions": ["Questin ID"],
                   "intro_message": "Hi , I am Gautam, working at masai in tech team",
                   "interviewer_name": "Gautam",
                   "voice_code": "en-US-GuyNeural", //Hardcoded
                   "redirect_url": "masaischool.com",
                   "schedule_start_time": "2023-08-28T01:25",
                   "schedule_end_time": "2023-08-28T03:28",
                   "max_duration_minutes": "10",
                   "lock_assessment_after_end_time": false, //Hardcoded
                   "model": "gpt-3.5-turbo" //Hardcoded
                   "webhooks":["Webhook Id"] //Hardcoded
                }
     ```
     
   ### Get Assessment By Id
   
   - Use `GET VI_API_URL/virtual-interview-template/assessments/:id`.
      
         


  

   

