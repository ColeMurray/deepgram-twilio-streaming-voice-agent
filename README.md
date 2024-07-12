# Deepgram Streaming Voice Agent

This is a basic server application that show cases end to end streaming voice agent

* Streaming Twilio - Inbound Audio
* Streaming Deepgram - Speech to Text
* Streaming OpenAI - LLM
* Streaming Deepgram - Text to Speech
* Streaming Twilio - Outbound Audio

It's a good starting point to develop your own application logic.

## App sever setup

###

```
export OPENAI_API_KEY=xxx
export DEEPGRAM_API_KEY=xxx
```

### Installation

**Requires Node >= v12.1.0**

Run `npm install`

npm dependencies (contained in the `package.json`):
* httpdispatcher
* websocket

#### Running the server

Start with `npm run start`r

## Setup

You can setup your environment to run the demo by using the CLI.

### Configure using the CLI

1. Find available phone number

```bash
twilio api:core:available-phone-numbers:local:list --country-code="US" --voice-enabled --properties="phoneNumber"`
```

2. Purchase the phone number (where `+123456789` is a number you found)

```bash
twilio api:core:incoming-phone-numbers:create --phone-number="+123456789"`
```

3. Start ngrok

```bash
ngrok http 8080
```

4. Edit the `templates/streams` file to replace `<ngrok url>` with your ngrok host.

5. Make the call where `+123456789` is the Twilio number you bought and `+19876543210` is your phone number and `abcdef.ngrok.io` is your ngrok host.

```
twilio api:core:calls:create --from="+123456789" --to="+19876543210" --url="https://abcdef.ngrok.io/twiml"
```
