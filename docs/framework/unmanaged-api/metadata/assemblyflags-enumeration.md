---
title: AssemblyFlags Numaralandırması
ms.date: 03/30/2017
api_name:
- AssemblyFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- AssemblyFlags
helpviewer_keywords:
- AssemblyFlags enumeration [.NET Framework metadata]
ms.assetid: 40f9bd9e-16ec-447e-81b0-168c875e9866
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7c86a4fd2788c8ea2df5d9e54c5c221afd179704
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59091427"
---
# <a name="assemblyflags-enumeration"></a><span data-ttu-id="47652-102">AssemblyFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="47652-102">AssemblyFlags Enumeration</span></span>
<span data-ttu-id="47652-103">Bir derlemenin çalışma zamanı özellikleri açıklayan değerlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="47652-103">Contains values that describe run-time features of an assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47652-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="47652-104">Syntax</span></span>  
  
```  
typedef enum {  
    afImplicitExportedTypes = 0x0001,  
    afImplicitResources = 0x0002,  
    afNonSideBySideAppDomain = 0x0010,  
    afNonSideBySideProcess = 0x0020,  
    afNonSideBySideMachine = 0x0030  
} AssemblyFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="47652-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="47652-105">Members</span></span>  
  
|<span data-ttu-id="47652-106">Üye</span><span class="sxs-lookup"><span data-stu-id="47652-106">Member</span></span>|<span data-ttu-id="47652-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="47652-107">Description</span></span>|  
|------------|-----------------|  
|`afImplicitExportedTypes`|<span data-ttu-id="47652-108">Dışarı aktarılan tür tanımlarını derlemeyi oluşturan dosyaları içinde örtük olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="47652-108">Specifies that exported type definitions are implicit within the files that comprise the assembly.</span></span> <span data-ttu-id="47652-109">.NET Framework sürüm 1.0 ve 1.1, bu değeri ayarlamak için her zaman varsayılır.</span><span class="sxs-lookup"><span data-stu-id="47652-109">In the .NET Framework versions 1.0 and 1.1, this value is always assumed to be set.</span></span>|  
|`afImplicitResources`|<span data-ttu-id="47652-110">Kaynak tanımları derlemeyi oluşturan dosyaları içinde örtük olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="47652-110">Specifies that resource definitions are implicit within the files that comprise the assembly.</span></span> <span data-ttu-id="47652-111">.NET Framework 1.0 ve 1.1, bu değeri ayarlamak için her zaman varsayılır.</span><span class="sxs-lookup"><span data-stu-id="47652-111">In the .NET Framework 1.0 and 1.1, this value is always assumed to be set.</span></span>|  
|`afNonSideBySideAppDomain`|<span data-ttu-id="47652-112">Derleme aynı uygulama etki alanında çalıştırıyorsanız diğer sürümlerle yürütülemez belirtir.</span><span class="sxs-lookup"><span data-stu-id="47652-112">Specifies that the assembly cannot execute with other versions if they are running in the same application domain.</span></span>|  
|`afNonSideBySideProcess`|<span data-ttu-id="47652-113">Aynı işlem içinde çalıştırıyorsanız derleme diğer sürümlerle yürütülemez belirtir.</span><span class="sxs-lookup"><span data-stu-id="47652-113">Specifies that the assembly cannot execute with other versions if they are running in the same process.</span></span>|  
|`afNonSideBySideMachine`|<span data-ttu-id="47652-114">Aynı bilgisayarda çalışıyorsa derleme diğer sürümlerle yürütülemez belirtir.</span><span class="sxs-lookup"><span data-stu-id="47652-114">Specifies that the assembly cannot execute with other versions if they are running on the same computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="47652-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="47652-115">Remarks</span></span>  
 <span data-ttu-id="47652-116">0x0010 ve 0x0070 (dahil) arasında değerler, yan yana uyumluluk özelliklerini başvurulan derlemeyi tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="47652-116">The values between 0x0010 and 0x0070, inclusive, are used to describe side-by-side compatibility features of the referenced assembly.</span></span> <span data-ttu-id="47652-117">Bu değerlerin hiçbiri ayarlanmazsa derleme yan yana uyumlu olduğu varsayılır.</span><span class="sxs-lookup"><span data-stu-id="47652-117">If none of these values are set, the assembly is assumed to be side-by-side compatible.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47652-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="47652-118">Requirements</span></span>  
 <span data-ttu-id="47652-119">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="47652-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47652-120">**Üst bilgi:** MsCorEE.h</span><span class="sxs-lookup"><span data-stu-id="47652-120">**Header:** MsCorEE.h</span></span>  
  
 <span data-ttu-id="47652-121">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="47652-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="47652-122">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47652-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47652-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="47652-123">See also</span></span>

- [<span data-ttu-id="47652-124">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="47652-124">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [<span data-ttu-id="47652-125">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="47652-125">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
