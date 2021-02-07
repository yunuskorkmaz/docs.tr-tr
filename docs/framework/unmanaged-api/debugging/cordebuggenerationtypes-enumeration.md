---
description: 'Şu konuda daha fazla bilgi edinin: CorDebugGenerationTypes sabit listesi'
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
ms.openlocfilehash: f86b2bc9bf947c6b285c50678f46494005bb5537
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662136"
---
# <a name="cordebuggenerationtypes-enumeration"></a><span data-ttu-id="f7a33-103">CorDebugGenerationTypes Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="f7a33-103">CorDebugGenerationTypes Enumeration</span></span>

<span data-ttu-id="f7a33-104">Yönetilen yığında bir bellek bölgesinin üretilmesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f7a33-104">Specifies the generation of a region of memory on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7a33-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="f7a33-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugGenerationTypes {  
    CorDebug_Gen0 = 0,  
    CorDebug_Gen1 = 1,  
    CorDebug_Gen2 = 2,  
    CorDebug_LOH  = 3,  
} CorDebugRegionTypes;  
```  
  
## <a name="members"></a><span data-ttu-id="f7a33-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="f7a33-106">Members</span></span>  
  
|<span data-ttu-id="f7a33-107">Üye adı</span><span class="sxs-lookup"><span data-stu-id="f7a33-107">Member name</span></span>|<span data-ttu-id="f7a33-108">Description</span><span class="sxs-lookup"><span data-stu-id="f7a33-108">Description</span></span>|  
|-----------------|-----------------|  
|`CorDebug_Gen0`|<span data-ttu-id="f7a33-109">Nesil 0.</span><span class="sxs-lookup"><span data-stu-id="f7a33-109">Generation 0.</span></span>|  
|`CorDebug_Gen1`|<span data-ttu-id="f7a33-110">1. nesil.</span><span class="sxs-lookup"><span data-stu-id="f7a33-110">Generation 1.</span></span>|  
|`CorDebug_Gen2`|<span data-ttu-id="f7a33-111">2. nesil.</span><span class="sxs-lookup"><span data-stu-id="f7a33-111">Generation 2.</span></span>|  
|`CorDebug_LOH`|<span data-ttu-id="f7a33-112">Büyük nesne yığını.</span><span class="sxs-lookup"><span data-stu-id="f7a33-112">The large object heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f7a33-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f7a33-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7a33-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f7a33-114">Requirements</span></span>  

 <span data-ttu-id="f7a33-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7a33-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7a33-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f7a33-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f7a33-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f7a33-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f7a33-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7a33-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7a33-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f7a33-119">See also</span></span>

- [<span data-ttu-id="f7a33-120">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="f7a33-120">Debugging Enumerations</span></span>](debugging-enumerations.md)
