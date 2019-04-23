---
title: ICorProfilerInfo7 Arabirimi
ms.date: 03/30/2017
ms.assetid: cf37c462-73c5-412a-a7f8-bb26ca746313
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6d8586031c5bcb0303a64b67ee601fe41b81ee3f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59134873"
---
# <a name="icorprofilerinfo7-interface"></a><span data-ttu-id="3379f-102">ICorProfilerInfo7 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3379f-102">ICorProfilerInfo7 Interface</span></span>
<span data-ttu-id="3379f-103">[Desteklenen [!INCLUDE[net_v461](../../../../includes/net-v461-md.md)] ve sonraki sürümlerinde]</span><span class="sxs-lookup"><span data-stu-id="3379f-103">[Supported in the [!INCLUDE[net_v461](../../../../includes/net-v461-md.md)] and later versions]</span></span>  
  
 <span data-ttu-id="3379f-104">Öğesinin [Icorprofilerınfo6](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md) yeni uygulamak için bir yöntem bir modül için meta verileri tanımlanmış ve bir bellek içi sembol akışına erişim sağlayan sağlar.</span><span class="sxs-lookup"><span data-stu-id="3379f-104">A subclass of [ICorProfilerInfo6](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md) that provides a method to apply newly defined metadata to a module and that provides access to an in-memory symbol stream.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3379f-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="3379f-105">Methods</span></span>  
  
|<span data-ttu-id="3379f-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="3379f-106">Method</span></span>|<span data-ttu-id="3379f-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3379f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3379f-108">ApplyMetaData Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3379f-108">ApplyMetaData Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-applymetadata-method.md)|<span data-ttu-id="3379f-109">Yeni tarafından tanımlanan meta veriler geçerli `IMetadataEmit::Define*` Belirtilen modül için yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="3379f-109">Applies the metadata newly defined by the `IMetadataEmit::Define*` methods to a specified module.</span></span>|  
|[<span data-ttu-id="3379f-110">GetInMemorySymbolsLength Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3379f-110">GetInMemorySymbolsLength Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-getinmemorysymbolslength-method.md)|<span data-ttu-id="3379f-111">Bir bellek içi sembol akış uzunluğunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="3379f-111">Returns the length of an in-memory symbol stream.</span></span>|  
|[<span data-ttu-id="3379f-112">ReadInMemorySymbols</span><span class="sxs-lookup"><span data-stu-id="3379f-112">ReadInMemorySymbols</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-readinmemorysymbols.md)|<span data-ttu-id="3379f-113">Bayt bir bellek içi sembol akıştan okur.</span><span class="sxs-lookup"><span data-stu-id="3379f-113">Reads bytes from an in-memory symbol stream.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3379f-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3379f-114">Requirements</span></span>  
 <span data-ttu-id="3379f-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3379f-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3379f-116">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3379f-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3379f-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3379f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3379f-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3379f-118">See also</span></span>

- [<span data-ttu-id="3379f-119">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="3379f-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
