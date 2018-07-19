### <a name="apps-published-with-clickonce-that-use-a-sha-256-code-signing-certificate-may-fail-on-windows-2003"></a>Windows 2003'te SHA-256 kod imzalama sertifikası kullanan ClickOnce ile yayımlanan uygulamalar başarısız olabilir

|   |   |
|---|---|
|Ayrıntılar|Yürütülebilir dosya ile SHA256 imzalanır. Daha önce kod imzalama sertifikası SHA-1 veya SHA-256'yı olup olmadığından bağımsız olarak SHA1 ile imzalandığından. Bu geçerlidir:<ul><li>Visual Studio 2012 veya daha sonra oluşturulan tüm uygulamalar.</li><li>Visual Studio 2010 veya önceki üzerinde sistemleri ile mevcut .NET Framework 4.5 ile oluşturulmuş uygulamalar.</li></ul>.NET Framework 4.5 veya sonraki bir sürümü varsa, ek olarak, ClickOnce bildirimi ayrıca SHA-256'yı SHA-256'yı sertifikalara karşı derlenen .NET Framework sürümünden bağımsız olarak imzalanır.|
|Öneri|ClickOnce yürütülebilir imzalama değişikliği yalnızca Windows Server 2003 sistemlerinde etkiler; Bunlar, KB 938397 yüklü olmasını gerektirir. Değişiklik bildirimine SHA-256'yı imzalama uygulama .NET Framework 4.0 veya daha önceki sürümlerini hedeflemiş olsa bile, .NET Framework 4.5 veya sonraki bir sürümü çalışma zamanı bağımlılık tanıtır.|
|Kapsam|Kenar|
|Sürüm|4,5|
|Tür|Yeniden hedefleme|

