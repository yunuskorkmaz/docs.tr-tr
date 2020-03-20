---
ms.openlocfilehash: 4892f75e4ae673d9d9cc7e9eeb6fb9b1a73f572e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67859365"
---
### <a name="rsacng-now-correctly-loads-rsa-keys-of-non-standard-key-size"></a>RSACng artık standart olmayan anahtar boyutundaki RSA tuşlarını doğru bir şekilde yükler

|   |   |
|---|---|
|Ayrıntılar|4.6.2'den önceki .NET Framework sürümlerinde, RSA sertifikaları için standart olmayan anahtar boyutlarına <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=name> <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=name> sahip müşteriler bu anahtarlara ve uzantı yöntemleriyle erişemez.  A <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> iletisi &quot;istenen anahtar boyutu desteklenmiyor&quot; atılır. .NET Framework 4.6.2'de bu sorun giderilmiştir. Benzer <xref:System.Security.Cryptography.RSA.ImportParameters(System.Security.Cryptography.RSAParameters)> şekilde, <xref:System.Security.Cryptography.RSACng.ImportParameters(System.Security.Cryptography.RSAParameters)> ve şimdi standart olmayan anahtar boyutları <xref:System.Security.Cryptography.CryptographicException?displayProperty=name>ile bir atmadan çalışmak .|
|Öneri|Standart olmayan anahtar boyutları kullanıldığında a'nın <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> atıldığı önceki davranışa dayanan bir özel durum işleme mantığı varsa, mantığı kaldırmayı düşünün.|
|Kapsam|Edge|
|Sürüm|4.6.2|
|Tür|Yeniden Hedefleme|
|Etkilenen API’ler|<ul><li><xref:System.Security.Cryptography.RSA.ImportParameters(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.RSACng.ImportParameters(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=nameWithType></li></ul>|
