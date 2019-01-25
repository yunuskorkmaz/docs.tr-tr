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
ms.openlocfilehash: d34aa954126cc26519aaea963f99299e5557d2c8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54743061"
---
# <a name="coreventattr-enumeration"></a><span data-ttu-id="0ab59-102">CorEventAttr Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="0ab59-102">CorEventAttr Enumeration</span></span>
<span data-ttu-id="0ab59-103">Bir olay meta verileri tanımlayan değerlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="0ab59-103">Contains values that describe the metadata of an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ab59-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0ab59-104">Syntax</span></span>  
  
```  
typedef enum CorEventAttr {  
  
    evSpecialName           =   0x0200,  
  
    evReservedMask          =   0x0400,  
    evRTSpecialName         =   0x0400,  
  
} CorEventAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="0ab59-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="0ab59-105">Members</span></span>  
  
|<span data-ttu-id="0ab59-106">Üye</span><span class="sxs-lookup"><span data-stu-id="0ab59-106">Member</span></span>|<span data-ttu-id="0ab59-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0ab59-107">Description</span></span>|  
|------------|-----------------|  
|`evSpecialName`|<span data-ttu-id="0ab59-108">Olay özeldir ve adını açıklayan belirtir nasıl.</span><span class="sxs-lookup"><span data-stu-id="0ab59-108">Specifies that the event is special, and that its name describes how.</span></span>|  
|`evReservedMask`|<span data-ttu-id="0ab59-109">İç kullanım için ortak dil çalışma zamanı tarafından ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="0ab59-109">Reserved for internal use by the common language runtime.</span></span>|  
|`evRTSpecialName`|<span data-ttu-id="0ab59-110">Ortak dil çalışma zamanı olay adı kodlama denetleyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0ab59-110">Specifies that the common language runtime should check the encoding of the event name.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0ab59-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0ab59-111">Requirements</span></span>  
 <span data-ttu-id="0ab59-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0ab59-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ab59-113">**Üst bilgi:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="0ab59-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="0ab59-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ab59-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ab59-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0ab59-115">See also</span></span>
- [<span data-ttu-id="0ab59-116">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="0ab59-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
