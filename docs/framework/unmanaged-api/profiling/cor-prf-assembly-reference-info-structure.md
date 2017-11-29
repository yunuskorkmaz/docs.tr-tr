---
title: "COR_PRF_ASSEMBLY_REFERENCE_INFO Yapısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
ms.assetid: c8c1d916-8d1a-4f82-8128-9fd3732383fc
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 000a338400efa0d70e690f585518304a8b525346
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="corprfassemblyreferenceinfo-structure"></a><span data-ttu-id="2c916-102">COR_PRF_ASSEMBLY_REFERENCE_INFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="2c916-102">COR_PRF_ASSEMBLY_REFERENCE_INFO Structure</span></span>
<span data-ttu-id="2c916-103">[.NET Framework 4.5.2 ve sonraki sürümlerinde desteklenen]</span><span class="sxs-lookup"><span data-stu-id="2c916-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="2c916-104">Ortak dil çalışma zamanı bir derleme başvurusu kapatma ilerlemesi gerçekleştirirken düşünmelisiniz bir derleme başvurusu hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="2c916-104">Provides the common language runtime with information about an assembly reference that it should consider when performing an assembly reference closure walk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c916-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2c916-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="2c916-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="2c916-106">Members</span></span>  
  
|<span data-ttu-id="2c916-107">Üye</span><span class="sxs-lookup"><span data-stu-id="2c916-107">Member</span></span>|<span data-ttu-id="2c916-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2c916-108">Description</span></span>|  
|------------|-----------------|  
|`pbPublicKeyOrToken`|<span data-ttu-id="2c916-109">Ortak anahtar veya derlemenin belirteci için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2c916-109">A pointer to the public key or token of the assembly.</span></span>|  
|`cbPublicKeyOrToken`|<span data-ttu-id="2c916-110">Ortak anahtar belirteci de bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="2c916-110">The number of bytes in the public key or token.</span></span>|  
|`szName`|<span data-ttu-id="2c916-111">Başvurulan derleme adı.</span><span class="sxs-lookup"><span data-stu-id="2c916-111">The name of the assembly that is referenced.</span></span>|  
|`pMetaData`|<span data-ttu-id="2c916-112">Derlemenin meta verilerini gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2c916-112">A pointer to the assembly's metadata.</span></span>|  
|`pbHashValue`|<span data-ttu-id="2c916-113">Karma ikili büyük nesne (BLOB) için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2c916-113">A pointer to a hash binary large object (BLOB).</span></span>|  
|`cbHashValue`|<span data-ttu-id="2c916-114">BLOB karma bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="2c916-114">The number of bytes in the hash BLOB.</span></span>|  
|`dwAssemblyRefFlags`|<span data-ttu-id="2c916-115">Derlemenin bayraklar.</span><span class="sxs-lookup"><span data-stu-id="2c916-115">The assembly's flags.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2c916-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2c916-116">Remarks</span></span>  
 <span data-ttu-id="2c916-117">`COR_PRF_EX_CLAUSE_INFO` Yapısı ortak dil çalışma zamanı, bir derleme başvurusu kapatma ilerlemesi gerçekleştirirken dikkate almanız gereken ek derleme başvuruları bildirir, Profil Oluşturucu tarafından doldurulur.</span><span class="sxs-lookup"><span data-stu-id="2c916-117">The `COR_PRF_EX_CLAUSE_INFO` structure is populated by the profiler when it declares additional assembly references that the common language runtime should consider when performing an assembly reference closure walk.</span></span>  
  
 <span data-ttu-id="2c916-118">Profil Oluşturucu için kaydettiğinde [Icorprofilercallback6::getassemblyreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) geri çağırma yöntemi, çalışma zamanı geçirir, bir işaretçi birlikte yüklenecek derlemenin adını ve yolunu bir [ Icorprofilerassemblyreferenceprovider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) bu yönteme arabirimi nesnesi.</span><span class="sxs-lookup"><span data-stu-id="2c916-118">If the profiler registers for the [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback method, the runtime passes the path and name of the assembly to be loaded, along with a pointer to an [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) interface object to that method.</span></span> <span data-ttu-id="2c916-119">Profil Oluşturucu sonra çağırabilirsiniz [Icorprofilerassemblyreferenceprovider::addassemblyreference](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) yöntemi ile bir `COR_PRF_ASSEMBLY_REFERENCE_INFO` nesne planları belirtilen derlemesinden başvurmak için her hedef derleme için [ Icorprofilercallback6::getassemblyreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="2c916-119">The profiler can then call the [ICorProfilerAssemblyReferenceProvider::AddAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) method with a `COR_PRF_ASSEMBLY_REFERENCE_INFO` object for each target assembly it plans to reference from the assembly specified in the [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c916-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2c916-120">Requirements</span></span>  
 <span data-ttu-id="2c916-121">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c916-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c916-122">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2c916-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2c916-123">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2c916-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2c916-124">**.NET framework sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c916-124">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c916-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2c916-125">See Also</span></span>  
 [<span data-ttu-id="2c916-126">Profil oluşturma yapıları</span><span class="sxs-lookup"><span data-stu-id="2c916-126">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)  
 [<span data-ttu-id="2c916-127">GetAssemblyReferences yöntemi</span><span class="sxs-lookup"><span data-stu-id="2c916-127">GetAssemblyReferences Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)  
 [<span data-ttu-id="2c916-128">AddAssemblyReference yöntemi</span><span class="sxs-lookup"><span data-stu-id="2c916-128">AddAssemblyReference Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)
