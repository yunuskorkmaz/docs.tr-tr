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
ms.openlocfilehash: c03251ab3120fd93cbb8e6c2f1bb62a4527a92bb
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2021
ms.locfileid: "104759930"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationstarted-method"></a><span data-ttu-id="cdc57-103">ICorProfilerCallback8::D ynamicMethodJITCompilationStarted yöntemi</span><span class="sxs-lookup"><span data-stu-id="cdc57-103">ICorProfilerCallback8::DynamicMethodJITCompilationStarted Method</span></span>

<span data-ttu-id="cdc57-104">[.NET Framework 4,7 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="cdc57-104">[Supported in the .NET Framework 4.7 and later versions]</span></span>  
  
<span data-ttu-id="cdc57-105">Dinamik bir yöntemin JıT derlemesi başladığında profil oluşturucuyu bilgilendirir.</span><span class="sxs-lookup"><span data-stu-id="cdc57-105">Notifies the profiler whenever JIT compilation of a dynamic method has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cdc57-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cdc57-106">Syntax</span></span>  
  
```cpp  
HRESULT DynamicMethodJITCompilationStarted(  
     [in]  FunctionID  functionId,
     [in]  BOOL        fIsSafeToBlock,
     [in]  LPCBYTE     pILHeader,
     [in]  LONG        cbILHeader
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cdc57-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cdc57-107">Parameters</span></span>  

`functionId`  
<span data-ttu-id="cdc57-108">'ndaki JıT derlemesinin başlatıldığı bellek içi işlevin tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="cdc57-108">[in] The identifier of the in-memory function for which JIT compilation is started.</span></span>

<span data-ttu-id="cdc57-109">`fIsSafeToBlock` [in] `true` Bu engellemenin, çalışma zamanının çağıran iş parçacığının bu geri aramadan dönmesini beklemesine neden olabileceğini göstermek için; `false` engellemenin çalışma zamanının işlemini etkilemeyeceğini göstermek için.</span><span class="sxs-lookup"><span data-stu-id="cdc57-109">`fIsSafeToBlock` [in] `true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  

<span data-ttu-id="cdc57-110">`pILHeader` 'ndaki Metodun Il üstbilgisinin ilk baytına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="cdc57-110">`pILHeader` [in] A pointer to the first byte of the method's IL header.</span></span>

<span data-ttu-id="cdc57-111">`cbILHeader` 'ndaki Il üstbilgisindeki bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="cdc57-111">`cbILHeader` [in] The number of bytes in the IL header.</span></span>

## <a name="remarks"></a><span data-ttu-id="cdc57-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cdc57-112">Remarks</span></span>  

<span data-ttu-id="cdc57-113">Bu geri çağırma, dinamik bir yöntem JıT olarak derlendiğinde tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="cdc57-113">This callback is triggered whenever a dynamic method is JIT-compiled.</span></span> <span data-ttu-id="cdc57-114">Buna çeşitli Il saplamaları ve LCG yöntemleri dahildir.</span><span class="sxs-lookup"><span data-stu-id="cdc57-114">This includes various IL stubs and LCG methods.</span></span> <span data-ttu-id="cdc57-115">Amacı, profil oluşturucu yazıcılarını kullanıcılara derlenen yöntemi tanımlamak için yeterli bilgi sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="cdc57-115">Its goal is to provide profiler writers with enough information to identify the compiled method to users.</span></span>

> [!NOTE]
> <span data-ttu-id="cdc57-116">`functionId` Dinamik metotların meta verisi olmadığından, meta veri belirteçlerine çözümlemek için değerler kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="cdc57-116">`functionId` values cannot be used to resolve to their metadata tokens, because dynamic methods have no metadata.</span></span>

<span data-ttu-id="cdc57-117">`pILHeader`İşaretçi yalnızca geri çağırma sırasında geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="cdc57-117">The `pILHeader` pointer is only valid during the callback.</span></span>

## <a name="requirements"></a><span data-ttu-id="cdc57-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cdc57-118">Requirements</span></span>  

 <span data-ttu-id="cdc57-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cdc57-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cdc57-120">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="cdc57-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cdc57-121">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="cdc57-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cdc57-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="cdc57-122">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdc57-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cdc57-123">See also</span></span>

- [<span data-ttu-id="cdc57-124">DynamicMethodJITCompilationFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cdc57-124">DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [<span data-ttu-id="cdc57-125">ICorProfilerCallback8 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cdc57-125">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)
