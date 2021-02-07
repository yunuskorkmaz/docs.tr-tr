---
description: 'Daha fazla bilgi edinin: ASSEMBLY_INFO yapısı'
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
ms.openlocfilehash: c28d9abf13769197b62705d51bbcf4f099616bbc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761294"
---
# <a name="assembly_info-structure"></a><span data-ttu-id="0b8d0-103">ASSEMBLY_INFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="0b8d0-103">ASSEMBLY_INFO Structure</span></span>

<span data-ttu-id="0b8d0-104">Genel derleme önbelleğinde kayıtlı olan bir derleme hakkındaki bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="0b8d0-104">Contains information about an assembly that is registered in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b8d0-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="0b8d0-105">Syntax</span></span>  
  
```cpp  
typedef struct _ASSEMBLY_INFO {  
    ULONG           cbAssemblyInfo;  
    DWORD           dwAssemblyFlags;  
    ULARGE_INTEGER  uliAssemblySizeInKB;  
    LPWSTR          pszCurrentAssemblyPathBuf;  
    ULONG           cchBuf;  
} ASSEMBLY_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="0b8d0-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="0b8d0-106">Members</span></span>  
  
|<span data-ttu-id="0b8d0-107">Üye</span><span class="sxs-lookup"><span data-stu-id="0b8d0-107">Member</span></span>|<span data-ttu-id="0b8d0-108">Description</span><span class="sxs-lookup"><span data-stu-id="0b8d0-108">Description</span></span>|  
|------------|-----------------|  
|`cbAssemblyInfo`|<span data-ttu-id="0b8d0-109">Yapının bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="0b8d0-109">The size, in bytes, of the structure.</span></span> <span data-ttu-id="0b8d0-110">Bu alan gelecekteki genişletilebilirlik için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="0b8d0-110">This field is reserved for future extensibility.</span></span>|  
|`dwAssemblyFlags`|<span data-ttu-id="0b8d0-111">Derlemeyle ilgili yükleme ayrıntılarını gösteren Bayraklar.</span><span class="sxs-lookup"><span data-stu-id="0b8d0-111">Flags that indicate installation details about the assembly.</span></span> <span data-ttu-id="0b8d0-112">Aşağıdaki değerler desteklenir:</span><span class="sxs-lookup"><span data-stu-id="0b8d0-112">The following values are supported:</span></span><br /><br /> <span data-ttu-id="0b8d0-113">-Derlemenin yüklendiğini gösteren ASSEMBLYINFO_FLAG_INSTALLED değeri.</span><span class="sxs-lookup"><span data-stu-id="0b8d0-113">-   The ASSEMBLYINFO_FLAG_INSTALLED value, which indicates that the assembly is installed.</span></span> <span data-ttu-id="0b8d0-114">.NET Framework geçerli sürümü her zaman `dwAssemblyFlags` bu değere ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="0b8d0-114">The current version of the .NET Framework always sets `dwAssemblyFlags` to this value.</span></span><br /><span data-ttu-id="0b8d0-115">-Derlemenin bir yük yerleşik olduğunu gösteren ASSEMBLYINFO_FLAG_PAYLOADRESIDENT değeri.</span><span class="sxs-lookup"><span data-stu-id="0b8d0-115">-   The ASSEMBLYINFO_FLAG_PAYLOADRESIDENT value, which indicates that the assembly is a payload resident.</span></span> <span data-ttu-id="0b8d0-116">.NET Framework geçerli sürümü hiçbir `dwAssemblyFlags` şekilde bu değere ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="0b8d0-116">The current version of the .NET Framework never sets `dwAssemblyFlags` to this value.</span></span>|  
|`uliAssemblySizeInKB`|<span data-ttu-id="0b8d0-117">Derlemenin içerdiği dosyaların kilobayt cinsinden toplam boyutu.</span><span class="sxs-lookup"><span data-stu-id="0b8d0-117">The total size, in kilobytes, of the files that the assembly contains.</span></span>|  
|`pszCurrentAssemblyPathBuf`|<span data-ttu-id="0b8d0-118">Bildirim dosyasının geçerli yolunu tutan bir dize arabelleği işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="0b8d0-118">A pointer to a string buffer that holds the current path to the manifest file.</span></span> <span data-ttu-id="0b8d0-119">Yol, null bir karakterle bitmelidir.</span><span class="sxs-lookup"><span data-stu-id="0b8d0-119">The path must end with a null character.</span></span>|  
|`cchBuf`|<span data-ttu-id="0b8d0-120">İçeren null Sonlandırıcı dahil olmak üzere geniş karakter sayısı `pszCurrentAssemblyPathBuf` .</span><span class="sxs-lookup"><span data-stu-id="0b8d0-120">The number of wide characters, including the null terminator, that `pszCurrentAssemblyPathBuf` contains.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0b8d0-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0b8d0-121">Requirements</span></span>  

 <span data-ttu-id="0b8d0-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b8d0-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b8d0-123">**Üst bilgi:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="0b8d0-123">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="0b8d0-124">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b8d0-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b8d0-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0b8d0-125">See also</span></span>

- [<span data-ttu-id="0b8d0-126">Fusion Yapıları</span><span class="sxs-lookup"><span data-stu-id="0b8d0-126">Fusion Structures</span></span>](fusion-structures.md)
- [<span data-ttu-id="0b8d0-127">Genel Derleme Önbelleği</span><span class="sxs-lookup"><span data-stu-id="0b8d0-127">Global Assembly Cache</span></span>](../../app-domains/gac.md)
