# Personal Assistant Chat Application Using OpenAI's GPT-3

Are you looking for a personal assistant that can understand and respond to your natural language commands and queries? Look no further! This project uses OpenAI's GPT-3 model to create a personal assistant that can interact with you via speech or text.

The project includes both Speech-to-Text and Text-to-Speech capabilities, allowing you to interact with the assistant in a natural, conversational way. The user interface is similar to a chat application, with typing animations and the ability to replay messages.

## Getting Started

Before you can start using the personal assistant, there are a few requirements and prerequisites that you'll need to take care of:

- Obtain an API key from OpenAI.
- Update the `OPENAI_API_KEY` value in the `.env` file.
- Obtain an Entitlement Key from IBM.
- Update the `IBM_ENTITLEMENT_KEY` value in the `.env` file.
- Ensure Docker is installed on your system.

Once you have your keys and the models deployed, you can use the application by following the steps in the "Using the Personal Assistant" section.

## Using the Personal Assistant

To run the application in a Docker container, follow these steps:

1. Open the terminal and navigate to the root directory of the repository.
2. Export your IBM Entitlement Key and login to a specific Docker registry:
    ```sh
    IBM_ENTITLEMENT_KEY=... # replace ... with your key
    echo $IBM_ENTITLEMENT_KEY | docker login -u cp --password-stdin cp.icr.io
    ```
3. Run the following command:
    ```sh
    docker compose up --build
    ```
4. Check the logs to make sure that both the TTS and STT containers are running correctly by ensuring the logs display "INFO: Chuck server ready." as shown below:
    ```sh
    ...
    chatapp-with-voice-and-openai-stt-1      | "INFO: Chuck server ready."
    ...
    chatapp-with-voice-and-openai-tts-1      | "INFO: Chuck server ready."
    ...
    ```
5. To stop the application, press `Ctrl + C` in the terminal where the `docker compose up` command was run. To tear down the containers and related resources, run:
    ```sh
    docker compose down
    ```

For the smoothest experience, run `docker compose down` and `docker compose up --build` each time you want to test new changes to ensure the image is rebuilt with the latest changes.

6. Open your browser and navigate to `http://localhost:8000` to interact with the Personal Assistant. You can then speak your queries by clicking on the microphone or typing into the message bar. The assistant will then respond with a message and read the message out loud.

Note: Any changes made to the files will require rebuilding and rerunning the service.

## Note

- Make sure to keep your API keys secure and not to share them with anyone.
- Make sure the URLs are working and are correctly used in the code.
- Make sure that the TTS and STT are ready to use (by checking their logs).

## Troubleshooting

If you experience an error like:
```sh
requests.exceptions.ConnectionError: ('Connection aborted.', RemoteDisconnected('Remote end closed connection without response'))
