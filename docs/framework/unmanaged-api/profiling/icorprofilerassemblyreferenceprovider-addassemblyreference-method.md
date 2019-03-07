---
title: ICorProfilerAssemblyReferenceProvider::AddAssemblyReference Yöntemi
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorProfilerAssemblyReferenceProvider.AddAssemblyReference
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 3d5af8e7-c337-48f4-9fa6-97c83878b9b1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ae7d896ee8e06921d685fad9ae2fcc0ac215d64a
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57485063"
---
# <a name="icorprofilerassemblyreferenceprovideraddassemblyreference-method"></a><span data-ttu-id="15838-102">ICorProfilerAssemblyReferenceProvider::AddAssemblyReference Yöntemi</span><span class="sxs-lookup"><span data-stu-id="15838-102">ICorProfilerAssemblyReferenceProvider::AddAssemblyReference Method</span></span>
<span data-ttu-id="15838-103">[.NET Framework 4.5.2 ve sonraki sürümlerinde desteklenen]</span><span class="sxs-lookup"><span data-stu-id="15838-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="15838-104">Ortak dil çalışma zamanı (CLR) profil oluşturucuyu eklemek için planlar bir bütünleştirilmiş kod başvurusu, bildirir [Icorprofilercallback::moduleloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="15838-104">Informs the common language runtime (CLR) of an assembly reference that the profiler plans to add in the [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15838-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="15838-105">Syntax</span></span>  
  
```cpp
HRESULT AddAssemblyReference(  
        const COR_PRF_ASSEMBLY_REFERENCE_INFO* pAssemblyRefInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="15838-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="15838-106">Parameters</span></span>  
 <span data-ttu-id="15838-107">pAssemblyRefInfo</span><span class="sxs-lookup"><span data-stu-id="15838-107">pAssemblyRefInfo</span></span>  
 <span data-ttu-id="15838-108">Bir işaretçi bir [cor_prf_assembly_reference_ınfo](../../../../docs/framework/unmanaged-api/profiling/cor-prf-assembly-reference-info-structure.md) yapısı CLR bir bütünleştirilmiş kod başvurusu kapanış Yürüme gerçekleştirirken düşünmelisiniz bir bütünleştirilmiş kod başvurusu hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="15838-108">A pointer to a [COR_PRF_ASSEMBLY_REFERENCE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-assembly-reference-info-structure.md) structure that provides the CLR with information about an assembly reference that it should consider when performing an assembly reference closure walk.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="15838-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="15838-109">Remarks</span></span>  
 <span data-ttu-id="15838-110">Profil Oluşturucu, her hedef derleme planları içinde belirtilen derleme başvuru yapmak için bu yöntemi çağırır. `wszAssemblyPath` bağımsız değişkeni [Icorprofilercallback6::getassemblyreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="15838-110">The profiler calls this method for each target assembly it plans to reference from the assembly specified in the `wszAssemblyPath` argument of the [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback.</span></span> <span data-ttu-id="15838-111">[Icorprofilerassemblyreferenceprovider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) arabirimi nesnesi oluşturucunun geçirilen [Icorprofilercallback6::getassemblyreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) derleme yolu ve adı ile birlikte bir geri çağırma `wszAssemblyPath` bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="15838-111">The [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) interface object is passed to the profiler's [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback, along with the assembly path and name in the `wszAssemblyPath` argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15838-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="15838-112">Requirements</span></span>  
 <span data-ttu-id="15838-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15838-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15838-114">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="15838-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="15838-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="15838-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="15838-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15838-116">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15838-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="15838-117">See also</span></span>
- [<span data-ttu-id="15838-118">ICorProfilerAssemblyReferenceProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="15838-118">ICorProfilerAssemblyReferenceProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md)
- [<span data-ttu-id="15838-119">GetAssemblyReferences Yöntemi</span><span class="sxs-lookup"><span data-stu-id="15838-119">GetAssemblyReferences Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)
- [<span data-ttu-id="15838-120">ModuleLoadFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="15838-120">ModuleLoadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)
