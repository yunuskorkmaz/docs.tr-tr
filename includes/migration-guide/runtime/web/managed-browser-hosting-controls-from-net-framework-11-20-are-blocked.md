### <a name="managed-browser-hosting-controls-from-the-net-framework-11-and-20-are-blocked"></a>.NET Framework 1.1 ve 2.0 barındırma denetimlerden yönetilen tarayıcı erişimi engellenir

|   |   |
|---|---|
|Ayrıntılar|Bu kontrollerin barındırılması Internet Explorer'da engellenir.|
|Öneri|Internet Explorer tarayıcı barındırma kontrollerini kullanan bir uygulamayı başlatmakta başarısız olacaktır. Kayıt defteri alt anahtarı EnableIEHosting değerini ayarlayarak önceki davranış geri yüklenebilir <code>HKLM/SOFTWARE/MICROSOFT/.NETFramework</code> için <code>1</code> x86 için sistemleri ve x64 32-bit işlemleri için sistemleri ve ayarlayarak <code>EnableIEHosting</code> kayıt defteri alt anahtarı değerini<code>HKLM/SOFTWARE/Wow6432Node/Microsoft/.NETFramework</code>için <code>1</code> x64 64 bit işlemleri için sistemler.|
|Kapsam|Küçük|
|Sürüm|4,5|
|Tür|Çalışma zamanı|

