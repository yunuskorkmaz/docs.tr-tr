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
ms.openlocfilehash: 0bf17e7c9d8ff16dc8f07e4a386f599284828f40
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95682256"
---
# <a name="cor_prf_jit_cache-enumeration"></a><span data-ttu-id="0f901-102">COR_PRF_JIT_CACHE Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="0f901-102">COR_PRF_JIT_CACHE Enumeration</span></span>

<span data-ttu-id="0f901-103">Önbelleğe alınmış işlev aramasının sonucunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="0f901-103">Indicates the result of a cached function search.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0f901-104">`COR_PRF_CACHED_FUNCTION_FOUND` sıfır değerine sahiptir, bu nedenle `COR_PRF_JIT_CACHE` Boole yedeği olarak kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="0f901-104">`COR_PRF_CACHED_FUNCTION_FOUND` has a value of zero, so `COR_PRF_JIT_CACHE` cannot be used as a Boolean surrogate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f901-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="0f901-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_CACHED_FUNCTION_FOUND,  
    COR_PRF_CACHED_FUNCTION_NOT_FOUND  
} COR_PRF_JIT_CACHE;  
```  
  
## <a name="members"></a><span data-ttu-id="0f901-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="0f901-106">Members</span></span>  
  
|<span data-ttu-id="0f901-107">Üye</span><span class="sxs-lookup"><span data-stu-id="0f901-107">Member</span></span>|<span data-ttu-id="0f901-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0f901-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FUNCTION_FOUND`|<span data-ttu-id="0f901-109">Arama işlevi buldu.</span><span class="sxs-lookup"><span data-stu-id="0f901-109">The search found the function.</span></span>|  
|`COR_PRF_FUNCTION_NOT_FOUND`|<span data-ttu-id="0f901-110">Arama işlevi bulamadı.</span><span class="sxs-lookup"><span data-stu-id="0f901-110">The search did not find the function.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0f901-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0f901-111">Requirements</span></span>  

 <span data-ttu-id="0f901-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f901-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f901-113">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="0f901-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0f901-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="0f901-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0f901-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f901-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f901-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0f901-116">See also</span></span>

- [<span data-ttu-id="0f901-117">Profil Oluşturma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="0f901-117">Profiling Enumerations</span></span>](profiling-enumerations.md)
