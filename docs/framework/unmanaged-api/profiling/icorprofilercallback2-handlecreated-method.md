---
description: 'Şu konuda daha fazla bilgi edinin: ICorProfilerCallback2:: HandleCreated Yöntemi'
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
ms.openlocfilehash: 17f4ed83646907a229dcc6a30dcce1b52fa608d5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99657092"
---
# <a name="icorprofilercallback2handlecreated-method"></a><span data-ttu-id="a800b-103">ICorProfilerCallback2::HandleCreated Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a800b-103">ICorProfilerCallback2::HandleCreated Method</span></span>

<span data-ttu-id="a800b-104">Kod Profilcisi bir çöp toplama tutamacının oluşturulduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="a800b-104">Notifies the code profiler that a garbage collection handle has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a800b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a800b-105">Syntax</span></span>  
  
```cpp  
HRESULT HandleCreated(  
    [in] GCHandleID handleId,  
    [in] ObjectID initialObjectId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a800b-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a800b-106">Parameters</span></span>  

 `handleId`  
 <span data-ttu-id="a800b-107">'ndaki Çöp toplama tanıtıcısının KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="a800b-107">[in] The ID of the handle for the garbage collection.</span></span>  
  
 `initialObjectId`  
 <span data-ttu-id="a800b-108">'ndaki Çöp toplama tanıtıcısının oluşturulduğu nesnenin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="a800b-108">[in] The ID of the object for which the garbage collection handle was created.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a800b-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a800b-109">Requirements</span></span>  

 <span data-ttu-id="a800b-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a800b-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a800b-111">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="a800b-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a800b-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a800b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a800b-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a800b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a800b-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a800b-114">See also</span></span>

- [<span data-ttu-id="a800b-115">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a800b-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="a800b-116">ICorProfilerCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a800b-116">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
