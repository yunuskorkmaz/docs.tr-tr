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
ms.openlocfilehash: 9dbe8d4f7050b93ffb34280be6d63367ef294ae8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59206596"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationfinished-method"></a><span data-ttu-id="1dc91-102">ICorProfilerCallback8::DynamicMethodJITCompilationFinished yöntemi</span><span class="sxs-lookup"><span data-stu-id="1dc91-102">ICorProfilerCallback8::DynamicMethodJITCompilationFinished Method</span></span>
<span data-ttu-id="1dc91-103">[.NET Framework 4.7 ve sonraki sürümlerinde desteklenen]</span><span class="sxs-lookup"><span data-stu-id="1dc91-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  
  
<span data-ttu-id="1dc91-104">Dinamik bir yöntem JIT derlemesi tamamlandı zaman profil oluşturucu bildirir.</span><span class="sxs-lookup"><span data-stu-id="1dc91-104">Notifies the profiler whenever JIT compilation of a dynamic method has completed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1dc91-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1dc91-105">Syntax</span></span>  
  
```  
HRESULT DynamicMethodJITCompilationFinished(  
     [in]  FunctionID  functionId,   
     [in]  BOOL        hrStatus,   
     [in]  BOOL        fIsSafeToBlock   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1dc91-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1dc91-106">Parameters</span></span>  
<span data-ttu-id="1dc91-107">[in] `functionId`</span><span class="sxs-lookup"><span data-stu-id="1dc91-107">[in] `functionId`</span></span>  
<span data-ttu-id="1dc91-108">Bellek içi işlev için hangi JIT derleme başlatıldığında tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="1dc91-108">The identifier of the in-memory function for which JIT compilation is started.</span></span>   

<span data-ttu-id="1dc91-109">[in] `hrStatus` </span><span class="sxs-lookup"><span data-stu-id="1dc91-109">[in] `hrStatus` </span></span>  
<span data-ttu-id="1dc91-110">JIT derlemesi başarılı olup olmadığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="1dc91-110">A value that indicates whether the JIT compilation was successful.</span></span>

<span data-ttu-id="1dc91-111">[in] `fIsSafeToBlock` </span><span class="sxs-lookup"><span data-stu-id="1dc91-111">[in] `fIsSafeToBlock` </span></span>  
<span data-ttu-id="1dc91-112">`true` Bu geri çağrısından döndürmek çağıran iş parçacığını beklemek çalışma zamanı engelleme neden olabileceğini göstermek için; `false` engelleme zamanının işlemi etkilemez belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="1dc91-112">`true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  

## <a name="remarks"></a><span data-ttu-id="1dc91-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1dc91-113">Remarks</span></span>  

<span data-ttu-id="1dc91-114">Bu geri çağırma dinamik bir yöntem JIT derlemesi Tamamlandı olduğunda tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="1dc91-114">This callback is triggered whenever JIT compilation of a dynamic method has finished.</span></span> <span data-ttu-id="1dc91-115">Bu, çeşitli IL saptamalar ve LCG yöntemleri içerir.</span><span class="sxs-lookup"><span data-stu-id="1dc91-115">This includes various IL stubs and LCG methods.</span></span> <span data-ttu-id="1dc91-116">Profil Oluşturucu yazarları kullanıcılara derlenmiş yöntemi tanımlamak için yeterli bilgi sağlamak için hedefi sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="1dc91-116">Its goal is to provide profiler writers with enough information to identify the compiled method to users.</span></span>

> [!NOTE]
> <span data-ttu-id="1dc91-117">`functionId` dinamik yöntemler meta veri olduğundan değerleri kendi meta veri belirteçleri için çözümlemek için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="1dc91-117">`functionId` values cannot be used to resolve to their metadata tokens, because dynamic methods have no metadata.</span></span>

## <a name="requirements"></a><span data-ttu-id="1dc91-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1dc91-118">Requirements</span></span>  
 <span data-ttu-id="1dc91-119">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1dc91-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1dc91-120">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1dc91-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1dc91-121">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1dc91-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1dc91-122">**.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="1dc91-122">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dc91-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1dc91-123">See also</span></span>

- [<span data-ttu-id="1dc91-124">DynamicMethodJITCompilationStarted Metodu</span><span class="sxs-lookup"><span data-stu-id="1dc91-124">DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="1dc91-125">ICorProfilerCallback8 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1dc91-125">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)
