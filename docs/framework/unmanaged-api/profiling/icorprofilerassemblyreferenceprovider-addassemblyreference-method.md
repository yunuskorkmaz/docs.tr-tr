---
title: "ICorProfilerAssemblyReferenceProvider::AddAssemblyReference Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: ICorProfilerAssemblyReferenceProvider.AddAssemblyReference
api_location: mscorwks.dll
api_type: COM
ms.assetid: 3d5af8e7-c337-48f4-9fa6-97c83878b9b1
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f67ef9832a7fb1ff1ec153a4f8aff74079e3b76c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerassemblyreferenceprovideraddassemblyreference-method"></a><span data-ttu-id="842aa-102">ICorProfilerAssemblyReferenceProvider::AddAssemblyReference Yöntemi</span><span class="sxs-lookup"><span data-stu-id="842aa-102">ICorProfilerAssemblyReferenceProvider::AddAssemblyReference Method</span></span>
<span data-ttu-id="842aa-103">[.NET Framework 4.5.2 ve sonraki sürümlerinde desteklenen]</span><span class="sxs-lookup"><span data-stu-id="842aa-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="842aa-104">Ortak dil çalışma zamanı (CLR) eklemek için profil oluşturucu planları bir derleme başvurusu bildirir [Icorprofilercallback::moduleloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="842aa-104">Informs the common language runtime (CLR) of an assembly reference that the profiler plans to add in the [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="842aa-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="842aa-105">Syntax</span></span>  
  
```cpp
HRESULT AddAssemblyReference(  
        const COR_PRF_ASSEMBLY_REFERENCE_INFO* pAssemblyRefInfo  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="842aa-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="842aa-106">Parameters</span></span>  
 <span data-ttu-id="842aa-107">pAssemblyRefInfo</span><span class="sxs-lookup"><span data-stu-id="842aa-107">pAssemblyRefInfo</span></span>  
 <span data-ttu-id="842aa-108">Bir işaretçi bir [cor_prf_assembly_reference_ınfo](../../../../docs/framework/unmanaged-api/profiling/cor-prf-assembly-reference-info-structure.md) yapısı CLR bir derleme başvurusu kapatma ilerlemesi gerçekleştirirken düşünmelisiniz bir derleme başvurusu hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="842aa-108">A pointer to a [COR_PRF_ASSEMBLY_REFERENCE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-assembly-reference-info-structure.md) structure that provides the CLR with information about an assembly reference that it should consider when performing an assembly reference closure walk.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="842aa-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="842aa-109">Remarks</span></span>  
 <span data-ttu-id="842aa-110">Profil Oluşturucu planları belirtilen derlemesinden başvurmak için her hedef derleme için bu yöntemi çağırır `wszAssemblyPath` bağımsız değişkeni [Icorprofilercallback6::getassemblyreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="842aa-110">The profiler calls this method for each target assembly it plans to reference from the assembly specified in the `wszAssemblyPath` argument of the [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback.</span></span> <span data-ttu-id="842aa-111">[Icorprofilerassemblyreferenceprovider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) arabirimi nesnesi profil oluşturucu için 's geçirilen [Icorprofilercallback6::getassemblyreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) derleme yolu ve adı ile birlikte geri çağırma `wszAssemblyPath` bağımsız değişkeni.</span><span class="sxs-lookup"><span data-stu-id="842aa-111">The [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) interface object is passed to the profiler's [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback, along with the assembly path and name in the `wszAssemblyPath` argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="842aa-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="842aa-112">Requirements</span></span>  
 <span data-ttu-id="842aa-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="842aa-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="842aa-114">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="842aa-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="842aa-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="842aa-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="842aa-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="842aa-116">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="842aa-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="842aa-117">See Also</span></span>  
 [<span data-ttu-id="842aa-118">Icorprofilerassemblyreferenceprovider arabirimi</span><span class="sxs-lookup"><span data-stu-id="842aa-118">ICorProfilerAssemblyReferenceProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md)  
 [<span data-ttu-id="842aa-119">GetAssemblyReferences yöntemi</span><span class="sxs-lookup"><span data-stu-id="842aa-119">GetAssemblyReferences Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)  
 [<span data-ttu-id="842aa-120">ModuleLoadFinished yöntemi</span><span class="sxs-lookup"><span data-stu-id="842aa-120">ModuleLoadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)
