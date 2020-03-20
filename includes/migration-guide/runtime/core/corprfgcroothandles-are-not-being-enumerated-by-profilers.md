---
ms.openlocfilehash: 8433899058c6f569e380999800557dbe8ed0a169
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858573"
---
### <a name="cor_prf_gc_root_handles-are-not-being-enumerated-by-profilers"></a><span data-ttu-id="51fb1-101">COR_PRF_GC_ROOT_HANDLEs profilciler tarafından numaralandırılmıyor</span><span class="sxs-lookup"><span data-stu-id="51fb1-101">COR_PRF_GC_ROOT_HANDLEs are not being enumerated by profilers</span></span>

|   |   |
|---|---|
|<span data-ttu-id="51fb1-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="51fb1-102">Details</span></span>|<span data-ttu-id="51fb1-103">.NET Framework v4.5.1'de profil oluşturma <code>RootReferences2()</code> API'si <code>COR_PRF_GC_ROOT_HANDLE</code> yanlış bir <code>COR_PRF_GC_ROOT_OTHER</code> şekilde asla döndürülmez (bunun yerine döndürülürler).</span><span class="sxs-lookup"><span data-stu-id="51fb1-103">In the .NET Framework v4.5.1, the profiling API <code>RootReferences2()</code> is incorrectly never returning <code>COR_PRF_GC_ROOT_HANDLE</code> (they are returned as <code>COR_PRF_GC_ROOT_OTHER</code> instead).</span></span> <span data-ttu-id="51fb1-104">Bu sorun .NET Framework 4.6'dan başlayarak giderilmiştir.</span><span class="sxs-lookup"><span data-stu-id="51fb1-104">This issue is fixed beginning in the .NET Framework 4.6.</span></span>|
|<span data-ttu-id="51fb1-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="51fb1-105">Suggestion</span></span>|<span data-ttu-id="51fb1-106">Bu sorun .NET Framework 4.6'da giderilmiştir ve .NET Framework'ün bu sürümüne yükseltilerek giderilebilir.</span><span class="sxs-lookup"><span data-stu-id="51fb1-106">This issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span>|
|<span data-ttu-id="51fb1-107">Kapsam</span><span class="sxs-lookup"><span data-stu-id="51fb1-107">Scope</span></span>|<span data-ttu-id="51fb1-108">İkincil</span><span class="sxs-lookup"><span data-stu-id="51fb1-108">Minor</span></span>|
|<span data-ttu-id="51fb1-109">Sürüm</span><span class="sxs-lookup"><span data-stu-id="51fb1-109">Version</span></span>|<span data-ttu-id="51fb1-110">4.5.1</span><span class="sxs-lookup"><span data-stu-id="51fb1-110">4.5.1</span></span>|
|<span data-ttu-id="51fb1-111">Tür</span><span class="sxs-lookup"><span data-stu-id="51fb1-111">Type</span></span>|<span data-ttu-id="51fb1-112">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="51fb1-112">Runtime</span></span>|
