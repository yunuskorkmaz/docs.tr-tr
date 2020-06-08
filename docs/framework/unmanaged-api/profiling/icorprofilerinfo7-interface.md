---
title: ICorProfilerInfo7 Arabirimi
ms.date: 03/30/2017
ms.assetid: cf37c462-73c5-412a-a7f8-bb26ca746313
ms.openlocfilehash: 0e9f76717aeff27e863245faac241927e7495076
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495495"
---
# <a name="icorprofilerinfo7-interface"></a><span data-ttu-id="3be55-102">ICorProfilerInfo7 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3be55-102">ICorProfilerInfo7 Interface</span></span>
<span data-ttu-id="3be55-103">[.NET Framework 4.6.1 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="3be55-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="3be55-104">Bir modüle yeni tanımlanmış meta verileri uygulamak için bir yöntem sağlayan ve bellek içi sembol akışına erişim sağlayan bir [ıcorprofilerınfo6](icorprofilerinfo6-interface.md) alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="3be55-104">A subclass of [ICorProfilerInfo6](icorprofilerinfo6-interface.md) that provides a method to apply newly defined metadata to a module and that provides access to an in-memory symbol stream.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3be55-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="3be55-105">Methods</span></span>  
  
|<span data-ttu-id="3be55-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="3be55-106">Method</span></span>|<span data-ttu-id="3be55-107">Description</span><span class="sxs-lookup"><span data-stu-id="3be55-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3be55-108">ApplyMetaData Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3be55-108">ApplyMetaData Method</span></span>](icorprofilerinfo7-applymetadata-method.md)|<span data-ttu-id="3be55-109">Yöntemler tarafından belirtilen bir modüle yeni tanımlanan meta verileri uygular `IMetadataEmit::Define*` .</span><span class="sxs-lookup"><span data-stu-id="3be55-109">Applies the metadata newly defined by the `IMetadataEmit::Define*` methods to a specified module.</span></span>|  
|[<span data-ttu-id="3be55-110">GetInMemorySymbolsLength Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3be55-110">GetInMemorySymbolsLength Method</span></span>](icorprofilerinfo7-getinmemorysymbolslength-method.md)|<span data-ttu-id="3be55-111">Bellek içi sembol akışının uzunluğunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="3be55-111">Returns the length of an in-memory symbol stream.</span></span>|  
|[<span data-ttu-id="3be55-112">ReadInMemorySymbols</span><span class="sxs-lookup"><span data-stu-id="3be55-112">ReadInMemorySymbols</span></span>](icorprofilerinfo7-readinmemorysymbols.md)|<span data-ttu-id="3be55-113">Bellek içi sembol akışından gelen baytları okur.</span><span class="sxs-lookup"><span data-stu-id="3be55-113">Reads bytes from an in-memory symbol stream.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3be55-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3be55-114">Requirements</span></span>  
 <span data-ttu-id="3be55-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3be55-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3be55-116">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="3be55-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3be55-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3be55-117">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3be55-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3be55-118">See also</span></span>

- [<span data-ttu-id="3be55-119">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="3be55-119">Profiling Interfaces</span></span>](profiling-interfaces.md)
