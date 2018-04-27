### <a name="rsacngverifyhash-now-returns-false-for-any-verification-failure"></a>RSACng.VerifyHash, False artık herhangi bir doğrulama hata değerini döndürür.

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6.2 ile başlayarak, bu yöntem <strong>False</strong> imzası hatalı biçimlendirilmiş olması gerekir. Şimdi, herhangi bir doğrulama hata false döndürür. .NET Framework 4.6 ve 4.6.1, yöntem oluşturulur bir <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> imzası hatalı biçimlendirilmiş olması gerekir.|
|Öneri|Yürütme bağlıdır işleme üzerinde herhangi bir kod <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> doğrulama başarısız olursa bunun yerine getirmesi gerekir ve yöntemi <strong>False</strong>.|
|Kapsam|Küçük|
|Sürüm|4.6.2|
|Tür|Çalışma zamanı|
|Etkilenen API'leri|<ul><li><xref:System.Security.Cryptography.RSACng.VerifyHash(System.Byte[],System.Byte[],System.Security.Cryptography.HashAlgorithmName,System.Security.Cryptography.RSASignaturePadding)?displayProperty=nameWithType></li></ul>|

