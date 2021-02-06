---
description: 'Daha fazla bilgi edinin: COR_PRF_ASSEMBLY_REFERENCE_INFO yapısı'
title: COR_PRF_ASSEMBLY_REFERENCE_INFO Yapısı
ms.date: 03/30/2017
dev_langs:
- cpp
ms.assetid: c8c1d916-8d1a-4f82-8128-9fd3732383fc
ms.openlocfilehash: fc384e0a302c83af510deefc6f9f3b9cd5a2f77f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99649227"
---
# <a name="cor_prf_assembly_reference_info-structure"></a><span data-ttu-id="dfaa6-103">COR_PRF_ASSEMBLY_REFERENCE_INFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="dfaa6-103">COR_PRF_ASSEMBLY_REFERENCE_INFO Structure</span></span>

<span data-ttu-id="dfaa6-104">[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="dfaa6-104">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="dfaa6-105">Ortak dil çalışma zamanını, bir derleme başvurusu kapatma ilerlemesi gerçekleştirirken göz önünde bulundurmanız gereken bir derleme başvurusu hakkındaki bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="dfaa6-105">Provides the common language runtime with information about an assembly reference that it should consider when performing an assembly reference closure walk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dfaa6-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="dfaa6-106">Syntax</span></span>  
  
```cpp  
typedef struct _COR_PRF_ASSEMBLY_REFERENCE_INFO {  
    void* pbPublicKeyOrToken;  
    ULONG cbPublicKeyOrToken;  
    LPCWSTR szName;  
    ASSEMBLYMETADATA* pMetaData;  
    void* pbHashValue;  
    ULONG cbHashValue;  
    DWORD dwAssemblyRefFlags;  
} COR_PRF_EX_CLAUSE_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="dfaa6-107">Üyeler</span><span class="sxs-lookup"><span data-stu-id="dfaa6-107">Members</span></span>  
  
|<span data-ttu-id="dfaa6-108">Üye</span><span class="sxs-lookup"><span data-stu-id="dfaa6-108">Member</span></span>|<span data-ttu-id="dfaa6-109">Description</span><span class="sxs-lookup"><span data-stu-id="dfaa6-109">Description</span></span>|  
|------------|-----------------|  
|`pbPublicKeyOrToken`|<span data-ttu-id="dfaa6-110">Derleme için ortak anahtar veya belirtece yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="dfaa6-110">A pointer to the public key or token of the assembly.</span></span>|  
|`cbPublicKeyOrToken`|<span data-ttu-id="dfaa6-111">Ortak anahtar veya belirteçteki bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="dfaa6-111">The number of bytes in the public key or token.</span></span>|  
|`szName`|<span data-ttu-id="dfaa6-112">Başvurulan derlemenin adı.</span><span class="sxs-lookup"><span data-stu-id="dfaa6-112">The name of the assembly that is referenced.</span></span>|  
|`pMetaData`|<span data-ttu-id="dfaa6-113">Derlemenin meta verilerine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="dfaa6-113">A pointer to the assembly's metadata.</span></span>|  
|`pbHashValue`|<span data-ttu-id="dfaa6-114">Karma ikili büyük nesne (BLOB) için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="dfaa6-114">A pointer to a hash binary large object (BLOB).</span></span>|  
|`cbHashValue`|<span data-ttu-id="dfaa6-115">Karma BLOBUN içindeki bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="dfaa6-115">The number of bytes in the hash BLOB.</span></span>|  
|`dwAssemblyRefFlags`|<span data-ttu-id="dfaa6-116">Derlemenin bayrakları.</span><span class="sxs-lookup"><span data-stu-id="dfaa6-116">The assembly's flags.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dfaa6-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dfaa6-117">Remarks</span></span>  

 <span data-ttu-id="dfaa6-118">`COR_PRF_EX_CLAUSE_INFO`Yapı, bir derleme başvurusu kapatma ilerlemesi gerçekleştirirken ortak dil çalışma zamanının göz önünde bulundurmanız gereken ek derleme başvuruları bildirirken profil oluşturucu tarafından doldurulur.</span><span class="sxs-lookup"><span data-stu-id="dfaa6-118">The `COR_PRF_EX_CLAUSE_INFO` structure is populated by the profiler when it declares additional assembly references that the common language runtime should consider when performing an assembly reference closure walk.</span></span>  
  
 <span data-ttu-id="dfaa6-119">Profil Oluşturucu [ICorProfilerCallback6:: GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) geri çağırma metoduna kaydolduktan sonra, çalışma zamanı yüklenecek derlemenin yolunu ve adını, bu yönteme bir [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) arabirim nesnesine yönelik bir işaretçi ile geçirir.</span><span class="sxs-lookup"><span data-stu-id="dfaa6-119">If the profiler registers for the [ICorProfilerCallback6::GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) callback method, the runtime passes the path and name of the assembly to be loaded, along with a pointer to an [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) interface object to that method.</span></span> <span data-ttu-id="dfaa6-120">Profil Oluşturucu daha sonra [ICorProfilerAssemblyReferenceProvider:: AddAssemblyReference](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) metodunu, `COR_PRF_ASSEMBLY_REFERENCE_INFO` [ICorProfilerCallback6:: GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) geri aramasında belirtilen derlemeden başvuruyu planlıyor olan her hedef derleme için bir nesneyle çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="dfaa6-120">The profiler can then call the [ICorProfilerAssemblyReferenceProvider::AddAssemblyReference](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) method with a `COR_PRF_ASSEMBLY_REFERENCE_INFO` object for each target assembly it plans to reference from the assembly specified in the [ICorProfilerCallback6::GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dfaa6-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dfaa6-121">Requirements</span></span>  

 <span data-ttu-id="dfaa6-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dfaa6-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dfaa6-123">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="dfaa6-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="dfaa6-124">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="dfaa6-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dfaa6-125">**.NET Framework sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dfaa6-125">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfaa6-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dfaa6-126">See also</span></span>

- [<span data-ttu-id="dfaa6-127">Profil Oluşturma Yapıları</span><span class="sxs-lookup"><span data-stu-id="dfaa6-127">Profiling Structures</span></span>](profiling-structures.md)
- [<span data-ttu-id="dfaa6-128">GetAssemblyReferences Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dfaa6-128">GetAssemblyReferences Method</span></span>](icorprofilercallback6-getassemblyreferences-method.md)
- [<span data-ttu-id="dfaa6-129">AddAssemblyReference Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dfaa6-129">AddAssemblyReference Method</span></span>](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)
