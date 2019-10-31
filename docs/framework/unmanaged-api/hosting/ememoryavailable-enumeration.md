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
ms.openlocfilehash: aec3c5f140df7eab10ea2bfa33634a4d853adcb0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134297"
---
# <a name="ememoryavailable-enumeration"></a><span data-ttu-id="3faa5-102">EMemoryAvailable Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="3faa5-102">EMemoryAvailable Enumeration</span></span>
<span data-ttu-id="3faa5-103">Bilgisayardaki boş fiziksel bellek miktarını belirten değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="3faa5-103">Contains values that indicate the amount of free physical memory on the computer.</span></span> <span data-ttu-id="3faa5-104">Bu değerler, Windows API 'sindeki `CreateMemoryResourceNotification` işlevinden döndürülen yüksek ve düşük bellek olaylarına mantıksal olarak eşlenir.</span><span class="sxs-lookup"><span data-stu-id="3faa5-104">These values logically map to the events for high and low memory returned from the `CreateMemoryResourceNotification` function in the Windows API.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3faa5-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3faa5-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eMemoryAvailableLow     = 1,  
    eMemoryAvailableNeutral = 2,  
    eMemoryAvailableHigh    = 3   
} EMemoryAvailable;  
```  
  
## <a name="members"></a><span data-ttu-id="3faa5-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="3faa5-106">Members</span></span>  
  
|<span data-ttu-id="3faa5-107">Üye</span><span class="sxs-lookup"><span data-stu-id="3faa5-107">Member</span></span>|<span data-ttu-id="3faa5-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3faa5-108">Description</span></span>|  
|------------|-----------------|  
|`eMemoryAvailableHigh`|<span data-ttu-id="3faa5-109">Yeterince fiziksel bellek mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="3faa5-109">Plenty of physical memory is available.</span></span>|  
|`eMemoryAvailableLow`|<span data-ttu-id="3faa5-110">Çok az fiziksel bellek mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="3faa5-110">Very little physical memory is available.</span></span>|  
|`eMemoryAvailableNeutral`|<span data-ttu-id="3faa5-111">Kullanılabilir fiziksel bellek nötr.</span><span class="sxs-lookup"><span data-stu-id="3faa5-111">The available physical memory is neutral.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3faa5-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3faa5-112">Remarks</span></span>  
 <span data-ttu-id="3faa5-113">Bu değer, [ICLRMemoryNotificationCallback:: OnMemoryNotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md) yöntemine yapılan bir çağrı kullanılarak ana bilgisayar tarafından ortak dil çalışma zamanına (CLR) geçirilir.</span><span class="sxs-lookup"><span data-stu-id="3faa5-113">This value is passed by the host to the common language runtime (CLR) by using a call to the [ICLRMemoryNotificationCallback::OnMemoryNotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3faa5-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3faa5-114">Requirements</span></span>  
 <span data-ttu-id="3faa5-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3faa5-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3faa5-116">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="3faa5-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3faa5-117">**Kitaplık:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="3faa5-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3faa5-118">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3faa5-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3faa5-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3faa5-119">See also</span></span>

- [<span data-ttu-id="3faa5-120">Barındırma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="3faa5-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
