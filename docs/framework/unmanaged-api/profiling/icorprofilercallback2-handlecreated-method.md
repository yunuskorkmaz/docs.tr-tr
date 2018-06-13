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
ms.openlocfilehash: 47654d7ad1803e57f5db846ea0370d1f736deaa5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33452279"
---
# <a name="icorprofilercallback2handlecreated-method"></a><span data-ttu-id="f2dde-102">ICorProfilerCallback2::HandleCreated Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f2dde-102">ICorProfilerCallback2::HandleCreated Method</span></span>
<span data-ttu-id="f2dde-103">Kod profil oluşturucu bir atık toplama tanıtıcı oluşturulduğunu size bildirir.</span><span class="sxs-lookup"><span data-stu-id="f2dde-103">Notifies the code profiler that a garbage collection handle has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2dde-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f2dde-104">Syntax</span></span>  
  
```  
HRESULT HandleCreated(  
    [in] GCHandleID handleId,  
    [in] ObjectID initialObjectId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f2dde-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f2dde-105">Parameters</span></span>  
 `handleId`  
 <span data-ttu-id="f2dde-106">[in] Çöp toplama için tanıtıcı kimliği.</span><span class="sxs-lookup"><span data-stu-id="f2dde-106">[in] The ID of the handle for the garbage collection.</span></span>  
  
 `initialObjectId`  
 <span data-ttu-id="f2dde-107">[in] Çöp toplama tanıtıcı oluşturulduğu nesnesinin kimliği.</span><span class="sxs-lookup"><span data-stu-id="f2dde-107">[in] The ID of the object for which the garbage collection handle was created.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2dde-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f2dde-108">Requirements</span></span>  
 <span data-ttu-id="f2dde-109">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2dde-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2dde-110">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f2dde-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f2dde-111">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f2dde-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f2dde-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2dde-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2dde-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f2dde-113">See Also</span></span>  
 [<span data-ttu-id="f2dde-114">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f2dde-114">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="f2dde-115">ICorProfilerCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f2dde-115">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
