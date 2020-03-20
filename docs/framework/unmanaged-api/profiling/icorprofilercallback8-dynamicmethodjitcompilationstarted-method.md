---
title: ICorProfilerCallback8::DynamicMethodJITCompilationStarted Method
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationStarted
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: e8b1a243b691d8d5eb364fd16821fd9156505c60
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177052"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationstarted-method"></a><span data-ttu-id="3e938-102">ICorProfilerCallback8::DynamicMethodJITCompilationStarted Method</span><span class="sxs-lookup"><span data-stu-id="3e938-102">ICorProfilerCallback8::DynamicMethodJITCompilationStarted Method</span></span>
<span data-ttu-id="3e938-103">[.NET Framework 4.7 ve sonraki sürümlerde desteklendi]</span><span class="sxs-lookup"><span data-stu-id="3e938-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  
  
<span data-ttu-id="3e938-104">Dinamik bir yöntemin JIT derlemesi başladığında profilleyiciyi not alar.</span><span class="sxs-lookup"><span data-stu-id="3e938-104">Notifies the profiler whenever JIT compilation of a dynamic method has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e938-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3e938-105">Syntax</span></span>  
  
```cpp  
HRESULT DynamicMethodJITCompilationStarted(  
     [in]  FunctionID  functionId,
     [in]  BOOL        fIsSafeToBlock,
     [in]  LPCBYTE     pILHeader,
     [in]  LONG        cbILHeader
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3e938-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3e938-106">Parameters</span></span>  
<span data-ttu-id="3e938-107">[içinde]`functionId`</span><span class="sxs-lookup"><span data-stu-id="3e938-107">[in] `functionId`</span></span>  
<span data-ttu-id="3e938-108">JIT derlemesinin başlatıldıği bellek içi işlevin tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="3e938-108">The identifier of the in-memory function for which JIT compilation is started.</span></span>

<span data-ttu-id="3e938-109">[içinde] `fIsSafeToBlock` engellemenin çalışma zamanının arama iş parçacığının bu geri aramadan dönmesini beklemesine neden olabileceğini belirtmek 
 `true` için; `false` engellemenin çalışma zamanının çalışmasını etkilemeyeceğini belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="3e938-109">[in] `fIsSafeToBlock`
`true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  

<span data-ttu-id="3e938-110">[içinde] `pILHeader` Yöntemin IL üstbilgisinin ilk baytına işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3e938-110">[in] `pILHeader` A pointer to the first byte of the method's IL header.</span></span>

<span data-ttu-id="3e938-111">[içinde] `cbILHeader` IL üstbilgisindeki bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="3e938-111">[in] `cbILHeader` The number of bytes in the IL header.</span></span>

## <a name="remarks"></a><span data-ttu-id="3e938-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3e938-112">Remarks</span></span>  

<span data-ttu-id="3e938-113">Dinamik bir yöntem JIT tarafından derlendiğinde bu geri arama tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="3e938-113">This callback is triggered whenever a dynamic method is JIT-compiled.</span></span> <span data-ttu-id="3e938-114">Bu çeşitli IL saplamaları ve LCG yöntemleri içerir.</span><span class="sxs-lookup"><span data-stu-id="3e938-114">This includes various IL stubs and LCG methods.</span></span> <span data-ttu-id="3e938-115">Amacı, profil oluşturucu yazarlara derlenen yöntemi kullanıcılara tanımlamak için yeterli bilgi sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="3e938-115">Its goal is to provide profiler writers with enough information to identify the compiled method to users.</span></span>

> [!NOTE]
> <span data-ttu-id="3e938-116">`functionId`dinamik yöntemlerin meta verisi olmadığından, değerler meta veri belirteçlerini gidermek için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="3e938-116">`functionId` values cannot be used to resolve to their metadata tokens, because dynamic methods have no metadata.</span></span>

<span data-ttu-id="3e938-117">İşaretçi `pILHeader` yalnızca geri arama sırasında geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="3e938-117">The `pILHeader` pointer is only valid during the callback.</span></span>

## <a name="requirements"></a><span data-ttu-id="3e938-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3e938-118">Requirements</span></span>  
 <span data-ttu-id="3e938-119">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3e938-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e938-120">**Üstbilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3e938-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3e938-121">**Kütüphane:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3e938-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3e938-122">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="3e938-122">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e938-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3e938-123">See also</span></span>

- [<span data-ttu-id="3e938-124">DynamicMethodJITCompilationFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3e938-124">DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [<span data-ttu-id="3e938-125">ICorProfilerCallback8 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3e938-125">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)
