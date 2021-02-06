---
description: ': ICorProfilerCallback:: ClassUnloadFinished yöntemi hakkında daha fazla bilgi edinin'
title: ICorProfilerCallback::ClassUnloadFinished Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassUnloadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassUnloadFinished
helpviewer_keywords:
- ICorProfilerCallback::ClassUnloadFinished method [.NET Framework profiling]
- ClassUnloadFinished method [.NET Framework profiling]
ms.assetid: 55674b68-678a-4747-ae06-4e91519c7305
topic_type:
- apiref
ms.openlocfilehash: ae1ef56a1eb3b9b45c2165ecceb0af826cc7a2ea
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99657742"
---
# <a name="icorprofilercallbackclassunloadfinished-method"></a><span data-ttu-id="f6572-103">ICorProfilerCallback::ClassUnloadFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f6572-103">ICorProfilerCallback::ClassUnloadFinished Method</span></span>

<span data-ttu-id="f6572-104">Profil oluşturucuyu bir sınıfın kaldırmayı tamamladığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="f6572-104">Notifies the profiler that a class has finished unloading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6572-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f6572-105">Syntax</span></span>  
  
```cpp  
HRESULT ClassUnloadFinished(  
    [in] ClassID classId,  
    [in] HRESULT hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f6572-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f6572-106">Parameters</span></span>

- `classId`

  <span data-ttu-id="f6572-107">\[' de], kaldırılan sınıfı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f6572-107">\[in] Identifies the class that was unloaded.</span></span>

- `hrStatus`

  <span data-ttu-id="f6572-108">\[içinde] sınıfın başarıyla yüklenip yüklenmediğini gösteren bir HRESULT.</span><span class="sxs-lookup"><span data-stu-id="f6572-108">\[in] An HRESULT that indicates whether the class was unloaded successfully.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="f6572-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f6572-109">Remarks</span></span>  

 <span data-ttu-id="f6572-110">Sınıfı kaldırma işleminin bazı bölümleri geri aramadan sonra devam edebilir `ClassUnloadFinished` .</span><span class="sxs-lookup"><span data-stu-id="f6572-110">Some parts of unloading the class might continue after the `ClassUnloadFinished` callback.</span></span> <span data-ttu-id="f6572-111">' De HRESULT hatası, `hrStatus` bir hatayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="f6572-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="f6572-112">Ancak, içinde başarılı bir HRESULT, `hrStatus` yalnızca sınıfın kaldırılmasının ilk bölümünün başarılı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="f6572-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the class has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6572-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f6572-113">Requirements</span></span>  

 <span data-ttu-id="f6572-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6572-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6572-115">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="f6572-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f6572-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f6572-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f6572-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6572-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6572-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f6572-118">See also</span></span>

- [<span data-ttu-id="f6572-119">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f6572-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="f6572-120">ClassUnloadStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f6572-120">ClassUnloadStarted Method</span></span>](icorprofilercallback-classunloadstarted-method.md)
