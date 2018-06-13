---
title: ICorProfilerCallback8::DynamicMethodJITCompilationFinished yöntemi
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationFinished
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 49b5ead8b5428d855b7dab81dced1de6325fd07b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455003"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationfinished-method"></a><span data-ttu-id="2213b-102">ICorProfilerCallback8::DynamicMethodJITCompilationFinished yöntemi</span><span class="sxs-lookup"><span data-stu-id="2213b-102">ICorProfilerCallback8::DynamicMethodJITCompilationFinished Method</span></span>
<span data-ttu-id="2213b-103">[.NET Framework 4.7 ve sonraki sürümlerinde desteklenen]</span><span class="sxs-lookup"><span data-stu-id="2213b-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  
  
<span data-ttu-id="2213b-104">Profil Oluşturucu JIT derleme dinamik yönteminin tamamlandı her bildirir.</span><span class="sxs-lookup"><span data-stu-id="2213b-104">Notifies the profiler whenever JIT compilation of a dynamic method has completed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2213b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2213b-105">Syntax</span></span>  
  
```  
HRESULT DynamicMethodJITCompilationFinished(  
     [in]  FunctionID  functionId,   
     [in]  BOOL        hrStatus,   
     [in]  BOOL        fIsSafeToBlock   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2213b-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2213b-106">Parameters</span></span>  
<span data-ttu-id="2213b-107">[in] `functionId`</span><span class="sxs-lookup"><span data-stu-id="2213b-107">[in] `functionId`</span></span>  
<span data-ttu-id="2213b-108">Bellek içi işlevi için hangi JIT derleme başladı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="2213b-108">The identifier of the in-memory function for which JIT compilation is started.</span></span>   

<span data-ttu-id="2213b-109">[in] `hrStatus` </span><span class="sxs-lookup"><span data-stu-id="2213b-109">[in] `hrStatus` </span></span>  
<span data-ttu-id="2213b-110">JIT derleme başarılı olup olmadığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="2213b-110">A value that indicates whether the JIT compilation was successful.</span></span>

<span data-ttu-id="2213b-111">[in] `fIsSafeToBlock` </span><span class="sxs-lookup"><span data-stu-id="2213b-111">[in] `fIsSafeToBlock` </span></span>  
<span data-ttu-id="2213b-112">`true` engelleme ten bu geri dönmek çağıran iş parçacığı beklemek çalışma zamanı yaratabilir belirtmek için; `false` engelleme işlemi çalışma zamanının etkilemez belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="2213b-112">`true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  

## <a name="remarks"></a><span data-ttu-id="2213b-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2213b-113">Remarks</span></span>  

<span data-ttu-id="2213b-114">Bu geri çağırma JIT derleme dinamik yönteminin bitirdi tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="2213b-114">This callback is triggered whenever JIT compilation of a dynamic method has finished.</span></span> <span data-ttu-id="2213b-115">Bu, çeşitli IL saplamalar ve LCG yöntemleri içerir.</span><span class="sxs-lookup"><span data-stu-id="2213b-115">This includes various IL stubs and LCG methods.</span></span> <span data-ttu-id="2213b-116">Profil Oluşturucu yazıcılarının kullanıcılara derlenmiş yöntemini belirlemek için yeterli bilgi sağlamak için kendi hedeftir.</span><span class="sxs-lookup"><span data-stu-id="2213b-116">Its goal is to provide profiler writers with enough information to identify the compiled method to users.</span></span>

> [!NOTE]
> <span data-ttu-id="2213b-117">`functionId` dinamik yöntemler meta verisi yok olduğundan değerleri kendi meta veri simgesi çözümlemek için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="2213b-117">`functionId` values cannot be used to resolve to their metadata tokens, because dynamic methods have no metadata.</span></span>

## <a name="requirements"></a><span data-ttu-id="2213b-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2213b-118">Requirements</span></span>  
 <span data-ttu-id="2213b-119">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2213b-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2213b-120">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2213b-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2213b-121">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2213b-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2213b-122">**.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="2213b-122">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2213b-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2213b-123">See Also</span></span>  
 [<span data-ttu-id="2213b-124">DynamicMethodJITCompilationStarted yöntemi</span><span class="sxs-lookup"><span data-stu-id="2213b-124">DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)  
 [<span data-ttu-id="2213b-125">ICorProfilerCallback8 arabirimi</span><span class="sxs-lookup"><span data-stu-id="2213b-125">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)
