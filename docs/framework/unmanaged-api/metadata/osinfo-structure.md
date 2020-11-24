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
ms.openlocfilehash: 49e29cc0367d5162dffcd641b163fd7b9a56ffd0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95672896"
---
# <a name="osinfo-structure"></a><span data-ttu-id="3fd21-102">OSINFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="3fd21-102">OSINFO Structure</span></span>

<span data-ttu-id="3fd21-103">Bir derleme veya modül için işletim sistemiyle ilgili ayrıntıları içerir.</span><span class="sxs-lookup"><span data-stu-id="3fd21-103">Contains details about the operating system for an assembly or module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fd21-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="3fd21-104">Syntax</span></span>  
  
```cpp  
typedef struct {  
    DWORD   dwOSPlatformId;  
    DWORD   dwOSMajorVersion;
    DWORD   dwOSMinorVersion;
} OSINFO;  
```  
  
## <a name="members"></a><span data-ttu-id="3fd21-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="3fd21-105">Members</span></span>  
  
|<span data-ttu-id="3fd21-106">Üye</span><span class="sxs-lookup"><span data-stu-id="3fd21-106">Member</span></span>|<span data-ttu-id="3fd21-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3fd21-107">Description</span></span>|  
|------------|-----------------|  
|`dwOSPlatformId`|<span data-ttu-id="3fd21-108">Microsoft Windows platformu işlevi tarafından tanımlanan tanımlayıcı değerlerinden biri `GetVersionEx` .</span><span class="sxs-lookup"><span data-stu-id="3fd21-108">One of the identifier values defined by the Microsoft Windows platform function `GetVersionEx`.</span></span> <span data-ttu-id="3fd21-109">Aşağıdaki değerler desteklenir:</span><span class="sxs-lookup"><span data-stu-id="3fd21-109">The following values are supported:</span></span><br /><br /> <span data-ttu-id="3fd21-110">-VER_PLATFORM_WIN32s veya 0x0000, Microsoft Windows 3,1 belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="3fd21-110">-   VER_PLATFORM_WIN32s, or 0x0000, to specify Microsoft Windows 3.1.</span></span><br /><span data-ttu-id="3fd21-111">-VER_PLATFORM_WIN32_WINDOWS veya 0x0001, Windows 95, Windows 98 veya bunların alt öğelerinden birine ait işletim sistemlerini belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="3fd21-111">-   VER_PLATFORM_WIN32_WINDOWS, or 0x0001, to specify Windows 95, Windows 98, or operating systems descended from them.</span></span><br /><span data-ttu-id="3fd21-112">-VER_PLATFORM_WIN32_NT veya 0x0002, Windows NT veya bundan sonra gelen işletim sistemlerini belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="3fd21-112">-   VER_PLATFORM_WIN32_NT, or 0x0002, to specify Windows NT or operating systems descended from it.</span></span>|  
|`dwOSMajorVersion`|<span data-ttu-id="3fd21-113">İşletim sistemi ana sürümü veya herhangi bir sürümü göstermek için NULL değer.</span><span class="sxs-lookup"><span data-stu-id="3fd21-113">The operating system major version, or a NULL value to indicate any version.</span></span>|  
|`dwOSMinorVersion`|<span data-ttu-id="3fd21-114">İşletim sistemi alt sürümü veya herhangi bir sürümü göstermek için NULL değer.</span><span class="sxs-lookup"><span data-stu-id="3fd21-114">The operating system minor version, or a NULL value to indicate any version.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3fd21-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3fd21-115">Remarks</span></span>  

 <span data-ttu-id="3fd21-116">`OSINFO` , `OSVERSIONINFOEX` Microsoft Windows platformu işlevi çağrılarında kullanılan yapıya dayalıdır `GetVersionEx` .</span><span class="sxs-lookup"><span data-stu-id="3fd21-116">`OSINFO` is based on the `OSVERSIONINFOEX` structure that is used in calls to the Microsoft Windows platform function `GetVersionEx`.</span></span> <span data-ttu-id="3fd21-117">Bu yapı, ASSEMBLYMETADATA yapısı tarafından, işletim sistemi desteğini göstermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3fd21-117">This structure is used by the ASSEMBLYMETADATA structure to indicate its operating system support.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3fd21-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3fd21-118">Requirements</span></span>  

 <span data-ttu-id="3fd21-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3fd21-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3fd21-120">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="3fd21-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3fd21-121">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="3fd21-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3fd21-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3fd21-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fd21-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3fd21-123">See also</span></span>

- [<span data-ttu-id="3fd21-124">Meta Veri Yapıları</span><span class="sxs-lookup"><span data-stu-id="3fd21-124">Metadata Structures</span></span>](metadata-structures.md)
- [<span data-ttu-id="3fd21-125">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3fd21-125">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
