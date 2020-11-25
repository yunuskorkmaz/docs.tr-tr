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
ms.openlocfilehash: 8071c3f43775975de37e3255582b6fc8f13f7de3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732794"
---
# <a name="assemblymetadata-structure"></a><span data-ttu-id="c7abd-102">ASSEMBLYMETADATA Yapısı</span><span class="sxs-lookup"><span data-stu-id="c7abd-102">ASSEMBLYMETADATA Structure</span></span>

<span data-ttu-id="c7abd-103">Başvurulan derleme hakkında, sürümü ve yerel ayarlar, işlemciler ve işletim sistemleri için destek düzeyi dahil olmak üzere bilgiler içerir.</span><span class="sxs-lookup"><span data-stu-id="c7abd-103">Contains information about the referenced assembly, including its version and its level of support for locales, processors, and operating systems.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7abd-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="c7abd-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="c7abd-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="c7abd-105">Members</span></span>  
  
|<span data-ttu-id="c7abd-106">Üye</span><span class="sxs-lookup"><span data-stu-id="c7abd-106">Member</span></span>|<span data-ttu-id="c7abd-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c7abd-107">Description</span></span>|  
|------------|-----------------|  
|`usMajorVersion`|<span data-ttu-id="c7abd-108">Başvurulan derlemenin ana sürüm numarası.</span><span class="sxs-lookup"><span data-stu-id="c7abd-108">The major version number of the referenced assembly.</span></span> <span data-ttu-id="c7abd-109">Bu değer sıfır olamaz.</span><span class="sxs-lookup"><span data-stu-id="c7abd-109">This value cannot be zero.</span></span> <span data-ttu-id="c7abd-110">Tüm bitleri `usMajorVersion` ayarlandıysa, ana sürüm belirtilmez.</span><span class="sxs-lookup"><span data-stu-id="c7abd-110">If all the bits of `usMajorVersion` are set, the major version is not specified.</span></span>|  
|`usMinorVersion`|<span data-ttu-id="c7abd-111">Başvurulan derlemenin ikincil sürüm numarası.</span><span class="sxs-lookup"><span data-stu-id="c7abd-111">The minor version number of the referenced assembly.</span></span> <span data-ttu-id="c7abd-112">Bu değer sıfır olamaz.</span><span class="sxs-lookup"><span data-stu-id="c7abd-112">This value cannot be zero.</span></span> <span data-ttu-id="c7abd-113">Tüm bitleri `usMinorVersion` ayarlandıysa, ikincil sürüm belirtilmez.</span><span class="sxs-lookup"><span data-stu-id="c7abd-113">If all the bits of `usMinorVersion` are set, the minor version is not specified.</span></span>|  
|`usBuildNumber`|<span data-ttu-id="c7abd-114">Başvurulan derlemenin yapı numarası.</span><span class="sxs-lookup"><span data-stu-id="c7abd-114">The build number of the referenced assembly.</span></span> <span data-ttu-id="c7abd-115">Bu değer sıfır olamaz.</span><span class="sxs-lookup"><span data-stu-id="c7abd-115">This value cannot be zero.</span></span> <span data-ttu-id="c7abd-116">Tüm bitleri `usBuildNumber` ayarlandıysa, yapı numarası belirtilmez.</span><span class="sxs-lookup"><span data-stu-id="c7abd-116">If all the bits of `usBuildNumber` are set, the build number is not specified.</span></span>|  
|`usRevisionNumber`|<span data-ttu-id="c7abd-117">Başvurulan derlemenin düzeltme numarası.</span><span class="sxs-lookup"><span data-stu-id="c7abd-117">The revision number of the referenced assembly.</span></span> <span data-ttu-id="c7abd-118">Bu değer sıfır olamaz.</span><span class="sxs-lookup"><span data-stu-id="c7abd-118">This value cannot be zero.</span></span> <span data-ttu-id="c7abd-119">Tüm bitleri `usRevisionNumber` ayarlandıysa, düzeltme numarası belirtilmez.</span><span class="sxs-lookup"><span data-stu-id="c7abd-119">If all the bits of `usRevisionNumber` are set, the revision number is not specified.</span></span>|  
|`szLocale`|<span data-ttu-id="c7abd-120">RFC1766 belirtimine uyan, başvurulan derleme tarafından desteklenen yerel ayarları belirten, noktalı virgülle ayrılmış yerel ayar adlarının listesi.</span><span class="sxs-lookup"><span data-stu-id="c7abd-120">A list of locale names conforming to the RFC1766 specification, separated by semicolons, specifying the locales supported by the referenced assembly.</span></span> <span data-ttu-id="c7abd-121">Null değer yerel ayar bağımsızlığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c7abd-121">A null value indicates locale independence.</span></span> <span data-ttu-id="c7abd-122">**Note:**  .NET Framework sürüm 1,0 ' de birden fazla yerel ayar belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="c7abd-122">**Note:**  In the .NET Framework version 1.0 you cannot specify more than one locale.</span></span>|  
|`cbLocale`|<span data-ttu-id="c7abd-123">Öğesinin geniş karakterdeki boyutu `szLocale` .</span><span class="sxs-lookup"><span data-stu-id="c7abd-123">The size in wide characters of `szLocale`.</span></span>|  
|`rdwProcessor`|<span data-ttu-id="c7abd-124">Başvurulan derleme tarafından desteklenen işlemci türleri için Winnt. h içinde tanımlanan bir dizi tanımlayıcıdır.</span><span class="sxs-lookup"><span data-stu-id="c7abd-124">An array of identifiers, as defined in Winnt.h, for the processor types that are supported by the referenced assembly.</span></span> <span data-ttu-id="c7abd-125">NULL değer işlemci bağımsızlığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c7abd-125">A NULL value indicates processor independence.</span></span>|  
|`ulProcessor`|<span data-ttu-id="c7abd-126">`rdwProcessor`Dizinin uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="c7abd-126">The length of the `rdwProcessor` array.</span></span>|  
|`rOS`|<span data-ttu-id="c7abd-127">Başvurulan derleme tarafından desteklenen işletim sistemlerini belirten bir [OSINFO](osinfo-structure.md) örnekleri dizisi.</span><span class="sxs-lookup"><span data-stu-id="c7abd-127">An array of [OSINFO](osinfo-structure.md) instances specifying the operating systems that are supported by the referenced assembly.</span></span> <span data-ttu-id="c7abd-128">NULL değer, işletim sistemi bağımsızlığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c7abd-128">A NULL value indicates operating-system independence.</span></span>|  
|`ulOS`|<span data-ttu-id="c7abd-129">`rOS`Dizinin uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="c7abd-129">The length of the `rOS` array.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c7abd-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c7abd-130">Requirements</span></span>  

 <span data-ttu-id="c7abd-131">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7abd-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7abd-132">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="c7abd-132">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c7abd-133">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="c7abd-133">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c7abd-134">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7abd-134">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7abd-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c7abd-135">See also</span></span>

- [<span data-ttu-id="c7abd-136">Meta Veri Yapıları</span><span class="sxs-lookup"><span data-stu-id="c7abd-136">Metadata Structures</span></span>](metadata-structures.md)
- [<span data-ttu-id="c7abd-137">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c7abd-137">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
- [<span data-ttu-id="c7abd-138">OSINFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="c7abd-138">OSINFO Structure</span></span>](osinfo-structure.md)
