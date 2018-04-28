### <a name="apps-published-with-clickonce-that-use-a-sha-256-code-signing-certificate-may-fail-on-windows-2003"></a>Windows 2003'te, SHA-256 kod imzalama sertifikası kullanan ClickOnce ile yayımlanan uygulamalar başarısız olabilir

|   |   |
|---|---|
|Ayrıntılar|Yürütülebilir dosya ile SHA256 imzalanır. Daha önce kod imzalama sertifikası SHA-1 veya SHA-256 bağımsız olarak SHA1 ile imzalandığından. Bu geçerlidir:<ul><li>Visual Studio 2012 veya daha sonra oluşturulan tüm uygulamaların.</li><li>Visual Studio 2010 veya önceki üzerinde sistemleriyle mevcut .NET Framework 4.5 ile oluşturulmuş uygulamalar.</li></ul>.NET Framework 4.5 veya üzeri varsa, ayrıca, ClickOnce bildirimi ayrıca SHA-256 ile SHA-256 sertifikalara karşı derlenen .NET Framework sürüm bağımsız olarak imzalanır.|
|Öneri|Yürütülebilir ClickOnce imzalama değişikliği yalnızca Windows Server 2003 sistemlerinde etkiler; Bunlar, KB 938397 yüklü olmasını gerektirir. Değişiklik bildirimini SHA-256 ile imzalama bile bir uygulama .NET Framework 4.0 veya daha önceki sürümlerini hedeflediğinde çalışma zamanı bağımlılık .NET Framework 4.5 veya sonraki bir sürümünü sunmaktadır.|
|Kapsam|Kenar|
|Sürüm|4,5|
|Tür|Yeniden hedefleme|

