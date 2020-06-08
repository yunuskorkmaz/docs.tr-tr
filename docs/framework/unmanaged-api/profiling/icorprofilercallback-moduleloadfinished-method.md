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
ms.openlocfilehash: 481fc2c40331e31f6a018d012fb2b2543d4fd9b5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503373"
---
# <a name="icorprofilercallbackmoduleloadfinished-method"></a><span data-ttu-id="2a777-102">ICorProfilerCallback::ModuleLoadFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2a777-102">ICorProfilerCallback::ModuleLoadFinished Method</span></span>
<span data-ttu-id="2a777-103">Profiler 'ın bir modülün yüklemeyi bitirdiğinden emin olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="2a777-103">Notifies the profiler that a module has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a777-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="2a777-104">Syntax</span></span>  
  
```cpp  
HRESULT ModuleLoadFinished(  
    [in] ModuleID moduleId,  
    [in] HRESULT  hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2a777-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2a777-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="2a777-106">'ndaki Yüklemeyi tamamlamış modülün KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="2a777-106">[in] The ID of the module that has finished loading.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="2a777-107">'ndaki Modülün başarıyla yüklenip yüklenmediğini gösteren bir HRESULT.</span><span class="sxs-lookup"><span data-stu-id="2a777-107">[in] An HRESULT that indicates whether the module was loaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2a777-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2a777-108">Remarks</span></span>  
 <span data-ttu-id="2a777-109">Değeri `moduleId` , `ModuleLoadFinished` yöntemi çağrılana kadar bir bilgi isteği için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="2a777-109">The value of `moduleId` is not valid for an information request until the `ModuleLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="2a777-110">Modülün yüklenmesinin bazı bölümleri geri aramadan sonra devam edebilir `ModuleLoadFinished` .</span><span class="sxs-lookup"><span data-stu-id="2a777-110">Some parts of loading the module might continue after the `ModuleLoadFinished` callback.</span></span> <span data-ttu-id="2a777-111">' De HRESULT hatası, `hrStatus` bir hatayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="2a777-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="2a777-112">Ancak, içinde başarılı bir HRESULT, `hrStatus` yalnızca modülün yüklenmesinin ilk bölümünün başarılı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="2a777-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the module has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a777-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2a777-113">Requirements</span></span>  
 <span data-ttu-id="2a777-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a777-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a777-115">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="2a777-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2a777-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="2a777-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2a777-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a777-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a777-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2a777-118">See also</span></span>

- [<span data-ttu-id="2a777-119">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2a777-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="2a777-120">ModuleLoadStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2a777-120">ModuleLoadStarted Method</span></span>](icorprofilercallback-moduleloadstarted-method.md)
