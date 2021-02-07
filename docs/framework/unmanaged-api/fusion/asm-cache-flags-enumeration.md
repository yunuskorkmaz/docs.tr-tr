---
description: 'Hakkında daha fazla bilgi edinin: ASM_CACHE_FLAGS numaralandırması'
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
ms.openlocfilehash: 866f61d2960074495ed036e3a8e89ebceec74e87
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761440"
---
# <a name="asm_cache_flags-enumeration"></a><span data-ttu-id="0faab-103">ASM_CACHE_FLAGS Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="0faab-103">ASM_CACHE_FLAGS Enumeration</span></span>

<span data-ttu-id="0faab-104">Genel derleme önbelleğinde [IAssemblyCacheItem](iassemblycacheitem-interface.md) tarafından temsil edilen bir derlemenin kaynağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0faab-104">Indicates the source of an assembly that is represented by [IAssemblyCacheItem](iassemblycacheitem-interface.md) in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0faab-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="0faab-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    ASM_CACHE_ZAP       = 0x01,  
    ASM_CACHE_GAC       = 0x02,  
    ASM_CACHE_DOWNLOAD  = 0x04,  
    ASM_CACHE_ROOT      = 0x08,  
    ASM_CACHE_ROOT_EX   = 0x80  
} ASM_CACHE_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="0faab-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="0faab-106">Members</span></span>  
  
|<span data-ttu-id="0faab-107">Üye</span><span class="sxs-lookup"><span data-stu-id="0faab-107">Member</span></span>|<span data-ttu-id="0faab-108">Description</span><span class="sxs-lookup"><span data-stu-id="0faab-108">Description</span></span>|  
|------------|-----------------|  
|`ASM_CACHE_ZAP`|<span data-ttu-id="0faab-109">Ngen.exe kullanarak önceden derlenmiş derlemelerin önbelleğini sıralar.</span><span class="sxs-lookup"><span data-stu-id="0faab-109">Enumerates the cache of precompiled assemblies by using Ngen.exe.</span></span>|  
|`ASM_CACHE_GAC`|<span data-ttu-id="0faab-110">Genel derleme önbelleğini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="0faab-110">Enumerates the global assembly cache.</span></span>|  
|`ASM_CACHE_DOWNLOAD`|<span data-ttu-id="0faab-111">İsteğe bağlı olarak indirilen veya gölge kopyalanmış derlemeleri numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="0faab-111">Enumerates the assemblies that have been downloaded on demand or that have been shadow-copied.</span></span>|  
|`ASM_CACHE_ROOT`|<span data-ttu-id="0faab-112">[GetCachePath](getcachepath-function.md) işlevinin, ortak dil çalışma zamanı (CLR) sürüm 2,0 için genel derleme önbelleği yolunu döndürmesi gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="0faab-112">Indicates that the [GetCachePath](getcachepath-function.md) function should return the path to the global assembly cache for the common language runtime (CLR) version 2.0.</span></span> <span data-ttu-id="0faab-113">Yalnızca bir [GetCachePath](getcachepath-function.md)çağrısı bağlamında anlamlıdır.</span><span class="sxs-lookup"><span data-stu-id="0faab-113">Meaningful only in the context of a call to [GetCachePath](getcachepath-function.md).</span></span>|  
|`ASM_CACHE_ROOT_EX`|<span data-ttu-id="0faab-114">[GetCachePath](getcachepath-function.md) işlevinin CLR sürüm 4 için genel derleme önbelleğinin yolunu döndürmesi gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="0faab-114">Indicates that the [GetCachePath](getcachepath-function.md) function should return the path to the global assembly cache for CLR version 4.</span></span> <span data-ttu-id="0faab-115">Yalnızca bir [GetCachePath](getcachepath-function.md)çağrısı bağlamında anlamlıdır.</span><span class="sxs-lookup"><span data-stu-id="0faab-115">Meaningful only in the context of a call to [GetCachePath](getcachepath-function.md).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0faab-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0faab-116">Requirements</span></span>  

 <span data-ttu-id="0faab-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0faab-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0faab-118">**Üst bilgi:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="0faab-118">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="0faab-119">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="0faab-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0faab-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0faab-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0faab-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0faab-121">See also</span></span>

- [<span data-ttu-id="0faab-122">GetCachePath İşlevi</span><span class="sxs-lookup"><span data-stu-id="0faab-122">GetCachePath Function</span></span>](getcachepath-function.md)
- [<span data-ttu-id="0faab-123">IAssemblyCacheItem Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0faab-123">IAssemblyCacheItem Interface</span></span>](iassemblycacheitem-interface.md)
- [<span data-ttu-id="0faab-124">Fusion Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="0faab-124">Fusion Enumerations</span></span>](fusion-enumerations.md)
