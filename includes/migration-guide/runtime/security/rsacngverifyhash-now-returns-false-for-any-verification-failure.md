---
ms.openlocfilehash: fc315faef750d93d914104dd568078aa3fc430d4
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72887850"
---
### <a name="rsacngverifyhash-now-returns-false-for-any-verification-failure"></a>RSACng. VerifyHash şimdi herhangi bir doğrulama hatası için yanlış değer döndürüyor

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6.2 başlayarak, bu yöntem imza hatalı biçimlendirildiyse **false** değerini döndürür. Artık herhangi bir doğrulama hatası için yanlış döndürür. .NET Framework 4,6 ve 4.6.1 içinde, imza kötü biçimlenir ise Yöntem bir <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> oluşturur.|
|Öneri|Yürütmesi <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> işlemeye bağlı olan tüm kodlar, doğrulama başarısız olursa ve Yöntem **false**döndürürse yürütülür.|
|Kapsam|İkincil|
|Version|4.6.2|
|Tür|Çalışma zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Security.Cryptography.RSACng.VerifyHash(System.Byte[],System.Byte[],System.Security.Cryptography.HashAlgorithmName,System.Security.Cryptography.RSASignaturePadding)?displayProperty=nameWithType></li></ul>|
