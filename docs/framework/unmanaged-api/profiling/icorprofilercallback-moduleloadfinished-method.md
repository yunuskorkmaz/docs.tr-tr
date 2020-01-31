---
title: ICorProfilerCallback::ModuleLoadFinished Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleLoadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleLoadFinished
helpviewer_keywords:
- ModuleLoadFinished method [.NET Framework profiling]
- ICorProfilerCallback::ModuleLoadFinished method [.NET Framework profiling]
ms.assetid: 050649e5-ffc0-4458-a0a4-d9ee128a219e
topic_type:
- apiref
ms.openlocfilehash: 661229e5fbd5d106662f0e823a1753bd76c33311
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866175"
---
# <a name="icorprofilercallbackmoduleloadfinished-method"></a><span data-ttu-id="bbb9c-102">ICorProfilerCallback::ModuleLoadFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bbb9c-102">ICorProfilerCallback::ModuleLoadFinished Method</span></span>
<span data-ttu-id="bbb9c-103">Profiler 'ın bir modülün yüklemeyi bitirdiğinden emin olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="bbb9c-103">Notifies the profiler that a module has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bbb9c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bbb9c-104">Syntax</span></span>  
  
```cpp  
HRESULT ModuleLoadFinished(  
    [in] ModuleID moduleId,  
    [in] HRESULT  hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bbb9c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bbb9c-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="bbb9c-106">'ndaki Yüklemeyi tamamlamış modülün KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="bbb9c-106">[in] The ID of the module that has finished loading.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="bbb9c-107">'ndaki Modülün başarıyla yüklenip yüklenmediğini gösteren bir HRESULT.</span><span class="sxs-lookup"><span data-stu-id="bbb9c-107">[in] An HRESULT that indicates whether the module was loaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bbb9c-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bbb9c-108">Remarks</span></span>  
 <span data-ttu-id="bbb9c-109">`moduleId` değeri, `ModuleLoadFinished` yöntemi çağrılana kadar bir bilgi isteği için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="bbb9c-109">The value of `moduleId` is not valid for an information request until the `ModuleLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="bbb9c-110">Modülün yüklenmesinin bazı bölümleri `ModuleLoadFinished` geri çağrısından sonra devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="bbb9c-110">Some parts of loading the module might continue after the `ModuleLoadFinished` callback.</span></span> <span data-ttu-id="bbb9c-111">`hrStatus` HRESULT hatası, bir hatayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="bbb9c-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="bbb9c-112">Ancak `hrStatus` başarılı bir HRESULT, yalnızca modülün yüklenmesinin ilk bölümünün başarılı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="bbb9c-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the module has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bbb9c-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bbb9c-113">Requirements</span></span>  
 <span data-ttu-id="bbb9c-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bbb9c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bbb9c-115">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="bbb9c-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bbb9c-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="bbb9c-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bbb9c-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bbb9c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbb9c-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bbb9c-118">See also</span></span>

- [<span data-ttu-id="bbb9c-119">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bbb9c-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="bbb9c-120">ModuleLoadStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bbb9c-120">ModuleLoadStarted Method</span></span>](icorprofilercallback-moduleloadstarted-method.md)
