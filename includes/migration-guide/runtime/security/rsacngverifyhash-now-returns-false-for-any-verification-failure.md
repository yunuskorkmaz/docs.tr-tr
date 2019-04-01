---
ms.openlocfilehash: 7d60578ac2913037e1cdeda329f06f9a4986574d
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760697"
---
### <a name="rsacngverifyhash-now-returns-false-for-any-verification-failure"></a><span data-ttu-id="e0ead-101">RSACng.VerifyHash için herhangi bir doğrulama hatası şimdi false değerini döndürür</span><span class="sxs-lookup"><span data-stu-id="e0ead-101">RSACng.VerifyHash now returns False for any verification failure</span></span>

|   |   |
|---|---|
|<span data-ttu-id="e0ead-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="e0ead-102">Details</span></span>|<span data-ttu-id="e0ead-103">.NET Framework 4.6.2 ile başlayarak, bu yöntemi döndürür <strong>False</strong> imzası hatalı biçimlendirilmiş olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e0ead-103">Starting with the .NET Framework 4.6.2, this method returns <strong>False</strong> if the signature itself is badly formatted.</span></span> <span data-ttu-id="e0ead-104">Artık, herhangi bir doğrulama hata için false döndürür. .NET Framework 4.6 ve 4.6.1 çağırılıyorsa yöntem bir <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> imzası hatalı biçimlendirilmiş olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e0ead-104">It now returns false for any verification failure.In the .NET Framework 4.6 and 4.6.1, the method throws a <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> if the signature itself is badly formatted.</span></span>|
|<span data-ttu-id="e0ead-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="e0ead-105">Suggestion</span></span>|<span data-ttu-id="e0ead-106">Yürütme bağlıdır işleme üzerinde herhangi bir kod <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> doğrulama başarısız olursa bunun yerine getirmesi gerekir ve yöntemi <strong>False</strong>.</span><span class="sxs-lookup"><span data-stu-id="e0ead-106">Any code whose execution depends on handling the <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> should instead execute if validation fails and the method returns <strong>False</strong>.</span></span>|
|<span data-ttu-id="e0ead-107">Kapsam</span><span class="sxs-lookup"><span data-stu-id="e0ead-107">Scope</span></span>|<span data-ttu-id="e0ead-108">İkincil</span><span class="sxs-lookup"><span data-stu-id="e0ead-108">Minor</span></span>|
|<span data-ttu-id="e0ead-109">Sürüm</span><span class="sxs-lookup"><span data-stu-id="e0ead-109">Version</span></span>|<span data-ttu-id="e0ead-110">4.6.2</span><span class="sxs-lookup"><span data-stu-id="e0ead-110">4.6.2</span></span>|
|<span data-ttu-id="e0ead-111">Tür</span><span class="sxs-lookup"><span data-stu-id="e0ead-111">Type</span></span>|<span data-ttu-id="e0ead-112">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="e0ead-112">Runtime</span></span>|
|<span data-ttu-id="e0ead-113">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="e0ead-113">Affected APIs</span></span>|<ul><li><xref:System.Security.Cryptography.RSACng.VerifyHash(System.Byte[],System.Byte[],System.Security.Cryptography.HashAlgorithmName,System.Security.Cryptography.RSASignaturePadding)?displayProperty=nameWithType></li></ul>|

