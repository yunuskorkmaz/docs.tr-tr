---
title: "ICorProfilerInfo4::EnumThreads Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorProfilerInfo4.EnumThreads
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::EnumThreads
helpviewer_keywords:
- ICorProfilerInfo4::EnumThreads method [.NET Framework profiling]
- EnumThreads method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: bca7a5b4-c207-4894-918c-0733926296dd
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6e4dc301458d87b08960ef7c0b64203c703491ea
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo4enumthreads-method"></a><span data-ttu-id="8846e-102">ICorProfilerInfo4::EnumThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8846e-102">ICorProfilerInfo4::EnumThreads Method</span></span>
<span data-ttu-id="8846e-103">Tüm yönetilen iş parçacıklarında profili işlem koleksiyonunu sırayla yinelemek için yöntemler sağlayan bir numaralandırıcı döndürür.</span><span class="sxs-lookup"><span data-stu-id="8846e-103">Returns an enumerator that provides methods to sequentially iterate through the collection of all managed threads in the profiled process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8846e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8846e-104">Syntax</span></span>  
  
```  
HRESULT EnumThreads([out]  
            ICorProfilerThreadEnum** ppEnum);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8846e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8846e-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="8846e-106">[out] Bir işaretçi bir [Icorprofilerthreadenum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="8846e-106">[out] A pointer to an [ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md) interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8846e-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8846e-107">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8846e-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8846e-108">Requirements</span></span>  
 <span data-ttu-id="8846e-109">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8846e-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8846e-110">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8846e-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8846e-111">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8846e-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8846e-112">**.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8846e-112">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8846e-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8846e-113">See Also</span></span>  
 [<span data-ttu-id="8846e-114">ICorProfilerThreadEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8846e-114">ICorProfilerThreadEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)  
 [<span data-ttu-id="8846e-115">ICorProfilerInfo4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8846e-115">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 [<span data-ttu-id="8846e-116">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8846e-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="8846e-117">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="8846e-117">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
