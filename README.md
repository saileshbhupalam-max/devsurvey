# Developer AI Tools Survey

A conversational survey to understand how developers use AI coding tools.

## Features

- **Conversational AI Survey**: Powered by Claude Haiku for natural conversations
- **Van Westendorp Pricing**: True willingness-to-pay testing
- **Referral System**: Users earn 3 months free premium for 2 successful referrals
- **Admin Dashboard**: Real-time analytics and CSV export
- **Mobile-Friendly**: Responsive design for all devices

## Tech Stack

- **Frontend**: Vanilla JavaScript, HTML5, CSS3
- **Backend**: Supabase Edge Functions (Deno)
- **AI**: Anthropic Claude 3.5 Haiku
- **Database**: PostgreSQL (Supabase)
- **Hosting**: Vercel

## Pages

- `/` - Main survey (conversational chat interface)
- `/admin` - Admin dashboard with analytics

## Survey Flow

1. **Tools** - Which AI coding tools do you use?
2. **Frequency** - How often?
3. **Pain Points** - Pain incident story + ratings (cost, quality, privacy, speed, reliability)
4. **Workarounds** - Any hacks?
5. **Rankings** - Rank priorities (Cost, Quality, Privacy, Speed, Reliability)
6. **Interest Pitch** - Tailored pitch based on top 2 priorities
7. **Van Westendorp Pricing** - 4 pricing questions (too cheap, bargain, expensive, too expensive)
8. **Commitment** - Free premium + early access / Waitlist / Pre-order / Pass
9. **Contact Info** - Email, name, phone (optional), social share

## Referral System

- Each completed survey generates a unique 8-character referral code
- Share link includes referral code: `?ref=A7B9X2K1`
- Progress tracked: 0/2 → 1/2 → 2/2 referrals
- Reward: 3 months free premium when 2 friends complete survey

## Deployment

Deployed on Vercel with automatic HTTPS and global CDN.

## Environment Variables

Set these in your Supabase Edge Function:
- `ANTHROPIC_API_KEY` - Claude API key
- `SUPABASE_URL` - Your Supabase project URL
- `SUPABASE_ANON_KEY` - Your Supabase anon key

## License

All rights reserved.
