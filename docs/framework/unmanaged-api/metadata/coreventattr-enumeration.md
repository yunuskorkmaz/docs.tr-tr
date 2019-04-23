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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a1a50c15071ea1e696e508c779309225c7e7bfa2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59097827"
---
# <a name="coreventattr-enumeration"></a><span data-ttu-id="7a5d8-102">CorEventAttr Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="7a5d8-102">CorEventAttr Enumeration</span></span>
<span data-ttu-id="7a5d8-103">Bir olay meta verileri tanımlayan değerlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="7a5d8-103">Contains values that describe the metadata of an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a5d8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7a5d8-104">Syntax</span></span>  
  
```  
typedef enum CorEventAttr {  
  
    evSpecialName           =   0x0200,  
  
    evReservedMask          =   0x0400,  
    evRTSpecialName         =   0x0400,  
  
} CorEventAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="7a5d8-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="7a5d8-105">Members</span></span>  
  
|<span data-ttu-id="7a5d8-106">Üye</span><span class="sxs-lookup"><span data-stu-id="7a5d8-106">Member</span></span>|<span data-ttu-id="7a5d8-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7a5d8-107">Description</span></span>|  
|------------|-----------------|  
|`evSpecialName`|<span data-ttu-id="7a5d8-108">Olay özeldir ve adını açıklayan belirtir nasıl.</span><span class="sxs-lookup"><span data-stu-id="7a5d8-108">Specifies that the event is special, and that its name describes how.</span></span>|  
|`evReservedMask`|<span data-ttu-id="7a5d8-109">İç kullanım için ortak dil çalışma zamanı tarafından ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="7a5d8-109">Reserved for internal use by the common language runtime.</span></span>|  
|`evRTSpecialName`|<span data-ttu-id="7a5d8-110">Ortak dil çalışma zamanı olay adı kodlama denetleyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="7a5d8-110">Specifies that the common language runtime should check the encoding of the event name.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7a5d8-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7a5d8-111">Requirements</span></span>  
 <span data-ttu-id="7a5d8-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7a5d8-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a5d8-113">**Üst bilgi:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="7a5d8-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="7a5d8-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a5d8-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a5d8-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7a5d8-115">See also</span></span>

- [<span data-ttu-id="7a5d8-116">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="7a5d8-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
