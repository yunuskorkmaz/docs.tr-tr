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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a5039117c649943a1f05a91ecccf22eb4230e5e7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776383"
---
# <a name="assemblymetadata-structure"></a><span data-ttu-id="79b47-102">ASSEMBLYMETADATA Yapısı</span><span class="sxs-lookup"><span data-stu-id="79b47-102">ASSEMBLYMETADATA Structure</span></span>
<span data-ttu-id="79b47-103">Başvurulan derlemenin sürümü ve yerel ayarlar, işlemcileri ve işletim sistemleri için destek düzeyini de dahil olmak üzere, ilgili bilgiler içerir.</span><span class="sxs-lookup"><span data-stu-id="79b47-103">Contains information about the referenced assembly, including its version and its level of support for locales, processors, and operating systems.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79b47-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="79b47-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="79b47-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="79b47-105">Members</span></span>  
  
|<span data-ttu-id="79b47-106">Üye</span><span class="sxs-lookup"><span data-stu-id="79b47-106">Member</span></span>|<span data-ttu-id="79b47-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="79b47-107">Description</span></span>|  
|------------|-----------------|  
|`usMajorVersion`|<span data-ttu-id="79b47-108">Başvurulan derlemenin sürüm sayısı.</span><span class="sxs-lookup"><span data-stu-id="79b47-108">The major version number of the referenced assembly.</span></span> <span data-ttu-id="79b47-109">Bu değer sıfır olamaz.</span><span class="sxs-lookup"><span data-stu-id="79b47-109">This value cannot be zero.</span></span> <span data-ttu-id="79b47-110">Tüm bit'leri `usMajorVersion` , ana sürüm belirtilmezse ayarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="79b47-110">If all the bits of `usMajorVersion` are set, the major version is not specified.</span></span>|  
|`usMinorVersion`|<span data-ttu-id="79b47-111">Başvurulan derlemenin ikincil sürüm sayısı.</span><span class="sxs-lookup"><span data-stu-id="79b47-111">The minor version number of the referenced assembly.</span></span> <span data-ttu-id="79b47-112">Bu değer sıfır olamaz.</span><span class="sxs-lookup"><span data-stu-id="79b47-112">This value cannot be zero.</span></span> <span data-ttu-id="79b47-113">Tüm bit'leri `usMinorVersion` , alt sürüm belirtilmezse ayarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="79b47-113">If all the bits of `usMinorVersion` are set, the minor version is not specified.</span></span>|  
|`usBuildNumber`|<span data-ttu-id="79b47-114">Başvurulan derlemenin derleme sayısı.</span><span class="sxs-lookup"><span data-stu-id="79b47-114">The build number of the referenced assembly.</span></span> <span data-ttu-id="79b47-115">Bu değer sıfır olamaz.</span><span class="sxs-lookup"><span data-stu-id="79b47-115">This value cannot be zero.</span></span> <span data-ttu-id="79b47-116">Tüm bit'leri `usBuildNumber` , derleme numarası belirtilmemiş ayarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="79b47-116">If all the bits of `usBuildNumber` are set, the build number is not specified.</span></span>|  
|`usRevisionNumber`|<span data-ttu-id="79b47-117">Başvurulan derlemenin düzeltme sayısı.</span><span class="sxs-lookup"><span data-stu-id="79b47-117">The revision number of the referenced assembly.</span></span> <span data-ttu-id="79b47-118">Bu değer sıfır olamaz.</span><span class="sxs-lookup"><span data-stu-id="79b47-118">This value cannot be zero.</span></span> <span data-ttu-id="79b47-119">Tüm bit'leri `usRevisionNumber` , düzeltme numarası belirtilmezse ayarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="79b47-119">If all the bits of `usRevisionNumber` are set, the revision number is not specified.</span></span>|  
|`szLocale`|<span data-ttu-id="79b47-120">Yerel ayar adları noktalı virgül, başvurulan derleme tarafından desteklenen yerel ayarlar belirterek ayırarak RFC1766 belirtimine uyan bir listesi.</span><span class="sxs-lookup"><span data-stu-id="79b47-120">A list of locale names conforming to the RFC1766 specification, separated by semicolons, specifying the locales supported by the referenced assembly.</span></span> <span data-ttu-id="79b47-121">Null değeri, yerel ayar bağımsızlığı gösterir.</span><span class="sxs-lookup"><span data-stu-id="79b47-121">A null value indicates locale independence.</span></span> <span data-ttu-id="79b47-122">**Not:**  .NET Framework sürüm 1.0 birden fazla yerel ayar belirtilemez.</span><span class="sxs-lookup"><span data-stu-id="79b47-122">**Note:**  In the .NET Framework version 1.0 you cannot specify more than one locale.</span></span>|  
|`cbLocale`|<span data-ttu-id="79b47-123">Geniş karakter cinsinden boyutu `szLocale`.</span><span class="sxs-lookup"><span data-stu-id="79b47-123">The size in wide characters of `szLocale`.</span></span>|  
|`rdwProcessor`|<span data-ttu-id="79b47-124">Tanımlayıcılar, Winnt.h başvurulan derleme tarafından desteklenmeyen İşlemci türleri için tanımlanan bir dizi.</span><span class="sxs-lookup"><span data-stu-id="79b47-124">An array of identifiers, as defined in Winnt.h, for the processor types that are supported by the referenced assembly.</span></span> <span data-ttu-id="79b47-125">NULL değeri işlemci bağımsızlığı gösterir.</span><span class="sxs-lookup"><span data-stu-id="79b47-125">A NULL value indicates processor independence.</span></span>|  
|`ulProcessor`|<span data-ttu-id="79b47-126">Uzunluğunu `rdwProcessor` dizisi.</span><span class="sxs-lookup"><span data-stu-id="79b47-126">The length of the `rdwProcessor` array.</span></span>|  
|`rOS`|<span data-ttu-id="79b47-127">Bir dizi [OSINFO](../../../../docs/framework/unmanaged-api/metadata/osinfo-structure.md) başvurulan derleme tarafından desteklenen işletim sistemlerini belirten örneği.</span><span class="sxs-lookup"><span data-stu-id="79b47-127">An array of [OSINFO](../../../../docs/framework/unmanaged-api/metadata/osinfo-structure.md) instances specifying the operating systems that are supported by the referenced assembly.</span></span> <span data-ttu-id="79b47-128">NULL değeri, işletim sistemi bağımsızlığı gösterir.</span><span class="sxs-lookup"><span data-stu-id="79b47-128">A NULL value indicates operating-system independence.</span></span>|  
|`ulOS`|<span data-ttu-id="79b47-129">Uzunluğunu `rOS` dizisi.</span><span class="sxs-lookup"><span data-stu-id="79b47-129">The length of the `rOS` array.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="79b47-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="79b47-130">Requirements</span></span>  
 <span data-ttu-id="79b47-131">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="79b47-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79b47-132">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="79b47-132">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="79b47-133">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="79b47-133">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="79b47-134">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79b47-134">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79b47-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="79b47-135">See also</span></span>

- [<span data-ttu-id="79b47-136">Meta Veri Yapıları</span><span class="sxs-lookup"><span data-stu-id="79b47-136">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [<span data-ttu-id="79b47-137">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="79b47-137">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [<span data-ttu-id="79b47-138">OSINFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="79b47-138">OSINFO Structure</span></span>](../../../../docs/framework/unmanaged-api/metadata/osinfo-structure.md)
