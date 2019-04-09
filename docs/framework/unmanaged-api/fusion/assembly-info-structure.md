---
title: ASSEMBLY_INFO Yapısı
ms.date: 03/30/2017
api_name:
- ASSEMBLY_INFO
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- ASSEMBLY_INFO
helpviewer_keywords:
- ASSEMBLY_INFO structure [.NET Framework fusion]
ms.assetid: b3cbb47c-457f-4083-8895-49562ca99ab8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bae19ec18c54eccc7aa54d2d3a006f36ba8ab762
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59110883"
---
# <a name="assemblyinfo-structure"></a><span data-ttu-id="51110-102">ASSEMBLY_INFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="51110-102">ASSEMBLY_INFO Structure</span></span>
<span data-ttu-id="51110-103">Genel derleme önbelleğinde kayıtlı bir derlemeyle ilgili bilgiler içerir.</span><span class="sxs-lookup"><span data-stu-id="51110-103">Contains information about an assembly that is registered in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51110-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="51110-104">Syntax</span></span>  
  
```  
typedef struct _ASSEMBLY_INFO {  
    ULONG           cbAssemblyInfo;  
    DWORD           dwAssemblyFlags;  
    ULARGE_INTEGER  uliAssemblySizeInKB;  
    LPWSTR          pszCurrentAssemblyPathBuf;  
    ULONG           cchBuf;  
} ASSEMBLY_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="51110-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="51110-105">Members</span></span>  
  
|<span data-ttu-id="51110-106">Üye</span><span class="sxs-lookup"><span data-stu-id="51110-106">Member</span></span>|<span data-ttu-id="51110-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="51110-107">Description</span></span>|  
|------------|-----------------|  
|`cbAssemblyInfo`|<span data-ttu-id="51110-108">Yapının bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="51110-108">The size, in bytes, of the structure.</span></span> <span data-ttu-id="51110-109">Bu alan sonra genişletilebilmek için ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="51110-109">This field is reserved for future extensibility.</span></span>|  
|`dwAssemblyFlags`|<span data-ttu-id="51110-110">Derlemeyle ilgili yükleme ayrıntılarını gösteren bayrak.</span><span class="sxs-lookup"><span data-stu-id="51110-110">Flags that indicate installation details about the assembly.</span></span> <span data-ttu-id="51110-111">Aşağıdaki değerleri desteklenir:</span><span class="sxs-lookup"><span data-stu-id="51110-111">The following values are supported:</span></span><br /><br /> <span data-ttu-id="51110-112">-Derleme yüklü olduğunu gösterecek ASSEMBLYINFO_FLAG_INSTALLED değeri.</span><span class="sxs-lookup"><span data-stu-id="51110-112">-   The ASSEMBLYINFO_FLAG_INSTALLED value, which indicates that the assembly is installed.</span></span> <span data-ttu-id="51110-113">Her zaman geçerli sürümü .NET Framework'ün ayarlar `dwAssemblyFlags` şu değer.</span><span class="sxs-lookup"><span data-stu-id="51110-113">The current version of the .NET Framework always sets `dwAssemblyFlags` to this value.</span></span><br /><span data-ttu-id="51110-114">-Yerleşik bir yükü derleme gösterir ASSEMBLYINFO_FLAG_PAYLOADRESIDENT değeri.</span><span class="sxs-lookup"><span data-stu-id="51110-114">-   The ASSEMBLYINFO_FLAG_PAYLOADRESIDENT value, which indicates that the assembly is a payload resident.</span></span> <span data-ttu-id="51110-115">Hiçbir zaman geçerli sürümü .NET Framework'ün ayarlar `dwAssemblyFlags` şu değer.</span><span class="sxs-lookup"><span data-stu-id="51110-115">The current version of the .NET Framework never sets `dwAssemblyFlags` to this value.</span></span>|  
|`uliAssemblySizeInKB`|<span data-ttu-id="51110-116">İçeren derleme dosyalarının kilobayt cinsinden toplam boyutu.</span><span class="sxs-lookup"><span data-stu-id="51110-116">The total size, in kilobytes, of the files that the assembly contains.</span></span>|  
|`pszCurrentAssemblyPathBuf`|<span data-ttu-id="51110-117">Bildirim dosyası için geçerli yol tutan dize arabellek için işaretçi.</span><span class="sxs-lookup"><span data-stu-id="51110-117">A pointer to a string buffer that holds the current path to the manifest file.</span></span> <span data-ttu-id="51110-118">Yol, bir null karakterle bitmelidir.</span><span class="sxs-lookup"><span data-stu-id="51110-118">The path must end with a null character.</span></span>|  
|`cchBuf`|<span data-ttu-id="51110-119">Null sonlandırıcıyı da dahil olmak üzere geniş karakter sayısı, `pszCurrentAssemblyPathBuf` içerir.</span><span class="sxs-lookup"><span data-stu-id="51110-119">The number of wide characters, including the null terminator, that `pszCurrentAssemblyPathBuf` contains.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="51110-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="51110-120">Requirements</span></span>  
 <span data-ttu-id="51110-121">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="51110-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51110-122">**Üst bilgi:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="51110-122">**Header:** Fusion.h</span></span>  
  
 **<span data-ttu-id="51110-123">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="51110-123">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="51110-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="51110-124">See also</span></span>

- [<span data-ttu-id="51110-125">Fusion Yapıları</span><span class="sxs-lookup"><span data-stu-id="51110-125">Fusion Structures</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)
- [<span data-ttu-id="51110-126">Genel Derleme Önbelleği</span><span class="sxs-lookup"><span data-stu-id="51110-126">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)
