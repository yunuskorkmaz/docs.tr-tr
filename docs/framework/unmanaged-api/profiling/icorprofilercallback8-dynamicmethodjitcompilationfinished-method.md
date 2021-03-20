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
ms.openlocfilehash: d610024af9959790b37a724c2bdbf4dabc89dd20
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2021
ms.locfileid: "104759826"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationfinished-method"></a><span data-ttu-id="e6ec2-103">ICorProfilerCallback8::D ynamicMethodJITCompilationFinished yöntemi</span><span class="sxs-lookup"><span data-stu-id="e6ec2-103">ICorProfilerCallback8::DynamicMethodJITCompilationFinished Method</span></span>

<span data-ttu-id="e6ec2-104">[.NET Framework 4,7 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="e6ec2-104">[Supported in the .NET Framework 4.7 and later versions]</span></span>  
  
<span data-ttu-id="e6ec2-105">Dinamik bir yöntemin JıT derlemesi tamamlandığında profil oluşturucuyu bilgilendirir.</span><span class="sxs-lookup"><span data-stu-id="e6ec2-105">Notifies the profiler whenever JIT compilation of a dynamic method has completed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6ec2-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e6ec2-106">Syntax</span></span>  
  
```cpp  
HRESULT DynamicMethodJITCompilationFinished(  
     [in]  FunctionID  functionId,
     [in]  BOOL        hrStatus,
     [in]  BOOL        fIsSafeToBlock
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e6ec2-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e6ec2-107">Parameters</span></span>  

`functionId`  
<span data-ttu-id="e6ec2-108">'ndaki JıT derlemesinin başlatıldığı bellek içi işlevin tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="e6ec2-108">[in] The identifier of the in-memory function for which JIT compilation is started.</span></span>

<span data-ttu-id="e6ec2-109">`hrStatus` 'ndaki JıT derlemesinin başarılı olup olmadığını gösteren bir değer.</span><span class="sxs-lookup"><span data-stu-id="e6ec2-109">`hrStatus` [in] A value that indicates whether the JIT compilation was successful.</span></span>

<span data-ttu-id="e6ec2-110">`fIsSafeToBlock` [in] `true` Bu engellemenin, çalışma zamanının çağıran iş parçacığının bu geri aramadan dönmesini beklemesine neden olabileceğini göstermek için; `false` engellemenin çalışma zamanının işlemini etkilemeyeceğini göstermek için.</span><span class="sxs-lookup"><span data-stu-id="e6ec2-110">`fIsSafeToBlock` [in] `true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  

## <a name="remarks"></a><span data-ttu-id="e6ec2-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e6ec2-111">Remarks</span></span>  

<span data-ttu-id="e6ec2-112">Bu geri çağırma, dinamik bir yöntemin JıT derlemesi tamamlandığında tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="e6ec2-112">This callback is triggered whenever JIT compilation of a dynamic method has finished.</span></span> <span data-ttu-id="e6ec2-113">Buna çeşitli Il saplamaları ve LCG yöntemleri dahildir.</span><span class="sxs-lookup"><span data-stu-id="e6ec2-113">This includes various IL stubs and LCG methods.</span></span> <span data-ttu-id="e6ec2-114">Amacı, profil oluşturucu yazıcılarını kullanıcılara derlenen yöntemi tanımlamak için yeterli bilgi sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="e6ec2-114">Its goal is to provide profiler writers with enough information to identify the compiled method to users.</span></span>

> [!NOTE]
> <span data-ttu-id="e6ec2-115">`functionId` Dinamik metotların meta verisi olmadığından, meta veri belirteçlerine çözümlemek için değerler kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="e6ec2-115">`functionId` values cannot be used to resolve to their metadata tokens, because dynamic methods have no metadata.</span></span>

## <a name="requirements"></a><span data-ttu-id="e6ec2-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e6ec2-116">Requirements</span></span>  

 <span data-ttu-id="e6ec2-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e6ec2-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6ec2-118">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="e6ec2-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e6ec2-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e6ec2-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e6ec2-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e6ec2-120">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6ec2-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e6ec2-121">See also</span></span>

- [<span data-ttu-id="e6ec2-122">DynamicMethodJITCompilationStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e6ec2-122">DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="e6ec2-123">ICorProfilerCallback8 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e6ec2-123">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)
