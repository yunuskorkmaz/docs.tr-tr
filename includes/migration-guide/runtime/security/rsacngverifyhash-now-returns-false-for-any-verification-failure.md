---
ms.openlocfilehash: 7d60578ac2913037e1cdeda329f06f9a4986574d
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67857484"
---
### <a name="rsacngverifyhash-now-returns-false-for-any-verification-failure"></a>RSACng.VerifyHash için herhangi bir doğrulama hatası şimdi false değerini döndürür

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6.2 ile başlayarak, bu yöntemi döndürür <strong>False</strong> imzası hatalı biçimlendirilmiş olması gerekir. Artık, herhangi bir doğrulama hata için false döndürür. .NET Framework 4.6 ve 4.6.1 çağırılıyorsa yöntem bir <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> imzası hatalı biçimlendirilmiş olması gerekir.|
|Öneri|Yürütme bağlıdır işleme üzerinde herhangi bir kod <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> doğrulama başarısız olursa bunun yerine getirmesi gerekir ve yöntemi <strong>False</strong>.|
|`Scope`|Küçük|
|Version|4.6.2|
|Type|Çalışma zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Security.Cryptography.RSACng.VerifyHash(System.Byte[],System.Byte[],System.Security.Cryptography.HashAlgorithmName,System.Security.Cryptography.RSASignaturePadding)?displayProperty=nameWithType></li></ul>|

