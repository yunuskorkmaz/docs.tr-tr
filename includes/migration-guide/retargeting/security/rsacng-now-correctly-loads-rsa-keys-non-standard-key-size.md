---
ms.openlocfilehash: 6d9f4b630e95d9a63393da3ae0ecd83c2b994712
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67859365"
---
### <a name="rsacng-now-correctly-loads-rsa-keys-of-non-standard-key-size"></a>RSACng artık düzgün şekilde standart anahtar boyutu RSA anahtarlarını yüklenir

|   |   |
|---|---|
|Ayrıntılar|Standart anahtar boyutları için RSA sertifikalarını müşterilerle 4.6.2 önce .NET Framework sürümlerinde bu anahtarlar aracılığıyla erişemiyor <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=name> ve <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=name> genişletme yöntemleri.  A <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> iletisiyle &quot;İstenen anahtar boyutu desteklenmiyor&quot; oluşturulur. .NET Framework 4.6.2, bu sorun düzeltilmiştir. Benzer şekilde, <xref:System.Security.Cryptography.RSA.ImportParameters(System.Security.Cryptography.RSAParameters)> ve <xref:System.Security.Cryptography.RSACng.ImportParameters(System.Security.Cryptography.RSAParameters)> standart anahtar boyutları ile durum oluşturmadan çalıştığını bir <xref:System.Security.Cryptography.CryptographicException?displayProperty=name>.|
|Öneri|İşleme mantığı, önceki davranışı güvenen herhangi bir özel durumu ise burada bir <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> standart anahtar boyutları kullanıldığında, özel mantığı kaldırmayı düşünün.|
|`Scope`|Kenar|
|Version|4.6.2|
|Type|Yeniden Hedefleme|
|Etkilenen API’ler|<ul><li><xref:System.Security.Cryptography.RSA.ImportParameters(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.RSACng.ImportParameters(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=nameWithType></li></ul>|

