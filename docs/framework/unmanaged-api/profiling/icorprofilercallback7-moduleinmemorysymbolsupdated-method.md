---
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
ms.openlocfilehash: f6dd10d196ffd3a653584e1bc8d1a5643850bc33
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136602"
---
# <a name="icorprofilercallback7moduleinmemorysymbolsupdated-method"></a><span data-ttu-id="622d2-102">ICorProfilerCallback7:: Moduleınmemorysymbolsupdated yöntemi</span><span class="sxs-lookup"><span data-stu-id="622d2-102">ICorProfilerCallback7::ModuleInMemorySymbolsUpdated Method</span></span>
<span data-ttu-id="622d2-103">[.NET Framework 4.6.1 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="622d2-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="622d2-104">Bellek içi modülle ilişkili sembol akışı güncelleştirildiğinde profil oluşturucuyu bilgilendirir.</span><span class="sxs-lookup"><span data-stu-id="622d2-104">Notifies the profiler whenever the symbol stream associated with an in-memory module is updated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="622d2-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="622d2-105">Syntax</span></span>  
  
```cpp  
HRESULT ModuleInMemorySymbolsUpdated(  
     ModuleID moduleId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="622d2-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="622d2-106">Parameters</span></span>  
 <span data-ttu-id="622d2-107">[in] `moduleId`</span><span class="sxs-lookup"><span data-stu-id="622d2-107">[in] `moduleId`</span></span>  
 <span data-ttu-id="622d2-108">Sembol akışı güncelleştirilmiş olan bellek içi modülün tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="622d2-108">The identifier of the in-memory module whose symbol stream is updated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="622d2-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="622d2-109">Remarks</span></span>  
 <span data-ttu-id="622d2-110">Bu geri çağırma, [ICorProfilerCallback5:: SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) yöntemi çağrılırken [COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) olay maskesi bayrağı ayarlanarak denetlenir.</span><span class="sxs-lookup"><span data-stu-id="622d2-110">This callback is controlled by setting the [COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) event mask flag when calling the [ICorProfilerCallback5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="622d2-111">Bu olay şu anda, <xref:System.Reflection.Emit> API 'Leri aracılığıyla örtük olarak oluşturulan veya değiştirilen semboller için çıkarılmamaktadır.</span><span class="sxs-lookup"><span data-stu-id="622d2-111">This event is not currently raised for symbols implicitly created or modified via <xref:System.Reflection.Emit> APIs.</span></span>  
  
 <span data-ttu-id="622d2-112">Semboller, derleme için sembolleri belirtmek üzere bir `rawSymbolStore` bağımsız değişkeni içeren yönetilen <xref:System.Reflection.Assembly.Load*?displayProperty=nameWithType> yöntemlerinin aşırı yüklerinden birine yapılan bir çağrıda ön yüklendiğinde bile, çalışma zamanı aslında sembolik verileri, [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) geri çağırma işlemi oluştu.</span><span class="sxs-lookup"><span data-stu-id="622d2-112">Even when symbols are provided up front in a call to one of the overloads of the managed <xref:System.Reflection.Assembly.Load*?displayProperty=nameWithType> methods that includes a `rawSymbolStore` argument to specify the symbols for the assembly, the runtime may not actually associate the symbolic data with the module until after the [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback has occurred.</span></span> <span data-ttu-id="622d2-113">Bu olay, bu tür modüller için sembolleri toplamaya yönelik daha sonraki bir fırsat sağlar.</span><span class="sxs-lookup"><span data-stu-id="622d2-113">This event provides a later opportunity to collect symbols for such modules.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="622d2-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="622d2-114">Requirements</span></span>  
 <span data-ttu-id="622d2-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="622d2-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="622d2-116">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="622d2-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="622d2-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="622d2-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="622d2-118">**.NET Framework sürümleri:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="622d2-118">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="622d2-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="622d2-119">See also</span></span>

- [<span data-ttu-id="622d2-120">ModuleLoadFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="622d2-120">ModuleLoadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)
- [<span data-ttu-id="622d2-121">SetEventMask2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="622d2-121">SetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)
- [<span data-ttu-id="622d2-122">ICorProfilerCallback7 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="622d2-122">ICorProfilerCallback7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-interface.md)
