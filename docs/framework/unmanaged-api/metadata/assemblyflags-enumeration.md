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
ms.openlocfilehash: 2fc6d08e960b0ba82c76945a318ec723546f71b9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444912"
---
# <a name="assemblyflags-enumeration"></a><span data-ttu-id="2c833-102">AssemblyFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="2c833-102">AssemblyFlags Enumeration</span></span>
<span data-ttu-id="2c833-103">Çalışma zamanı bütünleştirilmiş özelliklerini açıklayan değerlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="2c833-103">Contains values that describe run-time features of an assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c833-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2c833-104">Syntax</span></span>  
  
```  
typedef enum {  
    afImplicitExportedTypes = 0x0001,  
    afImplicitResources = 0x0002,  
    afNonSideBySideAppDomain = 0x0010,  
    afNonSideBySideProcess = 0x0020,  
    afNonSideBySideMachine = 0x0030  
} AssemblyFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="2c833-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="2c833-105">Members</span></span>  
  
|<span data-ttu-id="2c833-106">Üye</span><span class="sxs-lookup"><span data-stu-id="2c833-106">Member</span></span>|<span data-ttu-id="2c833-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2c833-107">Description</span></span>|  
|------------|-----------------|  
|`afImplicitExportedTypes`|<span data-ttu-id="2c833-108">Dışarı aktarılan tür tanımları derleme oluşturan dosyaların içinde örtük olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="2c833-108">Specifies that exported type definitions are implicit within the files that comprise the assembly.</span></span> <span data-ttu-id="2c833-109">.NET Framework sürüm 1.0 ve 1.1, bu değer her zaman için ayarlanacak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="2c833-109">In the .NET Framework versions 1.0 and 1.1, this value is always assumed to be set.</span></span>|  
|`afImplicitResources`|<span data-ttu-id="2c833-110">Kaynak tanımları derleme oluşturan dosyaların içinde örtük olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="2c833-110">Specifies that resource definitions are implicit within the files that comprise the assembly.</span></span> <span data-ttu-id="2c833-111">.NET Framework 1.0 ve 1.1, bu değer her zaman için ayarlanacak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="2c833-111">In the .NET Framework 1.0 and 1.1, this value is always assumed to be set.</span></span>|  
|`afNonSideBySideAppDomain`|<span data-ttu-id="2c833-112">Aynı uygulama etki alanında çalıştırıyorsanız derleme diğer sürümleriyle yürütülemiyor belirtir.</span><span class="sxs-lookup"><span data-stu-id="2c833-112">Specifies that the assembly cannot execute with other versions if they are running in the same application domain.</span></span>|  
|`afNonSideBySideProcess`|<span data-ttu-id="2c833-113">Aynı işlem içinde çalıştırıyorsanız derleme diğer sürümleriyle yürütülemiyor belirtir.</span><span class="sxs-lookup"><span data-stu-id="2c833-113">Specifies that the assembly cannot execute with other versions if they are running in the same process.</span></span>|  
|`afNonSideBySideMachine`|<span data-ttu-id="2c833-114">Aynı bilgisayar üzerinde çalıştırıyorsanız, derleme diğer sürümleriyle yürütülemiyor belirtir.</span><span class="sxs-lookup"><span data-stu-id="2c833-114">Specifies that the assembly cannot execute with other versions if they are running on the same computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2c833-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2c833-115">Remarks</span></span>  
 <span data-ttu-id="2c833-116">0x0010 ve 0x0070 (dahil) arasında değerler başvurulan derlemeyi yan yana uyumluluk özelliklerini tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2c833-116">The values between 0x0010 and 0x0070, inclusive, are used to describe side-by-side compatibility features of the referenced assembly.</span></span> <span data-ttu-id="2c833-117">Bu değerlerin hiçbiri ayarlanmazsa derleme yan yana uyumlu olduğu varsayılır.</span><span class="sxs-lookup"><span data-stu-id="2c833-117">If none of these values are set, the assembly is assumed to be side-by-side compatible.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c833-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2c833-118">Requirements</span></span>  
 <span data-ttu-id="2c833-119">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c833-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c833-120">**Başlık:** MsCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2c833-120">**Header:** MsCorEE.h</span></span>  
  
 <span data-ttu-id="2c833-121">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="2c833-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2c833-122">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c833-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c833-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2c833-123">See Also</span></span>  
 [<span data-ttu-id="2c833-124">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="2c833-124">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)  
 [<span data-ttu-id="2c833-125">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2c833-125">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
