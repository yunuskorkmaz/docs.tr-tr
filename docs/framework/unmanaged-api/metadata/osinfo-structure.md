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
ms.openlocfilehash: abab67f28a5fabfc6c348af6b8b502b46510d460
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54548761"
---
# <a name="osinfo-structure"></a><span data-ttu-id="7e4b9-102">OSINFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="7e4b9-102">OSINFO Structure</span></span>
<span data-ttu-id="7e4b9-103">İşletim sistemi için bir derleme veya modül ilgili ayrıntıları içerir.</span><span class="sxs-lookup"><span data-stu-id="7e4b9-103">Contains details about the operating system for an assembly or module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e4b9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7e4b9-104">Syntax</span></span>  
  
```  
typedef struct {  
    DWORD   dwOSPlatformId;  
    DWORD   dwOSMajorVersion;   
    DWORD   dwOSMinorVersion;   
} OSINFO;  
```  
  
## <a name="members"></a><span data-ttu-id="7e4b9-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="7e4b9-105">Members</span></span>  
  
|<span data-ttu-id="7e4b9-106">Üye</span><span class="sxs-lookup"><span data-stu-id="7e4b9-106">Member</span></span>|<span data-ttu-id="7e4b9-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7e4b9-107">Description</span></span>|  
|------------|-----------------|  
|`dwOSPlatformId`|<span data-ttu-id="7e4b9-108">Microsoft Windows platform işlevi tarafından tanımlanan tanımlayıcısı değerlerinden `GetVersionEx`.</span><span class="sxs-lookup"><span data-stu-id="7e4b9-108">One of the identifier values defined by the Microsoft Windows platform function `GetVersionEx`.</span></span> <span data-ttu-id="7e4b9-109">Aşağıdaki değerleri desteklenir:</span><span class="sxs-lookup"><span data-stu-id="7e4b9-109">The following values are supported:</span></span><br /><br /> <span data-ttu-id="7e4b9-110">-VER_PLATFORM_WIN32s, veya 0x0000, Microsoft Windows 3.1 belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="7e4b9-110">-   VER_PLATFORM_WIN32s, or 0x0000, to specify Microsoft Windows 3.1.</span></span><br /><span data-ttu-id="7e4b9-111">-VER_PLATFORM_WIN32_WINDOWS, veya 0x0001, Windows 95, Windows 98 veya onlardan descended işletim sistemlerini belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="7e4b9-111">-   VER_PLATFORM_WIN32_WINDOWS, or 0x0001, to specify Windows 95, Windows 98, or operating systems descended from them.</span></span><br /><span data-ttu-id="7e4b9-112">-VER_PLATFORM_WIN32_NT, veya 0x0010, Windows NT veya ondan descended işletim sistemlerini belirtin.</span><span class="sxs-lookup"><span data-stu-id="7e4b9-112">-   VER_PLATFORM_WIN32_NT, or 0x0010, to specify Windows NT or operating systems descended from it.</span></span>|  
|`dwOSMajorVersion`|<span data-ttu-id="7e4b9-113">İşletim sistemi ana sürümü veya herhangi bir sürümünü belirtmek için bir NULL değer.</span><span class="sxs-lookup"><span data-stu-id="7e4b9-113">The operating system major version, or a NULL value to indicate any version.</span></span>|  
|`dwOSMinorVersion`|<span data-ttu-id="7e4b9-114">İşletim sistemi alt sürümü veya herhangi bir sürümünü belirtmek için bir NULL değer.</span><span class="sxs-lookup"><span data-stu-id="7e4b9-114">The operating system minor version, or a NULL value to indicate any version.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7e4b9-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7e4b9-115">Remarks</span></span>  
 <span data-ttu-id="7e4b9-116">`OSINFO` dayanır `OSVERSIONINFOEX` yapısı Microsoft Windows platform işlev için kullanılan çağrılar `GetVersionEx`.</span><span class="sxs-lookup"><span data-stu-id="7e4b9-116">`OSINFO` is based on the `OSVERSIONINFOEX` structure that is used in calls to the Microsoft Windows platform function `GetVersionEx`.</span></span> <span data-ttu-id="7e4b9-117">Bu yapı ASSEMBLYMETADATA yapısı tarafından işletim sistemi desteği belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7e4b9-117">This structure is used by the ASSEMBLYMETADATA structure to indicate its operating system support.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e4b9-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7e4b9-118">Requirements</span></span>  
 <span data-ttu-id="7e4b9-119">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e4b9-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e4b9-120">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="7e4b9-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7e4b9-121">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="7e4b9-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7e4b9-122">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e4b9-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e4b9-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7e4b9-123">See also</span></span>
- [<span data-ttu-id="7e4b9-124">Meta Veri Yapıları</span><span class="sxs-lookup"><span data-stu-id="7e4b9-124">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [<span data-ttu-id="7e4b9-125">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7e4b9-125">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
