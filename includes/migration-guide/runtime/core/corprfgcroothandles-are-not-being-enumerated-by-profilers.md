---
ms.openlocfilehash: 4f52535e54607cc824500f9c6a14964a1dec9d32
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620556"
---
### <a name="cor_prf_gc_root_handles-are-not-being-enumerated-by-profilers"></a><span data-ttu-id="d9fb4-101">COR_PRF_GC_ROOT_HANDLEs, profil oluşturucular tarafından numaralandırılmıyor</span><span class="sxs-lookup"><span data-stu-id="d9fb4-101">COR_PRF_GC_ROOT_HANDLEs are not being enumerated by profilers</span></span>

#### <a name="details"></a><span data-ttu-id="d9fb4-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="d9fb4-102">Details</span></span>

<span data-ttu-id="d9fb4-103">.NET Framework v 4.5.1, profil oluşturma API 'SI yanlış bir şekilde <code>RootReferences2()</code> döndürülmez <code>COR_PRF_GC_ROOT_HANDLE</code> ( <code>COR_PRF_GC_ROOT_OTHER</code> bunun yerine döndürülür).</span><span class="sxs-lookup"><span data-stu-id="d9fb4-103">In the .NET Framework v4.5.1, the profiling API <code>RootReferences2()</code> is incorrectly never returning <code>COR_PRF_GC_ROOT_HANDLE</code> (they are returned as <code>COR_PRF_GC_ROOT_OTHER</code> instead).</span></span> <span data-ttu-id="d9fb4-104">Bu sorun 4,6 .NET Framework başlayarak düzeltildi.</span><span class="sxs-lookup"><span data-stu-id="d9fb4-104">This issue is fixed beginning in the .NET Framework 4.6.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="d9fb4-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="d9fb4-105">Suggestion</span></span>

<span data-ttu-id="d9fb4-106">Bu sorun .NET Framework 4,6 ' de düzeltilmiştir ve bu .NET Framework sürümüne yükselterek çözülebilir.</span><span class="sxs-lookup"><span data-stu-id="d9fb4-106">This issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span>

| <span data-ttu-id="d9fb4-107">Name</span><span class="sxs-lookup"><span data-stu-id="d9fb4-107">Name</span></span>    | <span data-ttu-id="d9fb4-108">Değer</span><span class="sxs-lookup"><span data-stu-id="d9fb4-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="d9fb4-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="d9fb4-109">Scope</span></span>   |<span data-ttu-id="d9fb4-110">İkincil</span><span class="sxs-lookup"><span data-stu-id="d9fb4-110">Minor</span></span>|
|<span data-ttu-id="d9fb4-111">Sürüm</span><span class="sxs-lookup"><span data-stu-id="d9fb4-111">Version</span></span>|<span data-ttu-id="d9fb4-112">4.5.1</span><span class="sxs-lookup"><span data-stu-id="d9fb4-112">4.5.1</span></span>|
|<span data-ttu-id="d9fb4-113">Tür</span><span class="sxs-lookup"><span data-stu-id="d9fb4-113">Type</span></span>|<span data-ttu-id="d9fb4-114">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="d9fb4-114">Runtime</span></span>|
