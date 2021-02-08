---
description: 'Hakkında daha fazla bilgi edinin: CLSID_RESOLUTION_FLAGS numaralandırması'
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
ms.openlocfilehash: 54d334147e13217f8ce20dae1b139cdc6d11a3b8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799882"
---
# <a name="clsid_resolution_flags-enumeration"></a><span data-ttu-id="7ff79-103">CLSID_RESOLUTION_FLAGS Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="7ff79-103">CLSID_RESOLUTION_FLAGS Enumeration</span></span>

<span data-ttu-id="7ff79-104">Ortak dil çalışma zamanının (CLR) bir kaç çözüm içermesi gerektiğini belirten değerleri içerir `CLSID` .</span><span class="sxs-lookup"><span data-stu-id="7ff79-104">Contains values that indicate how the common language runtime (CLR) should resolve a `CLSID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ff79-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="7ff79-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    CLSID_RESOLUTION_DEFAULT      = 0x0,  
    CLSID_RESOLUTION_REGISTERED   = 0x1  
} CLSID_RESOLUTION_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="7ff79-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="7ff79-106">Members</span></span>  
  
|<span data-ttu-id="7ff79-107">Üye</span><span class="sxs-lookup"><span data-stu-id="7ff79-107">Member</span></span>|<span data-ttu-id="7ff79-108">Description</span><span class="sxs-lookup"><span data-stu-id="7ff79-108">Description</span></span>|  
|------------|-----------------|  
|`CLSID_RESOLUTION_DEFAULT`|<span data-ttu-id="7ff79-109">Varsayılan davranışı gösterir.</span><span class="sxs-lookup"><span data-stu-id="7ff79-109">Indicates the default behavior.</span></span>|  
|`CLSID_RESOLUTION_REGISTERED`|<span data-ttu-id="7ff79-110">Çalışma zamanının kayıt defterini arayacağı ve dolgu ilkesi uyguladığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="7ff79-110">Indicates that the runtime searches the registry and applies shim policy.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7ff79-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7ff79-111">Requirements</span></span>  

 <span data-ttu-id="7ff79-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ff79-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ff79-113">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="7ff79-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7ff79-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ff79-114">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ff79-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7ff79-115">See also</span></span>

- [<span data-ttu-id="7ff79-116">Barındırma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="7ff79-116">Hosting Enumerations</span></span>](hosting-enumerations.md)
