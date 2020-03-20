---
ms.openlocfilehash: fc315faef750d93d914104dd568078aa3fc430d4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "72887850"
---
### <a name="rsacngverifyhash-now-returns-false-for-any-verification-failure"></a>RSACng.VerifyHash şimdi herhangi bir doğrulama hatası için False döndürür

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6.2 ile başlayarak, imzanın kendisi kötü biçimlendirilmişse bu yöntem **False** döndürür. Şimdi herhangi bir doğrulama hatası için yanlış döndürür. .NET Framework 4.6 ve 4.6.1'de, <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> imzanın kendisi kötü biçimlendirilmişse yöntem bir yöntem atar.|
|Öneri|Yürütme işleme bağlıdır herhangi bir <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> kod doğrulama başarısız olursa ve yöntem **False**döndürür yerine yürütme gerekir .|
|Kapsam|İkincil|
|Sürüm|4.6.2|
|Tür|Çalışma Zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Security.Cryptography.RSACng.VerifyHash(System.Byte[],System.Byte[],System.Security.Cryptography.HashAlgorithmName,System.Security.Cryptography.RSASignaturePadding)?displayProperty=nameWithType></li></ul>|
