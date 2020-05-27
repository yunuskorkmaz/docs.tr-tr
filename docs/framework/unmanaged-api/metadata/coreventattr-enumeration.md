---
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
ms.openlocfilehash: e22b390271a7813dd1d34aecf5f8a62d7eb81005
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007446"
---
# <a name="coreventattr-enumeration"></a><span data-ttu-id="b4f62-102">CorEventAttr Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="b4f62-102">CorEventAttr Enumeration</span></span>
<span data-ttu-id="b4f62-103">Bir olayın meta verilerini tanımlayan değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="b4f62-103">Contains values that describe the metadata of an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4f62-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b4f62-104">Syntax</span></span>  
  
```cpp  
typedef enum CorEventAttr {  
  
    evSpecialName           =   0x0200,  
  
    evReservedMask          =   0x0400,  
    evRTSpecialName         =   0x0400,  
  
} CorEventAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="b4f62-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="b4f62-105">Members</span></span>  
  
|<span data-ttu-id="b4f62-106">Üye</span><span class="sxs-lookup"><span data-stu-id="b4f62-106">Member</span></span>|<span data-ttu-id="b4f62-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b4f62-107">Description</span></span>|  
|------------|-----------------|  
|`evSpecialName`|<span data-ttu-id="b4f62-108">Olayın özel olduğunu ve adının nasıl olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="b4f62-108">Specifies that the event is special, and that its name describes how.</span></span>|  
|`evReservedMask`|<span data-ttu-id="b4f62-109">Ortak dil çalışma zamanı tarafından iç kullanım için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="b4f62-109">Reserved for internal use by the common language runtime.</span></span>|  
|`evRTSpecialName`|<span data-ttu-id="b4f62-110">Ortak dil çalışma zamanının olay adının kodlamasını denetlemesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b4f62-110">Specifies that the common language runtime should check the encoding of the event name.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b4f62-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b4f62-111">Requirements</span></span>  
 <span data-ttu-id="b4f62-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b4f62-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4f62-113">**Üst bilgi:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="b4f62-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="b4f62-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4f62-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4f62-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b4f62-115">See also</span></span>

- [<span data-ttu-id="b4f62-116">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="b4f62-116">Metadata Enumerations</span></span>](metadata-enumerations.md)
