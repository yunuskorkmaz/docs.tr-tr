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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 860ecde22dead112a42b6ac868e34f0e9cd3531d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916207"
---
# <a name="icorprofilercallback7moduleinmemorysymbolsupdated-method"></a><span data-ttu-id="b206f-102">ICorProfilerCallback7:: Moduleınmemorysymbolsupdated yöntemi</span><span class="sxs-lookup"><span data-stu-id="b206f-102">ICorProfilerCallback7::ModuleInMemorySymbolsUpdated Method</span></span>
<span data-ttu-id="b206f-103">[.NET Framework 4.6.1 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="b206f-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="b206f-104">Bellek içi modülle ilişkili sembol akışı güncelleştirildiğinde profil oluşturucuyu bilgilendirir.</span><span class="sxs-lookup"><span data-stu-id="b206f-104">Notifies the profiler whenever the symbol stream associated with an in-memory module is updated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b206f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b206f-105">Syntax</span></span>  
  
```cpp  
HRESULT ModuleInMemorySymbolsUpdated(  
     ModuleID moduleId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b206f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b206f-106">Parameters</span></span>  
 <span data-ttu-id="b206f-107">'ndaki`moduleId`</span><span class="sxs-lookup"><span data-stu-id="b206f-107">[in] `moduleId`</span></span>  
 <span data-ttu-id="b206f-108">Sembol akışı güncelleştirilmiş olan bellek içi modülün tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="b206f-108">The identifier of the in-memory module whose symbol stream is updated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b206f-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b206f-109">Remarks</span></span>  
 <span data-ttu-id="b206f-110">Bu geri çağırma, [ICorProfilerCallback5:: SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) yöntemi çağrılırken [COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) olay maskesi bayrağı ayarlanarak denetlenir.</span><span class="sxs-lookup"><span data-stu-id="b206f-110">This callback is controlled by setting the [COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) event mask flag when calling the [ICorProfilerCallback5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b206f-111">Bu olay şu anda, API 'ler aracılığıyla <xref:System.Reflection.Emit> örtük olarak oluşturulan veya değiştirilen semboller için çıkarılmamaktadır.</span><span class="sxs-lookup"><span data-stu-id="b206f-111">This event is not currently raised for symbols implicitly created or modified via <xref:System.Reflection.Emit> APIs.</span></span>  
  
 <span data-ttu-id="b206f-112">Semboller, derleme için sembolleri belirtmek üzere bir <xref:System.Reflection.Assembly.Load*?displayProperty=nameWithType> `rawSymbolStore` bağımsız değişken içeren yönetilen yöntemlerin aşırı yüklerinden birine yapılan bir çağrıda önde gelen olsa bile, çalışma zamanı aslında sembolik verileri modülle ilişkilendiremeyebilir [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) geri çağırması gerçekleşene kadar.</span><span class="sxs-lookup"><span data-stu-id="b206f-112">Even when symbols are provided up front in a call to one of the overloads of the managed <xref:System.Reflection.Assembly.Load*?displayProperty=nameWithType> methods that includes a `rawSymbolStore` argument to specify the symbols for the assembly, the runtime may not actually associate the symbolic data with the module until after the [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback has occurred.</span></span> <span data-ttu-id="b206f-113">Bu olay, bu tür modüller için sembolleri toplamaya yönelik daha sonraki bir fırsat sağlar.</span><span class="sxs-lookup"><span data-stu-id="b206f-113">This event provides a later opportunity to collect symbols for such modules.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b206f-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b206f-114">Requirements</span></span>  
 <span data-ttu-id="b206f-115">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b206f-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b206f-116">**Üst bilgi** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="b206f-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b206f-117">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b206f-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b206f-118">**.NET Framework sürümleri:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b206f-118">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b206f-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b206f-119">See also</span></span>

- [<span data-ttu-id="b206f-120">ModuleLoadFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b206f-120">ModuleLoadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)
- [<span data-ttu-id="b206f-121">SetEventMask2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b206f-121">SetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)
- [<span data-ttu-id="b206f-122">ICorProfilerCallback7 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b206f-122">ICorProfilerCallback7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-interface.md)
