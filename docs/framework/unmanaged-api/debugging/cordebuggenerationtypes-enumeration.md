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
ms.openlocfilehash: 189a276b4228038ab1d70620ce3a4a0f4342b245
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95712527"
---
# <a name="cordebuggenerationtypes-enumeration"></a><span data-ttu-id="46363-102">CorDebugGenerationTypes Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="46363-102">CorDebugGenerationTypes Enumeration</span></span>

<span data-ttu-id="46363-103">Yönetilen yığında bir bellek bölgesinin üretilmesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="46363-103">Specifies the generation of a region of memory on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46363-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="46363-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugGenerationTypes {  
    CorDebug_Gen0 = 0,  
    CorDebug_Gen1 = 1,  
    CorDebug_Gen2 = 2,  
    CorDebug_LOH  = 3,  
} CorDebugRegionTypes;  
```  
  
## <a name="members"></a><span data-ttu-id="46363-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="46363-105">Members</span></span>  
  
|<span data-ttu-id="46363-106">Üye adı</span><span class="sxs-lookup"><span data-stu-id="46363-106">Member name</span></span>|<span data-ttu-id="46363-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="46363-107">Description</span></span>|  
|-----------------|-----------------|  
|`CorDebug_Gen0`|<span data-ttu-id="46363-108">Nesil 0.</span><span class="sxs-lookup"><span data-stu-id="46363-108">Generation 0.</span></span>|  
|`CorDebug_Gen1`|<span data-ttu-id="46363-109">1. nesil.</span><span class="sxs-lookup"><span data-stu-id="46363-109">Generation 1.</span></span>|  
|`CorDebug_Gen2`|<span data-ttu-id="46363-110">2. nesil.</span><span class="sxs-lookup"><span data-stu-id="46363-110">Generation 2.</span></span>|  
|`CorDebug_LOH`|<span data-ttu-id="46363-111">Büyük nesne yığını.</span><span class="sxs-lookup"><span data-stu-id="46363-111">The large object heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="46363-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="46363-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46363-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="46363-113">Requirements</span></span>  

 <span data-ttu-id="46363-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="46363-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46363-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="46363-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="46363-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="46363-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="46363-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46363-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46363-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="46363-118">See also</span></span>

- [<span data-ttu-id="46363-119">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="46363-119">Debugging Enumerations</span></span>](debugging-enumerations.md)
