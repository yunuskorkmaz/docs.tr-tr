---
title: ICorProfilerInfo6 Arabirimi
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
ms.openlocfilehash: febe130b4d61b6179aeab3bfcd63891c38b13fbe
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59128940"
---
# <a name="icorprofilerinfo6-interface"></a><span data-ttu-id="c9aa4-102">ICorProfilerInfo6 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c9aa4-102">ICorProfilerInfo6 Interface</span></span>
<span data-ttu-id="c9aa4-103">[.NET Framework 4.6 ve sonraki sürümlerinde desteklenen]</span><span class="sxs-lookup"><span data-stu-id="c9aa4-103">[Supported in the .NET Framework 4.6 and later versions]</span></span>  
  
 <span data-ttu-id="c9aa4-104">Öğesinin [Icorprofilerınfo5](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md) verilen NGen modül ve satır içi belirli bir yöntemin içinde tanımlanan tüm yöntemleri için bir numaralandırıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="c9aa4-104">A subclass of [ICorProfilerInfo5](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md) that provides an enumerator for all methods that are defined in a given NGen module and inline a given method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c9aa4-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="c9aa4-105">Methods</span></span>  
  
|<span data-ttu-id="c9aa4-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="c9aa4-106">Method</span></span>|<span data-ttu-id="c9aa4-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c9aa4-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c9aa4-108">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c9aa4-108">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-enumngenmodulemethodsinliningthismethod-method.md)|<span data-ttu-id="c9aa4-109">Belirli bir NGen modüle ait olan ve belirli bir yöntemin gövdesinde satır içine alınmış olan tüm yöntemleri için bir numaralandırıcı döndürür.</span><span class="sxs-lookup"><span data-stu-id="c9aa4-109">Returns an enumerator for all methods that belong to a given NGen module and that are inlined in the body of a given method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c9aa4-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c9aa4-110">Requirements</span></span>  
 <span data-ttu-id="c9aa4-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9aa4-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9aa4-112">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c9aa4-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 **<span data-ttu-id="c9aa4-113">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="c9aa4-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c9aa4-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c9aa4-114">See also</span></span>

- [<span data-ttu-id="c9aa4-115">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c9aa4-115">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
