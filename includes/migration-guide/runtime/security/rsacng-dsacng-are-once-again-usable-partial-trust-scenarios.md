---
ms.openlocfilehash: e92cbb7decb5e530bbf611cec26ce03a05e06eb3
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622276"
---
### <a name="rsacng-and-dsacng-are-once-again-usable-in-partial-trust-scenarios"></a>RSACng ve DSACng kısmi güven senaryolarında yeniden kullanılabilir

#### <a name="details"></a>Ayrıntılar

Cngmaitipon (gibi, daha üst düzey şifreleme API 'lerinde kullanılır <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=nameWithType> ) ve <xref:System.Security.Cryptography.RSACng?displayProperty=nameWithType> bazı durumlarda tam güvenle yararlanır. Bunlar, izinleri belirtmeden P/Invoke <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode?displayProperty=nameWithType> ve <xref:System.Security.Cryptography.CngKey?displayProperty=nameWithType> için izin taleplerine sahip olan kod yollarını içerir <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode?displayProperty=nameWithType> . .NET Framework 4.6.2 ile başlayarak, mümkün olan her yerde geçiş yapmak için Cngaçıklabir şekilde kullanılmıştı <xref:System.Security.Cryptography.RSACng?displayProperty=nameWithType> . Sonuç olarak, başarıyla kullanılan kısmi güven uygulamaları <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=nameWithType> başarısız olur ve <xref:System.Security.SecurityException> özel durumlar oluşturur. Bu değişiklik, Cngışıklı kullanan tüm işlevlerin gerekli izinlere sahip olması için gerekli onayları ekler.

#### <a name="suggestion"></a>Öneri

.NET Framework 4.6.2 Bu değişiklik, kısmi güven uygulamalarınızı olumsuz yönde etkileirse, .NET Framework 4.7.1 ' ye yükseltin.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |Edge|
|Sürüm|4.6.2|
|Tür|Çalışma Zamanı

#### <a name="affected-apis"></a>Etkilenen API’ler

-<xref:System.Security.Cryptography.DSACng.%23ctor(System.Security.Cryptography.CngKey)></li><li><xref:System.Security.Cryptography.DSACng.Key?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.DSACng.LegalKeySizes?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.DSACng.CreateSignature(System.Byte[])?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.DSACng.VerifySignature(System.Byte[],System.Byte[])?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.RSACng.%23ctor(System.Security.Cryptography.CngKey)></li><li><xref:System.Security.Cryptography.RSACng.Key?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.RSACng.Decrypt(System.Byte[],System.Security.Cryptography.RSAEncryptionPadding)?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.RSACng.SignHash(System.Byte[],System.Security.Cryptography.HashAlgorithmName,System.Security.Cryptography.RSASignaturePadding)?displayProperty=nameWithType></li></ul>|
