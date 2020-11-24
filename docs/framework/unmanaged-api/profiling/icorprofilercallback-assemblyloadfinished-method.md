---
title: ICorProfilerCallback::AssemblyLoadFinished Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AssemblyLoadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyLoadFinished
helpviewer_keywords:
- ICorProfilerCallback::AssemblyLoadFinished method [.NET Framework profiling]
- AssemblyLoadFinished method [.NET Framework profiling]
ms.assetid: 86d98f39-52e6-4c61-a625-9760f695ff12
topic_type:
- apiref
ms.openlocfilehash: fd41463af0acac1bbe1a3d4515350905b6784f79
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95685350"
---
# <a name="icorprofilercallbackassemblyloadfinished-method"></a><span data-ttu-id="9e27d-102">ICorProfilerCallback::AssemblyLoadFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9e27d-102">ICorProfilerCallback::AssemblyLoadFinished Method</span></span>

<span data-ttu-id="9e27d-103">Profiler 'ın bir derlemenin yüklemeyi bitirmiş olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="9e27d-103">Notifies the profiler that an assembly has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e27d-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="9e27d-104">Syntax</span></span>  
  
```cpp  
HRESULT AssemblyLoadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9e27d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9e27d-105">Parameters</span></span>

- `assemblyId`

  <span data-ttu-id="9e27d-106">\[' de], yüklenmiş derlemeyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9e27d-106">\[in] Identifies the assembly that was loaded.</span></span>

- `hrStatus`

  <span data-ttu-id="9e27d-107">\[içinde] derlemenin başarıyla yüklenip yüklenmediğini belirten bir HRESULT.</span><span class="sxs-lookup"><span data-stu-id="9e27d-107">\[in] An HRESULT that indicates whether the assembly finished loading successfully.</span></span>

## <a name="remarks"></a><span data-ttu-id="9e27d-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9e27d-108">Remarks</span></span>  

 <span data-ttu-id="9e27d-109">Değeri `assemblyId` , `AssemblyLoadFinished` yöntemi çağrılana kadar bir bilgi isteği için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="9e27d-109">The value of `assemblyId` is not valid for an information request until the `AssemblyLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="9e27d-110">Derlemeyi yüklemenin bazı bölümleri geri aramadan sonra devam edebilir `AssemblyLoadFinished` .</span><span class="sxs-lookup"><span data-stu-id="9e27d-110">Some parts of loading the assembly might continue after the `AssemblyLoadFinished` callback.</span></span> <span data-ttu-id="9e27d-111">' De HRESULT hatası, `hrStatus` bir hatayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="9e27d-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="9e27d-112">Ancak, içinde başarılı bir HRESULT, `hrStatus` sadece derlemeyi yüklemenin ilk bölümünün başarılı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="9e27d-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the assembly has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e27d-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9e27d-113">Requirements</span></span>  

 <span data-ttu-id="9e27d-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e27d-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e27d-115">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="9e27d-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9e27d-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="9e27d-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9e27d-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e27d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e27d-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9e27d-118">See also</span></span>

- [<span data-ttu-id="9e27d-119">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e27d-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
