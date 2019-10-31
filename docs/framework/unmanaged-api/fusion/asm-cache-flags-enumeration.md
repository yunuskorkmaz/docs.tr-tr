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
ms.openlocfilehash: 85ac976daec8fd76ee21012a30611235609f4b34
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73109489"
---
# <a name="asm_cache_flags-enumeration"></a><span data-ttu-id="8eb14-102">ASM_CACHE_FLAGS Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="8eb14-102">ASM_CACHE_FLAGS Enumeration</span></span>
<span data-ttu-id="8eb14-103">Genel derleme önbelleğinde [IAssemblyCacheItem](iassemblycacheitem-interface.md) tarafından temsil edilen bir derlemenin kaynağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8eb14-103">Indicates the source of an assembly that is represented by [IAssemblyCacheItem](iassemblycacheitem-interface.md) in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8eb14-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8eb14-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    ASM_CACHE_ZAP       = 0x01,  
    ASM_CACHE_GAC       = 0x02,  
    ASM_CACHE_DOWNLOAD  = 0x04,  
    ASM_CACHE_ROOT      = 0x08,  
    ASM_CACHE_ROOT_EX   = 0x80  
} ASM_CACHE_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="8eb14-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="8eb14-105">Members</span></span>  
  
|<span data-ttu-id="8eb14-106">Üye</span><span class="sxs-lookup"><span data-stu-id="8eb14-106">Member</span></span>|<span data-ttu-id="8eb14-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8eb14-107">Description</span></span>|  
|------------|-----------------|  
|`ASM_CACHE_ZAP`|<span data-ttu-id="8eb14-108">Ngen. exe ' yi kullanarak önceden derlenmiş derlemelerin önbelleğini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="8eb14-108">Enumerates the cache of precompiled assemblies by using Ngen.exe.</span></span>|  
|`ASM_CACHE_GAC`|<span data-ttu-id="8eb14-109">Genel derleme önbelleğini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="8eb14-109">Enumerates the global assembly cache.</span></span>|  
|`ASM_CACHE_DOWNLOAD`|<span data-ttu-id="8eb14-110">İsteğe bağlı olarak indirilen veya gölge kopyalanmış derlemeleri numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="8eb14-110">Enumerates the assemblies that have been downloaded on demand or that have been shadow-copied.</span></span>|  
|`ASM_CACHE_ROOT`|<span data-ttu-id="8eb14-111">[GetCachePath](getcachepath-function.md) işlevinin, ortak dil çalışma zamanı (CLR) sürüm 2,0 için genel derleme önbelleği yolunu döndürmesi gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="8eb14-111">Indicates that the [GetCachePath](getcachepath-function.md) function should return the path to the global assembly cache for the common language runtime (CLR) version 2.0.</span></span> <span data-ttu-id="8eb14-112">Yalnızca bir [GetCachePath](getcachepath-function.md)çağrısı bağlamında anlamlıdır.</span><span class="sxs-lookup"><span data-stu-id="8eb14-112">Meaningful only in the context of a call to [GetCachePath](getcachepath-function.md).</span></span>|  
|`ASM_CACHE_ROOT_EX`|<span data-ttu-id="8eb14-113">[GetCachePath](getcachepath-function.md) işlevinin CLR sürüm 4 için genel derleme önbelleğinin yolunu döndürmesi gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="8eb14-113">Indicates that the [GetCachePath](getcachepath-function.md) function should return the path to the global assembly cache for CLR version 4.</span></span> <span data-ttu-id="8eb14-114">Yalnızca bir [GetCachePath](getcachepath-function.md)çağrısı bağlamında anlamlıdır.</span><span class="sxs-lookup"><span data-stu-id="8eb14-114">Meaningful only in the context of a call to [GetCachePath](getcachepath-function.md).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8eb14-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8eb14-115">Requirements</span></span>  
 <span data-ttu-id="8eb14-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8eb14-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8eb14-117">**Üst bilgi:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="8eb14-117">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="8eb14-118">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="8eb14-118">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8eb14-119">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8eb14-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8eb14-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8eb14-120">See also</span></span>

- [<span data-ttu-id="8eb14-121">GetCachePath İşlevi</span><span class="sxs-lookup"><span data-stu-id="8eb14-121">GetCachePath Function</span></span>](getcachepath-function.md)
- [<span data-ttu-id="8eb14-122">IAssemblyCacheItem Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8eb14-122">IAssemblyCacheItem Interface</span></span>](iassemblycacheitem-interface.md)
- [<span data-ttu-id="8eb14-123">Fusion Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="8eb14-123">Fusion Enumerations</span></span>](fusion-enumerations.md)
