---
title: ASSEMBLYMETADATA Yapısı
ms.date: 03/30/2017
api_name:
- ASSEMBLYMETADATA
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ASSEMBLYMETADATA
helpviewer_keywords:
- ASSEMBLYMETADATA structure [.NET Framework metadata]
ms.assetid: 1af98e57-9145-4d35-bb78-77d1da7c91a5
topic_type:
- apiref
ms.openlocfilehash: 24ec1f7d553a59425f7eb02af8e91010d940eb07
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444260"
---
# <a name="assemblymetadata-structure"></a><span data-ttu-id="1ae48-102">ASSEMBLYMETADATA Yapısı</span><span class="sxs-lookup"><span data-stu-id="1ae48-102">ASSEMBLYMETADATA Structure</span></span>
<span data-ttu-id="1ae48-103">Başvurulan derleme hakkında, sürümü ve yerel ayarlar, işlemciler ve işletim sistemleri için destek düzeyi dahil olmak üzere bilgiler içerir.</span><span class="sxs-lookup"><span data-stu-id="1ae48-103">Contains information about the referenced assembly, including its version and its level of support for locales, processors, and operating systems.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ae48-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1ae48-104">Syntax</span></span>  
  
```cpp  
typedef struct {  
    USHORT  usMajorVersion;  
    USHORT  usMinorVersion;  
    USHORT  usBuildNumber;  
    USHORT  usRevisionNumber;  
    LPWSTR  szLocale;  
    ULONG   cbLocale;  
    DWORD*  rdwProcessor[];  
    ULONG   ulProcessor  
    OSINFO* rOS[];  
    ULONG   ulOS;  
} ASSEMBLYMETADATA;  
```  
  
## <a name="members"></a><span data-ttu-id="1ae48-105">Üyeleri</span><span class="sxs-lookup"><span data-stu-id="1ae48-105">Members</span></span>  
  
