---
title: ICorProfilerInfo7 arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cf37c462-73c5-412a-a7f8-bb26ca746313
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 13282bec74df5e6159148aa4fbe92a84d035e044
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo7-interface"></a><span data-ttu-id="79a4b-102">ICorProfilerInfo7 arabirimi</span><span class="sxs-lookup"><span data-stu-id="79a4b-102">ICorProfilerInfo7 Interface</span></span>
<span data-ttu-id="79a4b-103">[Desteklenen [!INCLUDE[net_v461](../../../../includes/net-v461-md.md)] ve sonraki sürümlerinde]</span><span class="sxs-lookup"><span data-stu-id="79a4b-103">[Supported in the [!INCLUDE[net_v461](../../../../includes/net-v461-md.md)] and later versions]</span></span>  
  
 <span data-ttu-id="79a4b-104">Öğesinin bir alt [ICorProfilerInfo6](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md) sağlayan yeni uygulamak için bir yöntem meta verileri bir modüle tanımlanmış ve bir bellek içi simgesi akışına erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="79a4b-104">A subclass of [ICorProfilerInfo6](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md) that provides a method to apply newly defined metadata to a module and that provides access to an in-memory symbol stream.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="79a4b-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="79a4b-105">Methods</span></span>  
  
|<span data-ttu-id="79a4b-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="79a4b-106">Method</span></span>|<span data-ttu-id="79a4b-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="79a4b-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="79a4b-108">ApplyMetaData Yöntemi</span><span class="sxs-lookup"><span data-stu-id="79a4b-108">ApplyMetaData Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-applymetadata-method.md)|<span data-ttu-id="79a4b-109">Yeni tarafından tanımlanan meta verilerine uygulanır `IMetadataEmit::Define*` Belirtilen modül yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="79a4b-109">Applies the metadata newly defined by the `IMetadataEmit::Define*` methods to a specified module.</span></span>|  
|[<span data-ttu-id="79a4b-110">GetInMemorySymbolsLength Yöntemi</span><span class="sxs-lookup"><span data-stu-id="79a4b-110">GetInMemorySymbolsLength Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-getinmemorysymbolslength-method.md)|<span data-ttu-id="79a4b-111">Bellek içi simgesi akış uzunluğunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="79a4b-111">Returns the length of an in-memory symbol stream.</span></span>|  
|[<span data-ttu-id="79a4b-112">ReadInMemorySymbols</span><span class="sxs-lookup"><span data-stu-id="79a4b-112">ReadInMemorySymbols</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-readinmemorysymbols.md)|<span data-ttu-id="79a4b-113">Bayt bir bellek içi simgesi akıştan okur.</span><span class="sxs-lookup"><span data-stu-id="79a4b-113">Reads bytes from an in-memory symbol stream.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="79a4b-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="79a4b-114">Requirements</span></span>  
 <span data-ttu-id="79a4b-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="79a4b-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79a4b-116">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="79a4b-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="79a4b-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79a4b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79a4b-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="79a4b-118">See Also</span></span>  
 [<span data-ttu-id="79a4b-119">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="79a4b-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
