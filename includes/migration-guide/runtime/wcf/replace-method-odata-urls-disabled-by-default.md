---
ms.openlocfilehash: b2fcacdb02c411c4dcb12051bf0c6759faccdea2
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620664"
---
### <a name="the-replace-method-in-odata-urls-is-disabled-by-default"></a><span data-ttu-id="61212-101">OData URL 'Lerinde Replace yöntemi varsayılan olarak devre dışıdır</span><span class="sxs-lookup"><span data-stu-id="61212-101">The Replace method in OData URLs is disabled by default</span></span>

#### <a name="details"></a><span data-ttu-id="61212-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="61212-102">Details</span></span>

<span data-ttu-id="61212-103">.NET Framework 4,5 ' den başlayarak OData URL 'Lerinde Replace yöntemi varsayılan olarak devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="61212-103">Beginning in the .NET Framework 4.5, the Replace method in OData URLs is disabled by default.</span></span> <span data-ttu-id="61212-104">OData Replace devre dışı bırakıldığında (şimdi varsayılan olarak), Replace işlevleri de dahil olmak üzere tüm Kullanıcı istekleri başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="61212-104">When OData Replace is disabled (now by default), any user requests including replace functions (which are uncommon) will fail.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="61212-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="61212-105">Suggestion</span></span>

<span data-ttu-id="61212-106">Replace yöntemi gerekliyse (Bu çok nadir bir durumdur), bir yapılandırma ayarları () aracılığıyla yeniden etkinleştirilebilir <xref:System.Data.Services.Configuration.DataServicesFeaturesSection.ReplaceFunction?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="61212-106">If the replace method is required (which is uncommon), it can be re-enabled through a config settings (<xref:System.Data.Services.Configuration.DataServicesFeaturesSection.ReplaceFunction?displayProperty=fullName>).</span></span> <span data-ttu-id="61212-107">Ancak etkin bir Replace yöntemi güvenlik açıklarını açabilir ve yalnızca dikkatli bir inceleme sonrasında kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="61212-107">However, an enabled replace method can open security vulnerabilities and should only be used after careful review.</span></span>

| <span data-ttu-id="61212-108">Name</span><span class="sxs-lookup"><span data-stu-id="61212-108">Name</span></span>    | <span data-ttu-id="61212-109">Değer</span><span class="sxs-lookup"><span data-stu-id="61212-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="61212-110">Kapsam</span><span class="sxs-lookup"><span data-stu-id="61212-110">Scope</span></span>   |<span data-ttu-id="61212-111">Edge</span><span class="sxs-lookup"><span data-stu-id="61212-111">Edge</span></span>|
|<span data-ttu-id="61212-112">Sürüm</span><span class="sxs-lookup"><span data-stu-id="61212-112">Version</span></span>|<span data-ttu-id="61212-113">4,5</span><span class="sxs-lookup"><span data-stu-id="61212-113">4.5</span></span>|
|<span data-ttu-id="61212-114">Tür</span><span class="sxs-lookup"><span data-stu-id="61212-114">Type</span></span>|<span data-ttu-id="61212-115">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="61212-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="61212-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="61212-116">Affected APIs</span></span>

-<xref:System.Data.Services.DataService%601?displayProperty=nameWithType></li></ul>|
