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
ms.openlocfilehash: 0061e0772c48626a7ba88280e44b74ef32838a41
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867145"
---
# <a name="cor_prf_jit_cache-enumeration"></a><span data-ttu-id="e3bb1-102">COR_PRF_JIT_CACHE Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="e3bb1-102">COR_PRF_JIT_CACHE Enumeration</span></span>
<span data-ttu-id="e3bb1-103">Önbelleğe alınmış işlev aramasının sonucunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="e3bb1-103">Indicates the result of a cached function search.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e3bb1-104">`COR_PRF_CACHED_FUNCTION_FOUND` sıfır değerine sahiptir, bu nedenle `COR_PRF_JIT_CACHE` Boole yedeği olarak kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="e3bb1-104">`COR_PRF_CACHED_FUNCTION_FOUND` has a value of zero, so `COR_PRF_JIT_CACHE` cannot be used as a Boolean surrogate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3bb1-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e3bb1-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_CACHED_FUNCTION_FOUND,  
    COR_PRF_CACHED_FUNCTION_NOT_FOUND  
} COR_PRF_JIT_CACHE;  
```  
  
## <a name="members"></a><span data-ttu-id="e3bb1-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="e3bb1-106">Members</span></span>  
  
|<span data-ttu-id="e3bb1-107">Üye</span><span class="sxs-lookup"><span data-stu-id="e3bb1-107">Member</span></span>|<span data-ttu-id="e3bb1-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e3bb1-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FUNCTION_FOUND`|<span data-ttu-id="e3bb1-109">Arama işlevi buldu.</span><span class="sxs-lookup"><span data-stu-id="e3bb1-109">The search found the function.</span></span>|  
|`COR_PRF_FUNCTION_NOT_FOUND`|<span data-ttu-id="e3bb1-110">Arama işlevi bulamadı.</span><span class="sxs-lookup"><span data-stu-id="e3bb1-110">The search did not find the function.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e3bb1-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e3bb1-111">Requirements</span></span>  
 <span data-ttu-id="e3bb1-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3bb1-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3bb1-113">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="e3bb1-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e3bb1-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e3bb1-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e3bb1-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3bb1-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3bb1-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e3bb1-116">See also</span></span>

- [<span data-ttu-id="e3bb1-117">Profil Oluşturma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="e3bb1-117">Profiling Enumerations</span></span>](profiling-enumerations.md)
