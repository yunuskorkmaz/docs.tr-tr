---
description: 'Hakkında daha fazla bilgi edinin: ICorProfilerCallback8::D ynamicMethodJITCompilationStarted yöntemi'
title: ICorProfilerCallback8::D ynamicMethodJITCompilationStarted yöntemi
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationStarted
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 186b41564e0aabb069b06356b8eccbe90296ec4b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781707"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationstarted-method"></a><span data-ttu-id="6928a-103">ICorProfilerCallback8::D ynamicMethodJITCompilationStarted yöntemi</span><span class="sxs-lookup"><span data-stu-id="6928a-103">ICorProfilerCallback8::DynamicMethodJITCompilationStarted Method</span></span>

<span data-ttu-id="6928a-104">[.NET Framework 4,7 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="6928a-104">[Supported in the .NET Framework 4.7 and later versions]</span></span>  
  
<span data-ttu-id="6928a-105">Dinamik bir yöntemin JıT derlemesi başladığında profil oluşturucuyu bilgilendirir.</span><span class="sxs-lookup"><span data-stu-id="6928a-105">Notifies the profiler whenever JIT compilation of a dynamic method has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6928a-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6928a-106">Syntax</span></span>  
  
```cpp  
HRESULT DynamicMethodJITCompilationStarted(  
     [in]  FunctionID  functionId,
     [in]  BOOL        fIsSafeToBlock,
     [in]  LPCBYTE     pILHeader,
     [in]  LONG        cbILHeader
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6928a-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6928a-107">Parameters</span></span>  

<span data-ttu-id="6928a-108">'ndaki `functionId`</span><span class="sxs-lookup"><span data-stu-id="6928a-108">[in] `functionId`</span></span>  
<span data-ttu-id="6928a-109">JıT derlemesinin başlatıldığı bellek içi işlevin tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="6928a-109">The identifier of the in-memory function for which JIT compilation is started.</span></span>

<span data-ttu-id="6928a-110">[in] `fIsSafeToBlock` 
 `true` Bu engellemenin, çalışma zamanının çağıran iş parçacığının bu geri aramadan dönmesini beklemesine neden olabileceğini göstermek için; `false`engellemenin çalışma zamanının işlemini etkilemeyeceğini göstermek için.</span><span class="sxs-lookup"><span data-stu-id="6928a-110">[in] `fIsSafeToBlock`
`true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  

<span data-ttu-id="6928a-111">[in] `pILHeader` Metodun Il üstbilgisinin ilk baytına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6928a-111">[in] `pILHeader` A pointer to the first byte of the method's IL header.</span></span>

<span data-ttu-id="6928a-112">[in] `cbILHeader` Il üstbilgisindeki bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="6928a-112">[in] `cbILHeader` The number of bytes in the IL header.</span></span>

## <a name="remarks"></a><span data-ttu-id="6928a-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6928a-113">Remarks</span></span>  

<span data-ttu-id="6928a-114">Bu geri çağırma, dinamik bir yöntem JıT olarak derlendiğinde tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="6928a-114">This callback is triggered whenever a dynamic method is JIT-compiled.</span></span> <span data-ttu-id="6928a-115">Buna çeşitli Il saplamaları ve LCG yöntemleri dahildir.</span><span class="sxs-lookup"><span data-stu-id="6928a-115">This includes various IL stubs and LCG methods.</span></span> <span data-ttu-id="6928a-116">Amacı, profil oluşturucu yazıcılarını kullanıcılara derlenen yöntemi tanımlamak için yeterli bilgi sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="6928a-116">Its goal is to provide profiler writers with enough information to identify the compiled method to users.</span></span>

> [!NOTE]
> <span data-ttu-id="6928a-117">`functionId` Dinamik metotların meta verisi olmadığından, meta veri belirteçlerine çözümlemek için değerler kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="6928a-117">`functionId` values cannot be used to resolve to their metadata tokens, because dynamic methods have no metadata.</span></span>

<span data-ttu-id="6928a-118">`pILHeader`İşaretçi yalnızca geri çağırma sırasında geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="6928a-118">The `pILHeader` pointer is only valid during the callback.</span></span>

## <a name="requirements"></a><span data-ttu-id="6928a-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6928a-119">Requirements</span></span>  

 <span data-ttu-id="6928a-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6928a-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6928a-121">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="6928a-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6928a-122">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="6928a-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6928a-123">**.NET Framework sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="6928a-123">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6928a-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6928a-124">See also</span></span>

- [<span data-ttu-id="6928a-125">DynamicMethodJITCompilationFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6928a-125">DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [<span data-ttu-id="6928a-126">ICorProfilerCallback8 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6928a-126">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)
