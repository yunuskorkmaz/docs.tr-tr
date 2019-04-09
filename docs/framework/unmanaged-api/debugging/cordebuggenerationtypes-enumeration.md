---
title: CorDebugGenerationTypes Sabit Listesi
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c1707a09f14fbab6150c2ecbcd188d7bf88064fa
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59085902"
---
# <a name="cordebuggenerationtypes-enumeration"></a><span data-ttu-id="f3bd1-102">CorDebugGenerationTypes Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="f3bd1-102">CorDebugGenerationTypes Enumeration</span></span>
<span data-ttu-id="f3bd1-103">Yönetilen yığında bir bellek bölgesini oluşturulmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f3bd1-103">Specifies the generation of a region of memory on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3bd1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f3bd1-104">Syntax</span></span>  
  
```  
typedef enum CorDebugGenerationTypes {  
    CorDebug_Gen0 = 0,  
    CorDebug_Gen1 = 1,  
    CorDebug_Gen2 = 2,  
    CorDebug_LOH  = 3,  
} CorDebugRegionTypes;  
```  
  
## <a name="members"></a><span data-ttu-id="f3bd1-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="f3bd1-105">Members</span></span>  
  
|<span data-ttu-id="f3bd1-106">Üye adı</span><span class="sxs-lookup"><span data-stu-id="f3bd1-106">Member name</span></span>|<span data-ttu-id="f3bd1-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f3bd1-107">Description</span></span>|  
|-----------------|-----------------|  
|`CorDebug_Gen0`|<span data-ttu-id="f3bd1-108">Nesil 0.</span><span class="sxs-lookup"><span data-stu-id="f3bd1-108">Generation 0.</span></span>|  
|`CorDebug_Gen1`|<span data-ttu-id="f3bd1-109">1. nesil.</span><span class="sxs-lookup"><span data-stu-id="f3bd1-109">Generation 1.</span></span>|  
|`CorDebug_Gen2`|<span data-ttu-id="f3bd1-110">2. nesil.</span><span class="sxs-lookup"><span data-stu-id="f3bd1-110">Generation 2.</span></span>|  
|`CorDebug_LOH`|<span data-ttu-id="f3bd1-111">Büyük nesne yığını.</span><span class="sxs-lookup"><span data-stu-id="f3bd1-111">The large object heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f3bd1-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f3bd1-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3bd1-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f3bd1-113">Requirements</span></span>  
 <span data-ttu-id="f3bd1-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f3bd1-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3bd1-115">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f3bd1-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f3bd1-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f3bd1-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="f3bd1-117">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="f3bd1-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f3bd1-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f3bd1-118">See also</span></span>

- [<span data-ttu-id="f3bd1-119">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="f3bd1-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
