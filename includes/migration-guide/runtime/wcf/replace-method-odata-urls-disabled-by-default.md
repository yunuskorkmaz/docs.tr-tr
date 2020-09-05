---
ms.openlocfilehash: fccf349517133245ec85ae3c25cedbfb27a7dd8b
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497733"
---
### <a name="the-replace-method-in-odata-urls-is-disabled-by-default"></a><span data-ttu-id="78142-101">OData URL 'Lerinde Replace yöntemi varsayılan olarak devre dışıdır</span><span class="sxs-lookup"><span data-stu-id="78142-101">The Replace method in OData URLs is disabled by default</span></span>

#### <a name="details"></a><span data-ttu-id="78142-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="78142-102">Details</span></span>

<span data-ttu-id="78142-103">.NET Framework 4,5 ' den başlayarak OData URL 'Lerinde Replace yöntemi varsayılan olarak devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="78142-103">Beginning in the .NET Framework 4.5, the Replace method in OData URLs is disabled by default.</span></span> <span data-ttu-id="78142-104">OData Replace devre dışı bırakıldığında (şimdi varsayılan olarak), Replace işlevleri de dahil olmak üzere tüm Kullanıcı istekleri başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="78142-104">When OData Replace is disabled (now by default), any user requests including replace functions (which are uncommon) will fail.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="78142-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="78142-105">Suggestion</span></span>

<span data-ttu-id="78142-106">Replace yöntemi gerekliyse (Bu çok nadir bir durumdur), bir yapılandırma ayarları () aracılığıyla yeniden etkinleştirilebilir <xref:System.Data.Services.Configuration.DataServicesFeaturesSection.ReplaceFunction?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="78142-106">If the replace method is required (which is uncommon), it can be re-enabled through a config settings (<xref:System.Data.Services.Configuration.DataServicesFeaturesSection.ReplaceFunction?displayProperty=fullName>).</span></span> <span data-ttu-id="78142-107">Ancak etkin bir Replace yöntemi güvenlik açıklarını açabilir ve yalnızca dikkatli bir inceleme sonrasında kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="78142-107">However, an enabled replace method can open security vulnerabilities and should only be used after careful review.</span></span>

| <span data-ttu-id="78142-108">Name</span><span class="sxs-lookup"><span data-stu-id="78142-108">Name</span></span>    | <span data-ttu-id="78142-109">Değer</span><span class="sxs-lookup"><span data-stu-id="78142-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="78142-110">Kapsam</span><span class="sxs-lookup"><span data-stu-id="78142-110">Scope</span></span>   |<span data-ttu-id="78142-111">Edge</span><span class="sxs-lookup"><span data-stu-id="78142-111">Edge</span></span>|
|<span data-ttu-id="78142-112">Sürüm</span><span class="sxs-lookup"><span data-stu-id="78142-112">Version</span></span>|<span data-ttu-id="78142-113">4,5</span><span class="sxs-lookup"><span data-stu-id="78142-113">4.5</span></span>|
|<span data-ttu-id="78142-114">Tür</span><span class="sxs-lookup"><span data-stu-id="78142-114">Type</span></span>|<span data-ttu-id="78142-115">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="78142-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="78142-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="78142-116">Affected APIs</span></span>

- <xref:System.Data.Services.DataService%601?displayProperty=nameWithType>

<!--

#### Affected APIs

- ``T:System.Data.Services.DataService`1``

-->
