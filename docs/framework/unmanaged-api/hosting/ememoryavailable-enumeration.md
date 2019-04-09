---
title: EMemoryAvailable Numaralandırması
ms.date: 03/30/2017
api_name:
- EMemoryAvailable
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EMemoryAvailable
helpviewer_keywords:
- EMemoryAvailable enumeration [.NET Framework hosting]
ms.assetid: 38e72a06-dbed-473b-a59b-7e0b3ea4f2af
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d98a0c1c3187b81c44fae6eee91d975169a40045
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59072812"
---
# <a name="ememoryavailable-enumeration"></a><span data-ttu-id="6868a-102">EMemoryAvailable Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="6868a-102">EMemoryAvailable Enumeration</span></span>
<span data-ttu-id="6868a-103">Bilgisayardaki boş fiziksel bellek miktarını gösteren değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="6868a-103">Contains values that indicate the amount of free physical memory on the computer.</span></span> <span data-ttu-id="6868a-104">Bellek döndürüldüğü yüksek ve düşük için bu değerler mantıksal olarak olaylara harita `CreateMemoryResourceNotification` Windows API işlevi.</span><span class="sxs-lookup"><span data-stu-id="6868a-104">These values logically map to the events for high and low memory returned from the `CreateMemoryResourceNotification` function in the Windows API.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6868a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6868a-105">Syntax</span></span>  
  
```  
typedef enum {  
    eMemoryAvailableLow     = 1,  
    eMemoryAvailableNeutral = 2,  
    eMemoryAvailableHigh    = 3   
} EMemoryAvailable;  
```  
  
## <a name="members"></a><span data-ttu-id="6868a-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="6868a-106">Members</span></span>  
  
|<span data-ttu-id="6868a-107">Üye</span><span class="sxs-lookup"><span data-stu-id="6868a-107">Member</span></span>|<span data-ttu-id="6868a-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6868a-108">Description</span></span>|  
|------------|-----------------|  
|`eMemoryAvailableHigh`|<span data-ttu-id="6868a-109">Yeterince fiziksel belleğin kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6868a-109">Plenty of physical memory is available.</span></span>|  
|`eMemoryAvailableLow`|<span data-ttu-id="6868a-110">Çok az fiziksel bellek yok.</span><span class="sxs-lookup"><span data-stu-id="6868a-110">Very little physical memory is available.</span></span>|  
|`eMemoryAvailableNeutral`|<span data-ttu-id="6868a-111">Kullanılabilir fiziksel bellek neutral olur.</span><span class="sxs-lookup"><span data-stu-id="6868a-111">The available physical memory is neutral.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6868a-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6868a-112">Remarks</span></span>  
 <span data-ttu-id="6868a-113">Bu değer tarafından ortak dil çalışma zamanı (CLR) için ana bilgisayar tarafından yapılan bir çağrı kullanılarak geçirilir [Iclrmemorynotificationcallback::onmemorynotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6868a-113">This value is passed by the host to the common language runtime (CLR) by using a call to the [ICLRMemoryNotificationCallback::OnMemoryNotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6868a-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6868a-114">Requirements</span></span>  
 <span data-ttu-id="6868a-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6868a-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6868a-116">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6868a-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6868a-117">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6868a-117">**Library:** MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="6868a-118">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="6868a-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6868a-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6868a-119">See also</span></span>

- [<span data-ttu-id="6868a-120">Barındırma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="6868a-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
