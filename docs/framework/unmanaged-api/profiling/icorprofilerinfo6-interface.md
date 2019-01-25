---
title: Icorprofilerınfo6 arabirimi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo6
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 6f2bb148-1e2b-4e45-a5a5-0ceddc40064b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 53120508c4810270747f749f1adfbae6ba800404
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54567899"
---
# <a name="icorprofilerinfo6-interface"></a><span data-ttu-id="95e5c-102">Icorprofilerınfo6 arabirimi</span><span class="sxs-lookup"><span data-stu-id="95e5c-102">ICorProfilerInfo6 Interface</span></span>
<span data-ttu-id="95e5c-103">[.NET Framework 4.6 ve sonraki sürümlerinde desteklenen]</span><span class="sxs-lookup"><span data-stu-id="95e5c-103">[Supported in the .NET Framework 4.6 and later versions]</span></span>  
  
 <span data-ttu-id="95e5c-104">Öğesinin [Icorprofilerınfo5](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md) verilen NGen modül ve satır içi belirli bir yöntemin içinde tanımlanan tüm yöntemleri için bir numaralandırıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="95e5c-104">A subclass of [ICorProfilerInfo5](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md) that provides an enumerator for all methods that are defined in a given NGen module and inline a given method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="95e5c-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="95e5c-105">Methods</span></span>  
  
|<span data-ttu-id="95e5c-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="95e5c-106">Method</span></span>|<span data-ttu-id="95e5c-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="95e5c-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="95e5c-108">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="95e5c-108">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-enumngenmodulemethodsinliningthismethod-method.md)|<span data-ttu-id="95e5c-109">Belirli bir NGen modüle ait olan ve belirli bir yöntemin gövdesinde satır içine alınmış olan tüm yöntemleri için bir numaralandırıcı döndürür.</span><span class="sxs-lookup"><span data-stu-id="95e5c-109">Returns an enumerator for all methods that belong to a given NGen module and that are inlined in the body of a given method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="95e5c-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="95e5c-110">Requirements</span></span>  
 <span data-ttu-id="95e5c-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95e5c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95e5c-112">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="95e5c-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="95e5c-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95e5c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95e5c-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="95e5c-114">See also</span></span>
- [<span data-ttu-id="95e5c-115">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="95e5c-115">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
