---
title: CLSID_RESOLUTION_FLAGS Numaralandırması
ms.date: 03/30/2017
api_name:
- CLSID_RESOLUTION_FLAGS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CLSID_RESOLUTION_FLAGS
helpviewer_keywords:
- CLSID_RESOLUTION_FLAGS enumeration [.NET Framework hosting]
ms.assetid: cd8b9879-962a-4811-aa46-2e2b6bae0d84
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4bec138460d508371565c26017fab3a8c22266db
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429056"
---
# <a name="clsidresolutionflags-enumeration"></a><span data-ttu-id="141e1-102">CLSID_RESOLUTION_FLAGS Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="141e1-102">CLSID_RESOLUTION_FLAGS Enumeration</span></span>
<span data-ttu-id="141e1-103">Ortak dil çalışma zamanı (CLR) nasıl çözümlenmelidir belirtmek değerleri içeren bir `CLSID`.</span><span class="sxs-lookup"><span data-stu-id="141e1-103">Contains values that indicate how the common language runtime (CLR) should resolve a `CLSID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="141e1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="141e1-104">Syntax</span></span>  
  
```  
typedef enum {  
    CLSID_RESOLUTION_DEFAULT      = 0x0,  
    CLSID_RESOLUTION_REGISTERED   = 0x1  
} CLSID_RESOLUTION_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="141e1-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="141e1-105">Members</span></span>  
  
|<span data-ttu-id="141e1-106">Üye</span><span class="sxs-lookup"><span data-stu-id="141e1-106">Member</span></span>|<span data-ttu-id="141e1-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="141e1-107">Description</span></span>|  
|------------|-----------------|  
|`CLSID_RESOLUTION_DEFAULT`|<span data-ttu-id="141e1-108">Varsayılan davranış gösterir.</span><span class="sxs-lookup"><span data-stu-id="141e1-108">Indicates the default behavior.</span></span>|  
|`CLSID_RESOLUTION_REGISTERED`|<span data-ttu-id="141e1-109">Çalışma zamanı kayıt arar ve dolgusu ilke uygulanır gösterir.</span><span class="sxs-lookup"><span data-stu-id="141e1-109">Indicates that the runtime searches the registry and applies shim policy.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="141e1-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="141e1-110">Requirements</span></span>  
 <span data-ttu-id="141e1-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="141e1-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="141e1-112">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="141e1-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="141e1-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="141e1-113">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="141e1-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="141e1-114">See Also</span></span>  
 [<span data-ttu-id="141e1-115">Barındırma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="141e1-115">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
