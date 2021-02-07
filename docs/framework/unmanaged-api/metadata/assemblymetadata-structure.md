---
description: 'Daha fazla bilgi edinin: ASSEMBLYMETADATA yapısı'
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
ms.openlocfilehash: 6fc9c03bea3b1413cd3a8421746137e37d43bd90
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99678945"
---
# <a name="assemblymetadata-structure"></a><span data-ttu-id="44288-103">ASSEMBLYMETADATA Yapısı</span><span class="sxs-lookup"><span data-stu-id="44288-103">ASSEMBLYMETADATA Structure</span></span>

<span data-ttu-id="44288-104">Başvurulan derleme hakkında, sürümü ve yerel ayarlar, işlemciler ve işletim sistemleri için destek düzeyi dahil olmak üzere bilgiler içerir.</span><span class="sxs-lookup"><span data-stu-id="44288-104">Contains information about the referenced assembly, including its version and its level of support for locales, processors, and operating systems.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44288-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="44288-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="44288-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="44288-106">Members</span></span>  
  
|<span data-ttu-id="44288-107">Üye</span><span class="sxs-lookup"><span data-stu-id="44288-107">Member</span></span>|<span data-ttu-id="44288-108">Description</span><span class="sxs-lookup"><span data-stu-id="44288-108">Description</span></span>|  
|------------|-----------------|  
|`usMajorVersion`|<span data-ttu-id="44288-109">Başvurulan derlemenin ana sürüm numarası.</span><span class="sxs-lookup"><span data-stu-id="44288-109">The major version number of the referenced assembly.</span></span> <span data-ttu-id="44288-110">Bu değer sıfır olamaz.</span><span class="sxs-lookup"><span data-stu-id="44288-110">This value cannot be zero.</span></span> <span data-ttu-id="44288-111">Tüm bitleri `usMajorVersion` ayarlandıysa, ana sürüm belirtilmez.</span><span class="sxs-lookup"><span data-stu-id="44288-111">If all the bits of `usMajorVersion` are set, the major version is not specified.</span></span>|  
|`usMinorVersion`|<span data-ttu-id="44288-112">Başvurulan derlemenin ikincil sürüm numarası.</span><span class="sxs-lookup"><span data-stu-id="44288-112">The minor version number of the referenced assembly.</span></span> <span data-ttu-id="44288-113">Bu değer sıfır olamaz.</span><span class="sxs-lookup"><span data-stu-id="44288-113">This value cannot be zero.</span></span> <span data-ttu-id="44288-114">Tüm bitleri `usMinorVersion` ayarlandıysa, ikincil sürüm belirtilmez.</span><span class="sxs-lookup"><span data-stu-id="44288-114">If all the bits of `usMinorVersion` are set, the minor version is not specified.</span></span>|  
|`usBuildNumber`|<span data-ttu-id="44288-115">Başvurulan derlemenin yapı numarası.</span><span class="sxs-lookup"><span data-stu-id="44288-115">The build number of the referenced assembly.</span></span> <span data-ttu-id="44288-116">Bu değer sıfır olamaz.</span><span class="sxs-lookup"><span data-stu-id="44288-116">This value cannot be zero.</span></span> <span data-ttu-id="44288-117">Tüm bitleri `usBuildNumber` ayarlandıysa, yapı numarası belirtilmez.</span><span class="sxs-lookup"><span data-stu-id="44288-117">If all the bits of `usBuildNumber` are set, the build number is not specified.</span></span>|  
|`usRevisionNumber`|<span data-ttu-id="44288-118">Başvurulan derlemenin düzeltme numarası.</span><span class="sxs-lookup"><span data-stu-id="44288-118">The revision number of the referenced assembly.</span></span> <span data-ttu-id="44288-119">Bu değer sıfır olamaz.</span><span class="sxs-lookup"><span data-stu-id="44288-119">This value cannot be zero.</span></span> <span data-ttu-id="44288-120">Tüm bitleri `usRevisionNumber` ayarlandıysa, düzeltme numarası belirtilmez.</span><span class="sxs-lookup"><span data-stu-id="44288-120">If all the bits of `usRevisionNumber` are set, the revision number is not specified.</span></span>|  
|`szLocale`|<span data-ttu-id="44288-121">RFC1766 belirtimine uyan, başvurulan derleme tarafından desteklenen yerel ayarları belirten, noktalı virgülle ayrılmış yerel ayar adlarının listesi.</span><span class="sxs-lookup"><span data-stu-id="44288-121">A list of locale names conforming to the RFC1766 specification, separated by semicolons, specifying the locales supported by the referenced assembly.</span></span> <span data-ttu-id="44288-122">Null değer yerel ayar bağımsızlığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="44288-122">A null value indicates locale independence.</span></span> <span data-ttu-id="44288-123">**Note:**  .NET Framework sürüm 1,0 ' de birden fazla yerel ayar belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="44288-123">**Note:**  In the .NET Framework version 1.0 you cannot specify more than one locale.</span></span>|  
|`cbLocale`|<span data-ttu-id="44288-124">Öğesinin geniş karakterdeki boyutu `szLocale` .</span><span class="sxs-lookup"><span data-stu-id="44288-124">The size in wide characters of `szLocale`.</span></span>|  
|`rdwProcessor`|<span data-ttu-id="44288-125">Başvurulan derleme tarafından desteklenen işlemci türleri için Winnt. h içinde tanımlanan bir dizi tanımlayıcıdır.</span><span class="sxs-lookup"><span data-stu-id="44288-125">An array of identifiers, as defined in Winnt.h, for the processor types that are supported by the referenced assembly.</span></span> <span data-ttu-id="44288-126">NULL değer işlemci bağımsızlığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="44288-126">A NULL value indicates processor independence.</span></span>|  
|`ulProcessor`|<span data-ttu-id="44288-127">`rdwProcessor`Dizinin uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="44288-127">The length of the `rdwProcessor` array.</span></span>|  
|`rOS`|<span data-ttu-id="44288-128">Başvurulan derleme tarafından desteklenen işletim sistemlerini belirten bir [OSINFO](osinfo-structure.md) örnekleri dizisi.</span><span class="sxs-lookup"><span data-stu-id="44288-128">An array of [OSINFO](osinfo-structure.md) instances specifying the operating systems that are supported by the referenced assembly.</span></span> <span data-ttu-id="44288-129">NULL değer, işletim sistemi bağımsızlığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="44288-129">A NULL value indicates operating-system independence.</span></span>|  
|`ulOS`|<span data-ttu-id="44288-130">`rOS`Dizinin uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="44288-130">The length of the `rOS` array.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="44288-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="44288-131">Requirements</span></span>  

 <span data-ttu-id="44288-132">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="44288-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44288-133">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="44288-133">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="44288-134">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="44288-134">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="44288-135">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44288-135">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44288-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="44288-136">See also</span></span>

- [<span data-ttu-id="44288-137">Meta Veri Yapıları</span><span class="sxs-lookup"><span data-stu-id="44288-137">Metadata Structures</span></span>](metadata-structures.md)
- [<span data-ttu-id="44288-138">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="44288-138">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
- [<span data-ttu-id="44288-139">OSINFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="44288-139">OSINFO Structure</span></span>](osinfo-structure.md)
