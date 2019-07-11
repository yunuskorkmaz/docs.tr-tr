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
ms.openlocfilehash: 0a6e00d55157046679ee1de0a7ff8e2764c1e357
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67758044"
---
# <a name="icorprofilercallback7moduleinmemorysymbolsupdated-method"></a><span data-ttu-id="b6492-102">ICorProfilerCallback7::ModuleInMemorySymbolsUpdated yöntemi</span><span class="sxs-lookup"><span data-stu-id="b6492-102">ICorProfilerCallback7::ModuleInMemorySymbolsUpdated Method</span></span>
<span data-ttu-id="b6492-103">[.NET Framework 4.6.1 ve sonraki sürümlerinde desteklenen]</span><span class="sxs-lookup"><span data-stu-id="b6492-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="b6492-104">Her bir bellek içi modül ile ilişkili simge akışı güncelleştirildiğinde, profil oluşturucu bildirir.</span><span class="sxs-lookup"><span data-stu-id="b6492-104">Notifies the profiler whenever the symbol stream associated with an in-memory module is updated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6492-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b6492-105">Syntax</span></span>  
  
```cpp  
HRESULT ModuleInMemorySymbolsUpdated(  
     ModuleID moduleId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b6492-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b6492-106">Parameters</span></span>  
 <span data-ttu-id="b6492-107">[in] `moduleId`</span><span class="sxs-lookup"><span data-stu-id="b6492-107">[in] `moduleId`</span></span>  
 <span data-ttu-id="b6492-108">Bellek içi modülü, sembol stream güncelleştirilir tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="b6492-108">The identifier of the in-memory module whose symbol stream is updated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b6492-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b6492-109">Remarks</span></span>  
 <span data-ttu-id="b6492-110">Bu geri çağırma ayarlanmasıyla denetlenir [COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) çağırırken olay maskesini bayrağı [ICorProfilerCallback5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b6492-110">This callback is controlled by setting the [COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) event mask flag when calling the [ICorProfilerCallback5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b6492-111">Bu olay şu anda örtük olarak oluşturulmuş veya aracılığıyla değiştirilmiş sembolleri oluşmaz <xref:System.Reflection.Emit> API'leri.</span><span class="sxs-lookup"><span data-stu-id="b6492-111">This event is not currently raised for symbols implicitly created or modified via <xref:System.Reflection.Emit> APIs.</span></span>  
  
 <span data-ttu-id="b6492-112">Bile ne zaman sembolleri Önden yönetilen aşırı çağrısında sağlanan <xref:System.Reflection.Assembly.Load*?displayProperty=nameWithType> içeren yöntemleri bir `rawSymbolStore` çalışma zamanı derleme için sembolleri belirtmek için bağımsız değişken değil gerçekten ilişkilendirmek sembolik veri modülü ile kadar sonra [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) geri çağırma oluştu.</span><span class="sxs-lookup"><span data-stu-id="b6492-112">Even when symbols are provided up front in a call to one of the overloads of the managed <xref:System.Reflection.Assembly.Load*?displayProperty=nameWithType> methods that includes a `rawSymbolStore` argument to specify the symbols for the assembly, the runtime may not actually associate the symbolic data with the module until after the [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback has occurred.</span></span> <span data-ttu-id="b6492-113">Bu olay, bu modüller için semboller toplamak için daha yeni bir fırsat sağlar.</span><span class="sxs-lookup"><span data-stu-id="b6492-113">This event provides a later opportunity to collect symbols for such modules.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6492-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b6492-114">Requirements</span></span>  
 <span data-ttu-id="b6492-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6492-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6492-116">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b6492-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b6492-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b6492-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b6492-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6492-118">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6492-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b6492-119">See also</span></span>

- [<span data-ttu-id="b6492-120">ModuleLoadFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b6492-120">ModuleLoadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)
- [<span data-ttu-id="b6492-121">SetEventMask2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b6492-121">SetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)
- [<span data-ttu-id="b6492-122">ICorProfilerCallback7 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b6492-122">ICorProfilerCallback7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-interface.md)
