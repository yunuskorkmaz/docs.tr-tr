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
ms.openlocfilehash: 7d4fd1c85d496b7adea0096b03520a14c2fab11c
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2021
ms.locfileid: "104759266"
---
# <a name="icorprofilercallbackclassunloadfinished-method"></a><span data-ttu-id="47ed3-103">ICorProfilerCallback::ClassUnloadFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="47ed3-103">ICorProfilerCallback::ClassUnloadFinished Method</span></span>

<span data-ttu-id="47ed3-104">Profil oluşturucuyu bir sınıfın kaldırmayı tamamladığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="47ed3-104">Notifies the profiler that a class has finished unloading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47ed3-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="47ed3-105">Syntax</span></span>  
  
```cpp  
HRESULT ClassUnloadFinished(  
    [in] ClassID classId,  
    [in] HRESULT hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="47ed3-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="47ed3-106">Parameters</span></span>

<span data-ttu-id="47ed3-107">`classId` 'ndaki Kaldırılan sınıfı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="47ed3-107">`classId` [in] Identifies the class that was unloaded.</span></span>

<span data-ttu-id="47ed3-108">`hrStatus` 'ndaki Sınıfın başarıyla yüklenip yüklenmediğini gösteren bir HRESULT.</span><span class="sxs-lookup"><span data-stu-id="47ed3-108">`hrStatus` [in] An HRESULT that indicates whether the class was unloaded successfully.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="47ed3-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="47ed3-109">Remarks</span></span>  

 <span data-ttu-id="47ed3-110">Sınıfı kaldırma işleminin bazı bölümleri geri aramadan sonra devam edebilir `ClassUnloadFinished` .</span><span class="sxs-lookup"><span data-stu-id="47ed3-110">Some parts of unloading the class might continue after the `ClassUnloadFinished` callback.</span></span> <span data-ttu-id="47ed3-111">' De HRESULT hatası, `hrStatus` bir hatayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="47ed3-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="47ed3-112">Ancak, içinde başarılı bir HRESULT, `hrStatus` yalnızca sınıfın kaldırılmasının ilk bölümünün başarılı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="47ed3-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the class has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47ed3-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="47ed3-113">Requirements</span></span>  

 <span data-ttu-id="47ed3-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="47ed3-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47ed3-115">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="47ed3-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="47ed3-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="47ed3-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="47ed3-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47ed3-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47ed3-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="47ed3-118">See also</span></span>

- [<span data-ttu-id="47ed3-119">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="47ed3-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="47ed3-120">ClassUnloadStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="47ed3-120">ClassUnloadStarted Method</span></span>](icorprofilercallback-classunloadstarted-method.md)
