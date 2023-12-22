# Authentication and Authorization in Applications

[Reference from daily.dev](https://www.permit.io/blog/authentication-vs-authorization?ref=dailydev)

- Authentication: AuthN
- Authorization: AuthZ
- AuthN is the process of who has access to a system.
- AuthZ is the process of what they can do within the system.
- The other words to say:
  - AuthN verifies who someone is.
  - AuthZ verifies what specific applications, files, and data the can access.
- ![auth image](https://media.graphassets.com/resize=width:2402,height:1431/Lsa2537QZ2N7RCgY1nZQ)
- What is Authentication
  - First step in the process of access control.
  - Common authentication methods:
    - Passwords
    - Biometrics
    - Multi-factor authentication
    - OTPs
  - Usually using token-based method for web applications.
- What is Authorization
  - The process of establishing permissions for a user determining the operations that they can perform.
  - Role-Based Access Control (RBAC) is a common model where access rights are grouped by roles, and users are assigned roles based on their responsibilities.

# Prompt Engineering

[Reference from tldr](https://platform.openai.com/docs/guides/prompt-engineering?utm_source=tldrnewsletter)

### This is the guide to share strategies and tactics for getting better result from large language models(LLM).

- Six strategies for getting better results
  - Write clear instructions
    - Desc: These models can't read your mind. If outputs are too long, ask for brief replies. If outputs are too simple, ask for expert-level writing. 
    - Include details in your query to get more relevant answers.
    - Bad prompt
      - How do I add numbers in Excel?
      - Who's president?
      - Write code to calculate the Fibonacci sequence.
      - Summarize the meeting notes. 
    - Good prompt
      - How do I add up a row of dollar amounts in Excel? I want to do this automatically for a whole sheet of rows with all the totals ending up on the right in a column called "Total".
      - Who was the president of Mexico in 2021, and how frequently are elections held?
      - Write a TypeScript function to efficiently calculate the Fibonacci sequence. Comment the code liberally to explain what each piece does and why it's written that way.
      - Summarize the meeting notes in a single paragraph. Then write a markdown list of the speakers and each of their key points. Finally, list the next steps or action items suggested by the speakers, if any.
    - Ask the model to adopt a persona
      - When I ask for help to write something, you will reply with a document that contains at least one joke or playful comment in every paragraph.
      - Write a thank you note to my steel bolt vendor for getting the delivery in on time and in short notice. This made it possible for us to deliver an important order.
    - Provide examples
    - Specify desired length of the output
      - Example: Summarize the text delimited by triple quotes in about 50 words.
      - Example: Summarize the text delimited by triple quotes in 2 paragraphs.
  - Give models time to 'think'
    - Instruct the model to work out its own solution before rushing to a conclusion
      - Sometimes we get better results when we explicitly instruct the model to reason from first principles before coming to a conclusion.
    - Ask the model if it missed anything on previous passes
      - "Are there more relevant excerpts? Take care not to repeat excerpts. Also ensure that excerpts contain all relevant context needed to interpret them - in other words don't extract small snippets that are missing important context."
    - Use code exection to perform more accurate calculations
      - Example: Use the triple quote '''python
        def calculate_fibonacci(n):
          if n <= 1:
            return n
          else:
            return(calculate_fibonacci(n-1) + calculate_fibonacci(n-2))
        '''

# The Await Event Horizon In Javascript

[Reference from tldr](https://frontside.com/blog/2023-12-11-await-event-horizon/?utm_source=tldrwebdev)