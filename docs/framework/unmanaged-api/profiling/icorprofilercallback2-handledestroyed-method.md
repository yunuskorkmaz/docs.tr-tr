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
ms.openlocfilehash: 3cb8783ba1427ecc2396abb32f350664ddf83d19
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779318"
---
# <a name="icorprofilercallback2handledestroyed-method"></a><span data-ttu-id="85a35-102">ICorProfilerCallback2::HandleDestroyed Yöntemi</span><span class="sxs-lookup"><span data-stu-id="85a35-102">ICorProfilerCallback2::HandleDestroyed Method</span></span>
<span data-ttu-id="85a35-103">Kod profil oluşturucu, çöp toplama tanıtıcısı yok edildi bildirir.</span><span class="sxs-lookup"><span data-stu-id="85a35-103">Notifies the code profiler that a garbage collection handle has been destroyed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85a35-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="85a35-104">Syntax</span></span>  
  
```cpp  
HRESULT HandleDestroyed(  
    [in] GCHandleID handleId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="85a35-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="85a35-105">Parameters</span></span>  
 `handleId`  
 <span data-ttu-id="85a35-106">[in] Çöp toplama işlemi için tanıtıcı kimliği.</span><span class="sxs-lookup"><span data-stu-id="85a35-106">[in] The ID of the handle for the garbage collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85a35-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="85a35-107">Requirements</span></span>  
 <span data-ttu-id="85a35-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="85a35-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85a35-109">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="85a35-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="85a35-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="85a35-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="85a35-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85a35-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85a35-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="85a35-112">See also</span></span>

- [<span data-ttu-id="85a35-113">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="85a35-113">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="85a35-114">ICorProfilerCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="85a35-114">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
