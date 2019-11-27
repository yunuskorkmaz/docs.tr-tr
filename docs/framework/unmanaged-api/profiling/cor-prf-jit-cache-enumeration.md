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
ms.openlocfilehash: 57d6ba77081536eb2bce0bf62d43ac080b2f5554
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447347"
---
# <a name="cor_prf_jit_cache-enumeration"></a><span data-ttu-id="fddee-102">COR_PRF_JIT_CACHE Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="fddee-102">COR_PRF_JIT_CACHE Enumeration</span></span>
<span data-ttu-id="fddee-103">Önbelleğe alınmış işlev aramasının sonucunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="fddee-103">Indicates the result of a cached function search.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fddee-104">`COR_PRF_CACHED_FUNCTION_FOUND` sıfır değerine sahiptir, bu nedenle `COR_PRF_JIT_CACHE` Boole yedeği olarak kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="fddee-104">`COR_PRF_CACHED_FUNCTION_FOUND` has a value of zero, so `COR_PRF_JIT_CACHE` cannot be used as a Boolean surrogate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fddee-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fddee-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_CACHED_FUNCTION_FOUND,  
    COR_PRF_CACHED_FUNCTION_NOT_FOUND  
} COR_PRF_JIT_CACHE;  
```  
  
## <a name="members"></a><span data-ttu-id="fddee-106">Üyeleri</span><span class="sxs-lookup"><span data-stu-id="fddee-106">Members</span></span>  
  
|<span data-ttu-id="fddee-107">Üyesi</span><span class="sxs-lookup"><span data-stu-id="fddee-107">Member</span></span>|<span data-ttu-id="fddee-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fddee-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FUNCTION_FOUND`|<span data-ttu-id="fddee-109">Arama işlevi buldu.</span><span class="sxs-lookup"><span data-stu-id="fddee-109">The search found the function.</span></span>|  
|`COR_PRF_FUNCTION_NOT_FOUND`|<span data-ttu-id="fddee-110">Arama işlevi bulamadı.</span><span class="sxs-lookup"><span data-stu-id="fddee-110">The search did not find the function.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fddee-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fddee-111">Requirements</span></span>  
 <span data-ttu-id="fddee-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fddee-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fddee-113">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="fddee-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fddee-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="fddee-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fddee-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fddee-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fddee-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fddee-116">See also</span></span>

- [<span data-ttu-id="fddee-117">Profil Oluşturma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="fddee-117">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
