วิธีได้ APK โดยไม่ต้องลง Android Studio (ใช้ GitHub Actions ฟรี):
  1) สร้าง repo ใหม่บน GitHub (private ก็ได้) แล้วอัปโหลดไฟล์ในโฟลเดอร์นี้ทั้งหมด (รวมโฟลเดอร์ .github)
  2) แท็บ Actions > Build APK > Run workflow (รอ ~5-8 นาที)
  3) เปิดรันที่เสร็จ > Artifacts > cabby-drivers-apk > ดาวน์โหลด แตกซิป จะได้ app-debug.apk
  4) ส่งไฟล์เข้ามือถือ Android แล้วติดตั้ง (อนุญาต "ติดตั้งจากแหล่งที่ไม่รู้จัก")

หรือ build เองบนเครื่อง (Node 20, JDK 17, Android SDK):
  npm install && npx cap add android
  (เพิ่มสิทธิ์ INTERNET, ACCESS_FINE_LOCATION, ACCESS_COARSE_LOCATION, CAMERA ใน AndroidManifest.xml)
  npm run build:android
  ผลลัพธ์: android/app/build/outputs/apk/debug/app-debug.apk

อัปเดตแอป: แทนที่ www/index.html ด้วย driver.html ใหม่ แล้ว build ใหม่
ข้อจำกัด: ไฟล์เป็น debug-signed (ติดตั้งตรงได้ แต่ขึ้น Play Store ไม่ได้), Web Push (FCM) ไม่ทำงานใน WebView ของ APK
