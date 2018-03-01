---
title: CorDebugGenerationTypes Sabit Listesi
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
- CorDebugGenerationTypes
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugGenerationTypes
helpviewer_keywords:
- CorDebugGenerationTypes enumeration [.NET Framework debugging]
ms.assetid: 9f25b64f-eedd-4ae5-8b0e-cfdfb9b6c5d8
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c9b5126958b17ee2d1de5394ed07d78c3ffe29b5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="cordebuggenerationtypes-enumeration"></a><span data-ttu-id="048a9-102">CorDebugGenerationTypes Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="048a9-102">CorDebugGenerationTypes Enumeration</span></span>
<span data-ttu-id="048a9-103">Bellek bölgesi nesil yönetilen yığında belirtir.</span><span class="sxs-lookup"><span data-stu-id="048a9-103">Specifies the generation of a region of memory on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="048a9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="048a9-104">Syntax</span></span>  
  
```  
typedef enum CorDebugGenerationTypes {  
    CorDebug_Gen0 = 0,  
    CorDebug_Gen1 = 1,  
    CorDebug_Gen2 = 2,  
    CorDebug_LOH  = 3,  
} CorDebugRegionTypes;  
```  
  
## <a name="members"></a><span data-ttu-id="048a9-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="048a9-105">Members</span></span>  
  
|<span data-ttu-id="048a9-106">Üye adı</span><span class="sxs-lookup"><span data-stu-id="048a9-106">Member name</span></span>|<span data-ttu-id="048a9-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="048a9-107">Description</span></span>|  
|-----------------|-----------------|  
|`CorDebug_Gen0`|<span data-ttu-id="048a9-108">Kuşak 0.</span><span class="sxs-lookup"><span data-stu-id="048a9-108">Generation 0.</span></span>|  
|`CorDebug_Gen1`|<span data-ttu-id="048a9-109">1. nesil.</span><span class="sxs-lookup"><span data-stu-id="048a9-109">Generation 1.</span></span>|  
|`CorDebug_Gen2`|<span data-ttu-id="048a9-110">2. nesil.</span><span class="sxs-lookup"><span data-stu-id="048a9-110">Generation 2.</span></span>|  
|`CorDebug_LOH`|<span data-ttu-id="048a9-111">Büyük nesne yığın.</span><span class="sxs-lookup"><span data-stu-id="048a9-111">The large object heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="048a9-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="048a9-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="048a9-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="048a9-113">Requirements</span></span>  
 <span data-ttu-id="048a9-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="048a9-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="048a9-115">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="048a9-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="048a9-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="048a9-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="048a9-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="048a9-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="048a9-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="048a9-118">See Also</span></span>  
 [<span data-ttu-id="048a9-119">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="048a9-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
