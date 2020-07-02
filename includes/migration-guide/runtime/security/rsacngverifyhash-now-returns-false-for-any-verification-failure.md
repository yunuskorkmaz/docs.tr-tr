---
ms.openlocfilehash: fa5cf2280cdd9535962568a6272d047d261eeba5
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621380"
---
### <a name="rsacngverifyhash-now-returns-false-for-any-verification-failure"></a><span data-ttu-id="a0ae4-101">RSACng. VerifyHash şimdi herhangi bir doğrulama hatası için yanlış değer döndürüyor</span><span class="sxs-lookup"><span data-stu-id="a0ae4-101">RSACng.VerifyHash now returns False for any verification failure</span></span>

#### <a name="details"></a><span data-ttu-id="a0ae4-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="a0ae4-102">Details</span></span>

<span data-ttu-id="a0ae4-103">.NET Framework 4.6.2 başlayarak, bu yöntem imza hatalı biçimlendirildiyse **false** değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="a0ae4-103">Starting with the .NET Framework 4.6.2, this method returns **False** if the signature itself is badly formatted.</span></span> <span data-ttu-id="a0ae4-104">Artık herhangi bir doğrulama hatası için yanlış döndürür. .NET Framework 4,6 ve 4.6.1 içinde, <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName> imza kötü biçimlenir ise Yöntem bir oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a0ae4-104">It now returns false for any verification failure.In the .NET Framework 4.6 and 4.6.1, the method throws a <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName> if the signature itself is badly formatted.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="a0ae4-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="a0ae4-105">Suggestion</span></span>

<span data-ttu-id="a0ae4-106">Yürütmesi, <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName> doğrulama başarısız olursa ve Yöntem **false**döndürürse yürütme, bunun yerine yürütülmesi gereken her türlü kod.</span><span class="sxs-lookup"><span data-stu-id="a0ae4-106">Any code whose execution depends on handling the <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName> should instead execute if validation fails and the method returns **False**.</span></span>

| <span data-ttu-id="a0ae4-107">Name</span><span class="sxs-lookup"><span data-stu-id="a0ae4-107">Name</span></span>    | <span data-ttu-id="a0ae4-108">Değer</span><span class="sxs-lookup"><span data-stu-id="a0ae4-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="a0ae4-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="a0ae4-109">Scope</span></span>   |<span data-ttu-id="a0ae4-110">İkincil</span><span class="sxs-lookup"><span data-stu-id="a0ae4-110">Minor</span></span>|
|<span data-ttu-id="a0ae4-111">Sürüm</span><span class="sxs-lookup"><span data-stu-id="a0ae4-111">Version</span></span>|<span data-ttu-id="a0ae4-112">4.6.2</span><span class="sxs-lookup"><span data-stu-id="a0ae4-112">4.6.2</span></span>|
|<span data-ttu-id="a0ae4-113">Tür</span><span class="sxs-lookup"><span data-stu-id="a0ae4-113">Type</span></span>|<span data-ttu-id="a0ae4-114">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="a0ae4-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a0ae4-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="a0ae4-115">Affected APIs</span></span>

-<xref:System.Security.Cryptography.RSACng.VerifyHash(System.Byte[],System.Byte[],System.Security.Cryptography.HashAlgorithmName,System.Security.Cryptography.RSASignaturePadding)?displayProperty=nameWithType></li></ul>|
