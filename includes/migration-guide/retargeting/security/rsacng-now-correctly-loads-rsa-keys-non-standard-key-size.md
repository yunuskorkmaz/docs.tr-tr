---
ms.openlocfilehash: 4892f75e4ae673d9d9cc7e9eeb6fb9b1a73f572e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59805324"
---
### <a name="rsacng-now-correctly-loads-rsa-keys-of-non-standard-key-size"></a>RSACng artık düzgün şekilde standart anahtar boyutu RSA anahtarlarını yüklenir

|   |   |
|---|---|
|Ayrıntılar|Standart anahtar boyutları için RSA sertifikalarını müşterilerle 4.6.2 önce .NET Framework sürümlerinde bu anahtarlar aracılığıyla erişemiyor <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=name> ve <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=name> genişletme yöntemleri.  A <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> iletisiyle &quot;İstenen anahtar boyutu desteklenmiyor&quot; oluşturulur. .NET Framework 4.6.2, bu sorun düzeltilmiştir. Benzer şekilde, <xref:System.Security.Cryptography.RSA.ImportParameters(System.Security.Cryptography.RSAParameters)> ve <xref:System.Security.Cryptography.RSACng.ImportParameters(System.Security.Cryptography.RSAParameters)> standart anahtar boyutları ile durum oluşturmadan çalıştığını bir <xref:System.Security.Cryptography.CryptographicException?displayProperty=name>.|
|Öneri|İşleme mantığı, önceki davranışı güvenen herhangi bir özel durumu ise burada bir <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> standart anahtar boyutları kullanıldığında, özel mantığı kaldırmayı düşünün.|
|Kapsam|Kenar|
|Sürüm|4.6.2|
|Tür|Yeniden Hedefleme|
|Etkilenen API’ler|<ul><li><xref:System.Security.Cryptography.RSA.ImportParameters(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.RSACng.ImportParameters(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=nameWithType></li></ul>|
