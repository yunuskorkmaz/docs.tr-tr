---
description: ': ICorProfilerCallback:: ModuleUnloadFinished yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 32182beb879813a4e60f69494bd93799c0f66e1d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99745264"
---
# <a name="icorprofilercallbackmoduleunloadfinished-method"></a><span data-ttu-id="80e67-103">ICorProfilerCallback::ModuleUnloadFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="80e67-103">ICorProfilerCallback::ModuleUnloadFinished Method</span></span>

<span data-ttu-id="80e67-104">Profil oluşturucuyu bir modülün kaldırmayı bitirmediğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="80e67-104">Notifies the profiler that a module has finished unloading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80e67-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="80e67-105">Syntax</span></span>  
  
```cpp  
HRESULT ModuleUnloadFinished(  
    [in] ModuleID moduleId,  
    [in] HRESULT  hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="80e67-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="80e67-106">Parameters</span></span>  

 `moduleId`  
 <span data-ttu-id="80e67-107">'ndaki Bellekten kaldırılan modülün KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="80e67-107">[in] The ID of the module that was unloaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="80e67-108">'ndaki Modülün başarıyla yüklenip yüklenmediğini gösteren bir HRESULT.</span><span class="sxs-lookup"><span data-stu-id="80e67-108">[in] An HRESULT that indicates whether the module was unloaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="80e67-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="80e67-109">Remarks</span></span>  

 <span data-ttu-id="80e67-110">Değeri, `moduleId` [ICorProfilerCallback:: ModuleUnloadStarted](icorprofilercallback-moduleunloadstarted-method.md) yönteminin döndürdüğü bir bilgi isteği için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="80e67-110">The value of `moduleId` is not valid for an information request after the [ICorProfilerCallback::ModuleUnloadStarted](icorprofilercallback-moduleunloadstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="80e67-111">Sınıfı kaldırma işleminin bazı bölümleri geri aramadan sonra devam edebilir `ModuleUnloadFinished` .</span><span class="sxs-lookup"><span data-stu-id="80e67-111">Some parts of unloading the class might continue after the `ModuleUnloadFinished` callback.</span></span> <span data-ttu-id="80e67-112">' De HRESULT hatası, `hrStatus` bir hatayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="80e67-112">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="80e67-113">Ancak, içinde başarılı bir HRESULT, `hrStatus` yalnızca modülün kaldırılmasının ilk bölümünün başarılı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="80e67-113">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the module has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80e67-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="80e67-114">Requirements</span></span>  

 <span data-ttu-id="80e67-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80e67-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80e67-116">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="80e67-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="80e67-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="80e67-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="80e67-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80e67-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80e67-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="80e67-119">See also</span></span>

- [<span data-ttu-id="80e67-120">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="80e67-120">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
