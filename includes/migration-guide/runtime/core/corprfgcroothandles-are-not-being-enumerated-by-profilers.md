---
ms.openlocfilehash: 25437dcc0c814ed2265b2efb34316af48b372ebd
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497796"
---
### <a name="cor_prf_gc_root_handles-are-not-being-enumerated-by-profilers"></a><span data-ttu-id="5a3ae-101">COR_PRF_GC_ROOT_HANDLEs, profil oluşturucular tarafından numaralandırılmıyor</span><span class="sxs-lookup"><span data-stu-id="5a3ae-101">COR_PRF_GC_ROOT_HANDLEs are not being enumerated by profilers</span></span>

#### <a name="details"></a><span data-ttu-id="5a3ae-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="5a3ae-102">Details</span></span>

<span data-ttu-id="5a3ae-103">.NET Framework v 4.5.1, profil oluşturma API 'SI yanlış bir şekilde <code>RootReferences2()</code> döndürülmez <code>COR_PRF_GC_ROOT_HANDLE</code> ( <code>COR_PRF_GC_ROOT_OTHER</code> bunun yerine döndürülür).</span><span class="sxs-lookup"><span data-stu-id="5a3ae-103">In the .NET Framework v4.5.1, the profiling API <code>RootReferences2()</code> is incorrectly never returning <code>COR_PRF_GC_ROOT_HANDLE</code> (they are returned as <code>COR_PRF_GC_ROOT_OTHER</code> instead).</span></span> <span data-ttu-id="5a3ae-104">Bu sorun 4,6 .NET Framework başlayarak düzeltildi.</span><span class="sxs-lookup"><span data-stu-id="5a3ae-104">This issue is fixed beginning in the .NET Framework 4.6.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="5a3ae-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="5a3ae-105">Suggestion</span></span>

<span data-ttu-id="5a3ae-106">Bu sorun .NET Framework 4,6 ' de düzeltilmiştir ve bu .NET Framework sürümüne yükselterek çözülebilir.</span><span class="sxs-lookup"><span data-stu-id="5a3ae-106">This issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span>

| <span data-ttu-id="5a3ae-107">Name</span><span class="sxs-lookup"><span data-stu-id="5a3ae-107">Name</span></span>    | <span data-ttu-id="5a3ae-108">Değer</span><span class="sxs-lookup"><span data-stu-id="5a3ae-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="5a3ae-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="5a3ae-109">Scope</span></span>   |<span data-ttu-id="5a3ae-110">İkincil</span><span class="sxs-lookup"><span data-stu-id="5a3ae-110">Minor</span></span>|
|<span data-ttu-id="5a3ae-111">Sürüm</span><span class="sxs-lookup"><span data-stu-id="5a3ae-111">Version</span></span>|<span data-ttu-id="5a3ae-112">4.5.1</span><span class="sxs-lookup"><span data-stu-id="5a3ae-112">4.5.1</span></span>|
|<span data-ttu-id="5a3ae-113">Tür</span><span class="sxs-lookup"><span data-stu-id="5a3ae-113">Type</span></span>|<span data-ttu-id="5a3ae-114">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="5a3ae-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="5a3ae-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="5a3ae-115">Affected APIs</span></span>

<span data-ttu-id="5a3ae-116">API analizi aracılığıyla algılanamaz.</span><span class="sxs-lookup"><span data-stu-id="5a3ae-116">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
