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
ms.openlocfilehash: 6d732c6c2871cc5e042b8504db26aabb19963f8c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500513"
---
# <a name="icorprofilerassemblyreferenceprovideraddassemblyreference-method"></a><span data-ttu-id="5cdd2-102">ICorProfilerAssemblyReferenceProvider::AddAssemblyReference Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5cdd2-102">ICorProfilerAssemblyReferenceProvider::AddAssemblyReference Method</span></span>
<span data-ttu-id="5cdd2-103">[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="5cdd2-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="5cdd2-104">Profiler planlarının [ICorProfilerCallback:: ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) geri çağırması içine eklemesi için bir derleme başvurusunun ortak dil çalışma zamanına (CLR) bildirir.</span><span class="sxs-lookup"><span data-stu-id="5cdd2-104">Informs the common language runtime (CLR) of an assembly reference that the profiler plans to add in the [ICorProfilerCallback::ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5cdd2-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="5cdd2-105">Syntax</span></span>  
  
```cpp
HRESULT AddAssemblyReference(  
        const COR_PRF_ASSEMBLY_REFERENCE_INFO* pAssemblyRefInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5cdd2-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5cdd2-106">Parameters</span></span>

- `pAssemblyRefInfo`

  <span data-ttu-id="5cdd2-107">Bir derleme başvurusu kapatma ilerlemesi gerçekleştirirken göz önünde bulundurmanız gereken bir derleme başvurusu hakkındaki bilgilerle CLR sağlayan [COR_PRF_ASSEMBLY_REFERENCE_INFO](cor-prf-assembly-reference-info-structure.md) yapısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5cdd2-107">A pointer to a [COR_PRF_ASSEMBLY_REFERENCE_INFO](cor-prf-assembly-reference-info-structure.md) structure that provides the CLR with information about an assembly reference that it should consider when performing an assembly reference closure walk.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="5cdd2-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5cdd2-108">Remarks</span></span>  
 <span data-ttu-id="5cdd2-109">Profil Oluşturucu, `wszAssemblyPath` [ICorProfilerCallback6:: GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) geri çağrısının bağımsız değişkeninde belirtilen derlemeden başvuruyu planlıyor olan her bir hedef derleme için bu yöntemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="5cdd2-109">The profiler calls this method for each target assembly it plans to reference from the assembly specified in the `wszAssemblyPath` argument of the [ICorProfilerCallback6::GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) callback.</span></span> <span data-ttu-id="5cdd2-110">[ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) arabirim nesnesi, bağımsız değişkende derleme yolu ve adı ile birlikte Profiler 'ın [ICorProfilerCallback6:: GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) geri aramaya geçirilir `wszAssemblyPath` .</span><span class="sxs-lookup"><span data-stu-id="5cdd2-110">The [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) interface object is passed to the profiler's [ICorProfilerCallback6::GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) callback, along with the assembly path and name in the `wszAssemblyPath` argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5cdd2-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5cdd2-111">Requirements</span></span>  
 <span data-ttu-id="5cdd2-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5cdd2-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5cdd2-113">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="5cdd2-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5cdd2-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="5cdd2-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5cdd2-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5cdd2-115">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cdd2-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5cdd2-116">See also</span></span>

- [<span data-ttu-id="5cdd2-117">ICorProfilerAssemblyReferenceProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5cdd2-117">ICorProfilerAssemblyReferenceProvider Interface</span></span>](icorprofilerassemblyreferenceprovider-interface.md)
- [<span data-ttu-id="5cdd2-118">GetAssemblyReferences Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5cdd2-118">GetAssemblyReferences Method</span></span>](icorprofilercallback6-getassemblyreferences-method.md)
- [<span data-ttu-id="5cdd2-119">ModuleLoadFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5cdd2-119">ModuleLoadFinished Method</span></span>](icorprofilercallback-moduleloadfinished-method.md)
