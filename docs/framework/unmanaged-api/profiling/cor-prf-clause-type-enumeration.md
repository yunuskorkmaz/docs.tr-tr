---
title: "COR_PRF_CLAUSE_TYPE Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e03b3f2462b8876bfba3cf7d0df40311935722f8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="corprfclausetype-enumeration"></a><span data-ttu-id="0a9de-102">COR_PRF_CLAUSE_TYPE Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="0a9de-102">COR_PRF_CLAUSE_TYPE Enumeration</span></span>
<span data-ttu-id="0a9de-103">Kod yalnızca geçtiğini özel durum yan tümcesi veya sol türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="0a9de-103">Indicates the type of exception clause that the code has just entered or left.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a9de-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0a9de-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_CLAUSE_NONE = 0,  
    COR_PRF_CLAUSE_FILTER = 1,  
    COR_PRF_CLAUSE_CATCH = 2,  
    COR_PRF_CLAUSE_FINALLY = 3,  
} COR_PRF_CLAUSE_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="0a9de-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="0a9de-105">Members</span></span>  
  
|<span data-ttu-id="0a9de-106">Üye</span><span class="sxs-lookup"><span data-stu-id="0a9de-106">Member</span></span>|<span data-ttu-id="0a9de-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0a9de-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_CLAUSE_NONE`|<span data-ttu-id="0a9de-108">Özel durum yan tümcesi geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="0a9de-108">The exception clause is not valid.</span></span>|  
|`COR_PRF_CLAUSE_FILTER`|<span data-ttu-id="0a9de-109">Özel durum yan tümcesi bir filtre ifadesi değil.</span><span class="sxs-lookup"><span data-stu-id="0a9de-109">The exception clause is a filter expression.</span></span>|  
|`COR_PRF_CLAUSE_CATCH`|<span data-ttu-id="0a9de-110">Özel durum yan tümcesi bir `catch` deyimi.</span><span class="sxs-lookup"><span data-stu-id="0a9de-110">The exception clause is a `catch` statement.</span></span>|  
|`COR_PRF_CLAUSE_FINALLY`|<span data-ttu-id="0a9de-111">Özel durum yan tümcesi bir `finally` deyimi.</span><span class="sxs-lookup"><span data-stu-id="0a9de-111">The exception clause is a `finally` statement.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0a9de-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0a9de-112">Requirements</span></span>  
 <span data-ttu-id="0a9de-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0a9de-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a9de-114">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0a9de-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0a9de-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0a9de-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0a9de-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a9de-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a9de-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0a9de-117">See Also</span></span>  
 [<span data-ttu-id="0a9de-118">Profil Oluşturma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="0a9de-118">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
