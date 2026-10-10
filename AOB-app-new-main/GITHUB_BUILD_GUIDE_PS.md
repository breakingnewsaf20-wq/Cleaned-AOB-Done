# د افغان آنلاین بازار (AOB) د خطا معلومولو او APK جوړولو لارښود

## څه کوي؟
- GitHub Actions په کلاوډ کې Flutter او Java چمتو کوي؛ په موبایل کې Flutter نصبولو ته اړتیا نشته.
- د `flutter analyze` او `flutter test` بشپړ راپورونه جوړوي.
- په جلا کار کې Debug APK جوړوي؛ نو د تحلیل تېروتنه د APK جوړولو هڅه نه بندوي.
- راپورونه او APK د GitHub د workflow د `Artifacts` برخې څخه ښکته کېدای شي.

## څنګه یې وچلوئ؟
1. په GitHub کې نوی repository جوړ کړئ، مثلاً `AOB-app`.
2. د دې ZIP ټول فایلونه په repository کې upload/commit کړئ؛ د `AOB-app-main` دننه فایلونه د repository په root کې وي، نه په اضافي فولډر کې.
3. که د `main` یا `master` څانګې ته commit وشي، workflow پخپله چلېږي.
4. یا GitHub repository خلاص کړئ، `Actions` ته لاړ شئ، `AOB - Check Errors and Build APK` انتخاب کړئ او `Run workflow` کېکاږئ.
5. د run پای ته رسېدو وروسته په همدې run کې `Artifacts` خلاص کړئ:
   - `AOB-error-reports`: د analyze/test راپورونه؛
   - `Afghan-Online-Bazaar-debug-APK`: د نصبولو APK، که build بریالی شوی وي.

## مهم
- دا اتومات راپور جوړوي؛ کوډ پخپله نه بدلوي. د راپور له مخې باید تېروتنې اصلاح شي او workflow بیا وچلول شي.
- APK دلته Debug build دی، د ازموینې لپاره. د عامه خپرولو لپاره Release build، signing او د Firebase/Firestore امنیتي قواعدو جلا بیاکتنه پکار ده.
- د Firebase د اصلي رازونو، service account key یا signing keystore فایلونه عام repository ته مه پورته کوئ. `google-services.json` باید د Firebase پروژې له سم Android package ID سره برابر وي.
