---
title: COR_PRF_ASSEMBLY_REFERENCE_INFO Yapısı
ms.date: 03/30/2017
dev_langs:
- cpp
ms.assetid: c8c1d916-8d1a-4f82-8128-9fd3732383fc
ms.openlocfilehash: 7c7d447afcb5a8617aa92212f3325719d5f43bf5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95718624"
---
# <a name="cor_prf_assembly_reference_info-structure"></a><span data-ttu-id="9c72e-102">COR_PRF_ASSEMBLY_REFERENCE_INFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="9c72e-102">COR_PRF_ASSEMBLY_REFERENCE_INFO Structure</span></span>

<span data-ttu-id="9c72e-103">[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="9c72e-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="9c72e-104">Ortak dil çalışma zamanını, bir derleme başvurusu kapatma ilerlemesi gerçekleştirirken göz önünde bulundurmanız gereken bir derleme başvurusu hakkındaki bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="9c72e-104">Provides the common language runtime with information about an assembly reference that it should consider when performing an assembly reference closure walk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c72e-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="9c72e-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="9c72e-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="9c72e-106">Members</span></span>  
  
|<span data-ttu-id="9c72e-107">Üye</span><span class="sxs-lookup"><span data-stu-id="9c72e-107">Member</span></span>|<span data-ttu-id="9c72e-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9c72e-108">Description</span></span>|  
|------------|-----------------|  
|`pbPublicKeyOrToken`|<span data-ttu-id="9c72e-109">Derleme için ortak anahtar veya belirtece yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9c72e-109">A pointer to the public key or token of the assembly.</span></span>|  
|`cbPublicKeyOrToken`|<span data-ttu-id="9c72e-110">Ortak anahtar veya belirteçteki bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="9c72e-110">The number of bytes in the public key or token.</span></span>|  
|`szName`|<span data-ttu-id="9c72e-111">Başvurulan derlemenin adı.</span><span class="sxs-lookup"><span data-stu-id="9c72e-111">The name of the assembly that is referenced.</span></span>|  
|`pMetaData`|<span data-ttu-id="9c72e-112">Derlemenin meta verilerine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9c72e-112">A pointer to the assembly's metadata.</span></span>|  
|`pbHashValue`|<span data-ttu-id="9c72e-113">Karma ikili büyük nesne (BLOB) için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9c72e-113">A pointer to a hash binary large object (BLOB).</span></span>|  
|`cbHashValue`|<span data-ttu-id="9c72e-114">Karma BLOBUN içindeki bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="9c72e-114">The number of bytes in the hash BLOB.</span></span>|  
|`dwAssemblyRefFlags`|<span data-ttu-id="9c72e-115">Derlemenin bayrakları.</span><span class="sxs-lookup"><span data-stu-id="9c72e-115">The assembly's flags.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9c72e-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9c72e-116">Remarks</span></span>  

 <span data-ttu-id="9c72e-117">`COR_PRF_EX_CLAUSE_INFO`Yapı, bir derleme başvurusu kapatma ilerlemesi gerçekleştirirken ortak dil çalışma zamanının göz önünde bulundurmanız gereken ek derleme başvuruları bildirirken profil oluşturucu tarafından doldurulur.</span><span class="sxs-lookup"><span data-stu-id="9c72e-117">The `COR_PRF_EX_CLAUSE_INFO` structure is populated by the profiler when it declares additional assembly references that the common language runtime should consider when performing an assembly reference closure walk.</span></span>  
  
 <span data-ttu-id="9c72e-118">Profil Oluşturucu [ICorProfilerCallback6:: GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) geri çağırma metoduna kaydolduktan sonra, çalışma zamanı yüklenecek derlemenin yolunu ve adını, bu yönteme bir [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) arabirim nesnesine yönelik bir işaretçi ile geçirir.</span><span class="sxs-lookup"><span data-stu-id="9c72e-118">If the profiler registers for the [ICorProfilerCallback6::GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) callback method, the runtime passes the path and name of the assembly to be loaded, along with a pointer to an [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) interface object to that method.</span></span> <span data-ttu-id="9c72e-119">Profil Oluşturucu daha sonra [ICorProfilerAssemblyReferenceProvider:: AddAssemblyReference](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) metodunu, `COR_PRF_ASSEMBLY_REFERENCE_INFO` [ICorProfilerCallback6:: GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) geri aramasında belirtilen derlemeden başvuruyu planlıyor olan her hedef derleme için bir nesneyle çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="9c72e-119">The profiler can then call the [ICorProfilerAssemblyReferenceProvider::AddAssemblyReference](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) method with a `COR_PRF_ASSEMBLY_REFERENCE_INFO` object for each target assembly it plans to reference from the assembly specified in the [ICorProfilerCallback6::GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c72e-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9c72e-120">Requirements</span></span>  

 <span data-ttu-id="9c72e-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9c72e-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c72e-122">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="9c72e-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9c72e-123">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="9c72e-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9c72e-124">**.NET Framework sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c72e-124">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c72e-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9c72e-125">See also</span></span>

- [<span data-ttu-id="9c72e-126">Profil Oluşturma Yapıları</span><span class="sxs-lookup"><span data-stu-id="9c72e-126">Profiling Structures</span></span>](profiling-structures.md)
- [<span data-ttu-id="9c72e-127">GetAssemblyReferences Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9c72e-127">GetAssemblyReferences Method</span></span>](icorprofilercallback6-getassemblyreferences-method.md)
- [<span data-ttu-id="9c72e-128">AddAssemblyReference Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9c72e-128">AddAssemblyReference Method</span></span>](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)
