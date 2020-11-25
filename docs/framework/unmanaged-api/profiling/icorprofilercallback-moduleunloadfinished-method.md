---
title: ICorProfilerCallback::ModuleUnloadFinished Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleUnloadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleUnloadFinished
helpviewer_keywords:
- ModuleUnloadFinished method [.NET Framework profiling]
- ICorProfilerCallback::ModuleUnloadFinished method [.NET Framework profiling]
ms.assetid: 185e3327-9f9c-44bc-8a5c-febea9a6bb5b
topic_type:
- apiref
ms.openlocfilehash: 514c20455b95ecf74ffaecd349982fd8f8f49816
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723239"
---
# <a name="icorprofilercallbackmoduleunloadfinished-method"></a><span data-ttu-id="190e4-102">ICorProfilerCallback::ModuleUnloadFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="190e4-102">ICorProfilerCallback::ModuleUnloadFinished Method</span></span>

<span data-ttu-id="190e4-103">Profil oluşturucuyu bir modülün kaldırmayı bitirmediğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="190e4-103">Notifies the profiler that a module has finished unloading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="190e4-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="190e4-104">Syntax</span></span>  
  
```cpp  
HRESULT ModuleUnloadFinished(  
    [in] ModuleID moduleId,  
    [in] HRESULT  hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="190e4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="190e4-105">Parameters</span></span>  

 `moduleId`  
 <span data-ttu-id="190e4-106">'ndaki Bellekten kaldırılan modülün KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="190e4-106">[in] The ID of the module that was unloaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="190e4-107">'ndaki Modülün başarıyla yüklenip yüklenmediğini gösteren bir HRESULT.</span><span class="sxs-lookup"><span data-stu-id="190e4-107">[in] An HRESULT that indicates whether the module was unloaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="190e4-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="190e4-108">Remarks</span></span>  

 <span data-ttu-id="190e4-109">Değeri, `moduleId` [ICorProfilerCallback:: ModuleUnloadStarted](icorprofilercallback-moduleunloadstarted-method.md) yönteminin döndürdüğü bir bilgi isteği için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="190e4-109">The value of `moduleId` is not valid for an information request after the [ICorProfilerCallback::ModuleUnloadStarted](icorprofilercallback-moduleunloadstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="190e4-110">Sınıfı kaldırma işleminin bazı bölümleri geri aramadan sonra devam edebilir `ModuleUnloadFinished` .</span><span class="sxs-lookup"><span data-stu-id="190e4-110">Some parts of unloading the class might continue after the `ModuleUnloadFinished` callback.</span></span> <span data-ttu-id="190e4-111">' De HRESULT hatası, `hrStatus` bir hatayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="190e4-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="190e4-112">Ancak, içinde başarılı bir HRESULT, `hrStatus` yalnızca modülün kaldırılmasının ilk bölümünün başarılı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="190e4-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the module has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="190e4-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="190e4-113">Requirements</span></span>  

 <span data-ttu-id="190e4-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="190e4-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="190e4-115">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="190e4-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="190e4-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="190e4-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="190e4-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="190e4-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="190e4-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="190e4-118">See also</span></span>

- [<span data-ttu-id="190e4-119">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="190e4-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
