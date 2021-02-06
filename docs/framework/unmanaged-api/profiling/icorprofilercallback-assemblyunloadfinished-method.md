---
description: ': ICorProfilerCallback:: AssemblyUnloadFinished yöntemi hakkında daha fazla bilgi edinin'
title: ICorProfilerCallback::AssemblyUnloadFinished Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AssemblyUnloadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyUnloadFinished
helpviewer_keywords:
- AssemblyUnloadFinished method [.NET Framework profiling]
- ICorProfilerCallback::AssemblyUnloadFinished method [.NET Framework profiling]
ms.assetid: 53fca564-84b1-44d4-9e21-17a492d2aae7
topic_type:
- apiref
ms.openlocfilehash: 30d6bd805a1466d6a65728b22f677ba00e09ffb6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99648031"
---
# <a name="icorprofilercallbackassemblyunloadfinished-method"></a><span data-ttu-id="c310d-103">ICorProfilerCallback::AssemblyUnloadFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c310d-103">ICorProfilerCallback::AssemblyUnloadFinished Method</span></span>

<span data-ttu-id="c310d-104">Profiler öğesine bir derlemenin kaldırılmış olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="c310d-104">Notifies the profiler that an assembly has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c310d-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c310d-105">Syntax</span></span>  
  
```cpp  
HRESULT AssemblyUnloadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c310d-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c310d-106">Parameters</span></span>

- `assemblyId`

  <span data-ttu-id="c310d-107">\[' de], kaldırılmakta olan derlemeyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c310d-107">\[in] Identifies the assembly that is being unloaded.</span></span>

- `hrStatus`

  <span data-ttu-id="c310d-108">\[içinde] derlemenin başarıyla yüklenip yüklenmediğini gösteren bir HRESULT.</span><span class="sxs-lookup"><span data-stu-id="c310d-108">\[in] An HRESULT that indicates whether the assembly was unloaded successfully.</span></span>

## <a name="remarks"></a><span data-ttu-id="c310d-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c310d-109">Remarks</span></span>  

 <span data-ttu-id="c310d-110">Değeri, `assemblyId` [ICorProfilerCallback:: AssemblyUnloadStarted](icorprofilercallback-assemblyunloadstarted-method.md) yönteminin döndürdüğü bir bilgi isteği için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="c310d-110">The value of `assemblyId` is not valid for an information request after the [ICorProfilerCallback::AssemblyUnloadStarted](icorprofilercallback-assemblyunloadstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="c310d-111">Derlemeyi kaldırma işleminin bazı bölümleri geri aramadan sonra devam edebilir `AssemblyUnloadFinished` .</span><span class="sxs-lookup"><span data-stu-id="c310d-111">Some parts of unloading the assembly might continue after the `AssemblyUnloadFinished` callback.</span></span> <span data-ttu-id="c310d-112">' De HRESULT hatası, `hrStatus` bir hatayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="c310d-112">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="c310d-113">Ancak, içinde başarılı bir HRESULT, `hrStatus` sadece derlemeyi kaldırma ilk bölümünün başarılı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="c310d-113">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the assembly has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c310d-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c310d-114">Requirements</span></span>  

 <span data-ttu-id="c310d-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c310d-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c310d-116">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="c310d-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c310d-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c310d-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c310d-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c310d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c310d-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c310d-119">See also</span></span>

- [<span data-ttu-id="c310d-120">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c310d-120">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
