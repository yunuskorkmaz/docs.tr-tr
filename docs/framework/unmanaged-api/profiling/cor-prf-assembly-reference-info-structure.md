---
title: COR_PRF_ASSEMBLY_REFERENCE_INFO Yapısı
ms.date: 03/30/2017
dev_langs:
- cpp
ms.assetid: c8c1d916-8d1a-4f82-8128-9fd3732383fc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 380dbe43c09e0be48410431b87d796f502a7012b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54634980"
---
# <a name="corprfassemblyreferenceinfo-structure"></a><span data-ttu-id="cfdda-102">COR_PRF_ASSEMBLY_REFERENCE_INFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="cfdda-102">COR_PRF_ASSEMBLY_REFERENCE_INFO Structure</span></span>
<span data-ttu-id="cfdda-103">[.NET Framework 4.5.2 ve sonraki sürümlerinde desteklenen]</span><span class="sxs-lookup"><span data-stu-id="cfdda-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="cfdda-104">Ortak dil çalışma zamanı bir bütünleştirilmiş kod başvurusu kapanış Yürüme gerçekleştirirken düşünmelisiniz bir bütünleştirilmiş kod başvurusu hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="cfdda-104">Provides the common language runtime with information about an assembly reference that it should consider when performing an assembly reference closure walk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cfdda-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cfdda-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="cfdda-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="cfdda-106">Members</span></span>  
  
|<span data-ttu-id="cfdda-107">Üye</span><span class="sxs-lookup"><span data-stu-id="cfdda-107">Member</span></span>|<span data-ttu-id="cfdda-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cfdda-108">Description</span></span>|  
|------------|-----------------|  
|`pbPublicKeyOrToken`|<span data-ttu-id="cfdda-109">Ortak anahtar veya belirteç derlemenin bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="cfdda-109">A pointer to the public key or token of the assembly.</span></span>|  
|`cbPublicKeyOrToken`|<span data-ttu-id="cfdda-110">Ortak anahtar veya belirteç bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="cfdda-110">The number of bytes in the public key or token.</span></span>|  
|`szName`|<span data-ttu-id="cfdda-111">Başvurulan derlemenin adı.</span><span class="sxs-lookup"><span data-stu-id="cfdda-111">The name of the assembly that is referenced.</span></span>|  
|`pMetaData`|<span data-ttu-id="cfdda-112">Derlemenin meta verilerini bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="cfdda-112">A pointer to the assembly's metadata.</span></span>|  
|`pbHashValue`|<span data-ttu-id="cfdda-113">Karma ikili büyük nesne (BLOB) için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="cfdda-113">A pointer to a hash binary large object (BLOB).</span></span>|  
|`cbHashValue`|<span data-ttu-id="cfdda-114">BLOB karma bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="cfdda-114">The number of bytes in the hash BLOB.</span></span>|  
|`dwAssemblyRefFlags`|<span data-ttu-id="cfdda-115">Derlemenin bayraklar.</span><span class="sxs-lookup"><span data-stu-id="cfdda-115">The assembly's flags.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cfdda-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cfdda-116">Remarks</span></span>  
 <span data-ttu-id="cfdda-117">`COR_PRF_EX_CLAUSE_INFO` Yapısı, ortak dil çalışma zamanı, bir derleme başvurusu kapanış Yürüme yaparken dikkate almanız gereken ek derleme başvurularını bildirir, Profil Oluşturucu tarafından doldurulur.</span><span class="sxs-lookup"><span data-stu-id="cfdda-117">The `COR_PRF_EX_CLAUSE_INFO` structure is populated by the profiler when it declares additional assembly references that the common language runtime should consider when performing an assembly reference closure walk.</span></span>  
  
 <span data-ttu-id="cfdda-118">Profil Oluşturucu kayıtlıysa [Icorprofilercallback6::getassemblyreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) geri çağırma yöntemi, çalışma zamanı geçirir, bir işaretçi ile birlikte yüklenecek derlemenin adı ve yolunu bir [ Icorprofilerassemblyreferenceprovider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) bu yönteme arabirimi nesnesi.</span><span class="sxs-lookup"><span data-stu-id="cfdda-118">If the profiler registers for the [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback method, the runtime passes the path and name of the assembly to be loaded, along with a pointer to an [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) interface object to that method.</span></span> <span data-ttu-id="cfdda-119">Profil Oluşturucu ardından çağırabilirsiniz [Icorprofilerassemblyreferenceprovider::addassemblyreference](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) yöntemi ile bir `COR_PRF_ASSEMBLY_REFERENCE_INFO` her hedef derleme planları içinde belirtilen derleme başvuru yapmak için nesne [ Icorprofilercallback6::getassemblyreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="cfdda-119">The profiler can then call the [ICorProfilerAssemblyReferenceProvider::AddAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) method with a `COR_PRF_ASSEMBLY_REFERENCE_INFO` object for each target assembly it plans to reference from the assembly specified in the [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cfdda-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cfdda-120">Requirements</span></span>  
 <span data-ttu-id="cfdda-121">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cfdda-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cfdda-122">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="cfdda-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cfdda-123">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cfdda-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cfdda-124">**.NET framework sürümleri:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cfdda-124">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfdda-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cfdda-125">See also</span></span>
- [<span data-ttu-id="cfdda-126">Profil Oluşturma Yapıları</span><span class="sxs-lookup"><span data-stu-id="cfdda-126">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
- [<span data-ttu-id="cfdda-127">GetAssemblyReferences Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cfdda-127">GetAssemblyReferences Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)
- [<span data-ttu-id="cfdda-128">AddAssemblyReference Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cfdda-128">AddAssemblyReference Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)
