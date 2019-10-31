---
title: ICorProfilerAssemblyReferenceProvider Arabirimi
ms.date: 03/30/2017
api_name:
- ICorProfilerAssemblyReferenceProvider
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 17205116-66e1-4acc-8f01-532fb3867028
topic_type:
- apiref
ms.openlocfilehash: f5ba72dca25889fb57c0ae1bb2429e54a8cf2228
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128711"
---
# <a name="icorprofilerassemblyreferenceprovider-interface"></a><span data-ttu-id="eaf5f-102">ICorProfilerAssemblyReferenceProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="eaf5f-102">ICorProfilerAssemblyReferenceProvider Interface</span></span>
<span data-ttu-id="eaf5f-103">[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="eaf5f-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="eaf5f-104">Profiler 'ın, profil oluşturucunun [ICorProfilerCallback:: ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) geri çağırması içinde ekleneceği derleme başvurularının ortak dil çalışma ZAMANıNı (CLR) bilgilendirmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="eaf5f-104">Enables the profiler to inform the common language runtime (CLR) of assembly references that the profiler will add in the [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="eaf5f-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="eaf5f-105">Methods</span></span>  
  
|<span data-ttu-id="eaf5f-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="eaf5f-106">Method</span></span>|<span data-ttu-id="eaf5f-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="eaf5f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="eaf5f-108">AddAssemblyReference Yöntemi</span><span class="sxs-lookup"><span data-stu-id="eaf5f-108">AddAssemblyReference Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)|<span data-ttu-id="eaf5f-109">Profiler planlarına eklenen ve [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) geri çağırmasına Eklenecek derleme başvurusunun clr 'sini bilgilendirir.</span><span class="sxs-lookup"><span data-stu-id="eaf5f-109">Informs the CLR of an assembly reference that the profiler plans to add in the [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eaf5f-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="eaf5f-110">Remarks</span></span>  
 <span data-ttu-id="eaf5f-111">CLR, profil oluşturucuyu [ICorProfilerCallback6:: GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) geri aramasında bir `ICorProfilerAssemblyReferenceProvider` Interface nesnesine geçirir.</span><span class="sxs-lookup"><span data-stu-id="eaf5f-111">The CLR passes the profiler an `ICorProfilerAssemblyReferenceProvider` interface object in the [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback.</span></span> <span data-ttu-id="eaf5f-112">Bu, profil oluşturucunun Profiler planının CLR 'yi [ICorProfilerCallback:: ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)içinde eklemesi için derleme başvurularını bilgilendirmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="eaf5f-112">This enables the profiler to inform the CLR of assembly references that the profiler plans to add later in the [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md).</span></span> <span data-ttu-id="eaf5f-113">callback.</span><span class="sxs-lookup"><span data-stu-id="eaf5f-113">callback.</span></span> <span data-ttu-id="eaf5f-114">Bu, CLR 'nin derleme başvurusu kapatma denetçisi ve derlemelerin paylaşılıp paylaşılamayacağını belirlemek için algoritmalarının doğruluğunu geliştirir.</span><span class="sxs-lookup"><span data-stu-id="eaf5f-114">This improves the accuracy of the CLR's assembly reference closure walker and its algorithms for determining whether assemblies may be shared.</span></span>  
  
 <span data-ttu-id="eaf5f-115">Bu arabirim yalnızca bu arabirim nesnesini Profiler 'a geçiren [ICorProfilerCallback6:: GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) geri aramasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="eaf5f-115">This interface can be used only in the [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback that passes this interface object to the profiler.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eaf5f-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="eaf5f-116">Requirements</span></span>  
 <span data-ttu-id="eaf5f-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eaf5f-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eaf5f-118">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="eaf5f-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="eaf5f-119">**.NET Framework sürümleri:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eaf5f-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eaf5f-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eaf5f-120">See also</span></span>

- [<span data-ttu-id="eaf5f-121">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="eaf5f-121">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
