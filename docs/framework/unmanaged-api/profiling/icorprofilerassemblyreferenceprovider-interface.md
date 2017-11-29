---
title: ICorProfilerAssemblyReferenceProvider Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerAssemblyReferenceProvider
api_location: mscorwks.dll
api_type: COM
ms.assetid: 17205116-66e1-4acc-8f01-532fb3867028
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2120e400d4ecd23c86cdae7b12d8706b35e8ca08
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerassemblyreferenceprovider-interface"></a><span data-ttu-id="ce9c2-102">ICorProfilerAssemblyReferenceProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ce9c2-102">ICorProfilerAssemblyReferenceProvider Interface</span></span>
<span data-ttu-id="ce9c2-103">[.NET Framework 4.5.2 ve sonraki sürümlerinde desteklenen]</span><span class="sxs-lookup"><span data-stu-id="ce9c2-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="ce9c2-104">Profil oluşturucu içinde ekleyeceksiniz derleme başvurularını ortak dil çalışma zamanı (CLR) bilgilendirmek profil oluşturucu etkinleştirir [Icorprofilercallback::moduleloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="ce9c2-104">Enables the profiler to inform the common language runtime (CLR) of assembly references that the profiler will add in the [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ce9c2-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="ce9c2-105">Methods</span></span>  
  
|<span data-ttu-id="ce9c2-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="ce9c2-106">Method</span></span>|<span data-ttu-id="ce9c2-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ce9c2-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ce9c2-108">AddAssemblyReference yöntemi</span><span class="sxs-lookup"><span data-stu-id="ce9c2-108">AddAssemblyReference Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)|<span data-ttu-id="ce9c2-109">Profil Oluşturucu ekleme planlarını bir derleme başvurusu CLR bildirir [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="ce9c2-109">Informs the CLR of an assembly reference that the profiler plans to add in the [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ce9c2-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ce9c2-110">Remarks</span></span>  
 <span data-ttu-id="ce9c2-111">Profil Oluşturucu CLR geçirmeden bir `ICorProfilerAssemblyReferenceProvider` arabirimi nesnesinde [Icorprofilercallback6::getassemblyreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="ce9c2-111">The CLR passes the profiler an `ICorProfilerAssemblyReferenceProvider` interface object in the [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback.</span></span> <span data-ttu-id="ce9c2-112">Bu daha sonra eklemek için profil oluşturucu planları derleme başvurularını CLR bildirmek profil oluşturucu sağlar [Icorprofilercallback::moduleloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md).</span><span class="sxs-lookup"><span data-stu-id="ce9c2-112">This enables the profiler to inform the CLR of assembly references that the profiler plans to add later in the [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md).</span></span> <span data-ttu-id="ce9c2-113">geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="ce9c2-113">callback.</span></span> <span data-ttu-id="ce9c2-114">Bu, CLR'ın derleme başvurusu kapatma walker ve derlemeler paylaşılabilir olup olmadığını belirlemek için kendi algoritmaları doğruluğunu artırır.</span><span class="sxs-lookup"><span data-stu-id="ce9c2-114">This improves the accuracy of the CLR's assembly reference closure walker and its algorithms for determining whether assemblies may be shared.</span></span>  
  
 <span data-ttu-id="ce9c2-115">Bu arabirim yalnızca kullanılabilir [Icorprofilercallback6::getassemblyreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) bu arabirimi nesnesi için profil oluşturucu geçirir geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="ce9c2-115">This interface can be used only in the [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback that passes this interface object to the profiler.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce9c2-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ce9c2-116">Requirements</span></span>  
 <span data-ttu-id="ce9c2-117">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ce9c2-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce9c2-118">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ce9c2-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ce9c2-119">**.NET framework sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce9c2-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce9c2-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ce9c2-120">See Also</span></span>  
 [<span data-ttu-id="ce9c2-121">Profil oluşturma arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ce9c2-121">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
