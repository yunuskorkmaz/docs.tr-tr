### <a name="rsacngverifyhash-now-returns-false-for-any-verification-failure"></a>RSACng.VerifyHash için herhangi bir doğrulama hatası şimdi false değerini döndürür

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6.2 ile başlayarak, bu yöntemi döndürür <strong>False</strong> imzası hatalı biçimlendirilmiş olması gerekir. Artık, herhangi bir doğrulama hata için false döndürür. .NET Framework 4.6 ve 4.6.1 çağırılıyorsa yöntem bir <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> imzası hatalı biçimlendirilmiş olması gerekir.|
|Öneri|Yürütme bağlıdır işleme üzerinde herhangi bir kod <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> doğrulama başarısız olursa bunun yerine getirmesi gerekir ve yöntemi <strong>False</strong>.|
|Kapsam|Küçük|
|Sürüm|4.6.2|
|Tür|Çalışma zamanı|
|Etkilenen API'leri|<ul><li><xref:System.Security.Cryptography.RSACng.VerifyHash(System.Byte[],System.Byte[],System.Security.Cryptography.HashAlgorithmName,System.Security.Cryptography.RSASignaturePadding)?displayProperty=nameWithType></li></ul>|

