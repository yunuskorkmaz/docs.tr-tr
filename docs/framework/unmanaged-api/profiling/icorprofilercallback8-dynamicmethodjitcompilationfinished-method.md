---
description: 'Hakkında daha fazla bilgi edinin: ICorProfilerCallback8::D ynamicMethodJITCompilationFinished yöntemi'
title: ICorProfilerCallback8::D ynamicMethodJITCompilationFinished yöntemi
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationFinished
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: d076307b9e57c27753297cad8eebc1b9aa9433f6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781720"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationfinished-method"></a><span data-ttu-id="09cf2-103">ICorProfilerCallback8::D ynamicMethodJITCompilationFinished yöntemi</span><span class="sxs-lookup"><span data-stu-id="09cf2-103">ICorProfilerCallback8::DynamicMethodJITCompilationFinished Method</span></span>

<span data-ttu-id="09cf2-104">[.NET Framework 4,7 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="09cf2-104">[Supported in the .NET Framework 4.7 and later versions]</span></span>  
  
<span data-ttu-id="09cf2-105">Dinamik bir yöntemin JıT derlemesi tamamlandığında profil oluşturucuyu bilgilendirir.</span><span class="sxs-lookup"><span data-stu-id="09cf2-105">Notifies the profiler whenever JIT compilation of a dynamic method has completed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09cf2-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="09cf2-106">Syntax</span></span>  
  
```cpp  
HRESULT DynamicMethodJITCompilationFinished(  
     [in]  FunctionID  functionId,
     [in]  BOOL        hrStatus,
     [in]  BOOL        fIsSafeToBlock
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="09cf2-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="09cf2-107">Parameters</span></span>  

<span data-ttu-id="09cf2-108">'ndaki `functionId`</span><span class="sxs-lookup"><span data-stu-id="09cf2-108">[in] `functionId`</span></span>  
<span data-ttu-id="09cf2-109">JıT derlemesinin başlatıldığı bellek içi işlevin tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="09cf2-109">The identifier of the in-memory function for which JIT compilation is started.</span></span>

<span data-ttu-id="09cf2-110">[in] `hrStatus` JıT derlemesinin başarılı olup olmadığını gösteren bir değer.</span><span class="sxs-lookup"><span data-stu-id="09cf2-110">[in] `hrStatus` A value that indicates whether the JIT compilation was successful.</span></span>

<span data-ttu-id="09cf2-111">[in] `fIsSafeToBlock` 
 `true` Bu engellemenin, çalışma zamanının çağıran iş parçacığının bu geri aramadan dönmesini beklemesine neden olabileceğini göstermek için; `false`engellemenin çalışma zamanının işlemini etkilemeyeceğini göstermek için.</span><span class="sxs-lookup"><span data-stu-id="09cf2-111">[in] `fIsSafeToBlock`
`true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  

## <a name="remarks"></a><span data-ttu-id="09cf2-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="09cf2-112">Remarks</span></span>  

<span data-ttu-id="09cf2-113">Bu geri çağırma, dinamik bir yöntemin JıT derlemesi tamamlandığında tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="09cf2-113">This callback is triggered whenever JIT compilation of a dynamic method has finished.</span></span> <span data-ttu-id="09cf2-114">Buna çeşitli Il saplamaları ve LCG yöntemleri dahildir.</span><span class="sxs-lookup"><span data-stu-id="09cf2-114">This includes various IL stubs and LCG methods.</span></span> <span data-ttu-id="09cf2-115">Amacı, profil oluşturucu yazıcılarını kullanıcılara derlenen yöntemi tanımlamak için yeterli bilgi sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="09cf2-115">Its goal is to provide profiler writers with enough information to identify the compiled method to users.</span></span>

> [!NOTE]
> <span data-ttu-id="09cf2-116">`functionId` Dinamik metotların meta verisi olmadığından, meta veri belirteçlerine çözümlemek için değerler kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="09cf2-116">`functionId` values cannot be used to resolve to their metadata tokens, because dynamic methods have no metadata.</span></span>

## <a name="requirements"></a><span data-ttu-id="09cf2-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="09cf2-117">Requirements</span></span>  

 <span data-ttu-id="09cf2-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="09cf2-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09cf2-119">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="09cf2-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="09cf2-120">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="09cf2-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="09cf2-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="09cf2-121">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09cf2-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="09cf2-122">See also</span></span>

- [<span data-ttu-id="09cf2-123">DynamicMethodJITCompilationStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="09cf2-123">DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="09cf2-124">ICorProfilerCallback8 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="09cf2-124">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)
