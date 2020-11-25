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
ms.openlocfilehash: 6a8765bfd62a2e6543661804ab8d009ce19f8813
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724318"
---
# <a name="ememoryavailable-enumeration"></a><span data-ttu-id="cd5be-102">EMemoryAvailable Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="cd5be-102">EMemoryAvailable Enumeration</span></span>

<span data-ttu-id="cd5be-103">Bilgisayardaki boş fiziksel bellek miktarını belirten değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="cd5be-103">Contains values that indicate the amount of free physical memory on the computer.</span></span> <span data-ttu-id="cd5be-104">Bu değerler, Windows API 'sindeki işlevden döndürülen yüksek ve düşük bellek olaylarına mantıksal olarak eşlenir `CreateMemoryResourceNotification` .</span><span class="sxs-lookup"><span data-stu-id="cd5be-104">These values logically map to the events for high and low memory returned from the `CreateMemoryResourceNotification` function in the Windows API.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd5be-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="cd5be-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eMemoryAvailableLow     = 1,  
    eMemoryAvailableNeutral = 2,  
    eMemoryAvailableHigh    = 3
} EMemoryAvailable;  
```  
  
## <a name="members"></a><span data-ttu-id="cd5be-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="cd5be-106">Members</span></span>  
  
|<span data-ttu-id="cd5be-107">Üye</span><span class="sxs-lookup"><span data-stu-id="cd5be-107">Member</span></span>|<span data-ttu-id="cd5be-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cd5be-108">Description</span></span>|  
|------------|-----------------|  
|`eMemoryAvailableHigh`|<span data-ttu-id="cd5be-109">Yeterince fiziksel bellek mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="cd5be-109">Plenty of physical memory is available.</span></span>|  
|`eMemoryAvailableLow`|<span data-ttu-id="cd5be-110">Çok az fiziksel bellek mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="cd5be-110">Very little physical memory is available.</span></span>|  
|`eMemoryAvailableNeutral`|<span data-ttu-id="cd5be-111">Kullanılabilir fiziksel bellek nötr.</span><span class="sxs-lookup"><span data-stu-id="cd5be-111">The available physical memory is neutral.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cd5be-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cd5be-112">Remarks</span></span>  

 <span data-ttu-id="cd5be-113">Bu değer, [ICLRMemoryNotificationCallback:: OnMemoryNotification](iclrmemorynotificationcallback-onmemorynotification-method.md) yöntemine yapılan bir çağrı kullanılarak ana bilgisayar tarafından ortak dil çalışma zamanına (CLR) geçirilir.</span><span class="sxs-lookup"><span data-stu-id="cd5be-113">This value is passed by the host to the common language runtime (CLR) by using a call to the [ICLRMemoryNotificationCallback::OnMemoryNotification](iclrmemorynotificationcallback-onmemorynotification-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd5be-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cd5be-114">Requirements</span></span>  

 <span data-ttu-id="cd5be-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd5be-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd5be-116">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="cd5be-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cd5be-117">**Kitaplık:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cd5be-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cd5be-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd5be-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd5be-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cd5be-119">See also</span></span>

- [<span data-ttu-id="cd5be-120">Barındırma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="cd5be-120">Hosting Enumerations</span></span>](hosting-enumerations.md)
