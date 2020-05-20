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
ms.openlocfilehash: 5ac015f958d9504bbd14a66ead86548b8df32764
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616781"
---
# <a name="clsid_resolution_flags-enumeration"></a><span data-ttu-id="6d1ae-102">CLSID_RESOLUTION_FLAGS Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="6d1ae-102">CLSID_RESOLUTION_FLAGS Enumeration</span></span>
<span data-ttu-id="6d1ae-103">Ortak dil çalışma zamanının (CLR) bir kaç çözüm içermesi gerektiğini belirten değerleri içerir `CLSID` .</span><span class="sxs-lookup"><span data-stu-id="6d1ae-103">Contains values that indicate how the common language runtime (CLR) should resolve a `CLSID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d1ae-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="6d1ae-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    CLSID_RESOLUTION_DEFAULT      = 0x0,  
    CLSID_RESOLUTION_REGISTERED   = 0x1  
} CLSID_RESOLUTION_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="6d1ae-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="6d1ae-105">Members</span></span>  
  
|<span data-ttu-id="6d1ae-106">Üye</span><span class="sxs-lookup"><span data-stu-id="6d1ae-106">Member</span></span>|<span data-ttu-id="6d1ae-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6d1ae-107">Description</span></span>|  
|------------|-----------------|  
|`CLSID_RESOLUTION_DEFAULT`|<span data-ttu-id="6d1ae-108">Varsayılan davranışı gösterir.</span><span class="sxs-lookup"><span data-stu-id="6d1ae-108">Indicates the default behavior.</span></span>|  
|`CLSID_RESOLUTION_REGISTERED`|<span data-ttu-id="6d1ae-109">Çalışma zamanının kayıt defterini arayacağı ve dolgu ilkesi uyguladığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="6d1ae-109">Indicates that the runtime searches the registry and applies shim policy.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6d1ae-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6d1ae-110">Requirements</span></span>  
 <span data-ttu-id="6d1ae-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d1ae-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d1ae-112">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6d1ae-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6d1ae-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d1ae-113">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d1ae-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6d1ae-114">See also</span></span>

- [<span data-ttu-id="6d1ae-115">Barındırma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="6d1ae-115">Hosting Enumerations</span></span>](hosting-enumerations.md)
