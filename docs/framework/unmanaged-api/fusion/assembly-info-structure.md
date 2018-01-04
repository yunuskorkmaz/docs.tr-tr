---
title: "ASSEMBLY_INFO Yapısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ASSEMBLY_INFO
api_location: fusion.dll
api_type: COM
f1_keywords: ASSEMBLY_INFO
helpviewer_keywords: ASSEMBLY_INFO structure [.NET Framework fusion]
ms.assetid: b3cbb47c-457f-4083-8895-49562ca99ab8
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 215d80c3d207c2f50cfbd74386915b0467692b57
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="assemblyinfo-structure"></a><span data-ttu-id="4b265-102">ASSEMBLY_INFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="4b265-102">ASSEMBLY_INFO Structure</span></span>
<span data-ttu-id="4b265-103">Genel Derleme Önbelleği'nde kayıtlı bir derlemeyle ilgili bilgiler içerir.</span><span class="sxs-lookup"><span data-stu-id="4b265-103">Contains information about an assembly that is registered in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b265-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4b265-104">Syntax</span></span>  
  
```  
typedef struct _ASSEMBLY_INFO {  
    ULONG           cbAssemblyInfo;  
    DWORD           dwAssemblyFlags;  
    ULARGE_INTEGER  uliAssemblySizeInKB;  
    LPWSTR          pszCurrentAssemblyPathBuf;  
    ULONG           cchBuf;  
} ASSEMBLY_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="4b265-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="4b265-105">Members</span></span>  
  
|<span data-ttu-id="4b265-106">Üye</span><span class="sxs-lookup"><span data-stu-id="4b265-106">Member</span></span>|<span data-ttu-id="4b265-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4b265-107">Description</span></span>|  
|------------|-----------------|  
|`cbAssemblyInfo`|<span data-ttu-id="4b265-108">Yapısı bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="4b265-108">The size, in bytes, of the structure.</span></span> <span data-ttu-id="4b265-109">Bu alan, gelecekteki genişletilebilirliği için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="4b265-109">This field is reserved for future extensibility.</span></span>|  
|`dwAssemblyFlags`|<span data-ttu-id="4b265-110">Derleme yükleme ayrıntılarını belirtmek bayraklar.</span><span class="sxs-lookup"><span data-stu-id="4b265-110">Flags that indicate installation details about the assembly.</span></span> <span data-ttu-id="4b265-111">Aşağıdaki değerleri desteklenir:</span><span class="sxs-lookup"><span data-stu-id="4b265-111">The following values are supported:</span></span><br /><br /> <span data-ttu-id="4b265-112">-Derleme yüklendiğini gösterir ASSEMBLYINFO_FLAG_INSTALLED değeri.</span><span class="sxs-lookup"><span data-stu-id="4b265-112">-   The ASSEMBLYINFO_FLAG_INSTALLED value, which indicates that the assembly is installed.</span></span> <span data-ttu-id="4b265-113">Geçerli .NET Framework sürümü her zaman ayarlar `dwAssemblyFlags` bu değeri.</span><span class="sxs-lookup"><span data-stu-id="4b265-113">The current version of the .NET Framework always sets `dwAssemblyFlags` to this value.</span></span><br /><span data-ttu-id="4b265-114">-Yerleşik bir yükü derleme gösterir ASSEMBLYINFO_FLAG_PAYLOADRESIDENT değeri.</span><span class="sxs-lookup"><span data-stu-id="4b265-114">-   The ASSEMBLYINFO_FLAG_PAYLOADRESIDENT value, which indicates that the assembly is a payload resident.</span></span> <span data-ttu-id="4b265-115">Geçerli .NET Framework sürümünü hiçbir zaman ayarlar `dwAssemblyFlags` bu değeri.</span><span class="sxs-lookup"><span data-stu-id="4b265-115">The current version of the .NET Framework never sets `dwAssemblyFlags` to this value.</span></span>|  
|`uliAssemblySizeInKB`|<span data-ttu-id="4b265-116">Derleme içeren dosyalarının kilobayt cinsinden toplam boyutu.</span><span class="sxs-lookup"><span data-stu-id="4b265-116">The total size, in kilobytes, of the files that the assembly contains.</span></span>|  
|`pszCurrentAssemblyPathBuf`|<span data-ttu-id="4b265-117">Bildirim dosyasının geçerli yolunu tutan bir dize arabellek için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4b265-117">A pointer to a string buffer that holds the current path to the manifest file.</span></span> <span data-ttu-id="4b265-118">Yolun bir null karakteri ile bitmelidir.</span><span class="sxs-lookup"><span data-stu-id="4b265-118">The path must end with a null character.</span></span>|  
|`cchBuf`|<span data-ttu-id="4b265-119">Null Sonlandırıcı dahil olmak üzere geniş karakter sayısını, `pszCurrentAssemblyPathBuf` içerir.</span><span class="sxs-lookup"><span data-stu-id="4b265-119">The number of wide characters, including the null terminator, that `pszCurrentAssemblyPathBuf` contains.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4b265-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4b265-120">Requirements</span></span>  
 <span data-ttu-id="4b265-121">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4b265-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b265-122">**Başlık:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="4b265-122">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="4b265-123">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b265-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b265-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4b265-124">See Also</span></span>  
 [<span data-ttu-id="4b265-125">Fusion Yapıları</span><span class="sxs-lookup"><span data-stu-id="4b265-125">Fusion Structures</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)  
 [<span data-ttu-id="4b265-126">Genel Derleme Önbelleği</span><span class="sxs-lookup"><span data-stu-id="4b265-126">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)
