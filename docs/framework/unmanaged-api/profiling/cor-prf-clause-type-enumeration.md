---
description: 'Hakkında daha fazla bilgi edinin: COR_PRF_CLAUSE_TYPE numaralandırması'
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
ms.openlocfilehash: 413dbc0ad94e4ab670cd7cd9537bbd1735ffd7cf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99649292"
---
# <a name="cor_prf_clause_type-enumeration"></a><span data-ttu-id="204fb-103">COR_PRF_CLAUSE_TYPE Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="204fb-103">COR_PRF_CLAUSE_TYPE Enumeration</span></span>

<span data-ttu-id="204fb-104">Kodun yalnızca girdiği veya solundaki özel durum yan tümcesinin türünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="204fb-104">Indicates the type of exception clause that the code has just entered or left.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="204fb-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="204fb-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_CLAUSE_NONE = 0,  
    COR_PRF_CLAUSE_FILTER = 1,  
    COR_PRF_CLAUSE_CATCH = 2,  
    COR_PRF_CLAUSE_FINALLY = 3,  
} COR_PRF_CLAUSE_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="204fb-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="204fb-106">Members</span></span>  
  
|<span data-ttu-id="204fb-107">Üye</span><span class="sxs-lookup"><span data-stu-id="204fb-107">Member</span></span>|<span data-ttu-id="204fb-108">Description</span><span class="sxs-lookup"><span data-stu-id="204fb-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_CLAUSE_NONE`|<span data-ttu-id="204fb-109">Exception yan tümcesi geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="204fb-109">The exception clause is not valid.</span></span>|  
|`COR_PRF_CLAUSE_FILTER`|<span data-ttu-id="204fb-110">Exception yan tümcesi bir filtre ifadesidir.</span><span class="sxs-lookup"><span data-stu-id="204fb-110">The exception clause is a filter expression.</span></span>|  
|`COR_PRF_CLAUSE_CATCH`|<span data-ttu-id="204fb-111">Exception yan tümcesi bir `catch` ifadedir.</span><span class="sxs-lookup"><span data-stu-id="204fb-111">The exception clause is a `catch` statement.</span></span>|  
|`COR_PRF_CLAUSE_FINALLY`|<span data-ttu-id="204fb-112">Exception yan tümcesi bir `finally` ifadedir.</span><span class="sxs-lookup"><span data-stu-id="204fb-112">The exception clause is a `finally` statement.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="204fb-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="204fb-113">Requirements</span></span>  

 <span data-ttu-id="204fb-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="204fb-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="204fb-115">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="204fb-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="204fb-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="204fb-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="204fb-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="204fb-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="204fb-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="204fb-118">See also</span></span>

- [<span data-ttu-id="204fb-119">Profil Oluşturma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="204fb-119">Profiling Enumerations</span></span>](profiling-enumerations.md)
