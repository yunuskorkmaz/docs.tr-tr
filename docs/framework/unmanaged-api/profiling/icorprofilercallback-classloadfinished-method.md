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
ms.openlocfilehash: 4be2a50664b001e865b5ecdd9aabe8ba727b8c26
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500396"
---
# <a name="icorprofilercallbackclassloadfinished-method"></a><span data-ttu-id="838d8-102">ICorProfilerCallback::ClassLoadFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="838d8-102">ICorProfilerCallback::ClassLoadFinished Method</span></span>
<span data-ttu-id="838d8-103">Profil oluşturucuyu bir sınıfın yükleme tamamlandığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="838d8-103">Notifies the profiler that a class has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="838d8-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="838d8-104">Syntax</span></span>  
  
```cpp  
HRESULT ClassLoadFinished(  
    [in] ClassID classId,  
    [in] HRESULT hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="838d8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="838d8-105">Parameters</span></span>

- `classId`

  <span data-ttu-id="838d8-106">\[' de], yüklenen sınıfı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="838d8-106">\[in] Identifies the class that was loaded.</span></span>

- `hrStatus`

  <span data-ttu-id="838d8-107">\[içinde] sınıfın başarıyla yüklenip yüklenmediğini gösteren bir HRESULT.</span><span class="sxs-lookup"><span data-stu-id="838d8-107">\[in] An HRESULT that indicates whether the class loaded successfully.</span></span>

## <a name="remarks"></a><span data-ttu-id="838d8-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="838d8-108">Remarks</span></span>  
 <span data-ttu-id="838d8-109">Değeri `classId` , `ClassLoadFinished` yöntemi çağrılana kadar bir bilgi isteği için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="838d8-109">The value of `classId` is not valid for an information request until the `ClassLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="838d8-110">Sınıfı yüklemenin bazı bölümleri geri aramadan sonra devam edebilir `ClassLoadFinished` .</span><span class="sxs-lookup"><span data-stu-id="838d8-110">Some parts of loading the class might continue after the `ClassLoadFinished` callback.</span></span> <span data-ttu-id="838d8-111">' De HRESULT hatası, `hrStatus` bir hatayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="838d8-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="838d8-112">Ancak, içinde başarılı bir HRESULT, `hrStatus` yalnızca sınıfın yüklemesinin ilk bölümünün başarılı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="838d8-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the class has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="838d8-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="838d8-113">Requirements</span></span>  
 <span data-ttu-id="838d8-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="838d8-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="838d8-115">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="838d8-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="838d8-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="838d8-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="838d8-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="838d8-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="838d8-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="838d8-118">See also</span></span>

- [<span data-ttu-id="838d8-119">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="838d8-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="838d8-120">ClassLoadStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="838d8-120">ClassLoadStarted Method</span></span>](icorprofilercallback-classloadstarted-method.md)
