---
description: 'Daha fazla bilgi edinin: AssemblyFlags sabit listesi'
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
ms.openlocfilehash: 17cc0dec305c21d21693fe8f4f8d82c039f73278
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99679010"
---
# <a name="assemblyflags-enumeration"></a><span data-ttu-id="77c23-103">AssemblyFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="77c23-103">AssemblyFlags Enumeration</span></span>

<span data-ttu-id="77c23-104">Bir derlemenin çalışma zamanı özelliklerini tanımlayan değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="77c23-104">Contains values that describe run-time features of an assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77c23-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="77c23-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    afImplicitExportedTypes = 0x0001,  
    afImplicitResources = 0x0002,  
    afNonSideBySideAppDomain = 0x0010,  
    afNonSideBySideProcess = 0x0020,  
    afNonSideBySideMachine = 0x0030  
} AssemblyFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="77c23-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="77c23-106">Members</span></span>  
  
|<span data-ttu-id="77c23-107">Üye</span><span class="sxs-lookup"><span data-stu-id="77c23-107">Member</span></span>|<span data-ttu-id="77c23-108">Description</span><span class="sxs-lookup"><span data-stu-id="77c23-108">Description</span></span>|  
|------------|-----------------|  
|`afImplicitExportedTypes`|<span data-ttu-id="77c23-109">İçe aktarılmış tür tanımlarının derlemeyi oluşturan dosyalar içinde örtük olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="77c23-109">Specifies that exported type definitions are implicit within the files that comprise the assembly.</span></span> <span data-ttu-id="77c23-110">.NET Framework sürüm 1,0 ve 1,1 ' de, bu değer her zaman ayarlandığı varsayılır.</span><span class="sxs-lookup"><span data-stu-id="77c23-110">In the .NET Framework versions 1.0 and 1.1, this value is always assumed to be set.</span></span>|  
|`afImplicitResources`|<span data-ttu-id="77c23-111">Kaynak tanımlarının derlemeyi oluşturan dosyalar içinde örtük olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="77c23-111">Specifies that resource definitions are implicit within the files that comprise the assembly.</span></span> <span data-ttu-id="77c23-112">.NET Framework 1,0 ve 1,1 ' de, bu değer her zaman ayarlandığı varsayılır.</span><span class="sxs-lookup"><span data-stu-id="77c23-112">In the .NET Framework 1.0 and 1.1, this value is always assumed to be set.</span></span>|  
|`afNonSideBySideAppDomain`|<span data-ttu-id="77c23-113">Derlemenin aynı uygulama etki alanında çalışıyorsa diğer sürümlerle yürütümeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="77c23-113">Specifies that the assembly cannot execute with other versions if they are running in the same application domain.</span></span>|  
|`afNonSideBySideProcess`|<span data-ttu-id="77c23-114">Derlemenin aynı işlemde çalışıyorsa diğer sürümlerle yürütümeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="77c23-114">Specifies that the assembly cannot execute with other versions if they are running in the same process.</span></span>|  
|`afNonSideBySideMachine`|<span data-ttu-id="77c23-115">Derlemenin aynı bilgisayarda çalışıyorsa diğer sürümlerle yürütümeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="77c23-115">Specifies that the assembly cannot execute with other versions if they are running on the same computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="77c23-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="77c23-116">Remarks</span></span>  

 <span data-ttu-id="77c23-117">0x0010 ile 0x0070 (dahil) arasındaki değerler, başvurulan derlemenin yan yana uyumluluk özelliklerini anlatmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="77c23-117">The values between 0x0010 and 0x0070, inclusive, are used to describe side-by-side compatibility features of the referenced assembly.</span></span> <span data-ttu-id="77c23-118">Bu değerlerden hiçbiri ayarlanmamışsa, derlemenin yan yana uyumlu olduğu varsayılır.</span><span class="sxs-lookup"><span data-stu-id="77c23-118">If none of these values are set, the assembly is assumed to be side-by-side compatible.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77c23-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="77c23-119">Requirements</span></span>  

 <span data-ttu-id="77c23-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77c23-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77c23-121">**Üst bilgi:** MsCorEE. h</span><span class="sxs-lookup"><span data-stu-id="77c23-121">**Header:** MsCorEE.h</span></span>  
  
 <span data-ttu-id="77c23-122">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="77c23-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="77c23-123">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77c23-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77c23-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="77c23-124">See also</span></span>

- [<span data-ttu-id="77c23-125">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="77c23-125">Metadata Enumerations</span></span>](metadata-enumerations.md)
- [<span data-ttu-id="77c23-126">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="77c23-126">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
