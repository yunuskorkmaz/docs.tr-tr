---
title: "ASSEMBLYMETADATA Yapısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ASSEMBLYMETADATA
api_location: mscoree.dll
api_type: COM
f1_keywords: ASSEMBLYMETADATA
helpviewer_keywords: ASSEMBLYMETADATA structure [.NET Framework metadata]
ms.assetid: 1af98e57-9145-4d35-bb78-77d1da7c91a5
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5652907abc17868414c554cb5c87b0856d2c5a0c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="assemblymetadata-structure"></a><span data-ttu-id="caae8-102">ASSEMBLYMETADATA Yapısı</span><span class="sxs-lookup"><span data-stu-id="caae8-102">ASSEMBLYMETADATA Structure</span></span>
<span data-ttu-id="caae8-103">Kendi sürüm ve alt düzey yerel ayarlar, işlemcileri ve işletim sistemleri için destek dahil olmak üzere başvurulan derleme hakkında bilgiler içerir.</span><span class="sxs-lookup"><span data-stu-id="caae8-103">Contains information about the referenced assembly, including its version and its level of support for locales, processors, and operating systems.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="caae8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="caae8-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="caae8-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="caae8-105">Members</span></span>  
  
|<span data-ttu-id="caae8-106">Üye</span><span class="sxs-lookup"><span data-stu-id="caae8-106">Member</span></span>|<span data-ttu-id="caae8-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="caae8-107">Description</span></span>|  
|------------|-----------------|  
|`usMajorVersion`|<span data-ttu-id="caae8-108">Başvurulan derlemeyi ana sürüm numarası.</span><span class="sxs-lookup"><span data-stu-id="caae8-108">The major version number of the referenced assembly.</span></span> <span data-ttu-id="caae8-109">Bu değer sıfır olamaz.</span><span class="sxs-lookup"><span data-stu-id="caae8-109">This value cannot be zero.</span></span> <span data-ttu-id="caae8-110">Varsa, tüm BITS `usMajorVersion` , ana sürüm belirtilmezse ayarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="caae8-110">If all the bits of `usMajorVersion` are set, the major version is not specified.</span></span>|  
|`usMinorVersion`|<span data-ttu-id="caae8-111">Başvurulan derlemeyi ikincil sürüm numarası.</span><span class="sxs-lookup"><span data-stu-id="caae8-111">The minor version number of the referenced assembly.</span></span> <span data-ttu-id="caae8-112">Bu değer sıfır olamaz.</span><span class="sxs-lookup"><span data-stu-id="caae8-112">This value cannot be zero.</span></span> <span data-ttu-id="caae8-113">Varsa, tüm BITS `usMinorVersion` , alt sürüm belirtilmezse ayarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="caae8-113">If all the bits of `usMinorVersion` are set, the minor version is not specified.</span></span>|  
|`usBuildNumber`|<span data-ttu-id="caae8-114">Başvurulan derlemeyi yapı sayısı.</span><span class="sxs-lookup"><span data-stu-id="caae8-114">The build number of the referenced assembly.</span></span> <span data-ttu-id="caae8-115">Bu değer sıfır olamaz.</span><span class="sxs-lookup"><span data-stu-id="caae8-115">This value cannot be zero.</span></span> <span data-ttu-id="caae8-116">Varsa, tüm BITS `usBuildNumber` , yapı numarası belirtilmezse ayarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="caae8-116">If all the bits of `usBuildNumber` are set, the build number is not specified.</span></span>|  
|`usRevisionNumber`|<span data-ttu-id="caae8-117">Başvurulan derlemeyi düzeltme sayısı.</span><span class="sxs-lookup"><span data-stu-id="caae8-117">The revision number of the referenced assembly.</span></span> <span data-ttu-id="caae8-118">Bu değer sıfır olamaz.</span><span class="sxs-lookup"><span data-stu-id="caae8-118">This value cannot be zero.</span></span> <span data-ttu-id="caae8-119">Varsa, tüm BITS `usRevisionNumber` , düzeltme numarası belirtilmezse ayarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="caae8-119">If all the bits of `usRevisionNumber` are set, the revision number is not specified.</span></span>|  
|`szLocale`|<span data-ttu-id="caae8-120">Başvurulan derleme tarafından desteklenen yerel ayarlar belirtme noktalı virgül ile ayrılmış RFC1766 belirtimine uygun yerel ayar adları listesi.</span><span class="sxs-lookup"><span data-stu-id="caae8-120">A list of locale names conforming to the RFC1766 specification, separated by semicolons, specifying the locales supported by the referenced assembly.</span></span> <span data-ttu-id="caae8-121">Bir null değer yerel bağımsızlığı gösterir.</span><span class="sxs-lookup"><span data-stu-id="caae8-121">A null value indicates locale independence.</span></span> <span data-ttu-id="caae8-122">**Not:** .NET Framework sürüm 1.0 birden fazla yerel ayar belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="caae8-122">**Note:**  In the .NET Framework version 1.0 you cannot specify more than one locale.</span></span>|  
|`cbLocale`|<span data-ttu-id="caae8-123">Geniş karakter cinsinden boyutu `szLocale`.</span><span class="sxs-lookup"><span data-stu-id="caae8-123">The size in wide characters of `szLocale`.</span></span>|  
|`rdwProcessor`|<span data-ttu-id="caae8-124">Winnt.h içinde başvurulan derleme tarafından desteklenen İşlemci türleri için tanımlanan tanımlayıcıları dizisi.</span><span class="sxs-lookup"><span data-stu-id="caae8-124">An array of identifiers, as defined in Winnt.h, for the processor types that are supported by the referenced assembly.</span></span> <span data-ttu-id="caae8-125">NULL değeri işlemci bağımsızlığı gösterir.</span><span class="sxs-lookup"><span data-stu-id="caae8-125">A NULL value indicates processor independence.</span></span>|  
|`ulProcessor`|<span data-ttu-id="caae8-126">Uzunluğu `rdwProcessor` dizi.</span><span class="sxs-lookup"><span data-stu-id="caae8-126">The length of the `rdwProcessor` array.</span></span>|  
|`rOS`|<span data-ttu-id="caae8-127">Bir dizi [OSINFO](../../../../docs/framework/unmanaged-api/metadata/osinfo-structure.md) başvurulan derleme tarafından desteklenen işletim sistemleri belirtme örnekleri.</span><span class="sxs-lookup"><span data-stu-id="caae8-127">An array of [OSINFO](../../../../docs/framework/unmanaged-api/metadata/osinfo-structure.md) instances specifying the operating systems that are supported by the referenced assembly.</span></span> <span data-ttu-id="caae8-128">NULL değeri, işletim sistemi bağımsızlığı gösterir.</span><span class="sxs-lookup"><span data-stu-id="caae8-128">A NULL value indicates operating-system independence.</span></span>|  
|`ulOS`|<span data-ttu-id="caae8-129">Uzunluğu `rOS` dizi.</span><span class="sxs-lookup"><span data-stu-id="caae8-129">The length of the `rOS` array.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="caae8-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="caae8-130">Requirements</span></span>  
 <span data-ttu-id="caae8-131">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="caae8-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="caae8-132">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="caae8-132">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="caae8-133">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="caae8-133">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="caae8-134">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="caae8-134">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="caae8-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="caae8-135">See Also</span></span>  
 [<span data-ttu-id="caae8-136">Meta veri yapıları</span><span class="sxs-lookup"><span data-stu-id="caae8-136">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)  
 [<span data-ttu-id="caae8-137">Imetadataassemblyemit arabirimi</span><span class="sxs-lookup"><span data-stu-id="caae8-137">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)  
 [<span data-ttu-id="caae8-138">OSINFO yapısı</span><span class="sxs-lookup"><span data-stu-id="caae8-138">OSINFO Structure</span></span>](../../../../docs/framework/unmanaged-api/metadata/osinfo-structure.md)
