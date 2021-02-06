---
description: ': ICorProfilerCallback:: AssemblyLoadFinished yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 19c0871808455e64ad8a4eb002806a87030f7882
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99648044"
---
# <a name="icorprofilercallbackassemblyloadfinished-method"></a><span data-ttu-id="7bd27-103">ICorProfilerCallback::AssemblyLoadFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7bd27-103">ICorProfilerCallback::AssemblyLoadFinished Method</span></span>

<span data-ttu-id="7bd27-104">Profiler 'ın bir derlemenin yüklemeyi bitirmiş olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="7bd27-104">Notifies the profiler that an assembly has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7bd27-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7bd27-105">Syntax</span></span>  
  
```cpp  
HRESULT AssemblyLoadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7bd27-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7bd27-106">Parameters</span></span>

- `assemblyId`

  <span data-ttu-id="7bd27-107">\[' de], yüklenmiş derlemeyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7bd27-107">\[in] Identifies the assembly that was loaded.</span></span>

- `hrStatus`

  <span data-ttu-id="7bd27-108">\[içinde] derlemenin başarıyla yüklenip yüklenmediğini belirten bir HRESULT.</span><span class="sxs-lookup"><span data-stu-id="7bd27-108">\[in] An HRESULT that indicates whether the assembly finished loading successfully.</span></span>

## <a name="remarks"></a><span data-ttu-id="7bd27-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7bd27-109">Remarks</span></span>  

 <span data-ttu-id="7bd27-110">Değeri `assemblyId` , `AssemblyLoadFinished` yöntemi çağrılana kadar bir bilgi isteği için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="7bd27-110">The value of `assemblyId` is not valid for an information request until the `AssemblyLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="7bd27-111">Derlemeyi yüklemenin bazı bölümleri geri aramadan sonra devam edebilir `AssemblyLoadFinished` .</span><span class="sxs-lookup"><span data-stu-id="7bd27-111">Some parts of loading the assembly might continue after the `AssemblyLoadFinished` callback.</span></span> <span data-ttu-id="7bd27-112">' De HRESULT hatası, `hrStatus` bir hatayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="7bd27-112">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="7bd27-113">Ancak, içinde başarılı bir HRESULT, `hrStatus` sadece derlemeyi yüklemenin ilk bölümünün başarılı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="7bd27-113">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the assembly has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7bd27-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7bd27-114">Requirements</span></span>  

 <span data-ttu-id="7bd27-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7bd27-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7bd27-116">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="7bd27-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7bd27-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="7bd27-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7bd27-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7bd27-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bd27-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7bd27-119">See also</span></span>

- [<span data-ttu-id="7bd27-120">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7bd27-120">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
