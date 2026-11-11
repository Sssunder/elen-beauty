# Changelog — Elen Beauty

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
- **Verified**: Local Playwright E2E passed (`4` themes × `3` viewports `1440x900`/`393x852`/`360x800` across client + 3 master tabs: `0` console/page/network errors, `0px` horizontal overflow, `min_contrast 4.87..6.69`, DB config restored cleanly). Next: live GitHub Pages audit post-push.
