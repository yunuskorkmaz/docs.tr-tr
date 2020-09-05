---
ms.openlocfilehash: b7b16e39fa5df9732fa769f2bcd3696dff3b2a49
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497047"
---
### <a name="rsacngverifyhash-now-returns-false-for-any-verification-failure"></a>RSACng. VerifyHash şimdi herhangi bir doğrulama hatası için yanlış değer döndürüyor

#### <a name="details"></a>Ayrıntılar

.NET Framework 4.6.2 başlayarak, bu yöntem imza hatalı biçimlendirildiyse **false** değerini döndürür. Artık herhangi bir doğrulama hatası için yanlış döndürür. .NET Framework 4,6 ve 4.6.1 içinde, <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName> imza kötü biçimlenir ise Yöntem bir oluşturur.

#### <a name="suggestion"></a>Öneri

Yürütmesi, <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName> doğrulama başarısız olursa ve Yöntem **false**döndürürse yürütme, bunun yerine yürütülmesi gereken her türlü kod.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |İkincil|
|Sürüm|4.6.2|
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Security.Cryptography.RSACng.VerifyHash(System.Byte[],System.Byte[],System.Security.Cryptography.HashAlgorithmName,System.Security.Cryptography.RSASignaturePadding)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Security.Cryptography.RSACng.VerifyHash(System.Byte[],System.Byte[],System.Security.Cryptography.HashAlgorithmName,System.Security.Cryptography.RSASignaturePadding)`

-->
