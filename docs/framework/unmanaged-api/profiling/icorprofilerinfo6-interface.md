---
title: ICorProfilerInfo6 arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorProfilerInfo6
api_location: mscorwks.dll
api_type: COM
ms.assetid: 6f2bb148-1e2b-4e45-a5a5-0ceddc40064b
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 805f1e451b2c13c356d904c42dff87304aa2093c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo6-interface"></a><span data-ttu-id="2dc02-102">ICorProfilerInfo6 arabirimi</span><span class="sxs-lookup"><span data-stu-id="2dc02-102">ICorProfilerInfo6 Interface</span></span>
<span data-ttu-id="2dc02-103">[.NET Framework 4.6 ve sonraki sürümlerinde desteklenen]</span><span class="sxs-lookup"><span data-stu-id="2dc02-103">[Supported in the .NET Framework 4.6 and later versions]</span></span>  
  
 <span data-ttu-id="2dc02-104">Öğesinin bir alt [Icorprofilerınfo5](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md) verilen NGen modülü ve satır içi belirli bir yöntemin içinde tanımlanan tüm yöntemleri için bir numaralandırıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="2dc02-104">A subclass of [ICorProfilerInfo5](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md) that provides an enumerator for all methods that are defined in a given NGen module and inline a given method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2dc02-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="2dc02-105">Methods</span></span>  
  
|<span data-ttu-id="2dc02-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="2dc02-106">Method</span></span>|<span data-ttu-id="2dc02-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2dc02-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2dc02-108">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2dc02-108">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-enumngenmodulemethodsinliningthismethod-method.md)|<span data-ttu-id="2dc02-109">Belirli bir NGen modüle ait ve belirli bir yöntemin gövdesine içermesinden tüm yöntemleri için bir numaralandırıcı döndürür.</span><span class="sxs-lookup"><span data-stu-id="2dc02-109">Returns an enumerator for all methods that belong to a given NGen module and that are inlined in the body of a given method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2dc02-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2dc02-110">Requirements</span></span>  
 <span data-ttu-id="2dc02-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2dc02-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2dc02-112">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2dc02-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2dc02-113">**.NET framework sürümleri:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2dc02-113">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2dc02-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2dc02-114">See Also</span></span>  
 [<span data-ttu-id="2dc02-115">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="2dc02-115">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
