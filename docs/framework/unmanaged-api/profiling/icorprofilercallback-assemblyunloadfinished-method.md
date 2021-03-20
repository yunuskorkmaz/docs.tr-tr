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
ms.openlocfilehash: c3c87644602ede3b849d13624b0cc0a2df71e2fd
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2021
ms.locfileid: "104760677"
---
# <a name="icorprofilercallbackassemblyunloadfinished-method"></a><span data-ttu-id="76a8b-103">ICorProfilerCallback::AssemblyUnloadFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="76a8b-103">ICorProfilerCallback::AssemblyUnloadFinished Method</span></span>

<span data-ttu-id="76a8b-104">Profiler öğesine bir derlemenin kaldırılmış olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="76a8b-104">Notifies the profiler that an assembly has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76a8b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="76a8b-105">Syntax</span></span>  
  
```cpp  
HRESULT AssemblyUnloadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="76a8b-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="76a8b-106">Parameters</span></span>

<span data-ttu-id="76a8b-107">`assemblyId` 'ndaki Kaldırılmakta olan derlemeyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="76a8b-107">`assemblyId` [in] Identifies the assembly that is being unloaded.</span></span>

<span data-ttu-id="76a8b-108">`hrStatus` 'ndaki Derlemenin başarıyla yüklenip yüklenmediğini gösteren bir HRESULT.</span><span class="sxs-lookup"><span data-stu-id="76a8b-108">`hrStatus` [in] An HRESULT that indicates whether the assembly was unloaded successfully.</span></span>

## <a name="remarks"></a><span data-ttu-id="76a8b-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="76a8b-109">Remarks</span></span>  

 <span data-ttu-id="76a8b-110">Değeri, `assemblyId` [ICorProfilerCallback:: AssemblyUnloadStarted](icorprofilercallback-assemblyunloadstarted-method.md) yönteminin döndürdüğü bir bilgi isteği için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="76a8b-110">The value of `assemblyId` is not valid for an information request after the [ICorProfilerCallback::AssemblyUnloadStarted](icorprofilercallback-assemblyunloadstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="76a8b-111">Derlemeyi kaldırma işleminin bazı bölümleri geri aramadan sonra devam edebilir `AssemblyUnloadFinished` .</span><span class="sxs-lookup"><span data-stu-id="76a8b-111">Some parts of unloading the assembly might continue after the `AssemblyUnloadFinished` callback.</span></span> <span data-ttu-id="76a8b-112">' De HRESULT hatası, `hrStatus` bir hatayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="76a8b-112">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="76a8b-113">Ancak, içinde başarılı bir HRESULT, `hrStatus` sadece derlemeyi kaldırma ilk bölümünün başarılı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="76a8b-113">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the assembly has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76a8b-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="76a8b-114">Requirements</span></span>  

 <span data-ttu-id="76a8b-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="76a8b-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76a8b-116">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="76a8b-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="76a8b-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="76a8b-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="76a8b-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="76a8b-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76a8b-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="76a8b-119">See also</span></span>

- [<span data-ttu-id="76a8b-120">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="76a8b-120">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
