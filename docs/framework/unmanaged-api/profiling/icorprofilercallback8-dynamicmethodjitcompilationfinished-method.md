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
ms.openlocfilehash: 554cc93de934061e87322c7557e05545e5e7bc62
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499083"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationfinished-method"></a><span data-ttu-id="cda7a-102">ICorProfilerCallback8::D ynamicMethodJITCompilationFinished yöntemi</span><span class="sxs-lookup"><span data-stu-id="cda7a-102">ICorProfilerCallback8::DynamicMethodJITCompilationFinished Method</span></span>
<span data-ttu-id="cda7a-103">[.NET Framework 4,7 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="cda7a-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  
  
<span data-ttu-id="cda7a-104">Dinamik bir yöntemin JıT derlemesi tamamlandığında profil oluşturucuyu bilgilendirir.</span><span class="sxs-lookup"><span data-stu-id="cda7a-104">Notifies the profiler whenever JIT compilation of a dynamic method has completed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cda7a-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="cda7a-105">Syntax</span></span>  
  
```cpp  
HRESULT DynamicMethodJITCompilationFinished(  
     [in]  FunctionID  functionId,
     [in]  BOOL        hrStatus,
     [in]  BOOL        fIsSafeToBlock
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cda7a-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cda7a-106">Parameters</span></span>  
<span data-ttu-id="cda7a-107">'ndaki`functionId`</span><span class="sxs-lookup"><span data-stu-id="cda7a-107">[in] `functionId`</span></span>  
<span data-ttu-id="cda7a-108">JıT derlemesinin başlatıldığı bellek içi işlevin tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="cda7a-108">The identifier of the in-memory function for which JIT compilation is started.</span></span>

<span data-ttu-id="cda7a-109">[in] `hrStatus` JıT derlemesinin başarılı olup olmadığını gösteren bir değer.</span><span class="sxs-lookup"><span data-stu-id="cda7a-109">[in] `hrStatus` A value that indicates whether the JIT compilation was successful.</span></span>

<span data-ttu-id="cda7a-110">[in] `fIsSafeToBlock` 
 `true` Bu engellemenin, çalışma zamanının çağıran iş parçacığının bu geri aramadan dönmesini beklemesine neden olabileceğini göstermek için; `false`engellemenin çalışma zamanının işlemini etkilemeyeceğini göstermek için.</span><span class="sxs-lookup"><span data-stu-id="cda7a-110">[in] `fIsSafeToBlock`
`true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  

## <a name="remarks"></a><span data-ttu-id="cda7a-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cda7a-111">Remarks</span></span>  

<span data-ttu-id="cda7a-112">Bu geri çağırma, dinamik bir yöntemin JıT derlemesi tamamlandığında tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="cda7a-112">This callback is triggered whenever JIT compilation of a dynamic method has finished.</span></span> <span data-ttu-id="cda7a-113">Buna çeşitli Il saplamaları ve LCG yöntemleri dahildir.</span><span class="sxs-lookup"><span data-stu-id="cda7a-113">This includes various IL stubs and LCG methods.</span></span> <span data-ttu-id="cda7a-114">Amacı, profil oluşturucu yazıcılarını kullanıcılara derlenen yöntemi tanımlamak için yeterli bilgi sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="cda7a-114">Its goal is to provide profiler writers with enough information to identify the compiled method to users.</span></span>

> [!NOTE]
> <span data-ttu-id="cda7a-115">`functionId`Dinamik metotların meta verisi olmadığından, meta veri belirteçlerine çözümlemek için değerler kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="cda7a-115">`functionId` values cannot be used to resolve to their metadata tokens, because dynamic methods have no metadata.</span></span>

## <a name="requirements"></a><span data-ttu-id="cda7a-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cda7a-116">Requirements</span></span>  
 <span data-ttu-id="cda7a-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cda7a-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cda7a-118">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="cda7a-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cda7a-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="cda7a-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cda7a-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="cda7a-120">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cda7a-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cda7a-121">See also</span></span>

- [<span data-ttu-id="cda7a-122">DynamicMethodJITCompilationStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cda7a-122">DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="cda7a-123">ICorProfilerCallback8 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cda7a-123">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)
