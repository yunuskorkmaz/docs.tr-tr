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
ms.openlocfilehash: 362e917e1684c91bde80a8b5c2e6a27a18a99190
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73098193"
---
# <a name="cordebuggenerationtypes-enumeration"></a><span data-ttu-id="d0658-102">CorDebugGenerationTypes Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="d0658-102">CorDebugGenerationTypes Enumeration</span></span>
<span data-ttu-id="d0658-103">Yönetilen yığında bir bellek bölgesinin üretilmesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d0658-103">Specifies the generation of a region of memory on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0658-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d0658-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugGenerationTypes {  
    CorDebug_Gen0 = 0,  
    CorDebug_Gen1 = 1,  
    CorDebug_Gen2 = 2,  
    CorDebug_LOH  = 3,  
} CorDebugRegionTypes;  
```  
  
## <a name="members"></a><span data-ttu-id="d0658-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="d0658-105">Members</span></span>  
  
|<span data-ttu-id="d0658-106">Üye adı</span><span class="sxs-lookup"><span data-stu-id="d0658-106">Member name</span></span>|<span data-ttu-id="d0658-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d0658-107">Description</span></span>|  
|-----------------|-----------------|  
|`CorDebug_Gen0`|<span data-ttu-id="d0658-108">Nesil 0.</span><span class="sxs-lookup"><span data-stu-id="d0658-108">Generation 0.</span></span>|  
|`CorDebug_Gen1`|<span data-ttu-id="d0658-109">1\. nesil.</span><span class="sxs-lookup"><span data-stu-id="d0658-109">Generation 1.</span></span>|  
|`CorDebug_Gen2`|<span data-ttu-id="d0658-110">2\. nesil.</span><span class="sxs-lookup"><span data-stu-id="d0658-110">Generation 2.</span></span>|  
|`CorDebug_LOH`|<span data-ttu-id="d0658-111">Büyük nesne yığını.</span><span class="sxs-lookup"><span data-stu-id="d0658-111">The large object heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d0658-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d0658-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0658-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d0658-113">Requirements</span></span>  
 <span data-ttu-id="d0658-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d0658-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0658-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d0658-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d0658-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d0658-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d0658-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0658-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0658-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d0658-118">See also</span></span>

- [<span data-ttu-id="d0658-119">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="d0658-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
