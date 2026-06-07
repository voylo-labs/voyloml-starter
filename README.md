# VoyloML Starter - Hello World

The simplest possible Voylo app. Answers a call, plays a welcome message, hangs up. Start here to verify your setup works.

**Time to deploy:** 5 minutes  
**Prerequisites:** A Voylo number ([get one here](https://voylo.ai/app))

## What This Does

When someone calls your Voylo number, this app:
1. Answers the call
2. Plays a welcome audio message
3. Hangs up

That's it. Once this works, you know your application → VoyloML connection is good.

## Quick Start

### 1. Configure your application

In the [Voylo Console](https://voylo.ai/app), you have two options for call control:

**Option A: Static XML (easiest)**
1. Copy the contents of `app.xml` from this repo
2. Paste it directly into your application's Static XML field
3. Save

**Option B: Action URL**
1. Deploy `app.xml` to any HTTPS endpoint:
   - **GitHub Pages**: Fork this repo, enable Pages, URL will be `https://[your-github].github.io/voyloml-starter/app.xml`
   - **Vercel**: `vercel --prod` in this directory
   - **Any static host**: Upload `app.xml` anywhere serving HTTPS
2. Set your application's Action URL to your deployed endpoint
3. Save

### 2. Test it

Call your Voylo number. You'll hear the welcome message, then the call ends.

## How It Works

The entire app is 6 lines of VoyloML:

```xml
<Response>
  <!-- Play the Voylo welcome audio -->
  <Play>https://voylo.s3.ap-south-1.amazonaws.com/voylo-welcom.wav</Play>
  
  <!-- Hang up -->
  <Hangup/>
</Response>
```

When Voylo receives a call to your number:
1. It fetches your VoyloML (from Static XML or Action URL)
2. Executes the instructions (play audio, hang up)
3. Done

## Next Steps

Once this works, you're ready for real apps:
- **[voylo-elevenlabs-ivr-failover](https://github.com/voylo-labs/voylo-elevenlabs-ivr-failover)** - Add AI agents with quota protection
- **[Voylo Docs](https://voylo.ai/docs)** - Full VoyloML reference

## Troubleshooting

**Call fails immediately**
- Check your application is active in the console
- Verify the VoyloML is correctly configured (Static XML or Action URL)
- For Action URL: make sure it's publicly accessible and serves raw XML

**No audio plays**
- The audio file must be accessible over HTTPS
- Check browser console if testing via WebRTC

**Still stuck?**
- Check application logs in the [Voylo Console](https://voylo.ai/app)
- Open an issue in this repo

## License

MIT - Use this however you want.