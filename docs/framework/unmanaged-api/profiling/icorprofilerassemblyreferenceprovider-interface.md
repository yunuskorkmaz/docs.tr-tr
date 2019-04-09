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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3bad1cc71b9a27896141837a6d342f2cfe068fc5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59089738"
---
# <a name="icorprofilerassemblyreferenceprovider-interface"></a><span data-ttu-id="53bad-102">ICorProfilerAssemblyReferenceProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="53bad-102">ICorProfilerAssemblyReferenceProvider Interface</span></span>
<span data-ttu-id="53bad-103">[.NET Framework 4.5.2 ve sonraki sürümlerinde desteklenen]</span><span class="sxs-lookup"><span data-stu-id="53bad-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="53bad-104">Profil oluşturucu içinde ekleyeceğiniz derleme başvuruları, ortak dil çalışma zamanı (CLR) bildirmek profil oluşturucu sağlar [Icorprofilercallback::moduleloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="53bad-104">Enables the profiler to inform the common language runtime (CLR) of assembly references that the profiler will add in the [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="53bad-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="53bad-105">Methods</span></span>  
  
|<span data-ttu-id="53bad-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="53bad-106">Method</span></span>|<span data-ttu-id="53bad-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="53bad-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="53bad-108">AddAssemblyReference Yöntemi</span><span class="sxs-lookup"><span data-stu-id="53bad-108">AddAssemblyReference Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)|<span data-ttu-id="53bad-109">CLR Profil Oluşturucu ekleme planları bir bütünleştirilmiş kod başvurusu bildirir [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="53bad-109">Informs the CLR of an assembly reference that the profiler plans to add in the [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="53bad-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="53bad-110">Remarks</span></span>  
 <span data-ttu-id="53bad-111">CLR Profil Oluşturucu geçirmeden bir `ICorProfilerAssemblyReferenceProvider` arabirimi nesnesinde [Icorprofilercallback6::getassemblyreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="53bad-111">The CLR passes the profiler an `ICorProfilerAssemblyReferenceProvider` interface object in the [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback.</span></span> <span data-ttu-id="53bad-112">CLR Profil Oluşturucu, daha sonra eklenecek planları derleme başvuruları bildirmek profil oluşturucu böylece [Icorprofilercallback::moduleloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md).</span><span class="sxs-lookup"><span data-stu-id="53bad-112">This enables the profiler to inform the CLR of assembly references that the profiler plans to add later in the [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md).</span></span> <span data-ttu-id="53bad-113">geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="53bad-113">callback.</span></span> <span data-ttu-id="53bad-114">Bu, CLR'nin bütünleştirilmiş kod başvurusu kapanış walker ve derlemeleri paylaşılabilir olup olmadığını belirlemek için kendi algoritmaları doğruluğu artırır.</span><span class="sxs-lookup"><span data-stu-id="53bad-114">This improves the accuracy of the CLR's assembly reference closure walker and its algorithms for determining whether assemblies may be shared.</span></span>  
  
 <span data-ttu-id="53bad-115">Bu arabirim yalnızca kullanılabilir [Icorprofilercallback6::getassemblyreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) geri çağırma profil oluşturucu için bu arabirimi nesnesini geçirir.</span><span class="sxs-lookup"><span data-stu-id="53bad-115">This interface can be used only in the [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback that passes this interface object to the profiler.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53bad-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="53bad-116">Requirements</span></span>  
 <span data-ttu-id="53bad-117">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="53bad-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53bad-118">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="53bad-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 **<span data-ttu-id="53bad-119">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="53bad-119">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="53bad-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="53bad-120">See also</span></span>

- [<span data-ttu-id="53bad-121">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="53bad-121">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
