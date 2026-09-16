RS-PREMIUM Bot — Deploy លើ Render
================================

1) GitHub
   - Upload folder rs-premium-bot (bot.py, requirements.txt, Procfile, render.yaml)

2) Render Dashboard
   A) Blueprint: New → Blueprint → តភ្ជាប់ repo (អាន render.yaml)
   B) Manual: New → Web Service
      - Runtime: Python
      - Build: pip install -r requirements.txt
      - Start: python bot.py
      - Instance: Free (ឬ Starter)

3) Environment Variables (ចាំបាច់)
   BOT_TOKEN   = ពី @BotFather
   ADMIN_ID    = Telegram user id របស់អ្នក (លេខ)
   STORE_NAME  = RS-PREMIUM

   ស្រេចចិត្ត (ទូទាត់):
   CAMRAPIDPAY_API_KEY = ...
   ABA_API_KEY / ABA_MERCHANT_ID = ...
   DATA_DIR = /var/data

4) Persistent Disk (សំខាន់ — កុំឲ្យ data បាត់ពេល redeploy)
   Service → Disks → Add Disk
   - Name: data
   - Mount Path: /var/data
   - Size: 1 GB
   Env: DATA_DIR=/var/data

5) បន្ទាប់ Deploy
   - បើក URL service (health: / → "RS-PREMIUM Bot is running")
   - Telegram: /start លើ bot
   - Admin: ម៉ឺនុយ admin លេចពេល ADMIN_ID ត្រូវ

6) កំណត់រូប bot
   @BotFather → /setuserpic → ផ្ញើ logo RS-PREMIUM
