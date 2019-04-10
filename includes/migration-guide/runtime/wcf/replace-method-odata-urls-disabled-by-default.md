---
ms.openlocfilehash: 6dc3669433804a4524c18d5a932f9879343ab508
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235811"
---
### <a name="the-replace-method-in-odata-urls-is-disabled-by-default"></a><span data-ttu-id="b274e-101">OData URL'lerinde Değiştir yöntemi varsayılan olarak devre dışıdır</span><span class="sxs-lookup"><span data-stu-id="b274e-101">The Replace method in OData URLs is disabled by default</span></span>

|   |   |
|---|---|
|<span data-ttu-id="b274e-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="b274e-102">Details</span></span>|<span data-ttu-id="b274e-103">OData URL'lerinde Değiştir yöntemi, .NET Framework 4. 5 ' başlayarak, varsayılan olarak devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="b274e-103">Beginning in the .NET Framework 4.5, the Replace method in OData URLs is disabled by default.</span></span> <span data-ttu-id="b274e-104">OData Değiştir (şimdi varsayılan olarak) devre dışı bırakıldığında (Bu nadir) Değiştir işlevleri dahil olmak üzere herhangi bir kullanıcı isteğinin başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="b274e-104">When OData Replace is disabled (now by default), any user requests including replace functions (which are uncommon) will fail.</span></span>|
|<span data-ttu-id="b274e-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="b274e-105">Suggestion</span></span>|<span data-ttu-id="b274e-106">Replace yöntemi gerekiyorsa (olduğu genel olmayan), yapılandırma ayarları aracılığıyla yeniden etkin olabilir (<xref:System.Data.Services.Configuration.DataServicesFeaturesSection.ReplaceFunction?displayProperty=name>).</span><span class="sxs-lookup"><span data-stu-id="b274e-106">If the replace method is required (which is uncommon), it can be re-enabled through a config settings (<xref:System.Data.Services.Configuration.DataServicesFeaturesSection.ReplaceFunction?displayProperty=name>).</span></span> <span data-ttu-id="b274e-107">Ancak, bir etkin Değiştir yöntemi güvenlik açıklarını açabilirsiniz ve yalnızca inceledikten sonra kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b274e-107">However, an enabled replace method can open security vulnerabilities and should only be used after careful review.</span></span>|
|<span data-ttu-id="b274e-108">Kapsam</span><span class="sxs-lookup"><span data-stu-id="b274e-108">Scope</span></span>|<span data-ttu-id="b274e-109">Kenar</span><span class="sxs-lookup"><span data-stu-id="b274e-109">Edge</span></span>|
|<span data-ttu-id="b274e-110">Sürüm</span><span class="sxs-lookup"><span data-stu-id="b274e-110">Version</span></span>|<span data-ttu-id="b274e-111">4,5</span><span class="sxs-lookup"><span data-stu-id="b274e-111">4.5</span></span>|
|<span data-ttu-id="b274e-112">Tür</span><span class="sxs-lookup"><span data-stu-id="b274e-112">Type</span></span>|<span data-ttu-id="b274e-113">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="b274e-113">Runtime</span></span>|
|<span data-ttu-id="b274e-114">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="b274e-114">Affected APIs</span></span>|<ul><li><xref:System.Data.Services.DataService%601?displayProperty=nameWithType></li></ul>|
