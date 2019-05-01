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
ms.openlocfilehash: 36792d01ebdad72271a8b0597a33d83cab34780e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789590"
---
# <a name="clsidresolutionflags-enumeration"></a><span data-ttu-id="3eb5c-102">CLSID_RESOLUTION_FLAGS Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="3eb5c-102">CLSID_RESOLUTION_FLAGS Enumeration</span></span>
<span data-ttu-id="3eb5c-103">Ortak dil çalışma zamanı (CLR) nasıl çözümlenmelidir gösteren değerleri içeren bir `CLSID`.</span><span class="sxs-lookup"><span data-stu-id="3eb5c-103">Contains values that indicate how the common language runtime (CLR) should resolve a `CLSID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3eb5c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3eb5c-104">Syntax</span></span>  
  
```  
typedef enum {  
    CLSID_RESOLUTION_DEFAULT      = 0x0,  
    CLSID_RESOLUTION_REGISTERED   = 0x1  
} CLSID_RESOLUTION_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="3eb5c-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="3eb5c-105">Members</span></span>  
  
|<span data-ttu-id="3eb5c-106">Üye</span><span class="sxs-lookup"><span data-stu-id="3eb5c-106">Member</span></span>|<span data-ttu-id="3eb5c-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3eb5c-107">Description</span></span>|  
|------------|-----------------|  
|`CLSID_RESOLUTION_DEFAULT`|<span data-ttu-id="3eb5c-108">Varsayılan davranış gösterir.</span><span class="sxs-lookup"><span data-stu-id="3eb5c-108">Indicates the default behavior.</span></span>|  
|`CLSID_RESOLUTION_REGISTERED`|<span data-ttu-id="3eb5c-109">Çalışma zamanı kayıt defteri arar ve dolgu ilkenin geçerli olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="3eb5c-109">Indicates that the runtime searches the registry and applies shim policy.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3eb5c-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3eb5c-110">Requirements</span></span>  
 <span data-ttu-id="3eb5c-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3eb5c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3eb5c-112">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3eb5c-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3eb5c-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3eb5c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3eb5c-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3eb5c-114">See also</span></span>

- [<span data-ttu-id="3eb5c-115">Barındırma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="3eb5c-115">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
