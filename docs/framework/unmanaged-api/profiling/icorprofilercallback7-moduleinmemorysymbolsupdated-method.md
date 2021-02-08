---
description: 'Şu konuda daha fazla bilgi edinin: ICorProfilerCallback7:: Moduleınmemorysymbolsupdated yöntemi'
title: 'ICorProfilerCallback7:: Moduleınmemorysymbolsupdated yöntemi'
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback7.ModuleInMemorySymbolsUpdated
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.assetid: f362a896-3247-4894-9727-e48dbbcd2c78
ms.openlocfilehash: 74adf7edc5269824a924933eb3284a5964e1bac1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781733"
---
# <a name="icorprofilercallback7moduleinmemorysymbolsupdated-method"></a><span data-ttu-id="a3397-103">ICorProfilerCallback7:: Moduleınmemorysymbolsupdated yöntemi</span><span class="sxs-lookup"><span data-stu-id="a3397-103">ICorProfilerCallback7::ModuleInMemorySymbolsUpdated Method</span></span>

<span data-ttu-id="a3397-104">[.NET Framework 4.6.1 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="a3397-104">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="a3397-105">Bellek içi modülle ilişkili sembol akışı güncelleştirildiğinde profil oluşturucuyu bilgilendirir.</span><span class="sxs-lookup"><span data-stu-id="a3397-105">Notifies the profiler whenever the symbol stream associated with an in-memory module is updated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3397-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a3397-106">Syntax</span></span>  
  
```cpp  
HRESULT ModuleInMemorySymbolsUpdated(  
     ModuleID moduleId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a3397-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a3397-107">Parameters</span></span>  

 <span data-ttu-id="a3397-108">'ndaki `moduleId`</span><span class="sxs-lookup"><span data-stu-id="a3397-108">[in] `moduleId`</span></span>  
 <span data-ttu-id="a3397-109">Sembol akışı güncelleştirilmiş olan bellek içi modülün tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="a3397-109">The identifier of the in-memory module whose symbol stream is updated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a3397-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a3397-110">Remarks</span></span>  

 <span data-ttu-id="a3397-111">Bu geri çağırma, [ICorProfilerCallback5:: SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) yöntemi çağrılırken [COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED](cor-prf-high-monitor-enumeration.md) Event Mask bayrağı ayarlanarak denetlenir.</span><span class="sxs-lookup"><span data-stu-id="a3397-111">This callback is controlled by setting the [COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED](cor-prf-high-monitor-enumeration.md) event mask flag when calling the [ICorProfilerCallback5::SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a3397-112">Bu olay şu anda, API 'ler aracılığıyla örtük olarak oluşturulan veya değiştirilen semboller için çıkarılmamaktadır <xref:System.Reflection.Emit> .</span><span class="sxs-lookup"><span data-stu-id="a3397-112">This event is not currently raised for symbols implicitly created or modified via <xref:System.Reflection.Emit> APIs.</span></span>  
  
 <span data-ttu-id="a3397-113">Semboller, derleme için sembolleri belirtmek üzere bir bağımsız değişken içeren yönetilen yöntemlerin aşırı yüklerinden birine yapılan bir çağrıda önde gelen olsa bile <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> `rawSymbolStore` , [ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) geri çağırması gerçekleşene kadar çalışma zamanı aslında sembolik verileri modülle ilişkilendirmeyebilir.</span><span class="sxs-lookup"><span data-stu-id="a3397-113">Even when symbols are provided up front in a call to one of the overloads of the managed <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> methods that includes a `rawSymbolStore` argument to specify the symbols for the assembly, the runtime may not actually associate the symbolic data with the module until after the [ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) callback has occurred.</span></span> <span data-ttu-id="a3397-114">Bu olay, bu tür modüller için sembolleri toplamaya yönelik daha sonraki bir fırsat sağlar.</span><span class="sxs-lookup"><span data-stu-id="a3397-114">This event provides a later opportunity to collect symbols for such modules.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3397-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a3397-115">Requirements</span></span>  

 <span data-ttu-id="a3397-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a3397-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3397-117">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="a3397-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a3397-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a3397-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a3397-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3397-119">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3397-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a3397-120">See also</span></span>

- [<span data-ttu-id="a3397-121">ModuleLoadFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a3397-121">ModuleLoadFinished Method</span></span>](icorprofilercallback-moduleloadfinished-method.md)
- [<span data-ttu-id="a3397-122">SetEventMask2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a3397-122">SetEventMask2 Method</span></span>](icorprofilerinfo5-seteventmask2-method.md)
- [<span data-ttu-id="a3397-123">ICorProfilerCallback7 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a3397-123">ICorProfilerCallback7 Interface</span></span>](icorprofilercallback7-interface.md)
