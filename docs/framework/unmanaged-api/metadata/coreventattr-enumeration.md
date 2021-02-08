---
description: 'Hakkında daha fazla bilgi edinin: CorEventAttr numaralandırması'
title: CorEventAttr Numaralandırması
ms.date: 03/30/2017
api_name:
- CorEventAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorEventAttr
helpviewer_keywords:
- CorEventAttr enumeration [.NET Framework metadata]
ms.assetid: dc2b3281-3820-487e-930d-350b66dc6417
topic_type:
- apiref
ms.openlocfilehash: 70f05eacf2cc7c7975b9b52d402cceb60bbea426
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784515"
---
# <a name="coreventattr-enumeration"></a><span data-ttu-id="c3d9a-103">CorEventAttr Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="c3d9a-103">CorEventAttr Enumeration</span></span>

<span data-ttu-id="c3d9a-104">Bir olayın meta verilerini tanımlayan değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="c3d9a-104">Contains values that describe the metadata of an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3d9a-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="c3d9a-105">Syntax</span></span>  
  
```cpp  
typedef enum CorEventAttr {  
  
    evSpecialName           =   0x0200,  
  
    evReservedMask          =   0x0400,  
    evRTSpecialName         =   0x0400,  
  
} CorEventAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="c3d9a-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="c3d9a-106">Members</span></span>  
  
|<span data-ttu-id="c3d9a-107">Üye</span><span class="sxs-lookup"><span data-stu-id="c3d9a-107">Member</span></span>|<span data-ttu-id="c3d9a-108">Description</span><span class="sxs-lookup"><span data-stu-id="c3d9a-108">Description</span></span>|  
|------------|-----------------|  
|`evSpecialName`|<span data-ttu-id="c3d9a-109">Olayın özel olduğunu ve adının nasıl olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="c3d9a-109">Specifies that the event is special, and that its name describes how.</span></span>|  
|`evReservedMask`|<span data-ttu-id="c3d9a-110">Ortak dil çalışma zamanı tarafından iç kullanım için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="c3d9a-110">Reserved for internal use by the common language runtime.</span></span>|  
|`evRTSpecialName`|<span data-ttu-id="c3d9a-111">Ortak dil çalışma zamanının olay adının kodlamasını denetlemesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c3d9a-111">Specifies that the common language runtime should check the encoding of the event name.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c3d9a-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c3d9a-112">Requirements</span></span>  

 <span data-ttu-id="c3d9a-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3d9a-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3d9a-114">**Üst bilgi:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="c3d9a-114">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="c3d9a-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3d9a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3d9a-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c3d9a-116">See also</span></span>

- [<span data-ttu-id="c3d9a-117">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="c3d9a-117">Metadata Enumerations</span></span>](metadata-enumerations.md)
