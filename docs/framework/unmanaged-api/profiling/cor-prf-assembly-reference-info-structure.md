---
title: COR_PRF_ASSEMBLY_REFERENCE_INFO Yapısı
ms.date: 03/30/2017
dev_langs:
- cpp
ms.assetid: c8c1d916-8d1a-4f82-8128-9fd3732383fc
ms.openlocfilehash: 4fdc8e1074bf45de3a8ab85500a85b124ce34fa1
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867340"
---
# <a name="cor_prf_assembly_reference_info-structure"></a><span data-ttu-id="4d59b-102">COR_PRF_ASSEMBLY_REFERENCE_INFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="4d59b-102">COR_PRF_ASSEMBLY_REFERENCE_INFO Structure</span></span>
<span data-ttu-id="4d59b-103">[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="4d59b-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="4d59b-104">Ortak dil çalışma zamanını, bir derleme başvurusu kapatma ilerlemesi gerçekleştirirken göz önünde bulundurmanız gereken bir derleme başvurusu hakkındaki bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="4d59b-104">Provides the common language runtime with information about an assembly reference that it should consider when performing an assembly reference closure walk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d59b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4d59b-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="4d59b-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="4d59b-106">Members</span></span>  
  
|<span data-ttu-id="4d59b-107">Üye</span><span class="sxs-lookup"><span data-stu-id="4d59b-107">Member</span></span>|<span data-ttu-id="4d59b-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4d59b-108">Description</span></span>|  
|------------|-----------------|  
|`pbPublicKeyOrToken`|<span data-ttu-id="4d59b-109">Derleme için ortak anahtar veya belirtece yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4d59b-109">A pointer to the public key or token of the assembly.</span></span>|  
|`cbPublicKeyOrToken`|<span data-ttu-id="4d59b-110">Ortak anahtar veya belirteçteki bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="4d59b-110">The number of bytes in the public key or token.</span></span>|  
|`szName`|<span data-ttu-id="4d59b-111">Başvurulan derlemenin adı.</span><span class="sxs-lookup"><span data-stu-id="4d59b-111">The name of the assembly that is referenced.</span></span>|  
|`pMetaData`|<span data-ttu-id="4d59b-112">Derlemenin meta verilerine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4d59b-112">A pointer to the assembly's metadata.</span></span>|  
|`pbHashValue`|<span data-ttu-id="4d59b-113">Karma ikili büyük nesne (BLOB) için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4d59b-113">A pointer to a hash binary large object (BLOB).</span></span>|  
|`cbHashValue`|<span data-ttu-id="4d59b-114">Karma BLOBUN içindeki bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="4d59b-114">The number of bytes in the hash BLOB.</span></span>|  
|`dwAssemblyRefFlags`|<span data-ttu-id="4d59b-115">Derlemenin bayrakları.</span><span class="sxs-lookup"><span data-stu-id="4d59b-115">The assembly's flags.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4d59b-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4d59b-116">Remarks</span></span>  
 <span data-ttu-id="4d59b-117">`COR_PRF_EX_CLAUSE_INFO` yapısı, ortak dil çalışma zamanının bir derleme başvuru kapanışı yürüirken dikkate alınması gereken ek derleme başvurularını bildirdiği zaman profil oluşturucu tarafından doldurulur.</span><span class="sxs-lookup"><span data-stu-id="4d59b-117">The `COR_PRF_EX_CLAUSE_INFO` structure is populated by the profiler when it declares additional assembly references that the common language runtime should consider when performing an assembly reference closure walk.</span></span>  
  
 <span data-ttu-id="4d59b-118">Profil Oluşturucu [ICorProfilerCallback6:: GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) geri çağırma metoduna kaydolduktan sonra, çalışma zamanı yüklenecek derlemenin yolunu ve adını, bu yönteme bir [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) arabirim nesnesine yönelik bir işaretçi ile geçirir.</span><span class="sxs-lookup"><span data-stu-id="4d59b-118">If the profiler registers for the [ICorProfilerCallback6::GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) callback method, the runtime passes the path and name of the assembly to be loaded, along with a pointer to an [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) interface object to that method.</span></span> <span data-ttu-id="4d59b-119">Profil Oluşturucu daha sonra [ICorProfilerAssemblyReferenceProvider:: AddAssemblyReference](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) yöntemini, [ICorProfilerCallback6:: GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) geri aramasında belirtilen derlemeden başvuruyu planlıyor olan her bir hedef derleme için bir `COR_PRF_ASSEMBLY_REFERENCE_INFO` nesnesi ile çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="4d59b-119">The profiler can then call the [ICorProfilerAssemblyReferenceProvider::AddAssemblyReference](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) method with a `COR_PRF_ASSEMBLY_REFERENCE_INFO` object for each target assembly it plans to reference from the assembly specified in the [ICorProfilerCallback6::GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d59b-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4d59b-120">Requirements</span></span>  
 <span data-ttu-id="4d59b-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4d59b-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d59b-122">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="4d59b-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4d59b-123">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="4d59b-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4d59b-124">**.NET Framework sürümleri:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d59b-124">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d59b-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4d59b-125">See also</span></span>

- [<span data-ttu-id="4d59b-126">Profil Oluşturma Yapıları</span><span class="sxs-lookup"><span data-stu-id="4d59b-126">Profiling Structures</span></span>](profiling-structures.md)
- [<span data-ttu-id="4d59b-127">GetAssemblyReferences Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4d59b-127">GetAssemblyReferences Method</span></span>](icorprofilercallback6-getassemblyreferences-method.md)
- [<span data-ttu-id="4d59b-128">AddAssemblyReference Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4d59b-128">AddAssemblyReference Method</span></span>](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)
