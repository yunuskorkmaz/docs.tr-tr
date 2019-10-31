---
title: ICorProfilerInfo7 Arabirimi
ms.date: 03/30/2017
ms.assetid: cf37c462-73c5-412a-a7f8-bb26ca746313
ms.openlocfilehash: 4c7e94ffa60bcfaead009e1a8baa9b54b2e8ab7e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125060"
---
# <a name="icorprofilerinfo7-interface"></a><span data-ttu-id="05e91-102">ICorProfilerInfo7 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="05e91-102">ICorProfilerInfo7 Interface</span></span>
<span data-ttu-id="05e91-103">[.NET Framework 4.6.1 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="05e91-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="05e91-104">Bir modüle yeni tanımlanmış meta verileri uygulamak için bir yöntem sağlayan ve bellek içi sembol akışına erişim sağlayan bir [ıcorprofilerınfo6](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md) alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="05e91-104">A subclass of [ICorProfilerInfo6](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md) that provides a method to apply newly defined metadata to a module and that provides access to an in-memory symbol stream.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="05e91-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="05e91-105">Methods</span></span>  
  
|<span data-ttu-id="05e91-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="05e91-106">Method</span></span>|<span data-ttu-id="05e91-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="05e91-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="05e91-108">ApplyMetaData Yöntemi</span><span class="sxs-lookup"><span data-stu-id="05e91-108">ApplyMetaData Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-applymetadata-method.md)|<span data-ttu-id="05e91-109">`IMetadataEmit::Define*` yöntemleri tarafından belirtilen bir modüle yeni tanımlanan meta verileri uygular.</span><span class="sxs-lookup"><span data-stu-id="05e91-109">Applies the metadata newly defined by the `IMetadataEmit::Define*` methods to a specified module.</span></span>|  
|[<span data-ttu-id="05e91-110">GetInMemorySymbolsLength Yöntemi</span><span class="sxs-lookup"><span data-stu-id="05e91-110">GetInMemorySymbolsLength Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-getinmemorysymbolslength-method.md)|<span data-ttu-id="05e91-111">Bellek içi sembol akışının uzunluğunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="05e91-111">Returns the length of an in-memory symbol stream.</span></span>|  
|[<span data-ttu-id="05e91-112">ReadInMemorySymbols</span><span class="sxs-lookup"><span data-stu-id="05e91-112">ReadInMemorySymbols</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-readinmemorysymbols.md)|<span data-ttu-id="05e91-113">Bellek içi sembol akışından gelen baytları okur.</span><span class="sxs-lookup"><span data-stu-id="05e91-113">Reads bytes from an in-memory symbol stream.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="05e91-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="05e91-114">Requirements</span></span>  
 <span data-ttu-id="05e91-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05e91-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05e91-116">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="05e91-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="05e91-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05e91-117">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05e91-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="05e91-118">See also</span></span>

- [<span data-ttu-id="05e91-119">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="05e91-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
