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
ms.openlocfilehash: 5b712c6ae5978e83dab085f48dd1fd572757384a
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2018
ms.locfileid: "45990498"
---
# <a name="asmcacheflags-enumeration"></a><span data-ttu-id="3adcd-102">ASM_CACHE_FLAGS Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="3adcd-102">ASM_CACHE_FLAGS Enumeration</span></span>
<span data-ttu-id="3adcd-103">Tarafından temsil edilen bir derleme kaynağını gösterir [Iassemblycacheıtem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md) genel derleme önbelleğinde.</span><span class="sxs-lookup"><span data-stu-id="3adcd-103">Indicates the source of an assembly that is represented by [IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md) in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3adcd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3adcd-104">Syntax</span></span>  
  
```  
typedef enum {  
    ASM_CACHE_ZAP       = 0x01,  
    ASM_CACHE_GAC       = 0x02,  
    ASM_CACHE_DOWNLOAD  = 0x04,  
    ASM_CACHE_ROOT      = 0x08,  
    ASM_CACHE_ROOT_EX   = 0x80  
} ASM_CACHE_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="3adcd-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="3adcd-105">Members</span></span>  
  
|<span data-ttu-id="3adcd-106">Üye</span><span class="sxs-lookup"><span data-stu-id="3adcd-106">Member</span></span>|<span data-ttu-id="3adcd-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3adcd-107">Description</span></span>|  
|------------|-----------------|  
|`ASM_CACHE_ZAP`|<span data-ttu-id="3adcd-108">Önceden derlenmiş bütünleştirilmiş kodlarda önbelleğini, Ngen.exe kullanarak sıralar.</span><span class="sxs-lookup"><span data-stu-id="3adcd-108">Enumerates the cache of precompiled assemblies by using Ngen.exe.</span></span>|  
|`ASM_CACHE_GAC`|<span data-ttu-id="3adcd-109">Genel Derleme Önbelleği numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="3adcd-109">Enumerates the global assembly cache.</span></span>|  
|`ASM_CACHE_DOWNLOAD`|<span data-ttu-id="3adcd-110">Gölge kopyalar silinmiş ya da isteğe bağlı olarak yüklenen derlemeleri listeler.</span><span class="sxs-lookup"><span data-stu-id="3adcd-110">Enumerates the assemblies that have been downloaded on demand or that have been shadow-copied.</span></span>|  
|`ASM_CACHE_ROOT`|<span data-ttu-id="3adcd-111">Bildiren [GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md) işlevi, ortak dil çalışma zamanı (CLR) sürüm 2.0 için genel bütünleştirilmiş kod önbelleğine yolu döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="3adcd-111">Indicates that the [GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md) function should return the path to the global assembly cache for the common language runtime (CLR) version 2.0.</span></span> <span data-ttu-id="3adcd-112">Yalnızca bir çağrı bağlamında anlamlı [GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md).</span><span class="sxs-lookup"><span data-stu-id="3adcd-112">Meaningful only in the context of a call to [GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md).</span></span>|  
|`ASM_CACHE_ROOT_EX`|<span data-ttu-id="3adcd-113">Bildiren [GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md) işlevi döndürmelidir yolu için genel derleme önbelleği için CLR sürüm 4.</span><span class="sxs-lookup"><span data-stu-id="3adcd-113">Indicates that the [GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md) function should return the path to the global assembly cache for CLR version 4.</span></span> <span data-ttu-id="3adcd-114">Yalnızca bir çağrı bağlamında anlamlı [GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md).</span><span class="sxs-lookup"><span data-stu-id="3adcd-114">Meaningful only in the context of a call to [GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3adcd-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3adcd-115">Requirements</span></span>  
 <span data-ttu-id="3adcd-116">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3adcd-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3adcd-117">**Başlık:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="3adcd-117">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="3adcd-118">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="3adcd-118">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3adcd-119">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3adcd-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3adcd-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3adcd-120">See Also</span></span>  
 [<span data-ttu-id="3adcd-121">GetCachePath İşlevi</span><span class="sxs-lookup"><span data-stu-id="3adcd-121">GetCachePath Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md)  
 [<span data-ttu-id="3adcd-122">IAssemblyCacheItem Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3adcd-122">IAssemblyCacheItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)  
 [<span data-ttu-id="3adcd-123">Fusion Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="3adcd-123">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
