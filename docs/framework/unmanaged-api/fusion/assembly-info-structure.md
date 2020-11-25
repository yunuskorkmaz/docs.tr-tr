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
ms.openlocfilehash: 520a24ced6e897d926ce68ef5973ab7083731b9d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717636"
---
# <a name="assembly_info-structure"></a><span data-ttu-id="ac10e-102">ASSEMBLY_INFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="ac10e-102">ASSEMBLY_INFO Structure</span></span>

<span data-ttu-id="ac10e-103">Genel derleme önbelleğinde kayıtlı olan bir derleme hakkındaki bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="ac10e-103">Contains information about an assembly that is registered in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac10e-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="ac10e-104">Syntax</span></span>  
  
```cpp  
typedef struct _ASSEMBLY_INFO {  
    ULONG           cbAssemblyInfo;  
    DWORD           dwAssemblyFlags;  
    ULARGE_INTEGER  uliAssemblySizeInKB;  
    LPWSTR          pszCurrentAssemblyPathBuf;  
    ULONG           cchBuf;  
} ASSEMBLY_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="ac10e-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="ac10e-105">Members</span></span>  
  
|<span data-ttu-id="ac10e-106">Üye</span><span class="sxs-lookup"><span data-stu-id="ac10e-106">Member</span></span>|<span data-ttu-id="ac10e-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ac10e-107">Description</span></span>|  
|------------|-----------------|  
|`cbAssemblyInfo`|<span data-ttu-id="ac10e-108">Yapının bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="ac10e-108">The size, in bytes, of the structure.</span></span> <span data-ttu-id="ac10e-109">Bu alan gelecekteki genişletilebilirlik için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="ac10e-109">This field is reserved for future extensibility.</span></span>|  
|`dwAssemblyFlags`|<span data-ttu-id="ac10e-110">Derlemeyle ilgili yükleme ayrıntılarını gösteren Bayraklar.</span><span class="sxs-lookup"><span data-stu-id="ac10e-110">Flags that indicate installation details about the assembly.</span></span> <span data-ttu-id="ac10e-111">Aşağıdaki değerler desteklenir:</span><span class="sxs-lookup"><span data-stu-id="ac10e-111">The following values are supported:</span></span><br /><br /> <span data-ttu-id="ac10e-112">-Derlemenin yüklendiğini gösteren ASSEMBLYINFO_FLAG_INSTALLED değeri.</span><span class="sxs-lookup"><span data-stu-id="ac10e-112">-   The ASSEMBLYINFO_FLAG_INSTALLED value, which indicates that the assembly is installed.</span></span> <span data-ttu-id="ac10e-113">.NET Framework geçerli sürümü her zaman `dwAssemblyFlags` bu değere ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="ac10e-113">The current version of the .NET Framework always sets `dwAssemblyFlags` to this value.</span></span><br /><span data-ttu-id="ac10e-114">-Derlemenin bir yük yerleşik olduğunu gösteren ASSEMBLYINFO_FLAG_PAYLOADRESIDENT değeri.</span><span class="sxs-lookup"><span data-stu-id="ac10e-114">-   The ASSEMBLYINFO_FLAG_PAYLOADRESIDENT value, which indicates that the assembly is a payload resident.</span></span> <span data-ttu-id="ac10e-115">.NET Framework geçerli sürümü hiçbir `dwAssemblyFlags` şekilde bu değere ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="ac10e-115">The current version of the .NET Framework never sets `dwAssemblyFlags` to this value.</span></span>|  
|`uliAssemblySizeInKB`|<span data-ttu-id="ac10e-116">Derlemenin içerdiği dosyaların kilobayt cinsinden toplam boyutu.</span><span class="sxs-lookup"><span data-stu-id="ac10e-116">The total size, in kilobytes, of the files that the assembly contains.</span></span>|  
|`pszCurrentAssemblyPathBuf`|<span data-ttu-id="ac10e-117">Bildirim dosyasının geçerli yolunu tutan bir dize arabelleği işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="ac10e-117">A pointer to a string buffer that holds the current path to the manifest file.</span></span> <span data-ttu-id="ac10e-118">Yol, null bir karakterle bitmelidir.</span><span class="sxs-lookup"><span data-stu-id="ac10e-118">The path must end with a null character.</span></span>|  
|`cchBuf`|<span data-ttu-id="ac10e-119">İçeren null Sonlandırıcı dahil olmak üzere geniş karakter sayısı `pszCurrentAssemblyPathBuf` .</span><span class="sxs-lookup"><span data-stu-id="ac10e-119">The number of wide characters, including the null terminator, that `pszCurrentAssemblyPathBuf` contains.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ac10e-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ac10e-120">Requirements</span></span>  

 <span data-ttu-id="ac10e-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac10e-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac10e-122">**Üst bilgi:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="ac10e-122">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="ac10e-123">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac10e-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac10e-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ac10e-124">See also</span></span>

- [<span data-ttu-id="ac10e-125">Fusion Yapıları</span><span class="sxs-lookup"><span data-stu-id="ac10e-125">Fusion Structures</span></span>](fusion-structures.md)
- [<span data-ttu-id="ac10e-126">Genel Derleme Önbelleği</span><span class="sxs-lookup"><span data-stu-id="ac10e-126">Global Assembly Cache</span></span>](../../app-domains/gac.md)
