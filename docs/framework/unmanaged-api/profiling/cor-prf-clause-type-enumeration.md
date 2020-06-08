---
title: COR_PRF_CLAUSE_TYPE Numaralandırması
ms.date: 03/30/2017
api_name:
- COR_PRF_CLAUSE_TYPE
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_CLAUSE_TYPE
helpviewer_keywords:
- COR_PRF_CLAUSE_TYPE enumeration [.NET Framework profiling]
ms.assetid: f64c325a-ed3a-4aaf-b847-a88edbc4fefc
topic_type:
- apiref
ms.openlocfilehash: a308017dc80dd973cbf108ba9df824193775f5ff
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501059"
---
# <a name="cor_prf_clause_type-enumeration"></a><span data-ttu-id="e959f-102">COR_PRF_CLAUSE_TYPE Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="e959f-102">COR_PRF_CLAUSE_TYPE Enumeration</span></span>
<span data-ttu-id="e959f-103">Kodun yalnızca girdiği veya solundaki özel durum yan tümcesinin türünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="e959f-103">Indicates the type of exception clause that the code has just entered or left.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e959f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e959f-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_CLAUSE_NONE = 0,  
    COR_PRF_CLAUSE_FILTER = 1,  
    COR_PRF_CLAUSE_CATCH = 2,  
    COR_PRF_CLAUSE_FINALLY = 3,  
} COR_PRF_CLAUSE_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="e959f-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="e959f-105">Members</span></span>  
  
|<span data-ttu-id="e959f-106">Üye</span><span class="sxs-lookup"><span data-stu-id="e959f-106">Member</span></span>|<span data-ttu-id="e959f-107">Description</span><span class="sxs-lookup"><span data-stu-id="e959f-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_CLAUSE_NONE`|<span data-ttu-id="e959f-108">Exception yan tümcesi geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="e959f-108">The exception clause is not valid.</span></span>|  
|`COR_PRF_CLAUSE_FILTER`|<span data-ttu-id="e959f-109">Exception yan tümcesi bir filtre ifadesidir.</span><span class="sxs-lookup"><span data-stu-id="e959f-109">The exception clause is a filter expression.</span></span>|  
|`COR_PRF_CLAUSE_CATCH`|<span data-ttu-id="e959f-110">Exception yan tümcesi bir `catch` ifadedir.</span><span class="sxs-lookup"><span data-stu-id="e959f-110">The exception clause is a `catch` statement.</span></span>|  
|`COR_PRF_CLAUSE_FINALLY`|<span data-ttu-id="e959f-111">Exception yan tümcesi bir `finally` ifadedir.</span><span class="sxs-lookup"><span data-stu-id="e959f-111">The exception clause is a `finally` statement.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e959f-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e959f-112">Requirements</span></span>  
 <span data-ttu-id="e959f-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e959f-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e959f-114">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="e959f-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e959f-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e959f-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e959f-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e959f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e959f-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e959f-117">See also</span></span>

- [<span data-ttu-id="e959f-118">Profil Oluşturma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="e959f-118">Profiling Enumerations</span></span>](profiling-enumerations.md)
