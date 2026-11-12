# Changelog — Elen Beauty

## 2026-11-12 — Obvious «Пройти обучение заново» button + post-skip hint, local only, NOT pushed
- Faint «Экскурсия» pill → prominent white «Пройти обучение заново» in master-cabinet tab bar; on skip (Пропустить/Esc) a ~6s bottom toast + button pulse point back to it (toast `pointer-events:none`).
- Verified `maria-loop/verify_tour.py` (8 steps) + live skip-hint check: PASS, 0 overflow 1440/360, 0 errors, zero DB writes. Additive UI only.

## 2026-11-12 — Plain-language connect guide + VPN links in Telegram card, local only, NOT pushed
- Telegram card now self-explains for non-technical owners: persistent «Как подключить (2 минуты)» list (VPN → «Подключить уведомления» → «Запустить» /start → «Я подписался — обновить статус») + Pavel's VPN referral links (`quattro.app/register?ref=HEmqibBsi5vz1Qz2` / `QuattroVPN_BOT?start=r_HEmqibBsi5vz1Qz2`); slim VPN line when connected.
- Tour Telegram section now 3 steps (8 total) switching to Texts before spotlighting the card.
- Verified `maria-loop/verify_platform.py` + `verify_tour.py` (mocked RPC, zero DB writes): PASS, 0 overflow 1440/360, 0 errors. Additive; booking logic untouched.

## 2026-11-12 — Joined universal Telegram booking-notification platform, local only, NOT pushed
- Connect-card + auto-notify ported from maria-math: `TG_NOTIFY_URL`, `notifyNewBooking()` after `create_public_booking_v2` success, Telegram card in master cabinet Texts tab (theme-surface/accent classes), `saveTelegramBotUsername`/`setTelegramEnabled`/`refreshTelegramStatus` via `persistConfigToCloud`. `DEFAULT_SITE_CONFIG.telegram.bot_username='GojoNotifyBot'` (shared platform bot → one-click connect), deep-merge in `mergeSiteConfig`.
- Tour gained a Telegram step (6 steps) that switches to Texts before spotlighting the card.
- Verified `maria-loop/verify_platform.py` + `verify_tour.py` (mocked RPC, zero DB writes): PASS, 0 overflow 1440/360, 0 errors. Additive; booking logic untouched.

## 2026-11-12 — Cabinet mini-tour (onboarding «Экскурсия»), local only, NOT pushed
- Same self-contained tour as maria-math appended before `</body>`: first master-cabinet login → spotlight + card walks «Расписание», «Тексты», «Отзывы» step-by-step; «Экскурсия» pill replays; shown once via localStorage. Auto-detects `masterView` tabs; theme-safe, mobile-clamped.
- Verified via `maria-loop/verify_tour.py` (mocked RPC, zero DB writes): 5 steps, auto-start, spotlight, card in viewport, flag, relaunch, 0 overflow 1440/360, 0 errors — PASS. Additive UI only; booking/data logic untouched.

## 2026-11-12 — Constructor v3 (Theme, Contacts Auto-Sync, Services & Reviews Studio)
- **URL**: https://sssunder.github.io/elen-beauty/ (branch `master`, Supabase `ngsonqwylcwcziwxurkc`, `SITE_SLUG=elena-beauty`)
- **Tab 2 (`#masterTabTexts`)**:
  - Added `#cfgDefaultTheme` (`nude`, `rose`, `pearl`, `noir`): auto-applies to visitors without `elena_theme_manual` and immediately on Save; upgraded `noir` & pill contrast (`min_contrast >= 4.87` across all themes).
  - Added Russian phone (`+7/8/9...` -> `+7XXXXXXXXXX`) and Telegram (`@user`/`user`/`+7...`/`t.me/...`) normalization, live `#cfgPhoneDisplay` -> WA/MAX/TG auto-sync (preserving custom TG handles), and 1-click `#cfgSyncMessengersBtn`.
  - Added `#cfgReviewsChannelUrl` rendered as `#reviewsChannelLink` + `#footerReviewsChannelLink`; wired `#headerPhoneBtn`, `#confirmPhoneBtn`, and all site-wide contact/messenger buttons dynamically to `siteConfig.contacts`.
  - Added service visibility toggle (`s.hidden`), `+ Добавить услугу` per category, and `selectedServiceIds`/calculator/quiz guards against hidden services.
- **Tab 3 (`#masterTabReviews`)**:
  - Added 3-step owner tips card, manual review form (`admin_add_review`) + live preview `#admReviewLivePreview` sharing `buildPublicReviewCardHtml()` with `renderReviews()`, plus visibility toggles (`admin_set_review_visibility`) and archive deletion (`admin_delete_review`).
- **Mobile & Layout**: Fixed `toggleVisibleLink` / `#headerPhoneBtn` responsive class toggling so desktop contact pills stay hidden `<1024px`.
- **Verified**: Local Playwright E2E passed (`4` themes × `3` viewports `1440x900`/`393x852`/`360x800` across client + 3 master tabs: `0` console/page/network errors, `0px` horizontal overflow, `min_contrast 4.87..6.69`, DB config restored cleanly). **Status**: commit `76dd4d9` pushed to `origin/master`; live audit passed 2026-11-12 via `tutor-platform-template/check_live_sites.py` (HTTP 200, Constructor v3 markers present, 0 console/network errors, 0px overflow at 1440x900 & 360x800).
