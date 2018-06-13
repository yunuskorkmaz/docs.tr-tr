---
title: OSINFO Yapısı
ms.date: 03/30/2017
api_name:
- OSINFO
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- OSINFO
helpviewer_keywords:
- OSINFO structure [.NET Framework metadata]
ms.assetid: fac7b480-7adb-4450-a5e9-690fed81ffae
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6c5bc63da7ebe86b653c9bef7caeb1cf28d3a7f8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33450056"
---
# <a name="osinfo-structure"></a><span data-ttu-id="632a0-102">OSINFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="632a0-102">OSINFO Structure</span></span>
<span data-ttu-id="632a0-103">Bir derlemeyi ya da modülü için işletim sistemini ayrıntılarını içerir.</span><span class="sxs-lookup"><span data-stu-id="632a0-103">Contains details about the operating system for an assembly or module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="632a0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="632a0-104">Syntax</span></span>  
  
```  
typedef struct {  
    DWORD   dwOSPlatformId;  
    DWORD   dwOSMajorVersion;   
    DWORD   dwOSMinorVersion;   
} OSINFO;  
```  
  
## <a name="members"></a><span data-ttu-id="632a0-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="632a0-105">Members</span></span>  
  
|<span data-ttu-id="632a0-106">Üye</span><span class="sxs-lookup"><span data-stu-id="632a0-106">Member</span></span>|<span data-ttu-id="632a0-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="632a0-107">Description</span></span>|  
|------------|-----------------|  
|`dwOSPlatformId`|<span data-ttu-id="632a0-108">Microsoft Windows platform işlevi tarafından tanımlanan tanımlayıcı değerlerden biri `GetVersionEx`.</span><span class="sxs-lookup"><span data-stu-id="632a0-108">One of the identifier values defined by the Microsoft Windows platform function `GetVersionEx`.</span></span> <span data-ttu-id="632a0-109">Aşağıdaki değerleri desteklenir:</span><span class="sxs-lookup"><span data-stu-id="632a0-109">The following values are supported:</span></span><br /><br /> <span data-ttu-id="632a0-110">-Microsoft Windows 3.1 belirtmek için VER_PLATFORM_WIN32s, ya 0x0000.</span><span class="sxs-lookup"><span data-stu-id="632a0-110">-   VER_PLATFORM_WIN32s, or 0x0000, to specify Microsoft Windows 3.1.</span></span><br /><span data-ttu-id="632a0-111">-Windows 95, Windows 98 ya da işletim sistemlerini belirtmek için VER_PLATFORM_WIN32_WINDOWS, veya 0x0001, onlardan descended.</span><span class="sxs-lookup"><span data-stu-id="632a0-111">-   VER_PLATFORM_WIN32_WINDOWS, or 0x0001, to specify Windows 95, Windows 98, or operating systems descended from them.</span></span><br /><span data-ttu-id="632a0-112">-Windows NT veya işletim sistemlerini belirtmek için VER_PLATFORM_WIN32_NT, ya da 0x0010, ondan descended.</span><span class="sxs-lookup"><span data-stu-id="632a0-112">-   VER_PLATFORM_WIN32_NT, or 0x0010, to specify Windows NT or operating systems descended from it.</span></span>|  
|`dwOSMajorVersion`|<span data-ttu-id="632a0-113">İşletim sistemi ana sürüm veya herhangi bir sürümünü belirten bir NULL değer.</span><span class="sxs-lookup"><span data-stu-id="632a0-113">The operating system major version, or a NULL value to indicate any version.</span></span>|  
|`dwOSMinorVersion`|<span data-ttu-id="632a0-114">İşletim sistemi alt sürümü veya herhangi bir sürümünü belirten bir NULL değer.</span><span class="sxs-lookup"><span data-stu-id="632a0-114">The operating system minor version, or a NULL value to indicate any version.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="632a0-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="632a0-115">Remarks</span></span>  
 <span data-ttu-id="632a0-116">`OSINFO` dayanır `OSVERSIONINFOEX` yapısı kullanılan Microsoft Windows platform işlev çağrıları `GetVersionEx`.</span><span class="sxs-lookup"><span data-stu-id="632a0-116">`OSINFO` is based on the `OSVERSIONINFOEX` structure that is used in calls to the Microsoft Windows platform function `GetVersionEx`.</span></span> <span data-ttu-id="632a0-117">Bu yapı tarafından ASSEMBLYMETADATA yapısı, işletim sistemi desteği göstermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="632a0-117">This structure is used by the ASSEMBLYMETADATA structure to indicate its operating system support.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="632a0-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="632a0-118">Requirements</span></span>  
 <span data-ttu-id="632a0-119">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="632a0-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="632a0-120">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="632a0-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="632a0-121">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="632a0-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="632a0-122">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="632a0-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="632a0-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="632a0-123">See Also</span></span>  
 [<span data-ttu-id="632a0-124">Meta Veri Yapıları</span><span class="sxs-lookup"><span data-stu-id="632a0-124">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)  
 [<span data-ttu-id="632a0-125">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="632a0-125">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