|<span data-ttu-id="1ae48-106">Üyesi</span><span class="sxs-lookup"><span data-stu-id="1ae48-106">Member</span></span>|<span data-ttu-id="1ae48-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1ae48-107">Description</span></span>|  
|------------|-----------------|  
|`usMajorVersion`|<span data-ttu-id="1ae48-108">Başvurulan derlemenin ana sürüm numarası.</span><span class="sxs-lookup"><span data-stu-id="1ae48-108">The major version number of the referenced assembly.</span></span> <span data-ttu-id="1ae48-109">Bu değer sıfır olamaz.</span><span class="sxs-lookup"><span data-stu-id="1ae48-109">This value cannot be zero.</span></span> <span data-ttu-id="1ae48-110">Tüm `usMajorVersion` bitleri ayarlanırsa, ana sürüm belirtilmez.</span><span class="sxs-lookup"><span data-stu-id="1ae48-110">If all the bits of `usMajorVersion` are set, the major version is not specified.</span></span>|  
|`usMinorVersion`|<span data-ttu-id="1ae48-111">Başvurulan derlemenin ikincil sürüm numarası.</span><span class="sxs-lookup"><span data-stu-id="1ae48-111">The minor version number of the referenced assembly.</span></span> <span data-ttu-id="1ae48-112">Bu değer sıfır olamaz.</span><span class="sxs-lookup"><span data-stu-id="1ae48-112">This value cannot be zero.</span></span> <span data-ttu-id="1ae48-113">Tüm `usMinorVersion` bitleri ayarlandıysa, ikincil sürüm belirtilmez.</span><span class="sxs-lookup"><span data-stu-id="1ae48-113">If all the bits of `usMinorVersion` are set, the minor version is not specified.</span></span>|  
|`usBuildNumber`|<span data-ttu-id="1ae48-114">Başvurulan derlemenin yapı numarası.</span><span class="sxs-lookup"><span data-stu-id="1ae48-114">The build number of the referenced assembly.</span></span> <span data-ttu-id="1ae48-115">Bu değer sıfır olamaz.</span><span class="sxs-lookup"><span data-stu-id="1ae48-115">This value cannot be zero.</span></span> <span data-ttu-id="1ae48-116">Tüm `usBuildNumber` bitleri ayarlandıysa, derleme numarası belirtilmez.</span><span class="sxs-lookup"><span data-stu-id="1ae48-116">If all the bits of `usBuildNumber` are set, the build number is not specified.</span></span>|  
|`usRevisionNumber`|<span data-ttu-id="1ae48-117">Başvurulan derlemenin düzeltme numarası.</span><span class="sxs-lookup"><span data-stu-id="1ae48-117">The revision number of the referenced assembly.</span></span> <span data-ttu-id="1ae48-118">Bu değer sıfır olamaz.</span><span class="sxs-lookup"><span data-stu-id="1ae48-118">This value cannot be zero.</span></span> <span data-ttu-id="1ae48-119">Tüm `usRevisionNumber` bitleri ayarlandıysa, düzeltme numarası belirtilmez.</span><span class="sxs-lookup"><span data-stu-id="1ae48-119">If all the bits of `usRevisionNumber` are set, the revision number is not specified.</span></span>|  
|`szLocale`|<span data-ttu-id="1ae48-120">RFC1766 belirtimine uyan, başvurulan derleme tarafından desteklenen yerel ayarları belirten, noktalı virgülle ayrılmış yerel ayar adlarının listesi.</span><span class="sxs-lookup"><span data-stu-id="1ae48-120">A list of locale names conforming to the RFC1766 specification, separated by semicolons, specifying the locales supported by the referenced assembly.</span></span> <span data-ttu-id="1ae48-121">Null değer yerel ayar bağımsızlığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1ae48-121">A null value indicates locale independence.</span></span> <span data-ttu-id="1ae48-122">**Note:**  .NET Framework sürüm 1,0 ' de birden fazla yerel ayar belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="1ae48-122">**Note:**  In the .NET Framework version 1.0 you cannot specify more than one locale.</span></span>|  
|`cbLocale`|<span data-ttu-id="1ae48-123">`szLocale`geniş karakterdeki boyut.</span><span class="sxs-lookup"><span data-stu-id="1ae48-123">The size in wide characters of `szLocale`.</span></span>|  
|`rdwProcessor`|<span data-ttu-id="1ae48-124">Başvurulan derleme tarafından desteklenen işlemci türleri için Winnt. h içinde tanımlanan bir dizi tanımlayıcıdır.</span><span class="sxs-lookup"><span data-stu-id="1ae48-124">An array of identifiers, as defined in Winnt.h, for the processor types that are supported by the referenced assembly.</span></span> <span data-ttu-id="1ae48-125">NULL değer işlemci bağımsızlığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1ae48-125">A NULL value indicates processor independence.</span></span>|  
|`ulProcessor`|<span data-ttu-id="1ae48-126">`rdwProcessor` dizisinin uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="1ae48-126">The length of the `rdwProcessor` array.</span></span>|  
|`rOS`|<span data-ttu-id="1ae48-127">Başvurulan derleme tarafından desteklenen işletim sistemlerini belirten bir [OSINFO](../../../../docs/framework/unmanaged-api/metadata/osinfo-structure.md) örnekleri dizisi.</span><span class="sxs-lookup"><span data-stu-id="1ae48-127">An array of [OSINFO](../../../../docs/framework/unmanaged-api/metadata/osinfo-structure.md) instances specifying the operating systems that are supported by the referenced assembly.</span></span> <span data-ttu-id="1ae48-128">NULL değer, işletim sistemi bağımsızlığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1ae48-128">A NULL value indicates operating-system independence.</span></span>|  
|`ulOS`|<span data-ttu-id="1ae48-129">`rOS` dizisinin uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="1ae48-129">The length of the `rOS` array.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1ae48-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1ae48-130">Requirements</span></span>  
 <span data-ttu-id="1ae48-131">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1ae48-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ae48-132">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="1ae48-132">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1ae48-133">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="1ae48-133">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1ae48-134">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ae48-134">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ae48-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1ae48-135">See also</span></span>

- [<span data-ttu-id="1ae48-136">Meta Veri Yapıları</span><span class="sxs-lookup"><span data-stu-id="1ae48-136">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [<span data-ttu-id="1ae48-137">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1ae48-137">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [<span data-ttu-id="1ae48-138">OSINFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="1ae48-138">OSINFO Structure</span></span>](../../../../docs/framework/unmanaged-api/metadata/osinfo-structure.md)
