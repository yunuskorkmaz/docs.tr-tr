---
title: "CLSID_RESOLUTION_FLAGS Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CLSID_RESOLUTION_FLAGS
api_location: mscoree.dll
api_type: COM
f1_keywords: CLSID_RESOLUTION_FLAGS
helpviewer_keywords: CLSID_RESOLUTION_FLAGS enumeration [.NET Framework hosting]
ms.assetid: cd8b9879-962a-4811-aa46-2e2b6bae0d84
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 17e74e8b39ff9079973063f4ea703607411ab93d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="clsidresolutionflags-enumeration"></a><span data-ttu-id="52422-102">CLSID_RESOLUTION_FLAGS Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="52422-102">CLSID_RESOLUTION_FLAGS Enumeration</span></span>
<span data-ttu-id="52422-103">Ortak dil çalışma zamanı (CLR) nasıl çözümlenmelidir belirtmek değerleri içeren bir `CLSID`.</span><span class="sxs-lookup"><span data-stu-id="52422-103">Contains values that indicate how the common language runtime (CLR) should resolve a `CLSID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52422-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="52422-104">Syntax</span></span>  
  
```  
typedef enum {  
    CLSID_RESOLUTION_DEFAULT      = 0x0,  
    CLSID_RESOLUTION_REGISTERED   = 0x1  
} CLSID_RESOLUTION_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="52422-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="52422-105">Members</span></span>  
  
|<span data-ttu-id="52422-106">Üye</span><span class="sxs-lookup"><span data-stu-id="52422-106">Member</span></span>|<span data-ttu-id="52422-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="52422-107">Description</span></span>|  
|------------|-----------------|  
|`CLSID_RESOLUTION_DEFAULT`|<span data-ttu-id="52422-108">Varsayılan davranış gösterir.</span><span class="sxs-lookup"><span data-stu-id="52422-108">Indicates the default behavior.</span></span>|  
|`CLSID_RESOLUTION_REGISTERED`|<span data-ttu-id="52422-109">Çalışma zamanı kayıt arar ve dolgusu ilke uygulanır gösterir.</span><span class="sxs-lookup"><span data-stu-id="52422-109">Indicates that the runtime searches the registry and applies shim policy.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="52422-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="52422-110">Requirements</span></span>  
 <span data-ttu-id="52422-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="52422-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52422-112">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="52422-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="52422-113">**.NET framework sürümleri:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52422-113">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52422-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="52422-114">See Also</span></span>  
 [<span data-ttu-id="52422-115">Barındırma numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="52422-115">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
