---
description: 'Hakkında daha fazla bilgi edinin: EMemoryAvailable numaralandırması'
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
ms.openlocfilehash: fdb33b45c354d39b1a52fd815a44041b659181ec
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785455"
---
# <a name="ememoryavailable-enumeration"></a><span data-ttu-id="b6040-103">EMemoryAvailable Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="b6040-103">EMemoryAvailable Enumeration</span></span>

<span data-ttu-id="b6040-104">Bilgisayardaki boş fiziksel bellek miktarını belirten değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="b6040-104">Contains values that indicate the amount of free physical memory on the computer.</span></span> <span data-ttu-id="b6040-105">Bu değerler, Windows API 'sindeki işlevden döndürülen yüksek ve düşük bellek olaylarına mantıksal olarak eşlenir `CreateMemoryResourceNotification` .</span><span class="sxs-lookup"><span data-stu-id="b6040-105">These values logically map to the events for high and low memory returned from the `CreateMemoryResourceNotification` function in the Windows API.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6040-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="b6040-106">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eMemoryAvailableLow     = 1,  
    eMemoryAvailableNeutral = 2,  
    eMemoryAvailableHigh    = 3
} EMemoryAvailable;  
```  
  
## <a name="members"></a><span data-ttu-id="b6040-107">Üyeler</span><span class="sxs-lookup"><span data-stu-id="b6040-107">Members</span></span>  
  
|<span data-ttu-id="b6040-108">Üye</span><span class="sxs-lookup"><span data-stu-id="b6040-108">Member</span></span>|<span data-ttu-id="b6040-109">Description</span><span class="sxs-lookup"><span data-stu-id="b6040-109">Description</span></span>|  
|------------|-----------------|  
|`eMemoryAvailableHigh`|<span data-ttu-id="b6040-110">Yeterince fiziksel bellek mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="b6040-110">Plenty of physical memory is available.</span></span>|  
|`eMemoryAvailableLow`|<span data-ttu-id="b6040-111">Çok az fiziksel bellek mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="b6040-111">Very little physical memory is available.</span></span>|  
|`eMemoryAvailableNeutral`|<span data-ttu-id="b6040-112">Kullanılabilir fiziksel bellek nötr.</span><span class="sxs-lookup"><span data-stu-id="b6040-112">The available physical memory is neutral.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b6040-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b6040-113">Remarks</span></span>  

 <span data-ttu-id="b6040-114">Bu değer, [ICLRMemoryNotificationCallback:: OnMemoryNotification](iclrmemorynotificationcallback-onmemorynotification-method.md) yöntemine yapılan bir çağrı kullanılarak ana bilgisayar tarafından ortak dil çalışma zamanına (CLR) geçirilir.</span><span class="sxs-lookup"><span data-stu-id="b6040-114">This value is passed by the host to the common language runtime (CLR) by using a call to the [ICLRMemoryNotificationCallback::OnMemoryNotification](iclrmemorynotificationcallback-onmemorynotification-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6040-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b6040-115">Requirements</span></span>  

 <span data-ttu-id="b6040-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6040-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6040-117">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b6040-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b6040-118">**Kitaplık:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b6040-118">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b6040-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6040-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6040-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b6040-120">See also</span></span>

- [<span data-ttu-id="b6040-121">Barındırma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="b6040-121">Hosting Enumerations</span></span>](hosting-enumerations.md)
