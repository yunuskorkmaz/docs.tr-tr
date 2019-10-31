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
ms.openlocfilehash: d52f9f0bc2ff27d7849a80a424714aa84d3688fe
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136992"
---
# <a name="clsid_resolution_flags-enumeration"></a><span data-ttu-id="e3a26-102">CLSID_RESOLUTION_FLAGS Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="e3a26-102">CLSID_RESOLUTION_FLAGS Enumeration</span></span>
<span data-ttu-id="e3a26-103">Ortak dil çalışma zamanının (CLR) `CLSID`nasıl çözümleneceğini belirten değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="e3a26-103">Contains values that indicate how the common language runtime (CLR) should resolve a `CLSID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3a26-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e3a26-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    CLSID_RESOLUTION_DEFAULT      = 0x0,  
    CLSID_RESOLUTION_REGISTERED   = 0x1  
} CLSID_RESOLUTION_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="e3a26-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="e3a26-105">Members</span></span>  
  
|<span data-ttu-id="e3a26-106">Üye</span><span class="sxs-lookup"><span data-stu-id="e3a26-106">Member</span></span>|<span data-ttu-id="e3a26-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e3a26-107">Description</span></span>|  
|------------|-----------------|  
|`CLSID_RESOLUTION_DEFAULT`|<span data-ttu-id="e3a26-108">Varsayılan davranışı gösterir.</span><span class="sxs-lookup"><span data-stu-id="e3a26-108">Indicates the default behavior.</span></span>|  
|`CLSID_RESOLUTION_REGISTERED`|<span data-ttu-id="e3a26-109">Çalışma zamanının kayıt defterini arayacağı ve dolgu ilkesi uyguladığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="e3a26-109">Indicates that the runtime searches the registry and applies shim policy.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e3a26-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e3a26-110">Requirements</span></span>  
 <span data-ttu-id="e3a26-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3a26-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3a26-112">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e3a26-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e3a26-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3a26-113">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3a26-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e3a26-114">See also</span></span>

- [<span data-ttu-id="e3a26-115">Barındırma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="e3a26-115">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
