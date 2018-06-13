---
title: ICorProfilerCallback2::HandleDestroyed Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.HandleDestroyed
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::HandleDestroyed
helpviewer_keywords:
- ICorProfilerCallback2::HandleDestroyed method [.NET Framework profiling]
- HandleDestroyed method [.NET Framework profiling]
ms.assetid: ab4f4bbd-40c7-4667-bfde-60cd73803110
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 31492711ea9927c07f611ff9ec9bbe49d4857d46
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33451967"
---
# <a name="icorprofilercallback2handledestroyed-method"></a><span data-ttu-id="d8cd2-102">ICorProfilerCallback2::HandleDestroyed Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d8cd2-102">ICorProfilerCallback2::HandleDestroyed Method</span></span>
<span data-ttu-id="d8cd2-103">Kod profil oluşturucu bir atık toplama tanıtıcı yok bildirir.</span><span class="sxs-lookup"><span data-stu-id="d8cd2-103">Notifies the code profiler that a garbage collection handle has been destroyed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8cd2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d8cd2-104">Syntax</span></span>  
  
```  
HRESULT HandleDestroyed(  
    [in] GCHandleID handleId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d8cd2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d8cd2-105">Parameters</span></span>  
 `handleId`  
 <span data-ttu-id="d8cd2-106">[in] Çöp toplama için tanıtıcı kimliği.</span><span class="sxs-lookup"><span data-stu-id="d8cd2-106">[in] The ID of the handle for the garbage collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8cd2-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d8cd2-107">Requirements</span></span>  
 <span data-ttu-id="d8cd2-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8cd2-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8cd2-109">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d8cd2-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d8cd2-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d8cd2-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d8cd2-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8cd2-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8cd2-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d8cd2-112">See Also</span></span>  
 [<span data-ttu-id="d8cd2-113">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d8cd2-113">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="d8cd2-114">ICorProfilerCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d8cd2-114">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
