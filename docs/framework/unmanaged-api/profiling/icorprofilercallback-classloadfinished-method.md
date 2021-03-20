---
description: ': ICorProfilerCallback:: ClassLoadFinished yöntemi hakkında daha fazla bilgi edinin'
title: ICorProfilerCallback::ClassLoadFinished Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassLoadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassLoadFinished
helpviewer_keywords:
- ClassLoadFinished method [.NET Framework profiling]
- ICorProfilerCallback::ClassLoadFinished method [.NET Framework profiling]
ms.assetid: 3dd80fbe-d62d-4d4d-acf8-5b7d0efe607e
topic_type:
- apiref
ms.openlocfilehash: 52fd26c1efaf9b85caeb5af7184ae70e1d29b9ff
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2021
ms.locfileid: "104760229"
---
# <a name="icorprofilercallbackclassloadfinished-method"></a><span data-ttu-id="71fd9-103">ICorProfilerCallback::ClassLoadFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="71fd9-103">ICorProfilerCallback::ClassLoadFinished Method</span></span>

<span data-ttu-id="71fd9-104">Profil oluşturucuyu bir sınıfın yükleme tamamlandığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="71fd9-104">Notifies the profiler that a class has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71fd9-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="71fd9-105">Syntax</span></span>  
  
```cpp  
HRESULT ClassLoadFinished(  
    [in] ClassID classId,  
    [in] HRESULT hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="71fd9-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="71fd9-106">Parameters</span></span>

<span data-ttu-id="71fd9-107">`classId` 'ndaki Yüklenen sınıfı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="71fd9-107">`classId` [in] Identifies the class that was loaded.</span></span>

<span data-ttu-id="71fd9-108">`hrStatus` 'ndaki Sınıfın başarıyla yüklenip yüklenmediğini gösteren bir HRESULT.</span><span class="sxs-lookup"><span data-stu-id="71fd9-108">`hrStatus` [in] An HRESULT that indicates whether the class loaded successfully.</span></span>

## <a name="remarks"></a><span data-ttu-id="71fd9-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="71fd9-109">Remarks</span></span>  

 <span data-ttu-id="71fd9-110">Değeri `classId` , `ClassLoadFinished` yöntemi çağrılana kadar bir bilgi isteği için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="71fd9-110">The value of `classId` is not valid for an information request until the `ClassLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="71fd9-111">Sınıfı yüklemenin bazı bölümleri geri aramadan sonra devam edebilir `ClassLoadFinished` .</span><span class="sxs-lookup"><span data-stu-id="71fd9-111">Some parts of loading the class might continue after the `ClassLoadFinished` callback.</span></span> <span data-ttu-id="71fd9-112">' De HRESULT hatası, `hrStatus` bir hatayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="71fd9-112">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="71fd9-113">Ancak, içinde başarılı bir HRESULT, `hrStatus` yalnızca sınıfın yüklemesinin ilk bölümünün başarılı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="71fd9-113">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the class has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71fd9-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="71fd9-114">Requirements</span></span>  

 <span data-ttu-id="71fd9-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="71fd9-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71fd9-116">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="71fd9-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="71fd9-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="71fd9-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="71fd9-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="71fd9-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71fd9-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="71fd9-119">See also</span></span>

- [<span data-ttu-id="71fd9-120">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="71fd9-120">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="71fd9-121">ClassLoadStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="71fd9-121">ClassLoadStarted Method</span></span>](icorprofilercallback-classloadstarted-method.md)
