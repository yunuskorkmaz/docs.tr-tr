---
title: ASM_CACHE_FLAGS Numaralandırması
ms.date: 03/30/2017
api_name:
- ASM_CACHE_FLAGS
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- ASM_CACHE_FLAGS
helpviewer_keywords:
- ASM_CACHE_FLAGS enumeration [.NET Framework fusion]
ms.assetid: 82e9a7da-321b-48b8-b239-52eaffda6be8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 619643eb50abc75fd10d59b38767013b2617c8cf
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59077784"
---
# <a name="asmcacheflags-enumeration"></a><span data-ttu-id="773c9-102">ASM_CACHE_FLAGS Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="773c9-102">ASM_CACHE_FLAGS Enumeration</span></span>
<span data-ttu-id="773c9-103">Tarafından temsil edilen bir derleme kaynağını gösterir [Iassemblycacheıtem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md) genel derleme önbelleğinde.</span><span class="sxs-lookup"><span data-stu-id="773c9-103">Indicates the source of an assembly that is represented by [IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md) in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="773c9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="773c9-104">Syntax</span></span>  
  
```  
typedef enum {  
    ASM_CACHE_ZAP       = 0x01,  
    ASM_CACHE_GAC       = 0x02,  
    ASM_CACHE_DOWNLOAD  = 0x04,  
    ASM_CACHE_ROOT      = 0x08,  
    ASM_CACHE_ROOT_EX   = 0x80  
} ASM_CACHE_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="773c9-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="773c9-105">Members</span></span>  
  
|<span data-ttu-id="773c9-106">Üye</span><span class="sxs-lookup"><span data-stu-id="773c9-106">Member</span></span>|<span data-ttu-id="773c9-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="773c9-107">Description</span></span>|  
|------------|-----------------|  
|`ASM_CACHE_ZAP`|<span data-ttu-id="773c9-108">Önceden derlenmiş bütünleştirilmiş kodlarda önbelleğini, Ngen.exe kullanarak sıralar.</span><span class="sxs-lookup"><span data-stu-id="773c9-108">Enumerates the cache of precompiled assemblies by using Ngen.exe.</span></span>|  
|`ASM_CACHE_GAC`|<span data-ttu-id="773c9-109">Genel Derleme Önbelleği numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="773c9-109">Enumerates the global assembly cache.</span></span>|  
|`ASM_CACHE_DOWNLOAD`|<span data-ttu-id="773c9-110">Gölge kopyalar silinmiş ya da isteğe bağlı olarak yüklenen derlemeleri listeler.</span><span class="sxs-lookup"><span data-stu-id="773c9-110">Enumerates the assemblies that have been downloaded on demand or that have been shadow-copied.</span></span>|  
|`ASM_CACHE_ROOT`|<span data-ttu-id="773c9-111">Bildiren [GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md) işlevi, ortak dil çalışma zamanı (CLR) sürüm 2.0 için genel bütünleştirilmiş kod önbelleğine yolu döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="773c9-111">Indicates that the [GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md) function should return the path to the global assembly cache for the common language runtime (CLR) version 2.0.</span></span> <span data-ttu-id="773c9-112">Yalnızca bir çağrı bağlamında anlamlı [GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md).</span><span class="sxs-lookup"><span data-stu-id="773c9-112">Meaningful only in the context of a call to [GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md).</span></span>|  
|`ASM_CACHE_ROOT_EX`|<span data-ttu-id="773c9-113">Bildiren [GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md) işlevi döndürmelidir yolu için genel derleme önbelleği için CLR sürüm 4.</span><span class="sxs-lookup"><span data-stu-id="773c9-113">Indicates that the [GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md) function should return the path to the global assembly cache for CLR version 4.</span></span> <span data-ttu-id="773c9-114">Yalnızca bir çağrı bağlamında anlamlı [GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md).</span><span class="sxs-lookup"><span data-stu-id="773c9-114">Meaningful only in the context of a call to [GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="773c9-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="773c9-115">Requirements</span></span>  
 <span data-ttu-id="773c9-116">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="773c9-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="773c9-117">**Üst bilgi:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="773c9-117">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="773c9-118">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="773c9-118">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="773c9-119">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="773c9-119">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="773c9-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="773c9-120">See also</span></span>

- [<span data-ttu-id="773c9-121">GetCachePath İşlevi</span><span class="sxs-lookup"><span data-stu-id="773c9-121">GetCachePath Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md)
- [<span data-ttu-id="773c9-122">IAssemblyCacheItem Arabirimi</span><span class="sxs-lookup"><span data-stu-id="773c9-122">IAssemblyCacheItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)
- [<span data-ttu-id="773c9-123">Fusion Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="773c9-123">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
