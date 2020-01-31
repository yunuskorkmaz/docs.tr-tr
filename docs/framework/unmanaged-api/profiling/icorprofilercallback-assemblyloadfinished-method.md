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
ms.openlocfilehash: 15ce195af0c0e8f8777f6e5d02043e17e32308da
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866656"
---
# <a name="icorprofilercallbackassemblyloadfinished-method"></a><span data-ttu-id="1c881-102">ICorProfilerCallback::AssemblyLoadFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1c881-102">ICorProfilerCallback::AssemblyLoadFinished Method</span></span>
<span data-ttu-id="1c881-103">Profiler 'ın bir derlemenin yüklemeyi bitirmiş olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="1c881-103">Notifies the profiler that an assembly has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c881-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1c881-104">Syntax</span></span>  
  
```cpp  
HRESULT AssemblyLoadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1c881-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1c881-105">Parameters</span></span>

- `assemblyId`

  <span data-ttu-id="1c881-106">\[in], yüklenen derlemeyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1c881-106">\[in] Identifies the assembly that was loaded.</span></span>

- `hrStatus`

  <span data-ttu-id="1c881-107">\[içinde] derlemenin başarıyla yüklenip yüklenmediğini gösteren bir HRESULT.</span><span class="sxs-lookup"><span data-stu-id="1c881-107">\[in] An HRESULT that indicates whether the assembly finished loading successfully.</span></span>

## <a name="remarks"></a><span data-ttu-id="1c881-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1c881-108">Remarks</span></span>  
 <span data-ttu-id="1c881-109">`assemblyId` değeri, `AssemblyLoadFinished` yöntemi çağrılana kadar bir bilgi isteği için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="1c881-109">The value of `assemblyId` is not valid for an information request until the `AssemblyLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="1c881-110">Derlemeyi yüklemenin bazı bölümleri `AssemblyLoadFinished` geri çağrısından sonra devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="1c881-110">Some parts of loading the assembly might continue after the `AssemblyLoadFinished` callback.</span></span> <span data-ttu-id="1c881-111">`hrStatus` HRESULT hatası, bir hatayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="1c881-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="1c881-112">Ancak, `hrStatus` başarılı bir HRESULT, sadece derlemeyi yüklemenin ilk bölümünün başarılı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="1c881-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the assembly has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c881-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1c881-113">Requirements</span></span>  
 <span data-ttu-id="1c881-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1c881-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c881-115">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="1c881-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1c881-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="1c881-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1c881-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c881-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c881-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1c881-118">See also</span></span>

- [<span data-ttu-id="1c881-119">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1c881-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
