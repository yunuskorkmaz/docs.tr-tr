---
ms.openlocfilehash: c1e85941c8c6c31c7d937d0671ad955fa6490783
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614654"
---
### <a name="rsacng-now-correctly-loads-rsa-keys-of-non-standard-key-size"></a>RSACng artık standart olmayan anahtar boyutunun RSA anahtarlarını doğru şekilde yükler

#### <a name="details"></a>Ayrıntılar

4.6.2 ' den önceki .NET Framework sürümlerde, RSA sertifikaları için standart olmayan anahtar boyutlarına sahip müşteriler bu anahtarlara <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=fullName> ve <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=fullName> genişletme yöntemleriyle erişemez.  <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName>İleti ile &quot; İstenen anahtar boyutu desteklenmiyor &quot; . .NET Framework 4.6.2 Bu sorun düzeltildi. Benzer şekilde, <xref:System.Security.Cryptography.RSA.ImportParameters(System.Security.Cryptography.RSAParameters)> ve <xref:System.Security.Cryptography.RSACng.ImportParameters(System.Security.Cryptography.RSAParameters)> Şimdi bir oluşturmadan standart olmayan anahtar boyutlarıyla çalışır <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName> .

#### <a name="suggestion"></a>Öneri

Standart olmayan anahtar boyutları kullanıldığında, bir önceki davranışa dayanan özel durum işleme mantığı varsa <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName> , mantığı kaldırmayı düşünün.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | Edge        |
| Sürüm | 4.6.2       |
| Tür    | Yeniden Hedefleme |

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Security.Cryptography.RSA.ImportParameters(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSACng.ImportParameters(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=nameWithType>
