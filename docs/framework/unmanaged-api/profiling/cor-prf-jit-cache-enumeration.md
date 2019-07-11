---
title: COR_PRF_JIT_CACHE Numaralandırması
ms.date: 03/30/2017
api_name:
- COR_PRF_JIT_CACHE
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_JIT_CACHE
helpviewer_keywords:
- COR_PRF_JIT_CACHE enumeration [.NET Framework profiling]
ms.assetid: e7b8f6b4-95bc-4ba5-b9eb-f5590a7326a4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a62199563c620156885c941204207b185834beb4
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67752152"
---
# <a name="corprfjitcache-enumeration"></a><span data-ttu-id="f5ea1-102">COR_PRF_JIT_CACHE Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="f5ea1-102">COR_PRF_JIT_CACHE Enumeration</span></span>
<span data-ttu-id="f5ea1-103">Önbelleğe alınan işlevi arama sonucu gösterir.</span><span class="sxs-lookup"><span data-stu-id="f5ea1-103">Indicates the result of a cached function search.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f5ea1-104">`COR_PRF_CACHED_FUNCTION_FOUND` sıfır, bir değer serileştirilmesini `COR_PRF_JIT_CACHE` Boole bir yedek kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="f5ea1-104">`COR_PRF_CACHED_FUNCTION_FOUND` has a value of zero, so `COR_PRF_JIT_CACHE` cannot be used as a Boolean surrogate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5ea1-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f5ea1-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_CACHED_FUNCTION_FOUND,  
    COR_PRF_CACHED_FUNCTION_NOT_FOUND  
} COR_PRF_JIT_CACHE;  
```  
  
## <a name="members"></a><span data-ttu-id="f5ea1-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="f5ea1-106">Members</span></span>  
  
|<span data-ttu-id="f5ea1-107">Üye</span><span class="sxs-lookup"><span data-stu-id="f5ea1-107">Member</span></span>|<span data-ttu-id="f5ea1-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f5ea1-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FUNCTION_FOUND`|<span data-ttu-id="f5ea1-109">Arama işlevi bulunamadı.</span><span class="sxs-lookup"><span data-stu-id="f5ea1-109">The search found the function.</span></span>|  
|`COR_PRF_FUNCTION_NOT_FOUND`|<span data-ttu-id="f5ea1-110">Arama işlevi bulunamadı.</span><span class="sxs-lookup"><span data-stu-id="f5ea1-110">The search did not find the function.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f5ea1-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f5ea1-111">Requirements</span></span>  
 <span data-ttu-id="f5ea1-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5ea1-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5ea1-113">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f5ea1-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f5ea1-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f5ea1-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f5ea1-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5ea1-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5ea1-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f5ea1-116">See also</span></span>

- [<span data-ttu-id="f5ea1-117">Profil Oluşturma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="f5ea1-117">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
