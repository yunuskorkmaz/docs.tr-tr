---
description: ': ICorProfilerCallback:: ModuleLoadFinished yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 960eb9edd036055069ef3f9ab3a93602ce4ef9bf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99745352"
---
# <a name="icorprofilercallbackmoduleloadfinished-method"></a><span data-ttu-id="20dfa-103">ICorProfilerCallback::ModuleLoadFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="20dfa-103">ICorProfilerCallback::ModuleLoadFinished Method</span></span>

<span data-ttu-id="20dfa-104">Profiler 'ın bir modülün yüklemeyi bitirdiğinden emin olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="20dfa-104">Notifies the profiler that a module has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20dfa-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="20dfa-105">Syntax</span></span>  
  
```cpp  
HRESULT ModuleLoadFinished(  
    [in] ModuleID moduleId,  
    [in] HRESULT  hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="20dfa-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="20dfa-106">Parameters</span></span>  

 `moduleId`  
 <span data-ttu-id="20dfa-107">'ndaki Yüklemeyi tamamlamış modülün KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="20dfa-107">[in] The ID of the module that has finished loading.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="20dfa-108">'ndaki Modülün başarıyla yüklenip yüklenmediğini gösteren bir HRESULT.</span><span class="sxs-lookup"><span data-stu-id="20dfa-108">[in] An HRESULT that indicates whether the module was loaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="20dfa-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="20dfa-109">Remarks</span></span>  

 <span data-ttu-id="20dfa-110">Değeri `moduleId` , `ModuleLoadFinished` yöntemi çağrılana kadar bir bilgi isteği için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="20dfa-110">The value of `moduleId` is not valid for an information request until the `ModuleLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="20dfa-111">Modülün yüklenmesinin bazı bölümleri geri aramadan sonra devam edebilir `ModuleLoadFinished` .</span><span class="sxs-lookup"><span data-stu-id="20dfa-111">Some parts of loading the module might continue after the `ModuleLoadFinished` callback.</span></span> <span data-ttu-id="20dfa-112">' De HRESULT hatası, `hrStatus` bir hatayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="20dfa-112">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="20dfa-113">Ancak, içinde başarılı bir HRESULT, `hrStatus` yalnızca modülün yüklenmesinin ilk bölümünün başarılı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="20dfa-113">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the module has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20dfa-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="20dfa-114">Requirements</span></span>  

 <span data-ttu-id="20dfa-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20dfa-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20dfa-116">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="20dfa-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="20dfa-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="20dfa-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="20dfa-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20dfa-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20dfa-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="20dfa-119">See also</span></span>

- [<span data-ttu-id="20dfa-120">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="20dfa-120">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="20dfa-121">ModuleLoadStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="20dfa-121">ModuleLoadStarted Method</span></span>](icorprofilercallback-moduleloadstarted-method.md)
