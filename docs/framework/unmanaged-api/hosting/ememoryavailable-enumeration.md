---
title: "EMemoryAvailable Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: EMemoryAvailable
api_location: mscoree.dll
api_type: COM
f1_keywords: EMemoryAvailable
helpviewer_keywords: EMemoryAvailable enumeration [.NET Framework hosting]
ms.assetid: 38e72a06-dbed-473b-a59b-7e0b3ea4f2af
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c378f2cd9b033e578ff15472a10a6dc295ad6539
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="ememoryavailable-enumeration"></a><span data-ttu-id="3aab0-102">EMemoryAvailable Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="3aab0-102">EMemoryAvailable Enumeration</span></span>
<span data-ttu-id="3aab0-103">Bilgisayardaki boş fiziksel bellek miktarını belirtin değerlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="3aab0-103">Contains values that indicate the amount of free physical memory on the computer.</span></span> <span data-ttu-id="3aab0-104">Bellek yüksek ve düşük döndürülen için bu değerleri mantıksal olarak olaylara eşleme `CreateMemoryResourceNotification` Win32 API işlev.</span><span class="sxs-lookup"><span data-stu-id="3aab0-104">These values logically map to the events for high and low memory returned from the `CreateMemoryResourceNotification` function in the Win32 API.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3aab0-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3aab0-105">Syntax</span></span>  
  
```  
typedef enum {  
    eMemoryAvailableLow     = 1,  
    eMemoryAvailableNeutral = 2,  
    eMemoryAvailableHigh    = 3   
} EMemoryAvailable;  
```  
  
## <a name="members"></a><span data-ttu-id="3aab0-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="3aab0-106">Members</span></span>  
  
|<span data-ttu-id="3aab0-107">Üye</span><span class="sxs-lookup"><span data-stu-id="3aab0-107">Member</span></span>|<span data-ttu-id="3aab0-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3aab0-108">Description</span></span>|  
|------------|-----------------|  
|`eMemoryAvailableHigh`|<span data-ttu-id="3aab0-109">Yeterli fiziksel bellek kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3aab0-109">Plenty of physical memory is available.</span></span>|  
|`eMemoryAvailableLow`|<span data-ttu-id="3aab0-110">Çok az fiziksel bellek yok.</span><span class="sxs-lookup"><span data-stu-id="3aab0-110">Very little physical memory is available.</span></span>|  
|`eMemoryAvailableNeutral`|<span data-ttu-id="3aab0-111">Kullanılabilir fiziksel bellek neutral olur.</span><span class="sxs-lookup"><span data-stu-id="3aab0-111">The available physical memory is neutral.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3aab0-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3aab0-112">Remarks</span></span>  
 <span data-ttu-id="3aab0-113">Bu değer tarafından ortak dil çalışma zamanı (CLR) için ana bilgisayar tarafından yapılan bir çağrı kullanılarak geçirilir [Iclrmemorynotificationcallback::onmemorynotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="3aab0-113">This value is passed by the host to the common language runtime (CLR) by using a call to the [ICLRMemoryNotificationCallback::OnMemoryNotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3aab0-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3aab0-114">Requirements</span></span>  
 <span data-ttu-id="3aab0-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3aab0-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3aab0-116">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3aab0-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3aab0-117">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3aab0-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3aab0-118">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3aab0-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3aab0-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3aab0-119">See Also</span></span>  
 [<span data-ttu-id="3aab0-120">Barındırma numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="3aab0-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
