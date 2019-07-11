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
ms.openlocfilehash: ba9f9d4ee5f95def3dcd2d757517e225c826cb9e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67757997"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationfinished-method"></a><span data-ttu-id="587a0-102">ICorProfilerCallback8::DynamicMethodJITCompilationFinished yöntemi</span><span class="sxs-lookup"><span data-stu-id="587a0-102">ICorProfilerCallback8::DynamicMethodJITCompilationFinished Method</span></span>
<span data-ttu-id="587a0-103">[.NET Framework 4.7 ve sonraki sürümlerinde desteklenen]</span><span class="sxs-lookup"><span data-stu-id="587a0-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  
  
<span data-ttu-id="587a0-104">Dinamik bir yöntem JIT derlemesi tamamlandı zaman profil oluşturucu bildirir.</span><span class="sxs-lookup"><span data-stu-id="587a0-104">Notifies the profiler whenever JIT compilation of a dynamic method has completed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="587a0-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="587a0-105">Syntax</span></span>  
  
```cpp  
HRESULT DynamicMethodJITCompilationFinished(  
     [in]  FunctionID  functionId,   
     [in]  BOOL        hrStatus,   
     [in]  BOOL        fIsSafeToBlock   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="587a0-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="587a0-106">Parameters</span></span>  
<span data-ttu-id="587a0-107">[in] `functionId`</span><span class="sxs-lookup"><span data-stu-id="587a0-107">[in] `functionId`</span></span>  
<span data-ttu-id="587a0-108">Bellek içi işlev için hangi JIT derleme başlatıldığında tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="587a0-108">The identifier of the in-memory function for which JIT compilation is started.</span></span>   

<span data-ttu-id="587a0-109">[in] `hrStatus` </span><span class="sxs-lookup"><span data-stu-id="587a0-109">[in] `hrStatus` </span></span>  
<span data-ttu-id="587a0-110">JIT derlemesi başarılı olup olmadığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="587a0-110">A value that indicates whether the JIT compilation was successful.</span></span>

<span data-ttu-id="587a0-111">[in] `fIsSafeToBlock` </span><span class="sxs-lookup"><span data-stu-id="587a0-111">[in] `fIsSafeToBlock` </span></span>  
<span data-ttu-id="587a0-112">`true` Bu geri çağrısından döndürmek çağıran iş parçacığını beklemek çalışma zamanı engelleme neden olabileceğini göstermek için; `false` engelleme zamanının işlemi etkilemez belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="587a0-112">`true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  

## <a name="remarks"></a><span data-ttu-id="587a0-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="587a0-113">Remarks</span></span>  

<span data-ttu-id="587a0-114">Bu geri çağırma dinamik bir yöntem JIT derlemesi Tamamlandı olduğunda tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="587a0-114">This callback is triggered whenever JIT compilation of a dynamic method has finished.</span></span> <span data-ttu-id="587a0-115">Bu, çeşitli IL saptamalar ve LCG yöntemleri içerir.</span><span class="sxs-lookup"><span data-stu-id="587a0-115">This includes various IL stubs and LCG methods.</span></span> <span data-ttu-id="587a0-116">Profil Oluşturucu yazarları kullanıcılara derlenmiş yöntemi tanımlamak için yeterli bilgi sağlamak için hedefi sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="587a0-116">Its goal is to provide profiler writers with enough information to identify the compiled method to users.</span></span>

> [!NOTE]
> <span data-ttu-id="587a0-117">`functionId` dinamik yöntemler meta veri olduğundan değerleri kendi meta veri belirteçleri için çözümlemek için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="587a0-117">`functionId` values cannot be used to resolve to their metadata tokens, because dynamic methods have no metadata.</span></span>

## <a name="requirements"></a><span data-ttu-id="587a0-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="587a0-118">Requirements</span></span>  
 <span data-ttu-id="587a0-119">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="587a0-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="587a0-120">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="587a0-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="587a0-121">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="587a0-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="587a0-122">**.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="587a0-122">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="587a0-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="587a0-123">See also</span></span>

- [<span data-ttu-id="587a0-124">DynamicMethodJITCompilationStarted Metodu</span><span class="sxs-lookup"><span data-stu-id="587a0-124">DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="587a0-125">ICorProfilerCallback8 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="587a0-125">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)
