---
title: ICorProfilerInfo7 Arabirimi
ms.date: 03/30/2017
ms.assetid: cf37c462-73c5-412a-a7f8-bb26ca746313
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a734bfdef89d4f8f9459f49a3ce2cee83faef9f6
ms.sourcegitcommit: 26f4a7697c32978f6a328c89dc4ea87034065989
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/28/2019
ms.locfileid: "66250981"
---
# <a name="icorprofilerinfo7-interface"></a><span data-ttu-id="bcccf-102">ICorProfilerInfo7 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bcccf-102">ICorProfilerInfo7 Interface</span></span>
<span data-ttu-id="bcccf-103">[.NET Framework 4.6.1 ve sonraki sürümlerinde desteklenen]</span><span class="sxs-lookup"><span data-stu-id="bcccf-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="bcccf-104">Öğesinin [Icorprofilerınfo6](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md) yeni uygulamak için bir yöntem bir modül için meta verileri tanımlanmış ve bir bellek içi sembol akışına erişim sağlayan sağlar.</span><span class="sxs-lookup"><span data-stu-id="bcccf-104">A subclass of [ICorProfilerInfo6](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md) that provides a method to apply newly defined metadata to a module and that provides access to an in-memory symbol stream.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bcccf-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="bcccf-105">Methods</span></span>  
  
|<span data-ttu-id="bcccf-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="bcccf-106">Method</span></span>|<span data-ttu-id="bcccf-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bcccf-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bcccf-108">ApplyMetaData Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bcccf-108">ApplyMetaData Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-applymetadata-method.md)|<span data-ttu-id="bcccf-109">Yeni tarafından tanımlanan meta veriler geçerli `IMetadataEmit::Define*` Belirtilen modül için yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="bcccf-109">Applies the metadata newly defined by the `IMetadataEmit::Define*` methods to a specified module.</span></span>|  
|[<span data-ttu-id="bcccf-110">GetInMemorySymbolsLength Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bcccf-110">GetInMemorySymbolsLength Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-getinmemorysymbolslength-method.md)|<span data-ttu-id="bcccf-111">Bir bellek içi sembol akış uzunluğunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="bcccf-111">Returns the length of an in-memory symbol stream.</span></span>|  
|[<span data-ttu-id="bcccf-112">ReadInMemorySymbols</span><span class="sxs-lookup"><span data-stu-id="bcccf-112">ReadInMemorySymbols</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-readinmemorysymbols.md)|<span data-ttu-id="bcccf-113">Bayt bir bellek içi sembol akıştan okur.</span><span class="sxs-lookup"><span data-stu-id="bcccf-113">Reads bytes from an in-memory symbol stream.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bcccf-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bcccf-114">Requirements</span></span>  
 <span data-ttu-id="bcccf-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bcccf-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bcccf-116">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="bcccf-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bcccf-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bcccf-117">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcccf-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bcccf-118">See also</span></span>

- [<span data-ttu-id="bcccf-119">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="bcccf-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
