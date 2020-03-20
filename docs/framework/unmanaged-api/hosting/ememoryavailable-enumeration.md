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
ms.openlocfilehash: 0073a532f680d8764ec9e76ea22326a630457043
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176441"
---
# <a name="ememoryavailable-enumeration"></a><span data-ttu-id="57941-102">EMemoryAvailable Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="57941-102">EMemoryAvailable Enumeration</span></span>
<span data-ttu-id="57941-103">Bilgisayardaki boş fiziksel bellek miktarını gösteren değerler içerir.</span><span class="sxs-lookup"><span data-stu-id="57941-103">Contains values that indicate the amount of free physical memory on the computer.</span></span> <span data-ttu-id="57941-104">Bu değerler, Windows API'daki `CreateMemoryResourceNotification` işlevden döndürülen yüksek ve düşük bellek olaylarının mantıksal olarak eşlenir.</span><span class="sxs-lookup"><span data-stu-id="57941-104">These values logically map to the events for high and low memory returned from the `CreateMemoryResourceNotification` function in the Windows API.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57941-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="57941-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eMemoryAvailableLow     = 1,  
    eMemoryAvailableNeutral = 2,  
    eMemoryAvailableHigh    = 3
} EMemoryAvailable;  
```  
  
## <a name="members"></a><span data-ttu-id="57941-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="57941-106">Members</span></span>  
  
|<span data-ttu-id="57941-107">Üye</span><span class="sxs-lookup"><span data-stu-id="57941-107">Member</span></span>|<span data-ttu-id="57941-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="57941-108">Description</span></span>|  
|------------|-----------------|  
|`eMemoryAvailableHigh`|<span data-ttu-id="57941-109">Çok sayıda fiziksel bellek mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="57941-109">Plenty of physical memory is available.</span></span>|  
|`eMemoryAvailableLow`|<span data-ttu-id="57941-110">Çok az fiziksel bellek mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="57941-110">Very little physical memory is available.</span></span>|  
|`eMemoryAvailableNeutral`|<span data-ttu-id="57941-111">Kullanılabilir fiziksel bellek nötrdür.</span><span class="sxs-lookup"><span data-stu-id="57941-111">The available physical memory is neutral.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="57941-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="57941-112">Remarks</span></span>  
 <span data-ttu-id="57941-113">Bu değer, [iCLRMemoryNotificationCallback::OnMemoryNotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md) yöntemine bir çağrı kullanılarak ana bilgisayar tarafından ortak dil çalışma süresine (CLR) aktarılır.</span><span class="sxs-lookup"><span data-stu-id="57941-113">This value is passed by the host to the common language runtime (CLR) by using a call to the [ICLRMemoryNotificationCallback::OnMemoryNotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57941-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="57941-114">Requirements</span></span>  
 <span data-ttu-id="57941-115">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57941-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57941-116">**Üstbilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="57941-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="57941-117">**Kütüphane:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="57941-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="57941-118">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57941-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57941-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="57941-119">See also</span></span>

- [<span data-ttu-id="57941-120">Barındırma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="57941-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
