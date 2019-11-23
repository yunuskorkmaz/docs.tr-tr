---
title: ICorProfilerCallback8::D ynamicMethodJITCompilationStarted yöntemi
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationStarted
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 1eaf29e1c93f352facde4af2ee57910783d82e5d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136459"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationstarted-method"></a><span data-ttu-id="a97e1-102">ICorProfilerCallback8::D ynamicMethodJITCompilationStarted yöntemi</span><span class="sxs-lookup"><span data-stu-id="a97e1-102">ICorProfilerCallback8::DynamicMethodJITCompilationStarted Method</span></span>
<span data-ttu-id="a97e1-103">[.NET Framework 4,7 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="a97e1-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  
  
<span data-ttu-id="a97e1-104">Dinamik bir yöntemin JıT derlemesi başladığında profil oluşturucuyu bilgilendirir.</span><span class="sxs-lookup"><span data-stu-id="a97e1-104">Notifies the profiler whenever JIT compilation of a dynamic method has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a97e1-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a97e1-105">Syntax</span></span>  
  
```cpp  
HRESULT DynamicMethodJITCompilationStarted(  
     [in]  FunctionID  functionId,   
     [in]  BOOL        fIsSafeToBlock,   
     [in]  LPCBYTE     pILHeader,   
     [in]  LONG        cbILHeader   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a97e1-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a97e1-106">Parameters</span></span>  
<span data-ttu-id="a97e1-107">[in] `functionId`</span><span class="sxs-lookup"><span data-stu-id="a97e1-107">[in] `functionId`</span></span>  
<span data-ttu-id="a97e1-108">JıT derlemesinin başlatıldığı bellek içi işlevin tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="a97e1-108">The identifier of the in-memory function for which JIT compilation is started.</span></span>   

<span data-ttu-id="a97e1-109">[in] `fIsSafeToBlock` </span><span class="sxs-lookup"><span data-stu-id="a97e1-109">[in] `fIsSafeToBlock` </span></span>  
<span data-ttu-id="a97e1-110">`true`, çalışma zamanının çağıran iş parçacığının bu geri aramadan dönmesini beklemesini sağlamak için; engellemenin çalışma zamanının işlemini etkilemeyeceğini belirten `false`.</span><span class="sxs-lookup"><span data-stu-id="a97e1-110">`true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  

<span data-ttu-id="a97e1-111">[in] `pILHeader`  </span><span class="sxs-lookup"><span data-stu-id="a97e1-111">[in] `pILHeader`  </span></span>  
<span data-ttu-id="a97e1-112">Metodun Il üstbilgisinin ilk baytına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a97e1-112">A pointer to the first byte of the method's IL header.</span></span>   

<span data-ttu-id="a97e1-113">[in] `cbILHeader`  </span><span class="sxs-lookup"><span data-stu-id="a97e1-113">[in] `cbILHeader`  </span></span>  
<span data-ttu-id="a97e1-114">Il üstbilgisindeki bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="a97e1-114">The number of bytes in the IL header.</span></span> 

## <a name="remarks"></a><span data-ttu-id="a97e1-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a97e1-115">Remarks</span></span>  

<span data-ttu-id="a97e1-116">Bu geri çağırma, dinamik bir yöntem JıT olarak derlendiğinde tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="a97e1-116">This callback is triggered whenever a dynamic method is JIT-compiled.</span></span> <span data-ttu-id="a97e1-117">Buna çeşitli Il saplamaları ve LCG yöntemleri dahildir.</span><span class="sxs-lookup"><span data-stu-id="a97e1-117">This includes various IL stubs and LCG methods.</span></span> <span data-ttu-id="a97e1-118">Amacı, profil oluşturucu yazıcılarını kullanıcılara derlenen yöntemi tanımlamak için yeterli bilgi sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="a97e1-118">Its goal is to provide profiler writers with enough information to identify the compiled method to users.</span></span>

> [!NOTE]
> <span data-ttu-id="a97e1-119">Dinamik metotların meta verisi olmadığından, `functionId` değerleri meta veri belirteçlerine çözümlemek için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="a97e1-119">`functionId` values cannot be used to resolve to their metadata tokens, because dynamic methods have no metadata.</span></span>

<span data-ttu-id="a97e1-120">`pILHeader` işaretçi yalnızca geri çağırma sırasında geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="a97e1-120">The `pILHeader` pointer is only valid during the callback.</span></span>

## <a name="requirements"></a><span data-ttu-id="a97e1-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a97e1-121">Requirements</span></span>  
 <span data-ttu-id="a97e1-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a97e1-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a97e1-123">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="a97e1-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a97e1-124">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a97e1-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a97e1-125">**.NET Framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a97e1-125">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a97e1-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a97e1-126">See also</span></span>

- [<span data-ttu-id="a97e1-127">DynamicMethodJITCompilationFinished Metodu</span><span class="sxs-lookup"><span data-stu-id="a97e1-127">DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [<span data-ttu-id="a97e1-128">ICorProfilerCallback8 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a97e1-128">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)
