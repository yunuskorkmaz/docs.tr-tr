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
ms.openlocfilehash: ef2c518f8f3f3069e93f06de89add1385cb4e45e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445121"
---
# <a name="icorprofilercallbackclassloadfinished-method"></a><span data-ttu-id="35a30-102">ICorProfilerCallback::ClassLoadFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="35a30-102">ICorProfilerCallback::ClassLoadFinished Method</span></span>
<span data-ttu-id="35a30-103">Profil oluşturucuyu bir sınıfın yükleme tamamlandığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="35a30-103">Notifies the profiler that a class has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35a30-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="35a30-104">Syntax</span></span>  
  
```cpp  
HRESULT ClassLoadFinished(  
    [in] ClassID classId,  
    [in] HRESULT hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="35a30-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="35a30-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="35a30-106">'ndaki Yüklenen sınıfı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="35a30-106">[in] Identifies the class that was loaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="35a30-107">'ndaki Sınıfın başarıyla yüklenip yüklenmediğini gösteren bir HRESULT.</span><span class="sxs-lookup"><span data-stu-id="35a30-107">[in] An HRESULT that indicates whether the class loaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="35a30-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="35a30-108">Remarks</span></span>  
 <span data-ttu-id="35a30-109">`classId` değeri, `ClassLoadFinished` yöntemi çağrılana kadar bir bilgi isteği için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="35a30-109">The value of `classId` is not valid for an information request until the `ClassLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="35a30-110">Sınıfı yüklemenin bazı bölümleri `ClassLoadFinished` geri çağrısından sonra devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="35a30-110">Some parts of loading the class might continue after the `ClassLoadFinished` callback.</span></span> <span data-ttu-id="35a30-111">`hrStatus` HRESULT hatası, bir hatayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="35a30-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="35a30-112">Ancak, `hrStatus` başarılı bir HRESULT, yalnızca sınıfın yüklemesinin ilk bölümünün başarılı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="35a30-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the class has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35a30-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="35a30-113">Requirements</span></span>  
 <span data-ttu-id="35a30-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="35a30-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35a30-115">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="35a30-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="35a30-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="35a30-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="35a30-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="35a30-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35a30-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="35a30-118">See also</span></span>

- [<span data-ttu-id="35a30-119">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="35a30-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="35a30-120">ClassLoadStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="35a30-120">ClassLoadStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadstarted-method.md)
