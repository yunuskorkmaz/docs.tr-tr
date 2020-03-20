---
ms.openlocfilehash: fc315faef750d93d914104dd568078aa3fc430d4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "72887850"
---
### <a name="rsacngverifyhash-now-returns-false-for-any-verification-failure"></a><span data-ttu-id="04a3f-101">RSACng.VerifyHash şimdi herhangi bir doğrulama hatası için False döndürür</span><span class="sxs-lookup"><span data-stu-id="04a3f-101">RSACng.VerifyHash now returns False for any verification failure</span></span>

|   |   |
|---|---|
|<span data-ttu-id="04a3f-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="04a3f-102">Details</span></span>|<span data-ttu-id="04a3f-103">.NET Framework 4.6.2 ile başlayarak, imzanın kendisi kötü biçimlendirilmişse bu yöntem **False** döndürür.</span><span class="sxs-lookup"><span data-stu-id="04a3f-103">Starting with the .NET Framework 4.6.2, this method returns **False** if the signature itself is badly formatted.</span></span> <span data-ttu-id="04a3f-104">Şimdi herhangi bir doğrulama hatası için yanlış döndürür. .NET Framework 4.6 ve 4.6.1'de, <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> imzanın kendisi kötü biçimlendirilmişse yöntem bir yöntem atar.</span><span class="sxs-lookup"><span data-stu-id="04a3f-104">It now returns false for any verification failure.In the .NET Framework 4.6 and 4.6.1, the method throws a <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> if the signature itself is badly formatted.</span></span>|
|<span data-ttu-id="04a3f-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="04a3f-105">Suggestion</span></span>|<span data-ttu-id="04a3f-106">Yürütme işleme bağlıdır herhangi bir <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> kod doğrulama başarısız olursa ve yöntem **False**döndürür yerine yürütme gerekir .</span><span class="sxs-lookup"><span data-stu-id="04a3f-106">Any code whose execution depends on handling the <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> should instead execute if validation fails and the method returns **False**.</span></span>|
|<span data-ttu-id="04a3f-107">Kapsam</span><span class="sxs-lookup"><span data-stu-id="04a3f-107">Scope</span></span>|<span data-ttu-id="04a3f-108">İkincil</span><span class="sxs-lookup"><span data-stu-id="04a3f-108">Minor</span></span>|
|<span data-ttu-id="04a3f-109">Sürüm</span><span class="sxs-lookup"><span data-stu-id="04a3f-109">Version</span></span>|<span data-ttu-id="04a3f-110">4.6.2</span><span class="sxs-lookup"><span data-stu-id="04a3f-110">4.6.2</span></span>|
|<span data-ttu-id="04a3f-111">Tür</span><span class="sxs-lookup"><span data-stu-id="04a3f-111">Type</span></span>|<span data-ttu-id="04a3f-112">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="04a3f-112">Runtime</span></span>|
|<span data-ttu-id="04a3f-113">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="04a3f-113">Affected APIs</span></span>|<ul><li><xref:System.Security.Cryptography.RSACng.VerifyHash(System.Byte[],System.Byte[],System.Security.Cryptography.HashAlgorithmName,System.Security.Cryptography.RSASignaturePadding)?displayProperty=nameWithType></li></ul>|
