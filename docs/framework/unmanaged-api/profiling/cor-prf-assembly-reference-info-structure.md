---
title: COR_PRF_ASSEMBLY_REFERENCE_INFO Yapısı
ms.date: 03/30/2017
dev_langs:
- cpp
ms.assetid: c8c1d916-8d1a-4f82-8128-9fd3732383fc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 99fa1cc05ee583cf1bd59235fcd9821d1c92d21f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59101438"
---
# <a name="corprfassemblyreferenceinfo-structure"></a><span data-ttu-id="1f924-102">COR_PRF_ASSEMBLY_REFERENCE_INFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="1f924-102">COR_PRF_ASSEMBLY_REFERENCE_INFO Structure</span></span>
<span data-ttu-id="1f924-103">[.NET Framework 4.5.2 ve sonraki sürümlerinde desteklenen]</span><span class="sxs-lookup"><span data-stu-id="1f924-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="1f924-104">Ortak dil çalışma zamanı bir bütünleştirilmiş kod başvurusu kapanış Yürüme gerçekleştirirken düşünmelisiniz bir bütünleştirilmiş kod başvurusu hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="1f924-104">Provides the common language runtime with information about an assembly reference that it should consider when performing an assembly reference closure walk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f924-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1f924-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="1f924-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="1f924-106">Members</span></span>  
  
|<span data-ttu-id="1f924-107">Üye</span><span class="sxs-lookup"><span data-stu-id="1f924-107">Member</span></span>|<span data-ttu-id="1f924-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1f924-108">Description</span></span>|  
|------------|-----------------|  
|`pbPublicKeyOrToken`|<span data-ttu-id="1f924-109">Ortak anahtar veya belirteç derlemenin bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1f924-109">A pointer to the public key or token of the assembly.</span></span>|  
|`cbPublicKeyOrToken`|<span data-ttu-id="1f924-110">Ortak anahtar veya belirteç bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="1f924-110">The number of bytes in the public key or token.</span></span>|  
|`szName`|<span data-ttu-id="1f924-111">Başvurulan derlemenin adı.</span><span class="sxs-lookup"><span data-stu-id="1f924-111">The name of the assembly that is referenced.</span></span>|  
|`pMetaData`|<span data-ttu-id="1f924-112">Derlemenin meta verilerini bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1f924-112">A pointer to the assembly's metadata.</span></span>|  
|`pbHashValue`|<span data-ttu-id="1f924-113">Karma ikili büyük nesne (BLOB) için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1f924-113">A pointer to a hash binary large object (BLOB).</span></span>|  
|`cbHashValue`|<span data-ttu-id="1f924-114">BLOB karma bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="1f924-114">The number of bytes in the hash BLOB.</span></span>|  
|`dwAssemblyRefFlags`|<span data-ttu-id="1f924-115">Derlemenin bayraklar.</span><span class="sxs-lookup"><span data-stu-id="1f924-115">The assembly's flags.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1f924-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1f924-116">Remarks</span></span>  
 <span data-ttu-id="1f924-117">`COR_PRF_EX_CLAUSE_INFO` Yapısı, ortak dil çalışma zamanı, bir derleme başvurusu kapanış Yürüme yaparken dikkate almanız gereken ek derleme başvurularını bildirir, Profil Oluşturucu tarafından doldurulur.</span><span class="sxs-lookup"><span data-stu-id="1f924-117">The `COR_PRF_EX_CLAUSE_INFO` structure is populated by the profiler when it declares additional assembly references that the common language runtime should consider when performing an assembly reference closure walk.</span></span>  
  
 <span data-ttu-id="1f924-118">Profil Oluşturucu kayıtlıysa [Icorprofilercallback6::getassemblyreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) geri çağırma yöntemi, çalışma zamanı geçirir, bir işaretçi ile birlikte yüklenecek derlemenin adı ve yolunu bir [ Icorprofilerassemblyreferenceprovider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) bu yönteme arabirimi nesnesi.</span><span class="sxs-lookup"><span data-stu-id="1f924-118">If the profiler registers for the [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback method, the runtime passes the path and name of the assembly to be loaded, along with a pointer to an [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) interface object to that method.</span></span> <span data-ttu-id="1f924-119">Profil Oluşturucu ardından çağırabilirsiniz [Icorprofilerassemblyreferenceprovider::addassemblyreference](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) yöntemi ile bir `COR_PRF_ASSEMBLY_REFERENCE_INFO` her hedef derleme planları içinde belirtilen derleme başvuru yapmak için nesne [ Icorprofilercallback6::getassemblyreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="1f924-119">The profiler can then call the [ICorProfilerAssemblyReferenceProvider::AddAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) method with a `COR_PRF_ASSEMBLY_REFERENCE_INFO` object for each target assembly it plans to reference from the assembly specified in the [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f924-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1f924-120">Requirements</span></span>  
 <span data-ttu-id="1f924-121">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1f924-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f924-122">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1f924-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1f924-123">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1f924-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1f924-124">**.NET framework sürümleri:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f924-124">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f924-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1f924-125">See also</span></span>

- [<span data-ttu-id="1f924-126">Profil Oluşturma Yapıları</span><span class="sxs-lookup"><span data-stu-id="1f924-126">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
- [<span data-ttu-id="1f924-127">GetAssemblyReferences Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1f924-127">GetAssemblyReferences Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)
- [<span data-ttu-id="1f924-128">AddAssemblyReference Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1f924-128">AddAssemblyReference Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)
