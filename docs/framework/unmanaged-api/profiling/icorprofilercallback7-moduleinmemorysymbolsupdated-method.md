---
title: ICorProfilerCallback7::ModuleInMemorySymbolsUpdated yöntemi
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
ms.openlocfilehash: 9aa690378a32ffee2def672f02dc8b5582647a5e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455820"
---
# <a name="icorprofilercallback7moduleinmemorysymbolsupdated-method"></a><span data-ttu-id="73fcf-102">ICorProfilerCallback7::ModuleInMemorySymbolsUpdated yöntemi</span><span class="sxs-lookup"><span data-stu-id="73fcf-102">ICorProfilerCallback7::ModuleInMemorySymbolsUpdated Method</span></span>
<span data-ttu-id="73fcf-103">[.NET Framework 4.6.1 ve sonraki sürümlerinde desteklenen]</span><span class="sxs-lookup"><span data-stu-id="73fcf-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="73fcf-104">Bellek içi modülü ile ilişkili simgesi akış güncelleştirildiğinde profil oluşturucu bildirir.</span><span class="sxs-lookup"><span data-stu-id="73fcf-104">Notifies the profiler whenever the symbol stream associated with an in-memory module is updated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73fcf-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="73fcf-105">Syntax</span></span>  
  
```  
HRESULT ModuleInMemorySymbolsUpdated(  
     ModuleID moduleId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="73fcf-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="73fcf-106">Parameters</span></span>  
 <span data-ttu-id="73fcf-107">[in] `moduleId`</span><span class="sxs-lookup"><span data-stu-id="73fcf-107">[in] `moduleId`</span></span>  
 <span data-ttu-id="73fcf-108">Simge akış güncelleştirilmiş bellek içi modülü tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="73fcf-108">The identifier of the in-memory module whose symbol stream is updated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73fcf-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="73fcf-109">Remarks</span></span>  
 <span data-ttu-id="73fcf-110">Bu geri çağırma ayarlanmasıyla denetlenir [COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) çağrılırken olay maskesi bayrağı [ICorProfilerCallback5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="73fcf-110">This callback is controlled by setting the [COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) event mask flag when calling the [ICorProfilerCallback5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="73fcf-111">Bu olay şu anda örtük olarak oluşturulmuş veya aracılığıyla değiştirilmiş sembolleri oluşmaz <xref:System.Reflection.Emit> API'leri.</span><span class="sxs-lookup"><span data-stu-id="73fcf-111">This event is not currently raised for symbols implicitly created or modified via <xref:System.Reflection.Emit> APIs.</span></span>  
  
 <span data-ttu-id="73fcf-112">Hatta zaman simgeleri Önden yönetilen aşırı birine çağrıda sağlanan <xref:System.Reflection.Assembly.Load*?displayProperty=nameWithType> içerir yöntemleri bir `rawSymbolStore` çalışma zamanı derlemesi için simgeler belirtmek için bağımsız değişken değil gerçekte ilişkilendirmek simgesel veri modülüyle kadar sonra [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) geri çağırma oluştu.</span><span class="sxs-lookup"><span data-stu-id="73fcf-112">Even when symbols are provided up front in a call to one of the overloads of the managed <xref:System.Reflection.Assembly.Load*?displayProperty=nameWithType> methods that includes a `rawSymbolStore` argument to specify the symbols for the assembly, the runtime may not actually associate the symbolic data with the module until after the [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback has occurred.</span></span> <span data-ttu-id="73fcf-113">Bu olay, bu tür modülleri simgelerini toplamak için bir sonraki fırsatı sağlar.</span><span class="sxs-lookup"><span data-stu-id="73fcf-113">This event provides a later opportunity to collect symbols for such modules.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73fcf-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="73fcf-114">Requirements</span></span>  
 <span data-ttu-id="73fcf-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73fcf-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73fcf-116">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="73fcf-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="73fcf-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="73fcf-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="73fcf-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73fcf-118">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73fcf-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="73fcf-119">See Also</span></span>  
 [<span data-ttu-id="73fcf-120">ModuleLoadFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="73fcf-120">ModuleLoadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)  
 [<span data-ttu-id="73fcf-121">SetEventMask2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="73fcf-121">SetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)  
 [<span data-ttu-id="73fcf-122">ICorProfilerCallback7 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="73fcf-122">ICorProfilerCallback7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-interface.md)
