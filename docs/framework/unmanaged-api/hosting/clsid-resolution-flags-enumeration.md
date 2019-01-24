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
ms.openlocfilehash: bee25122920a6fcec3bbd4e9e53bbdad008d5304
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54514121"
---
# <a name="clsidresolutionflags-enumeration"></a><span data-ttu-id="e27b6-102">CLSID_RESOLUTION_FLAGS Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="e27b6-102">CLSID_RESOLUTION_FLAGS Enumeration</span></span>
<span data-ttu-id="e27b6-103">Ortak dil çalışma zamanı (CLR) nasıl çözümlenmelidir gösteren değerleri içeren bir `CLSID`.</span><span class="sxs-lookup"><span data-stu-id="e27b6-103">Contains values that indicate how the common language runtime (CLR) should resolve a `CLSID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e27b6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e27b6-104">Syntax</span></span>  
  
```  
typedef enum {  
    CLSID_RESOLUTION_DEFAULT      = 0x0,  
    CLSID_RESOLUTION_REGISTERED   = 0x1  
} CLSID_RESOLUTION_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="e27b6-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="e27b6-105">Members</span></span>  
  
|<span data-ttu-id="e27b6-106">Üye</span><span class="sxs-lookup"><span data-stu-id="e27b6-106">Member</span></span>|<span data-ttu-id="e27b6-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e27b6-107">Description</span></span>|  
|------------|-----------------|  
|`CLSID_RESOLUTION_DEFAULT`|<span data-ttu-id="e27b6-108">Varsayılan davranış gösterir.</span><span class="sxs-lookup"><span data-stu-id="e27b6-108">Indicates the default behavior.</span></span>|  
|`CLSID_RESOLUTION_REGISTERED`|<span data-ttu-id="e27b6-109">Çalışma zamanı kayıt defteri arar ve dolgu ilkenin geçerli olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="e27b6-109">Indicates that the runtime searches the registry and applies shim policy.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e27b6-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e27b6-110">Requirements</span></span>  
 <span data-ttu-id="e27b6-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e27b6-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e27b6-112">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e27b6-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e27b6-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e27b6-113">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e27b6-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e27b6-114">See also</span></span>
- [<span data-ttu-id="e27b6-115">Barındırma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="e27b6-115">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
