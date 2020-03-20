---
title: ICorProfilerCallback8::DynamicMethodJITCompilationBitmiş Yöntem
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationFinished
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: c2e9489654a0fe5fa65ec638ed0f991a6c01415a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175115"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationfinished-method"></a><span data-ttu-id="6e880-102">ICorProfilerCallback8::DynamicMethodJITCompilationBitmiş Yöntem</span><span class="sxs-lookup"><span data-stu-id="6e880-102">ICorProfilerCallback8::DynamicMethodJITCompilationFinished Method</span></span>
<span data-ttu-id="6e880-103">[.NET Framework 4.7 ve sonraki sürümlerde desteklendi]</span><span class="sxs-lookup"><span data-stu-id="6e880-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  
  
<span data-ttu-id="6e880-104">Dinamik bir yöntemin JIT derlemesi tamamlandığında profiloluşturucuyu not edin.</span><span class="sxs-lookup"><span data-stu-id="6e880-104">Notifies the profiler whenever JIT compilation of a dynamic method has completed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e880-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6e880-105">Syntax</span></span>  
  
```cpp  
HRESULT DynamicMethodJITCompilationFinished(  
     [in]  FunctionID  functionId,
     [in]  BOOL        hrStatus,
     [in]  BOOL        fIsSafeToBlock
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6e880-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6e880-106">Parameters</span></span>  
<span data-ttu-id="6e880-107">[içinde]`functionId`</span><span class="sxs-lookup"><span data-stu-id="6e880-107">[in] `functionId`</span></span>  
<span data-ttu-id="6e880-108">JIT derlemesinin başlatıldıği bellek içi işlevin tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="6e880-108">The identifier of the in-memory function for which JIT compilation is started.</span></span>

<span data-ttu-id="6e880-109">[içinde] `hrStatus` JIT derlemesinin başarılı olup olmadığını gösteren bir değer.</span><span class="sxs-lookup"><span data-stu-id="6e880-109">[in] `hrStatus` A value that indicates whether the JIT compilation was successful.</span></span>

<span data-ttu-id="6e880-110">[içinde] `fIsSafeToBlock` engellemenin çalışma zamanının arama iş parçacığının bu geri aramadan dönmesini beklemesine neden olabileceğini belirtmek 
 `true` için; `false` engellemenin çalışma zamanının çalışmasını etkilemeyeceğini belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="6e880-110">[in] `fIsSafeToBlock`
`true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  

## <a name="remarks"></a><span data-ttu-id="6e880-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6e880-111">Remarks</span></span>  

<span data-ttu-id="6e880-112">Dinamik bir yöntemin JIT derlemesi tamamlandığında bu geri arama tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="6e880-112">This callback is triggered whenever JIT compilation of a dynamic method has finished.</span></span> <span data-ttu-id="6e880-113">Bu çeşitli IL saplamaları ve LCG yöntemleri içerir.</span><span class="sxs-lookup"><span data-stu-id="6e880-113">This includes various IL stubs and LCG methods.</span></span> <span data-ttu-id="6e880-114">Amacı, profil oluşturucu yazarlara derlenen yöntemi kullanıcılara tanımlamak için yeterli bilgi sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="6e880-114">Its goal is to provide profiler writers with enough information to identify the compiled method to users.</span></span>

> [!NOTE]
> <span data-ttu-id="6e880-115">`functionId`dinamik yöntemlerin meta verisi olmadığından, değerler meta veri belirteçlerini gidermek için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="6e880-115">`functionId` values cannot be used to resolve to their metadata tokens, because dynamic methods have no metadata.</span></span>

## <a name="requirements"></a><span data-ttu-id="6e880-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6e880-116">Requirements</span></span>  
 <span data-ttu-id="6e880-117">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6e880-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e880-118">**Üstbilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6e880-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6e880-119">**Kütüphane:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6e880-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6e880-120">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="6e880-120">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e880-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6e880-121">See also</span></span>

- [<span data-ttu-id="6e880-122">DynamicMethodJITCompilationStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6e880-122">DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="6e880-123">ICorProfilerCallback8 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6e880-123">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)
