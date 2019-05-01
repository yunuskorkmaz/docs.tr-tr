---
title: ICLRMemoryNotificationCallback Arabirimi
ms.date: 03/30/2017
api_name:
- ICLRMemoryNotificationCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMemoryNotificationCallback
helpviewer_keywords:
- ICLRMemoryNotificationCallback interface [.NET Framework hosting]
ms.assetid: 873639e2-4837-4568-83b3-4493e67e4174
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c98ece9d60571034f3298f15897b10c4d8fb06f4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61948557"
---
# <a name="iclrmemorynotificationcallback-interface"></a><span data-ttu-id="8fabf-102">ICLRMemoryNotificationCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8fabf-102">ICLRMemoryNotificationCallback Interface</span></span>
<span data-ttu-id="8fabf-103">Win32 için benzer bir yaklaşım kullanarak rapor bellek baskısı koşullarını konağa sağlayan `CreateMemoryResourceNotification` işlevi.</span><span class="sxs-lookup"><span data-stu-id="8fabf-103">Allows the host to report memory pressure conditions using an approach similar to that of the Win32 `CreateMemoryResourceNotification` function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8fabf-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="8fabf-104">Methods</span></span>  
  
|<span data-ttu-id="8fabf-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="8fabf-105">Method</span></span>|<span data-ttu-id="8fabf-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8fabf-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8fabf-107">OnMemoryNotification Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8fabf-107">OnMemoryNotification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md)|<span data-ttu-id="8fabf-108">Bellek Yükü bilgisayarda ortak dil çalışma zamanı (CLR) bildirir.</span><span class="sxs-lookup"><span data-stu-id="8fabf-108">Notifies the common language runtime (CLR) of the memory load on the computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8fabf-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8fabf-109">Remarks</span></span>  
 <span data-ttu-id="8fabf-110">Konağın kullandığı `ICLRMemoryNotificationCallback` CLR bellek kaynaklarını serbest istemek için arabirim.</span><span class="sxs-lookup"><span data-stu-id="8fabf-110">The host uses the `ICLRMemoryNotificationCallback` interface to request that the CLR free memory resources.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8fabf-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8fabf-111">Requirements</span></span>  
 <span data-ttu-id="8fabf-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8fabf-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8fabf-113">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8fabf-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8fabf-114">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="8fabf-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8fabf-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8fabf-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fabf-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8fabf-116">See also</span></span>

- [<span data-ttu-id="8fabf-117">IHostMemoryManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8fabf-117">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="8fabf-118">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8fabf-118">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
