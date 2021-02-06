---
description: ': ICorProfilerCallback:: RuntimeSuspendStarted yöntemi hakkında daha fazla bilgi edinin'
title: ICorProfilerCallback::RuntimeSuspendStarted Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeSuspendStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeSuspendStarted
helpviewer_keywords:
- ICorProfilerCallback::RuntimeSuspendStarted method [.NET Framework profiling]
- RuntimeSuspendStarted method [.NET Framework profiling]
ms.assetid: c8461cac-e31b-4efa-ad2c-26598173eb96
topic_type:
- apiref
ms.openlocfilehash: 7f7ba6a2a8523589b025d98ea925b77d05d8a59d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99657443"
---
# <a name="icorprofilercallbackruntimesuspendstarted-method"></a><span data-ttu-id="86667-103">ICorProfilerCallback::RuntimeSuspendStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="86667-103">ICorProfilerCallback::RuntimeSuspendStarted Method</span></span>

<span data-ttu-id="86667-104">Profil oluşturucuya çalışma zamanının tüm çalışma zamanı iş parçacıklarını askıya almak için olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="86667-104">Notifies the profiler that the runtime is about to suspend all runtime threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86667-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="86667-105">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeSuspendStarted(  
    [in] COR_PRF_SUSPEND_REASON suspendReason);  
```  
  
## <a name="parameters"></a><span data-ttu-id="86667-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="86667-106">Parameters</span></span>  

 `suspendReason`  
 <span data-ttu-id="86667-107">'ndaki Askıya alma nedenini gösteren [COR_PRF_SUSPEND_REASON](cor-prf-suspend-reason-enumeration.md) numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="86667-107">[in] A value of the [COR_PRF_SUSPEND_REASON](cor-prf-suspend-reason-enumeration.md) enumeration that indicates the reason for the suspension.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="86667-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="86667-108">Remarks</span></span>  

 <span data-ttu-id="86667-109">Yönetilmeyen koddaki tüm çalışma zamanı iş parçacıklarının, çalışma zamanını yeniden girmeye çalıştıklarında çalışmaya devam etmesine izin verilir.</span><span class="sxs-lookup"><span data-stu-id="86667-109">All runtime threads that are in unmanaged code are allowed to continue running until they try to re-enter the runtime.</span></span> <span data-ttu-id="86667-110">Bu noktada, çalışma zamanı sürdürülene kadar de askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="86667-110">At that point they will also be suspended until the runtime resumes.</span></span> <span data-ttu-id="86667-111">Bu, çalışma zamanını belirten yeni iş parçacıkları için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="86667-111">This also applies to new threads that enter the runtime.</span></span> <span data-ttu-id="86667-112">Çalışma zamanındaki tüm iş parçacıkları, zaten kesilebilir kodunda olduklarında askıya alınır ya da kesilebilir koduna ulaştığında askıya alınması istenir.</span><span class="sxs-lookup"><span data-stu-id="86667-112">All threads in the runtime are either suspended immediately if they are already in interruptible code, or they are asked to suspend when they reach interruptible code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86667-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="86667-113">Requirements</span></span>  

 <span data-ttu-id="86667-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86667-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86667-115">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="86667-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="86667-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="86667-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="86667-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86667-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86667-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="86667-118">See also</span></span>

- [<span data-ttu-id="86667-119">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="86667-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="86667-120">RuntimeSuspendAborted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="86667-120">RuntimeSuspendAborted Method</span></span>](icorprofilercallback-runtimesuspendaborted-method.md)
- [<span data-ttu-id="86667-121">RuntimeSuspendFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="86667-121">RuntimeSuspendFinished Method</span></span>](icorprofilercallback-runtimesuspendfinished-method.md)
