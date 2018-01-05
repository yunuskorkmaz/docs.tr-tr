---
title: "CorEventAttr Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorEventAttr
api_location: mscoree.dll
api_type: COM
f1_keywords: CorEventAttr
helpviewer_keywords: CorEventAttr enumeration [.NET Framework metadata]
ms.assetid: dc2b3281-3820-487e-930d-350b66dc6417
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c4302ff7627bf5e06f3c1b1263ec38a31393d411
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="coreventattr-enumeration"></a><span data-ttu-id="c6873-102">CorEventAttr Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="c6873-102">CorEventAttr Enumeration</span></span>
<span data-ttu-id="c6873-103">Bir olay meta verilerini açıklayan değerlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="c6873-103">Contains values that describe the metadata of an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6873-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c6873-104">Syntax</span></span>  
  
```  
typedef enum CorEventAttr {  
  
    evSpecialName           =   0x0200,  
  
    evReservedMask          =   0x0400,  
    evRTSpecialName         =   0x0400,  
  
} CorEventAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="c6873-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="c6873-105">Members</span></span>  
  
|<span data-ttu-id="c6873-106">Üye</span><span class="sxs-lookup"><span data-stu-id="c6873-106">Member</span></span>|<span data-ttu-id="c6873-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c6873-107">Description</span></span>|  
|------------|-----------------|  
|`evSpecialName`|<span data-ttu-id="c6873-108">Olay özeldir ve adını açıklayan belirtir nasıl.</span><span class="sxs-lookup"><span data-stu-id="c6873-108">Specifies that the event is special, and that its name describes how.</span></span>|  
|`evReservedMask`|<span data-ttu-id="c6873-109">İç kullanım için ortak dil çalışma zamanı tarafından ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="c6873-109">Reserved for internal use by the common language runtime.</span></span>|  
|`evRTSpecialName`|<span data-ttu-id="c6873-110">Ortak dil çalışma zamanı olay adı kodlama denetleyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c6873-110">Specifies that the common language runtime should check the encoding of the event name.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c6873-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c6873-111">Requirements</span></span>  
 <span data-ttu-id="c6873-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c6873-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6873-113">**Başlık:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="c6873-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="c6873-114">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6873-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6873-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c6873-115">See Also</span></span>  
 [<span data-ttu-id="c6873-116">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="c6873-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
