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
ms.openlocfilehash: accddef08f3cb76ef2cb1b70993aee24cf83ae50
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2021
ms.locfileid: "104760680"
---
# <a name="icorprofilercallbackassemblyloadfinished-method"></a><span data-ttu-id="75655-103">ICorProfilerCallback::AssemblyLoadFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="75655-103">ICorProfilerCallback::AssemblyLoadFinished Method</span></span>

<span data-ttu-id="75655-104">Profiler 'ın bir derlemenin yüklemeyi bitirmiş olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="75655-104">Notifies the profiler that an assembly has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75655-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="75655-105">Syntax</span></span>  
  
```cpp  
HRESULT AssemblyLoadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="75655-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="75655-106">Parameters</span></span>

<span data-ttu-id="75655-107">`assemblyId` 'ndaki Yüklenen derlemeyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="75655-107">`assemblyId` [in] Identifies the assembly that was loaded.</span></span>

<span data-ttu-id="75655-108">`hrStatus` 'ndaki Derlemenin başarıyla yüklenip yüklenmediğini gösteren bir HRESULT.</span><span class="sxs-lookup"><span data-stu-id="75655-108">`hrStatus` [in] An HRESULT that indicates whether the assembly finished loading successfully.</span></span>

## <a name="remarks"></a><span data-ttu-id="75655-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="75655-109">Remarks</span></span>  

 <span data-ttu-id="75655-110">Değeri `assemblyId` , `AssemblyLoadFinished` yöntemi çağrılana kadar bir bilgi isteği için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="75655-110">The value of `assemblyId` is not valid for an information request until the `AssemblyLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="75655-111">Derlemeyi yüklemenin bazı bölümleri geri aramadan sonra devam edebilir `AssemblyLoadFinished` .</span><span class="sxs-lookup"><span data-stu-id="75655-111">Some parts of loading the assembly might continue after the `AssemblyLoadFinished` callback.</span></span> <span data-ttu-id="75655-112">' De HRESULT hatası, `hrStatus` bir hatayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="75655-112">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="75655-113">Ancak, içinde başarılı bir HRESULT, `hrStatus` sadece derlemeyi yüklemenin ilk bölümünün başarılı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="75655-113">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the assembly has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75655-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="75655-114">Requirements</span></span>  

 <span data-ttu-id="75655-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="75655-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75655-116">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="75655-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="75655-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="75655-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="75655-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75655-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75655-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="75655-119">See also</span></span>

- [<span data-ttu-id="75655-120">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="75655-120">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
