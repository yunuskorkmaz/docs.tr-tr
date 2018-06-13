---
title: ICorProfilerCallback8::DynamicMethodJITCompilationStarted yöntemi
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationStarted
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ad74eeb4deeae73be40b3a0bc0f6a18ec2299780
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33454756"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationstarted-method"></a><span data-ttu-id="4f0ee-102">ICorProfilerCallback8::DynamicMethodJITCompilationStarted yöntemi</span><span class="sxs-lookup"><span data-stu-id="4f0ee-102">ICorProfilerCallback8::DynamicMethodJITCompilationStarted Method</span></span>
<span data-ttu-id="4f0ee-103">[.NET Framework 4.7 ve sonraki sürümlerinde desteklenen]</span><span class="sxs-lookup"><span data-stu-id="4f0ee-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  
  
<span data-ttu-id="4f0ee-104">Profil Oluşturucu JIT derleme dinamik yönteminin başlatıldı her bildirir.</span><span class="sxs-lookup"><span data-stu-id="4f0ee-104">Notifies the profiler whenever JIT compilation of a dynamic method has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f0ee-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4f0ee-105">Syntax</span></span>  
  
```  
HRESULT DynamicMethodJITCompilationStarted(  
     [in]  FunctionID  functionId,   
     [in]  BOOL        fIsSafeToBlock,   
     [in]  LPCBYTE     pILHeader,   
     [in]  LONG        cbILHeader   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4f0ee-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4f0ee-106">Parameters</span></span>  
<span data-ttu-id="4f0ee-107">[in] `functionId`</span><span class="sxs-lookup"><span data-stu-id="4f0ee-107">[in] `functionId`</span></span>  
<span data-ttu-id="4f0ee-108">Bellek içi işlevi için hangi JIT derleme başladı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="4f0ee-108">The identifier of the in-memory function for which JIT compilation is started.</span></span>   

<span data-ttu-id="4f0ee-109">[in] `fIsSafeToBlock` </span><span class="sxs-lookup"><span data-stu-id="4f0ee-109">[in] `fIsSafeToBlock` </span></span>  
<span data-ttu-id="4f0ee-110">`true` engelleme ten bu geri dönmek çağıran iş parçacığı beklemek çalışma zamanı yaratabilir belirtmek için; `false` engelleme işlemi çalışma zamanının etkilemez belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="4f0ee-110">`true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  

<span data-ttu-id="4f0ee-111">[in] `pILHeader`  </span><span class="sxs-lookup"><span data-stu-id="4f0ee-111">[in] `pILHeader`  </span></span>  
<span data-ttu-id="4f0ee-112">Bir işaretçi yöntemin IL üstbilgisinin ilk bayta.</span><span class="sxs-lookup"><span data-stu-id="4f0ee-112">A pointer to the first byte of the method's IL header.</span></span>   

<span data-ttu-id="4f0ee-113">[in] `cbILHeader`  </span><span class="sxs-lookup"><span data-stu-id="4f0ee-113">[in] `cbILHeader`  </span></span>  
<span data-ttu-id="4f0ee-114">IL üstbilgisinde bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="4f0ee-114">The number of bytes in the IL header.</span></span> 

## <a name="remarks"></a><span data-ttu-id="4f0ee-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4f0ee-115">Remarks</span></span>  

<span data-ttu-id="4f0ee-116">Dinamik bir yöntem JIT derlenmiş olduğunda bu geri çağırma tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="4f0ee-116">This callback is triggered whenever a dynamic method is JIT-compiled.</span></span> <span data-ttu-id="4f0ee-117">Bu, çeşitli IL saplamalar ve LCG yöntemleri içerir.</span><span class="sxs-lookup"><span data-stu-id="4f0ee-117">This includes various IL stubs and LCG methods.</span></span> <span data-ttu-id="4f0ee-118">Profil Oluşturucu yazıcılarının kullanıcılara derlenmiş yöntemini belirlemek için yeterli bilgi sağlamak için kendi hedeftir.</span><span class="sxs-lookup"><span data-stu-id="4f0ee-118">Its goal is to provide profiler writers with enough information to identify the compiled method to users.</span></span>

> [!NOTE]
> <span data-ttu-id="4f0ee-119">`functionId` dinamik yöntemler meta verisi yok olduğundan değerleri kendi meta veri simgesi çözümlemek için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="4f0ee-119">`functionId` values cannot be used to resolve to their metadata tokens, because dynamic methods have no metadata.</span></span>

<span data-ttu-id="4f0ee-120">`pILHeader` İşaretçidir yalnızca geçerli sırasında geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="4f0ee-120">The `pILHeader` pointer is only valid during the callback.</span></span>

## <a name="requirements"></a><span data-ttu-id="4f0ee-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4f0ee-121">Requirements</span></span>  
 <span data-ttu-id="4f0ee-122">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4f0ee-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f0ee-123">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4f0ee-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4f0ee-124">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4f0ee-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4f0ee-125">**.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="4f0ee-125">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f0ee-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4f0ee-126">See Also</span></span>  
 [<span data-ttu-id="4f0ee-127">DynamicMethodJITCompilationFinished yöntemi</span><span class="sxs-lookup"><span data-stu-id="4f0ee-127">DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)  
 [<span data-ttu-id="4f0ee-128">ICorProfilerCallback8 arabirimi</span><span class="sxs-lookup"><span data-stu-id="4f0ee-128">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)
