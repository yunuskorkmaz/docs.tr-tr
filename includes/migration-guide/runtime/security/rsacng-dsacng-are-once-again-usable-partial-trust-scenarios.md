---
ms.openlocfilehash: b3bf169f60279d245568367afb0bfe004c4ebcd7
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81275002"
---
### <a name="rsacng-and-dsacng-are-once-again-usable-in-partial-trust-scenarios"></a>RSACng ve DSACng kısmi güven senaryolarında bir kez daha kullanılabilir

|   |   |
|---|---|
|Ayrıntılar|CngLightup (birkaç üst düzey kripto apis <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=nameWithType>kullanılır, <xref:System.Security.Cryptography.RSACng?displayProperty=nameWithType> gibi) ve bazı durumlarda tam güven güveniyor. Bunlar arasında <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode?displayProperty=nameWithType> izin vermeden P/Invokes ve izin <xref:System.Security.Cryptography.CngKey?displayProperty=nameWithType> taleplerinin <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode?displayProperty=nameWithType>bulunduğu kod yolları yer alıyor. .NET Framework 4.6.2 ile başlayarak, CngLightup <xref:System.Security.Cryptography.RSACng?displayProperty=nameWithType> mümkün olan her yere geçmek için kullanıldı. Sonuç olarak, başarıyla kullanılan <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=nameWithType> kısmi güven uygulamaları <xref:System.Security.SecurityException> başarısız olmaya ve özel durumlar atmaya başladı. Bu değişiklik, CngLightup kullanan tüm işlevlerin gerekli izinlere sahip olması için gerekli ileri leri ekler.|
|Öneri|.NET Framework 4.6.2'deki bu değişiklik kısmi güven uygulamalarınızı olumsuz etkilediyse,.NET Framework 4.7.1'e yükseltin.|
|Kapsam|Edge|
|Sürüm|4.6.2|
|Tür|Çalışma Zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Security.Cryptography.DSACng.%23ctor(System.Security.Cryptography.CngKey)></li><li><xref:System.Security.Cryptography.DSACng.Key?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.DSACng.LegalKeySizes?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.DSACng.CreateSignature(System.Byte[])?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.DSACng.VerifySignature(System.Byte[],System.Byte[])?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.RSACng.%23ctor(System.Security.Cryptography.CngKey)></li><li><xref:System.Security.Cryptography.RSACng.Key?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.RSACng.Decrypt(System.Byte[],System.Security.Cryptography.RSAEncryptionPadding)?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.RSACng.SignHash(System.Byte[],System.Security.Cryptography.HashAlgorithmName,System.Security.Cryptography.RSASignaturePadding)?displayProperty=nameWithType></li></ul>|
