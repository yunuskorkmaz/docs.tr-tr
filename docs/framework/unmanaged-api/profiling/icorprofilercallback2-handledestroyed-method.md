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
ms.openlocfilehash: bc6b086b444a769afbf01369b50c69e242a21050
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59090491"
---
# <a name="icorprofilercallback2handledestroyed-method"></a><span data-ttu-id="11b26-102">ICorProfilerCallback2::HandleDestroyed Yöntemi</span><span class="sxs-lookup"><span data-stu-id="11b26-102">ICorProfilerCallback2::HandleDestroyed Method</span></span>
<span data-ttu-id="11b26-103">Kod profil oluşturucu, çöp toplama tanıtıcısı yok edildi bildirir.</span><span class="sxs-lookup"><span data-stu-id="11b26-103">Notifies the code profiler that a garbage collection handle has been destroyed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11b26-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="11b26-104">Syntax</span></span>  
  
```  
HRESULT HandleDestroyed(  
    [in] GCHandleID handleId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="11b26-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="11b26-105">Parameters</span></span>  
 `handleId`  
 <span data-ttu-id="11b26-106">[in] Çöp toplama işlemi için tanıtıcı kimliği.</span><span class="sxs-lookup"><span data-stu-id="11b26-106">[in] The ID of the handle for the garbage collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11b26-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="11b26-107">Requirements</span></span>  
 <span data-ttu-id="11b26-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="11b26-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11b26-109">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="11b26-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="11b26-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="11b26-110">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="11b26-111">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="11b26-111">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="11b26-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="11b26-112">See also</span></span>

- [<span data-ttu-id="11b26-113">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="11b26-113">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="11b26-114">ICorProfilerCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="11b26-114">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
