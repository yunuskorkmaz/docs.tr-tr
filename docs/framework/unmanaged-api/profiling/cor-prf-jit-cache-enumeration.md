---
description: 'Hakkında daha fazla bilgi edinin: COR_PRF_JIT_CACHE numaralandırması'
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
ms.openlocfilehash: 94b04b42504760be826f78cee0da3066f1936f32
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99648759"
---
# <a name="cor_prf_jit_cache-enumeration"></a><span data-ttu-id="42edd-103">COR_PRF_JIT_CACHE Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="42edd-103">COR_PRF_JIT_CACHE Enumeration</span></span>

<span data-ttu-id="42edd-104">Önbelleğe alınmış işlev aramasının sonucunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="42edd-104">Indicates the result of a cached function search.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="42edd-105">`COR_PRF_CACHED_FUNCTION_FOUND` sıfır değerine sahiptir, bu nedenle `COR_PRF_JIT_CACHE` Boole yedeği olarak kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="42edd-105">`COR_PRF_CACHED_FUNCTION_FOUND` has a value of zero, so `COR_PRF_JIT_CACHE` cannot be used as a Boolean surrogate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42edd-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="42edd-106">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_CACHED_FUNCTION_FOUND,  
    COR_PRF_CACHED_FUNCTION_NOT_FOUND  
} COR_PRF_JIT_CACHE;  
```  
  
## <a name="members"></a><span data-ttu-id="42edd-107">Üyeler</span><span class="sxs-lookup"><span data-stu-id="42edd-107">Members</span></span>  
  
|<span data-ttu-id="42edd-108">Üye</span><span class="sxs-lookup"><span data-stu-id="42edd-108">Member</span></span>|<span data-ttu-id="42edd-109">Description</span><span class="sxs-lookup"><span data-stu-id="42edd-109">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FUNCTION_FOUND`|<span data-ttu-id="42edd-110">Arama işlevi buldu.</span><span class="sxs-lookup"><span data-stu-id="42edd-110">The search found the function.</span></span>|  
|`COR_PRF_FUNCTION_NOT_FOUND`|<span data-ttu-id="42edd-111">Arama işlevi bulamadı.</span><span class="sxs-lookup"><span data-stu-id="42edd-111">The search did not find the function.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="42edd-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="42edd-112">Requirements</span></span>  

 <span data-ttu-id="42edd-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="42edd-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42edd-114">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="42edd-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="42edd-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="42edd-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="42edd-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42edd-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42edd-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="42edd-117">See also</span></span>

- [<span data-ttu-id="42edd-118">Profil Oluşturma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="42edd-118">Profiling Enumerations</span></span>](profiling-enumerations.md)
