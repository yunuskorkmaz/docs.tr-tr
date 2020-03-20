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
ms.openlocfilehash: 048fe687e4d979576896f5310bddc855b40bb695
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175232"
---
# <a name="osinfo-structure"></a><span data-ttu-id="aa2cf-102">OSINFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="aa2cf-102">OSINFO Structure</span></span>
<span data-ttu-id="aa2cf-103">Bir derleme veya modül için işletim sistemi hakkında ayrıntıları içerir.</span><span class="sxs-lookup"><span data-stu-id="aa2cf-103">Contains details about the operating system for an assembly or module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa2cf-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="aa2cf-104">Syntax</span></span>  
  
```cpp  
typedef struct {  
    DWORD   dwOSPlatformId;  
    DWORD   dwOSMajorVersion;
    DWORD   dwOSMinorVersion;
} OSINFO;  
```  
  
## <a name="members"></a><span data-ttu-id="aa2cf-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="aa2cf-105">Members</span></span>  
  
|<span data-ttu-id="aa2cf-106">Üye</span><span class="sxs-lookup"><span data-stu-id="aa2cf-106">Member</span></span>|<span data-ttu-id="aa2cf-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aa2cf-107">Description</span></span>|  
|------------|-----------------|  
|`dwOSPlatformId`|<span data-ttu-id="aa2cf-108">Microsoft Windows platformu işlevi `GetVersionEx`tarafından tanımlanan tanımlayıcı değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="aa2cf-108">One of the identifier values defined by the Microsoft Windows platform function `GetVersionEx`.</span></span> <span data-ttu-id="aa2cf-109">Aşağıdaki değerler desteklenir:</span><span class="sxs-lookup"><span data-stu-id="aa2cf-109">The following values are supported:</span></span><br /><br /> <span data-ttu-id="aa2cf-110">- VER_PLATFORM_WIN32s veya 0x0000, Microsoft Windows 3.1 belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="aa2cf-110">-   VER_PLATFORM_WIN32s, or 0x0000, to specify Microsoft Windows 3.1.</span></span><br /><span data-ttu-id="aa2cf-111">- VER_PLATFORM_WIN32_WINDOWS veya 0x0001, Windows 95, Windows 98 veya işletim sistemleri bunların indi belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="aa2cf-111">-   VER_PLATFORM_WIN32_WINDOWS, or 0x0001, to specify Windows 95, Windows 98, or operating systems descended from them.</span></span><br /><span data-ttu-id="aa2cf-112">- VER_PLATFORM_WIN32_NT veya 0x0002, Windows NT veya işletim sistemleri soyundan belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="aa2cf-112">-   VER_PLATFORM_WIN32_NT, or 0x0002, to specify Windows NT or operating systems descended from it.</span></span>|  
|`dwOSMajorVersion`|<span data-ttu-id="aa2cf-113">İşletim sistemi ana sürümü veya herhangi bir sürümü belirtmek için null değeri.</span><span class="sxs-lookup"><span data-stu-id="aa2cf-113">The operating system major version, or a NULL value to indicate any version.</span></span>|  
|`dwOSMinorVersion`|<span data-ttu-id="aa2cf-114">İşletim sistemi küçük sürümü veya herhangi bir sürümü belirtmek için null değeri.</span><span class="sxs-lookup"><span data-stu-id="aa2cf-114">The operating system minor version, or a NULL value to indicate any version.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aa2cf-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="aa2cf-115">Remarks</span></span>  
 <span data-ttu-id="aa2cf-116">`OSINFO`Microsoft Windows `OSVERSIONINFOEX` platform işlevine `GetVersionEx`yapılan aramalarda kullanılan yapıya dayanır.</span><span class="sxs-lookup"><span data-stu-id="aa2cf-116">`OSINFO` is based on the `OSVERSIONINFOEX` structure that is used in calls to the Microsoft Windows platform function `GetVersionEx`.</span></span> <span data-ttu-id="aa2cf-117">Bu yapı, assemblymetadata yapısı tarafından işletim sistemi desteğini belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="aa2cf-117">This structure is used by the ASSEMBLYMETADATA structure to indicate its operating system support.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa2cf-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="aa2cf-118">Requirements</span></span>  
 <span data-ttu-id="aa2cf-119">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aa2cf-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa2cf-120">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="aa2cf-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="aa2cf-121">**Kütüphane:** MsCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="aa2cf-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="aa2cf-122">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aa2cf-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa2cf-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aa2cf-123">See also</span></span>

- [<span data-ttu-id="aa2cf-124">Meta Veri Yapıları</span><span class="sxs-lookup"><span data-stu-id="aa2cf-124">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [<span data-ttu-id="aa2cf-125">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="aa2cf-125">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
