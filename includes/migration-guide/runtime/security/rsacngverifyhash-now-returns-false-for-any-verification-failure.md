---
ms.openlocfilehash: fc315faef750d93d914104dd568078aa3fc430d4
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72887850"
---
### <a name="rsacngverifyhash-now-returns-false-for-any-verification-failure"></a><span data-ttu-id="2a32e-101">RSACng. VerifyHash şimdi herhangi bir doğrulama hatası için yanlış değer döndürüyor</span><span class="sxs-lookup"><span data-stu-id="2a32e-101">RSACng.VerifyHash now returns False for any verification failure</span></span>

|   |   |
|---|---|
|<span data-ttu-id="2a32e-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="2a32e-102">Details</span></span>|<span data-ttu-id="2a32e-103">.NET Framework 4.6.2 başlayarak, bu yöntem imza hatalı biçimlendirildiyse **false** değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="2a32e-103">Starting with the .NET Framework 4.6.2, this method returns **False** if the signature itself is badly formatted.</span></span> <span data-ttu-id="2a32e-104">Artık herhangi bir doğrulama hatası için yanlış döndürür. .NET Framework 4,6 ve 4.6.1 içinde, imza kötü biçimlenir ise Yöntem bir <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2a32e-104">It now returns false for any verification failure.In the .NET Framework 4.6 and 4.6.1, the method throws a <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> if the signature itself is badly formatted.</span></span>|
|<span data-ttu-id="2a32e-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="2a32e-105">Suggestion</span></span>|<span data-ttu-id="2a32e-106">Yürütmesi <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> işlemeye bağlı olan tüm kodlar, doğrulama başarısız olursa ve Yöntem **false**döndürürse yürütülür.</span><span class="sxs-lookup"><span data-stu-id="2a32e-106">Any code whose execution depends on handling the <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> should instead execute if validation fails and the method returns **False**.</span></span>|
|<span data-ttu-id="2a32e-107">Kapsam</span><span class="sxs-lookup"><span data-stu-id="2a32e-107">Scope</span></span>|<span data-ttu-id="2a32e-108">İkincil</span><span class="sxs-lookup"><span data-stu-id="2a32e-108">Minor</span></span>|
|<span data-ttu-id="2a32e-109">Version</span><span class="sxs-lookup"><span data-stu-id="2a32e-109">Version</span></span>|<span data-ttu-id="2a32e-110">4.6.2</span><span class="sxs-lookup"><span data-stu-id="2a32e-110">4.6.2</span></span>|
|<span data-ttu-id="2a32e-111">Tür</span><span class="sxs-lookup"><span data-stu-id="2a32e-111">Type</span></span>|<span data-ttu-id="2a32e-112">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="2a32e-112">Runtime</span></span>|
|<span data-ttu-id="2a32e-113">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="2a32e-113">Affected APIs</span></span>|<ul><li><xref:System.Security.Cryptography.RSACng.VerifyHash(System.Byte[],System.Byte[],System.Security.Cryptography.HashAlgorithmName,System.Security.Cryptography.RSASignaturePadding)?displayProperty=nameWithType></li></ul>|
