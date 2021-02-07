---
description: 'Daha fazla bilgi edinin: ICorProfilerInfo7 Interface'
title: ICorProfilerInfo7 Arabirimi
ms.date: 03/30/2017
ms.assetid: cf37c462-73c5-412a-a7f8-bb26ca746313
ms.openlocfilehash: 7a33472d5562ad57d38291c64f8da7021ae2fe91
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99737083"
---
# <a name="icorprofilerinfo7-interface"></a><span data-ttu-id="ec837-103">ICorProfilerInfo7 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ec837-103">ICorProfilerInfo7 Interface</span></span>

<span data-ttu-id="ec837-104">[.NET Framework 4.6.1 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="ec837-104">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="ec837-105">Bir modüle yeni tanımlanmış meta verileri uygulamak için bir yöntem sağlayan ve bellek içi sembol akışına erişim sağlayan bir [ıcorprofilerınfo6](icorprofilerinfo6-interface.md) alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="ec837-105">A subclass of [ICorProfilerInfo6](icorprofilerinfo6-interface.md) that provides a method to apply newly defined metadata to a module and that provides access to an in-memory symbol stream.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ec837-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="ec837-106">Methods</span></span>  
  
|<span data-ttu-id="ec837-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="ec837-107">Method</span></span>|<span data-ttu-id="ec837-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ec837-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ec837-109">ApplyMetaData Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ec837-109">ApplyMetaData Method</span></span>](icorprofilerinfo7-applymetadata-method.md)|<span data-ttu-id="ec837-110">Yöntemler tarafından belirtilen bir modüle yeni tanımlanan meta verileri uygular `IMetadataEmit::Define*` .</span><span class="sxs-lookup"><span data-stu-id="ec837-110">Applies the metadata newly defined by the `IMetadataEmit::Define*` methods to a specified module.</span></span>|  
|[<span data-ttu-id="ec837-111">GetInMemorySymbolsLength Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ec837-111">GetInMemorySymbolsLength Method</span></span>](icorprofilerinfo7-getinmemorysymbolslength-method.md)|<span data-ttu-id="ec837-112">Bellek içi sembol akışının uzunluğunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="ec837-112">Returns the length of an in-memory symbol stream.</span></span>|  
|[<span data-ttu-id="ec837-113">ReadInMemorySymbols</span><span class="sxs-lookup"><span data-stu-id="ec837-113">ReadInMemorySymbols</span></span>](icorprofilerinfo7-readinmemorysymbols.md)|<span data-ttu-id="ec837-114">Bellek içi sembol akışından gelen baytları okur.</span><span class="sxs-lookup"><span data-stu-id="ec837-114">Reads bytes from an in-memory symbol stream.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ec837-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ec837-115">Requirements</span></span>  

 <span data-ttu-id="ec837-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec837-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec837-117">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="ec837-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ec837-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec837-118">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec837-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ec837-119">See also</span></span>

- [<span data-ttu-id="ec837-120">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ec837-120">Profiling Interfaces</span></span>](profiling-interfaces.md)
