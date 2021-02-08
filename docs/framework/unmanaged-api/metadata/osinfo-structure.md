---
description: 'Daha fazla bilgi edinin: OSıNFO yapısı'
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
ms.openlocfilehash: 5027ef5cf4137aa1e781134b325407e1251fdd31
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799115"
---
# <a name="osinfo-structure"></a><span data-ttu-id="cb905-103">OSINFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="cb905-103">OSINFO Structure</span></span>

<span data-ttu-id="cb905-104">Bir derleme veya modül için işletim sistemiyle ilgili ayrıntıları içerir.</span><span class="sxs-lookup"><span data-stu-id="cb905-104">Contains details about the operating system for an assembly or module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb905-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="cb905-105">Syntax</span></span>  
  
```cpp  
typedef struct {  
    DWORD   dwOSPlatformId;  
    DWORD   dwOSMajorVersion;
    DWORD   dwOSMinorVersion;
} OSINFO;  
```  
  
## <a name="members"></a><span data-ttu-id="cb905-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="cb905-106">Members</span></span>  
  
|<span data-ttu-id="cb905-107">Üye</span><span class="sxs-lookup"><span data-stu-id="cb905-107">Member</span></span>|<span data-ttu-id="cb905-108">Description</span><span class="sxs-lookup"><span data-stu-id="cb905-108">Description</span></span>|  
|------------|-----------------|  
|`dwOSPlatformId`|<span data-ttu-id="cb905-109">Microsoft Windows platformu işlevi tarafından tanımlanan tanımlayıcı değerlerinden biri `GetVersionEx` .</span><span class="sxs-lookup"><span data-stu-id="cb905-109">One of the identifier values defined by the Microsoft Windows platform function `GetVersionEx`.</span></span> <span data-ttu-id="cb905-110">Aşağıdaki değerler desteklenir:</span><span class="sxs-lookup"><span data-stu-id="cb905-110">The following values are supported:</span></span><br /><br /> <span data-ttu-id="cb905-111">-VER_PLATFORM_WIN32s veya 0x0000, Microsoft Windows 3,1 belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="cb905-111">-   VER_PLATFORM_WIN32s, or 0x0000, to specify Microsoft Windows 3.1.</span></span><br /><span data-ttu-id="cb905-112">-VER_PLATFORM_WIN32_WINDOWS veya 0x0001, Windows 95, Windows 98 veya bunların alt öğelerinden birine ait işletim sistemlerini belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="cb905-112">-   VER_PLATFORM_WIN32_WINDOWS, or 0x0001, to specify Windows 95, Windows 98, or operating systems descended from them.</span></span><br /><span data-ttu-id="cb905-113">-VER_PLATFORM_WIN32_NT veya 0x0002, Windows NT veya bundan sonra gelen işletim sistemlerini belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="cb905-113">-   VER_PLATFORM_WIN32_NT, or 0x0002, to specify Windows NT or operating systems descended from it.</span></span>|  
|`dwOSMajorVersion`|<span data-ttu-id="cb905-114">İşletim sistemi ana sürümü veya herhangi bir sürümü göstermek için NULL değer.</span><span class="sxs-lookup"><span data-stu-id="cb905-114">The operating system major version, or a NULL value to indicate any version.</span></span>|  
|`dwOSMinorVersion`|<span data-ttu-id="cb905-115">İşletim sistemi alt sürümü veya herhangi bir sürümü göstermek için NULL değer.</span><span class="sxs-lookup"><span data-stu-id="cb905-115">The operating system minor version, or a NULL value to indicate any version.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cb905-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cb905-116">Remarks</span></span>  

 <span data-ttu-id="cb905-117">`OSINFO` , `OSVERSIONINFOEX` Microsoft Windows platformu işlevi çağrılarında kullanılan yapıya dayalıdır `GetVersionEx` .</span><span class="sxs-lookup"><span data-stu-id="cb905-117">`OSINFO` is based on the `OSVERSIONINFOEX` structure that is used in calls to the Microsoft Windows platform function `GetVersionEx`.</span></span> <span data-ttu-id="cb905-118">Bu yapı, ASSEMBLYMETADATA yapısı tarafından, işletim sistemi desteğini göstermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cb905-118">This structure is used by the ASSEMBLYMETADATA structure to indicate its operating system support.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb905-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cb905-119">Requirements</span></span>  

 <span data-ttu-id="cb905-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb905-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb905-121">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="cb905-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cb905-122">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="cb905-122">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cb905-123">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb905-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb905-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cb905-124">See also</span></span>

- [<span data-ttu-id="cb905-125">Meta Veri Yapıları</span><span class="sxs-lookup"><span data-stu-id="cb905-125">Metadata Structures</span></span>](metadata-structures.md)
- [<span data-ttu-id="cb905-126">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cb905-126">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
