---
title: ICorProfilerCallback8::D ynamicMethodJITCompilationFinished yöntemi
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationFinished
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 0e04459614ca697908fb9b71ecc3931ac305a838
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136579"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationfinished-method"></a><span data-ttu-id="f931c-102">ICorProfilerCallback8::D ynamicMethodJITCompilationFinished yöntemi</span><span class="sxs-lookup"><span data-stu-id="f931c-102">ICorProfilerCallback8::DynamicMethodJITCompilationFinished Method</span></span>
<span data-ttu-id="f931c-103">[.NET Framework 4,7 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="f931c-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  
  
<span data-ttu-id="f931c-104">Dinamik bir yöntemin JıT derlemesi tamamlandığında profil oluşturucuyu bilgilendirir.</span><span class="sxs-lookup"><span data-stu-id="f931c-104">Notifies the profiler whenever JIT compilation of a dynamic method has completed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f931c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f931c-105">Syntax</span></span>  
  
```cpp  
HRESULT DynamicMethodJITCompilationFinished(  
     [in]  FunctionID  functionId,   
     [in]  BOOL        hrStatus,   
     [in]  BOOL        fIsSafeToBlock   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f931c-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f931c-106">Parameters</span></span>  
<span data-ttu-id="f931c-107">[in] `functionId`</span><span class="sxs-lookup"><span data-stu-id="f931c-107">[in] `functionId`</span></span>  
<span data-ttu-id="f931c-108">JıT derlemesinin başlatıldığı bellek içi işlevin tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="f931c-108">The identifier of the in-memory function for which JIT compilation is started.</span></span>   

<span data-ttu-id="f931c-109">[in] `hrStatus` </span><span class="sxs-lookup"><span data-stu-id="f931c-109">[in] `hrStatus` </span></span>  
<span data-ttu-id="f931c-110">JıT derlemesinin başarılı olup olmadığını gösteren bir değer.</span><span class="sxs-lookup"><span data-stu-id="f931c-110">A value that indicates whether the JIT compilation was successful.</span></span>

<span data-ttu-id="f931c-111">[in] `fIsSafeToBlock` </span><span class="sxs-lookup"><span data-stu-id="f931c-111">[in] `fIsSafeToBlock` </span></span>  
<span data-ttu-id="f931c-112">`true`, çalışma zamanının çağıran iş parçacığının bu geri aramadan dönmesini beklemesini sağlamak için; engellemenin çalışma zamanının işlemini etkilemeyeceğini belirten `false`.</span><span class="sxs-lookup"><span data-stu-id="f931c-112">`true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  

## <a name="remarks"></a><span data-ttu-id="f931c-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f931c-113">Remarks</span></span>  

<span data-ttu-id="f931c-114">Bu geri çağırma, dinamik bir yöntemin JıT derlemesi tamamlandığında tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="f931c-114">This callback is triggered whenever JIT compilation of a dynamic method has finished.</span></span> <span data-ttu-id="f931c-115">Buna çeşitli Il saplamaları ve LCG yöntemleri dahildir.</span><span class="sxs-lookup"><span data-stu-id="f931c-115">This includes various IL stubs and LCG methods.</span></span> <span data-ttu-id="f931c-116">Amacı, profil oluşturucu yazıcılarını kullanıcılara derlenen yöntemi tanımlamak için yeterli bilgi sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="f931c-116">Its goal is to provide profiler writers with enough information to identify the compiled method to users.</span></span>

> [!NOTE]
> <span data-ttu-id="f931c-117">Dinamik metotların meta verisi olmadığından, `functionId` değerleri meta veri belirteçlerine çözümlemek için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="f931c-117">`functionId` values cannot be used to resolve to their metadata tokens, because dynamic methods have no metadata.</span></span>

## <a name="requirements"></a><span data-ttu-id="f931c-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f931c-118">Requirements</span></span>  
 <span data-ttu-id="f931c-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f931c-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f931c-120">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="f931c-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f931c-121">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f931c-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f931c-122">**.NET Framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f931c-122">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f931c-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f931c-123">See also</span></span>

- [<span data-ttu-id="f931c-124">DynamicMethodJITCompilationStarted Metodu</span><span class="sxs-lookup"><span data-stu-id="f931c-124">DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="f931c-125">ICorProfilerCallback8 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f931c-125">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)
