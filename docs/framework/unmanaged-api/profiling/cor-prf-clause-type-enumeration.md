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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 861f4c18f4c5151dc7215d300775928b88f018aa
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59090634"
---
# <a name="corprfclausetype-enumeration"></a><span data-ttu-id="b559f-102">COR_PRF_CLAUSE_TYPE Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="b559f-102">COR_PRF_CLAUSE_TYPE Enumeration</span></span>
<span data-ttu-id="b559f-103">Kodu girdiğiniz özel durum yan tümcesi veya sol türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="b559f-103">Indicates the type of exception clause that the code has just entered or left.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b559f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b559f-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_CLAUSE_NONE = 0,  
    COR_PRF_CLAUSE_FILTER = 1,  
    COR_PRF_CLAUSE_CATCH = 2,  
    COR_PRF_CLAUSE_FINALLY = 3,  
} COR_PRF_CLAUSE_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="b559f-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="b559f-105">Members</span></span>  
  
|<span data-ttu-id="b559f-106">Üye</span><span class="sxs-lookup"><span data-stu-id="b559f-106">Member</span></span>|<span data-ttu-id="b559f-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b559f-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_CLAUSE_NONE`|<span data-ttu-id="b559f-108">Özel durum yan tümcesi geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="b559f-108">The exception clause is not valid.</span></span>|  
|`COR_PRF_CLAUSE_FILTER`|<span data-ttu-id="b559f-109">Özel durum yan tümcesi bir filtre ifadesi var.</span><span class="sxs-lookup"><span data-stu-id="b559f-109">The exception clause is a filter expression.</span></span>|  
|`COR_PRF_CLAUSE_CATCH`|<span data-ttu-id="b559f-110">Özel durum yan tümcesi bir `catch` deyimi.</span><span class="sxs-lookup"><span data-stu-id="b559f-110">The exception clause is a `catch` statement.</span></span>|  
|`COR_PRF_CLAUSE_FINALLY`|<span data-ttu-id="b559f-111">Özel durum yan tümcesi bir `finally` deyimi.</span><span class="sxs-lookup"><span data-stu-id="b559f-111">The exception clause is a `finally` statement.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b559f-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b559f-112">Requirements</span></span>  
 <span data-ttu-id="b559f-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b559f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b559f-114">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b559f-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b559f-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b559f-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b559f-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b559f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b559f-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b559f-117">See also</span></span>

- [<span data-ttu-id="b559f-118">Profil Oluşturma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="b559f-118">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
