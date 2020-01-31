---
title: ICorProfilerInfo7 Arabirimi
ms.date: 03/30/2017
ms.assetid: cf37c462-73c5-412a-a7f8-bb26ca746313
ms.openlocfilehash: f80f310c10bae33583cb7cd2048ede4f5efbe14c
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76861755"
---
# <a name="icorprofilerinfo7-interface"></a><span data-ttu-id="a9235-102">ICorProfilerInfo7 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a9235-102">ICorProfilerInfo7 Interface</span></span>
<span data-ttu-id="a9235-103">[.NET Framework 4.6.1 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="a9235-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="a9235-104">Bir modüle yeni tanımlanmış meta verileri uygulamak için bir yöntem sağlayan ve bellek içi sembol akışına erişim sağlayan bir [ıcorprofilerınfo6](icorprofilerinfo6-interface.md) alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="a9235-104">A subclass of [ICorProfilerInfo6](icorprofilerinfo6-interface.md) that provides a method to apply newly defined metadata to a module and that provides access to an in-memory symbol stream.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a9235-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="a9235-105">Methods</span></span>  
  
|<span data-ttu-id="a9235-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="a9235-106">Method</span></span>|<span data-ttu-id="a9235-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a9235-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a9235-108">ApplyMetaData Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a9235-108">ApplyMetaData Method</span></span>](icorprofilerinfo7-applymetadata-method.md)|<span data-ttu-id="a9235-109">`IMetadataEmit::Define*` yöntemleri tarafından belirtilen bir modüle yeni tanımlanan meta verileri uygular.</span><span class="sxs-lookup"><span data-stu-id="a9235-109">Applies the metadata newly defined by the `IMetadataEmit::Define*` methods to a specified module.</span></span>|  
|[<span data-ttu-id="a9235-110">GetInMemorySymbolsLength Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a9235-110">GetInMemorySymbolsLength Method</span></span>](icorprofilerinfo7-getinmemorysymbolslength-method.md)|<span data-ttu-id="a9235-111">Bellek içi sembol akışının uzunluğunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="a9235-111">Returns the length of an in-memory symbol stream.</span></span>|  
|[<span data-ttu-id="a9235-112">ReadInMemorySymbols</span><span class="sxs-lookup"><span data-stu-id="a9235-112">ReadInMemorySymbols</span></span>](icorprofilerinfo7-readinmemorysymbols.md)|<span data-ttu-id="a9235-113">Bellek içi sembol akışından gelen baytları okur.</span><span class="sxs-lookup"><span data-stu-id="a9235-113">Reads bytes from an in-memory symbol stream.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a9235-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a9235-114">Requirements</span></span>  
 <span data-ttu-id="a9235-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9235-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9235-116">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="a9235-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a9235-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9235-117">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9235-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a9235-118">See also</span></span>

- [<span data-ttu-id="a9235-119">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a9235-119">Profiling Interfaces</span></span>](profiling-interfaces.md)
