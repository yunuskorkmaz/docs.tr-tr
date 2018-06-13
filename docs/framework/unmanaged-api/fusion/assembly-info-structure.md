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
ms.openlocfilehash: 9ed65181abab58117d539d23fcfeffe71ac19388
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33430576"
---
# <a name="assemblyinfo-structure"></a><span data-ttu-id="7053b-102">ASSEMBLY_INFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="7053b-102">ASSEMBLY_INFO Structure</span></span>
<span data-ttu-id="7053b-103">Genel Derleme Önbelleği'nde kayıtlı bir derlemeyle ilgili bilgiler içerir.</span><span class="sxs-lookup"><span data-stu-id="7053b-103">Contains information about an assembly that is registered in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7053b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7053b-104">Syntax</span></span>  
  
```  
typedef struct _ASSEMBLY_INFO {  
    ULONG           cbAssemblyInfo;  
    DWORD           dwAssemblyFlags;  
    ULARGE_INTEGER  uliAssemblySizeInKB;  
    LPWSTR          pszCurrentAssemblyPathBuf;  
    ULONG           cchBuf;  
} ASSEMBLY_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="7053b-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="7053b-105">Members</span></span>  
  
|<span data-ttu-id="7053b-106">Üye</span><span class="sxs-lookup"><span data-stu-id="7053b-106">Member</span></span>|<span data-ttu-id="7053b-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7053b-107">Description</span></span>|  
|------------|-----------------|  
|`cbAssemblyInfo`|<span data-ttu-id="7053b-108">Yapısı bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="7053b-108">The size, in bytes, of the structure.</span></span> <span data-ttu-id="7053b-109">Bu alan, gelecekteki genişletilebilirliği için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="7053b-109">This field is reserved for future extensibility.</span></span>|  
|`dwAssemblyFlags`|<span data-ttu-id="7053b-110">Derleme yükleme ayrıntılarını belirtmek bayraklar.</span><span class="sxs-lookup"><span data-stu-id="7053b-110">Flags that indicate installation details about the assembly.</span></span> <span data-ttu-id="7053b-111">Aşağıdaki değerleri desteklenir:</span><span class="sxs-lookup"><span data-stu-id="7053b-111">The following values are supported:</span></span><br /><br /> <span data-ttu-id="7053b-112">-Derleme yüklendiğini gösterir ASSEMBLYINFO_FLAG_INSTALLED değeri.</span><span class="sxs-lookup"><span data-stu-id="7053b-112">-   The ASSEMBLYINFO_FLAG_INSTALLED value, which indicates that the assembly is installed.</span></span> <span data-ttu-id="7053b-113">Geçerli .NET Framework sürümü her zaman ayarlar `dwAssemblyFlags` bu değeri.</span><span class="sxs-lookup"><span data-stu-id="7053b-113">The current version of the .NET Framework always sets `dwAssemblyFlags` to this value.</span></span><br /><span data-ttu-id="7053b-114">-Yerleşik bir yükü derleme gösterir ASSEMBLYINFO_FLAG_PAYLOADRESIDENT değeri.</span><span class="sxs-lookup"><span data-stu-id="7053b-114">-   The ASSEMBLYINFO_FLAG_PAYLOADRESIDENT value, which indicates that the assembly is a payload resident.</span></span> <span data-ttu-id="7053b-115">Geçerli .NET Framework sürümünü hiçbir zaman ayarlar `dwAssemblyFlags` bu değeri.</span><span class="sxs-lookup"><span data-stu-id="7053b-115">The current version of the .NET Framework never sets `dwAssemblyFlags` to this value.</span></span>|  
|`uliAssemblySizeInKB`|<span data-ttu-id="7053b-116">Derleme içeren dosyalarının kilobayt cinsinden toplam boyutu.</span><span class="sxs-lookup"><span data-stu-id="7053b-116">The total size, in kilobytes, of the files that the assembly contains.</span></span>|  
|`pszCurrentAssemblyPathBuf`|<span data-ttu-id="7053b-117">Bildirim dosyasının geçerli yolunu tutan bir dize arabellek için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7053b-117">A pointer to a string buffer that holds the current path to the manifest file.</span></span> <span data-ttu-id="7053b-118">Yolun bir null karakteri ile bitmelidir.</span><span class="sxs-lookup"><span data-stu-id="7053b-118">The path must end with a null character.</span></span>|  
|`cchBuf`|<span data-ttu-id="7053b-119">Null Sonlandırıcı dahil olmak üzere geniş karakter sayısını, `pszCurrentAssemblyPathBuf` içerir.</span><span class="sxs-lookup"><span data-stu-id="7053b-119">The number of wide characters, including the null terminator, that `pszCurrentAssemblyPathBuf` contains.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7053b-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7053b-120">Requirements</span></span>  
 <span data-ttu-id="7053b-121">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7053b-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7053b-122">**Başlık:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="7053b-122">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="7053b-123">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7053b-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7053b-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7053b-124">See Also</span></span>  
 [<span data-ttu-id="7053b-125">Fusion Yapıları</span><span class="sxs-lookup"><span data-stu-id="7053b-125">Fusion Structures</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)  
 [<span data-ttu-id="7053b-126">Genel Derleme Önbelleği</span><span class="sxs-lookup"><span data-stu-id="7053b-126">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)
