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
ms.openlocfilehash: c4b8bffeb71497a7dd8e2ed25b833f9216d8017e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59142252"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationstarted-method"></a><span data-ttu-id="4aacf-102">ICorProfilerCallback8::DynamicMethodJITCompilationStarted yöntemi</span><span class="sxs-lookup"><span data-stu-id="4aacf-102">ICorProfilerCallback8::DynamicMethodJITCompilationStarted Method</span></span>
<span data-ttu-id="4aacf-103">[.NET Framework 4.7 ve sonraki sürümlerinde desteklenen]</span><span class="sxs-lookup"><span data-stu-id="4aacf-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  
  
<span data-ttu-id="4aacf-104">Dinamik bir yöntem JIT derlemesi başladı zaman profil oluşturucu bildirir.</span><span class="sxs-lookup"><span data-stu-id="4aacf-104">Notifies the profiler whenever JIT compilation of a dynamic method has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4aacf-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4aacf-105">Syntax</span></span>  
  
```  
HRESULT DynamicMethodJITCompilationStarted(  
     [in]  FunctionID  functionId,   
     [in]  BOOL        fIsSafeToBlock,   
     [in]  LPCBYTE     pILHeader,   
     [in]  LONG        cbILHeader   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4aacf-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4aacf-106">Parameters</span></span>  
<span data-ttu-id="4aacf-107">[in]</span><span class="sxs-lookup"><span data-stu-id="4aacf-107">[in]</span></span> `functionId`  
<span data-ttu-id="4aacf-108">Bellek içi işlev için hangi JIT derleme başlatıldığında tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="4aacf-108">The identifier of the in-memory function for which JIT compilation is started.</span></span>   

<span data-ttu-id="4aacf-109">[in]</span><span class="sxs-lookup"><span data-stu-id="4aacf-109">[in]</span></span> `fIsSafeToBlock`   
`true` <span data-ttu-id="4aacf-110">Bu geri çağrısından döndürmek çağıran iş parçacığını beklemek çalışma zamanı engelleme neden olabileceğini göstermek için; `false` engelleme zamanının işlemi etkilemez belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="4aacf-110">to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  

<span data-ttu-id="4aacf-111">[in]</span><span class="sxs-lookup"><span data-stu-id="4aacf-111">[in]</span></span> `pILHeader`    
<span data-ttu-id="4aacf-112">Yöntemin IL üstbilgi ilk baytına bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4aacf-112">A pointer to the first byte of the method's IL header.</span></span>   

<span data-ttu-id="4aacf-113">[in]</span><span class="sxs-lookup"><span data-stu-id="4aacf-113">[in]</span></span> `cbILHeader`    
<span data-ttu-id="4aacf-114">IL üst bilgisindeki bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="4aacf-114">The number of bytes in the IL header.</span></span> 

## <a name="remarks"></a><span data-ttu-id="4aacf-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4aacf-115">Remarks</span></span>  

<span data-ttu-id="4aacf-116">Bu geri çağırma JIT olarak derlenmiş bir dinamik yöntem olduğunda tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="4aacf-116">This callback is triggered whenever a dynamic method is JIT-compiled.</span></span> <span data-ttu-id="4aacf-117">Bu, çeşitli IL saptamalar ve LCG yöntemleri içerir.</span><span class="sxs-lookup"><span data-stu-id="4aacf-117">This includes various IL stubs and LCG methods.</span></span> <span data-ttu-id="4aacf-118">Profil Oluşturucu yazarları kullanıcılara derlenmiş yöntemi tanımlamak için yeterli bilgi sağlamak için hedefi sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="4aacf-118">Its goal is to provide profiler writers with enough information to identify the compiled method to users.</span></span>

> [!NOTE]
> `functionId` <span data-ttu-id="4aacf-119">dinamik yöntemler meta veri olduğundan değerleri kendi meta veri belirteçleri için çözümlemek için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="4aacf-119">values cannot be used to resolve to their metadata tokens, because dynamic methods have no metadata.</span></span>

<span data-ttu-id="4aacf-120">`pILHeader` İşaretçisi, yalnızca geçerli sırasında geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="4aacf-120">The `pILHeader` pointer is only valid during the callback.</span></span>

## <a name="requirements"></a><span data-ttu-id="4aacf-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4aacf-121">Requirements</span></span>  
 <span data-ttu-id="4aacf-122">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4aacf-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4aacf-123">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4aacf-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4aacf-124">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4aacf-124">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="4aacf-125">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="4aacf-125">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4aacf-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4aacf-126">See also</span></span>

- [<span data-ttu-id="4aacf-127">DynamicMethodJITCompilationFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4aacf-127">DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [<span data-ttu-id="4aacf-128">ICorProfilerCallback8 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4aacf-128">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)
