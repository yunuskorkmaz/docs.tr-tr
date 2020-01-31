---
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
ms.openlocfilehash: e0ff90f99c1127b5a4626f47514ba7099b5d48af
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866604"
---
# <a name="icorprofilercallbackclassloadfinished-method"></a><span data-ttu-id="b31f0-102">ICorProfilerCallback::ClassLoadFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b31f0-102">ICorProfilerCallback::ClassLoadFinished Method</span></span>
<span data-ttu-id="b31f0-103">Profil oluşturucuyu bir sınıfın yükleme tamamlandığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="b31f0-103">Notifies the profiler that a class has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b31f0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b31f0-104">Syntax</span></span>  
  
```cpp  
HRESULT ClassLoadFinished(  
    [in] ClassID classId,  
    [in] HRESULT hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b31f0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b31f0-105">Parameters</span></span>

- `classId`

  <span data-ttu-id="b31f0-106">\[in], yüklenen sınıfı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b31f0-106">\[in] Identifies the class that was loaded.</span></span>

- `hrStatus`

  <span data-ttu-id="b31f0-107">\[, sınıfın başarıyla yüklenip yüklenmediğini gösteren bir HRESULT.</span><span class="sxs-lookup"><span data-stu-id="b31f0-107">\[in] An HRESULT that indicates whether the class loaded successfully.</span></span>

## <a name="remarks"></a><span data-ttu-id="b31f0-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b31f0-108">Remarks</span></span>  
 <span data-ttu-id="b31f0-109">`classId` değeri, `ClassLoadFinished` yöntemi çağrılana kadar bir bilgi isteği için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="b31f0-109">The value of `classId` is not valid for an information request until the `ClassLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="b31f0-110">Sınıfı yüklemenin bazı bölümleri `ClassLoadFinished` geri çağrısından sonra devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="b31f0-110">Some parts of loading the class might continue after the `ClassLoadFinished` callback.</span></span> <span data-ttu-id="b31f0-111">`hrStatus` HRESULT hatası, bir hatayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="b31f0-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="b31f0-112">Ancak, `hrStatus` başarılı bir HRESULT, yalnızca sınıfın yüklemesinin ilk bölümünün başarılı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="b31f0-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the class has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b31f0-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b31f0-113">Requirements</span></span>  
 <span data-ttu-id="b31f0-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b31f0-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b31f0-115">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="b31f0-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b31f0-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b31f0-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b31f0-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b31f0-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b31f0-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b31f0-118">See also</span></span>

- [<span data-ttu-id="b31f0-119">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b31f0-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="b31f0-120">ClassLoadStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b31f0-120">ClassLoadStarted Method</span></span>](icorprofilercallback-classloadstarted-method.md)
