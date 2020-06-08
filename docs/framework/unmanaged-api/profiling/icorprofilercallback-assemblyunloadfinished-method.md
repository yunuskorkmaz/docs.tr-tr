---
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
ms.openlocfilehash: d00e67d29921edc6b7487ceeb12aaa9e9f9bd0ac
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500422"
---
# <a name="icorprofilercallbackassemblyunloadfinished-method"></a><span data-ttu-id="294d2-102">ICorProfilerCallback::AssemblyUnloadFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="294d2-102">ICorProfilerCallback::AssemblyUnloadFinished Method</span></span>
<span data-ttu-id="294d2-103">Profiler öğesine bir derlemenin kaldırılmış olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="294d2-103">Notifies the profiler that an assembly has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="294d2-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="294d2-104">Syntax</span></span>  
  
```cpp  
HRESULT AssemblyUnloadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="294d2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="294d2-105">Parameters</span></span>

- `assemblyId`

  <span data-ttu-id="294d2-106">\[' de], kaldırılmakta olan derlemeyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="294d2-106">\[in] Identifies the assembly that is being unloaded.</span></span>

- `hrStatus`

  <span data-ttu-id="294d2-107">\[içinde] derlemenin başarıyla yüklenip yüklenmediğini gösteren bir HRESULT.</span><span class="sxs-lookup"><span data-stu-id="294d2-107">\[in] An HRESULT that indicates whether the assembly was unloaded successfully.</span></span>

## <a name="remarks"></a><span data-ttu-id="294d2-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="294d2-108">Remarks</span></span>  
 <span data-ttu-id="294d2-109">Değeri, `assemblyId` [ICorProfilerCallback:: AssemblyUnloadStarted](icorprofilercallback-assemblyunloadstarted-method.md) yönteminin döndürdüğü bir bilgi isteği için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="294d2-109">The value of `assemblyId` is not valid for an information request after the [ICorProfilerCallback::AssemblyUnloadStarted](icorprofilercallback-assemblyunloadstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="294d2-110">Derlemeyi kaldırma işleminin bazı bölümleri geri aramadan sonra devam edebilir `AssemblyUnloadFinished` .</span><span class="sxs-lookup"><span data-stu-id="294d2-110">Some parts of unloading the assembly might continue after the `AssemblyUnloadFinished` callback.</span></span> <span data-ttu-id="294d2-111">' De HRESULT hatası, `hrStatus` bir hatayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="294d2-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="294d2-112">Ancak, içinde başarılı bir HRESULT, `hrStatus` sadece derlemeyi kaldırma ilk bölümünün başarılı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="294d2-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the assembly has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="294d2-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="294d2-113">Requirements</span></span>  
 <span data-ttu-id="294d2-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="294d2-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="294d2-115">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="294d2-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="294d2-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="294d2-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="294d2-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="294d2-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="294d2-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="294d2-118">See also</span></span>

- [<span data-ttu-id="294d2-119">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="294d2-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
