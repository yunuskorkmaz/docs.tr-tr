---
title: ICorProfilerCallback2::HandleCreated Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.HandleCreated
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::HandleCreated
helpviewer_keywords:
- HandleCreated method [.NET Framework profiling]
- ICorProfilerCallback2::HandleCreated method [.NET Framework profiling]
ms.assetid: 6bbb7786-7c38-490f-9834-91aa2795c355
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5cd8b08c630d56ca3b59cad768e285b630d64e59
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59175779"
---
# <a name="icorprofilercallback2handlecreated-method"></a><span data-ttu-id="b16ce-102">ICorProfilerCallback2::HandleCreated Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b16ce-102">ICorProfilerCallback2::HandleCreated Method</span></span>
<span data-ttu-id="b16ce-103">Kod profil oluşturucu, çöp toplama tanıtıcı oluşturulduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="b16ce-103">Notifies the code profiler that a garbage collection handle has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b16ce-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b16ce-104">Syntax</span></span>  
  
```  
HRESULT HandleCreated(  
    [in] GCHandleID handleId,  
    [in] ObjectID initialObjectId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b16ce-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b16ce-105">Parameters</span></span>  
 `handleId`  
 <span data-ttu-id="b16ce-106">[in] Çöp toplama işlemi için tanıtıcı kimliği.</span><span class="sxs-lookup"><span data-stu-id="b16ce-106">[in] The ID of the handle for the garbage collection.</span></span>  
  
 `initialObjectId`  
 <span data-ttu-id="b16ce-107">[in] Çöp toplama tanıtıcı oluşturulduğu nesnesinin kimliği.</span><span class="sxs-lookup"><span data-stu-id="b16ce-107">[in] The ID of the object for which the garbage collection handle was created.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b16ce-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b16ce-108">Requirements</span></span>  
 <span data-ttu-id="b16ce-109">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b16ce-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b16ce-110">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b16ce-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b16ce-111">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b16ce-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b16ce-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b16ce-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b16ce-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b16ce-113">See also</span></span>

- [<span data-ttu-id="b16ce-114">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b16ce-114">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="b16ce-115">ICorProfilerCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b16ce-115">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
