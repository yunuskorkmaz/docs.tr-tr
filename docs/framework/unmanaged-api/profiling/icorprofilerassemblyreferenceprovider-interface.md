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
ms.openlocfilehash: 17fb3de830d1aed2214631bbe8254a7f58030025
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500526"
---
# <a name="icorprofilerassemblyreferenceprovider-interface"></a><span data-ttu-id="c8aa3-102">ICorProfilerAssemblyReferenceProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c8aa3-102">ICorProfilerAssemblyReferenceProvider Interface</span></span>
<span data-ttu-id="c8aa3-103">[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="c8aa3-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="c8aa3-104">Profiler 'ın, profil oluşturucunun [ICorProfilerCallback:: ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) geri çağırması içinde ekleneceği derleme başvurularının ortak dil çalışma ZAMANıNı (CLR) bilgilendirmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="c8aa3-104">Enables the profiler to inform the common language runtime (CLR) of assembly references that the profiler will add in the [ICorProfilerCallback::ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c8aa3-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="c8aa3-105">Methods</span></span>  
  
|<span data-ttu-id="c8aa3-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="c8aa3-106">Method</span></span>|<span data-ttu-id="c8aa3-107">Description</span><span class="sxs-lookup"><span data-stu-id="c8aa3-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c8aa3-108">AddAssemblyReference Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c8aa3-108">AddAssemblyReference Method</span></span>](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)|<span data-ttu-id="c8aa3-109">Profiler planlarına eklenen ve [ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) geri çağırmasına Eklenecek derleme başvurusunun clr 'sini bilgilendirir.</span><span class="sxs-lookup"><span data-stu-id="c8aa3-109">Informs the CLR of an assembly reference that the profiler plans to add in the [ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c8aa3-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c8aa3-110">Remarks</span></span>  
 <span data-ttu-id="c8aa3-111">CLR, `ICorProfilerAssemblyReferenceProvider` [ICorProfilerCallback6:: GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) geri aramasında profil oluşturucu bir arabirim nesnesine geçirir.</span><span class="sxs-lookup"><span data-stu-id="c8aa3-111">The CLR passes the profiler an `ICorProfilerAssemblyReferenceProvider` interface object in the [ICorProfilerCallback6::GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) callback.</span></span> <span data-ttu-id="c8aa3-112">Bu, profil oluşturucunun Profiler planının CLR 'yi [ICorProfilerCallback:: ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md)içinde eklemesi için derleme başvurularını bilgilendirmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="c8aa3-112">This enables the profiler to inform the CLR of assembly references that the profiler plans to add later in the [ICorProfilerCallback::ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md).</span></span> <span data-ttu-id="c8aa3-113">callback.</span><span class="sxs-lookup"><span data-stu-id="c8aa3-113">callback.</span></span> <span data-ttu-id="c8aa3-114">Bu, CLR 'nin derleme başvurusu kapatma denetçisi ve derlemelerin paylaşılıp paylaşılamayacağını belirlemek için algoritmalarının doğruluğunu geliştirir.</span><span class="sxs-lookup"><span data-stu-id="c8aa3-114">This improves the accuracy of the CLR's assembly reference closure walker and its algorithms for determining whether assemblies may be shared.</span></span>  
  
 <span data-ttu-id="c8aa3-115">Bu arabirim yalnızca bu arabirim nesnesini Profiler 'a geçiren [ICorProfilerCallback6:: GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) geri aramasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c8aa3-115">This interface can be used only in the [ICorProfilerCallback6::GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) callback that passes this interface object to the profiler.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8aa3-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c8aa3-116">Requirements</span></span>  
 <span data-ttu-id="c8aa3-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c8aa3-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8aa3-118">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="c8aa3-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c8aa3-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8aa3-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8aa3-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c8aa3-120">See also</span></span>

- [<span data-ttu-id="c8aa3-121">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c8aa3-121">Profiling Interfaces</span></span>](profiling-interfaces.md)
