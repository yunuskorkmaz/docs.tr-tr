---
description: ': ICorProfilerAssemblyReferenceProvider arabirimi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 0f16bad95dba46452ce5cc8ad1bbe6ca1bfeb7c8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99648356"
---
# <a name="icorprofilerassemblyreferenceprovider-interface"></a><span data-ttu-id="772c8-103">ICorProfilerAssemblyReferenceProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="772c8-103">ICorProfilerAssemblyReferenceProvider Interface</span></span>

<span data-ttu-id="772c8-104">[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="772c8-104">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="772c8-105">Profiler 'ın, profil oluşturucunun [ICorProfilerCallback:: ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) geri çağırması içinde ekleneceği derleme başvurularının ortak dil çalışma ZAMANıNı (CLR) bilgilendirmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="772c8-105">Enables the profiler to inform the common language runtime (CLR) of assembly references that the profiler will add in the [ICorProfilerCallback::ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="772c8-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="772c8-106">Methods</span></span>  
  
|<span data-ttu-id="772c8-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="772c8-107">Method</span></span>|<span data-ttu-id="772c8-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="772c8-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="772c8-109">AddAssemblyReference Yöntemi</span><span class="sxs-lookup"><span data-stu-id="772c8-109">AddAssemblyReference Method</span></span>](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)|<span data-ttu-id="772c8-110">Profiler planlarına eklenen ve [ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) geri çağırmasına Eklenecek derleme başvurusunun clr 'sini bilgilendirir.</span><span class="sxs-lookup"><span data-stu-id="772c8-110">Informs the CLR of an assembly reference that the profiler plans to add in the [ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="772c8-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="772c8-111">Remarks</span></span>  

 <span data-ttu-id="772c8-112">CLR, `ICorProfilerAssemblyReferenceProvider` [ICorProfilerCallback6:: GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) geri aramasında profil oluşturucu bir arabirim nesnesine geçirir.</span><span class="sxs-lookup"><span data-stu-id="772c8-112">The CLR passes the profiler an `ICorProfilerAssemblyReferenceProvider` interface object in the [ICorProfilerCallback6::GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) callback.</span></span> <span data-ttu-id="772c8-113">Bu, profil oluşturucunun Profiler planının CLR 'yi [ICorProfilerCallback:: ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md)içinde eklemesi için derleme başvurularını bilgilendirmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="772c8-113">This enables the profiler to inform the CLR of assembly references that the profiler plans to add later in the [ICorProfilerCallback::ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md).</span></span> <span data-ttu-id="772c8-114">callback.</span><span class="sxs-lookup"><span data-stu-id="772c8-114">callback.</span></span> <span data-ttu-id="772c8-115">Bu, CLR 'nin derleme başvurusu kapatma denetçisi ve derlemelerin paylaşılıp paylaşılamayacağını belirlemek için algoritmalarının doğruluğunu geliştirir.</span><span class="sxs-lookup"><span data-stu-id="772c8-115">This improves the accuracy of the CLR's assembly reference closure walker and its algorithms for determining whether assemblies may be shared.</span></span>  
  
 <span data-ttu-id="772c8-116">Bu arabirim yalnızca bu arabirim nesnesini Profiler 'a geçiren [ICorProfilerCallback6:: GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) geri aramasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="772c8-116">This interface can be used only in the [ICorProfilerCallback6::GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) callback that passes this interface object to the profiler.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="772c8-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="772c8-117">Requirements</span></span>  

 <span data-ttu-id="772c8-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="772c8-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="772c8-119">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="772c8-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="772c8-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="772c8-120">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="772c8-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="772c8-121">See also</span></span>

- [<span data-ttu-id="772c8-122">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="772c8-122">Profiling Interfaces</span></span>](profiling-interfaces.md)
