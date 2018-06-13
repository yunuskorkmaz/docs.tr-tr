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
ms.openlocfilehash: 2c5cf7e17989f3c083c7c4e52fa8cfc09c00bc7d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431525"
---
# <a name="iclrmemorynotificationcallback-interface"></a><span data-ttu-id="c87dd-102">ICLRMemoryNotificationCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c87dd-102">ICLRMemoryNotificationCallback Interface</span></span>
<span data-ttu-id="c87dd-103">Win32 için benzer bir yaklaşım kullanarak rapor bellek baskısı koşullarını konağa verir `CreateMemoryResourceNotification` işlevi.</span><span class="sxs-lookup"><span data-stu-id="c87dd-103">Allows the host to report memory pressure conditions using an approach similar to that of the Win32 `CreateMemoryResourceNotification` function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c87dd-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="c87dd-104">Methods</span></span>  
  
|<span data-ttu-id="c87dd-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="c87dd-105">Method</span></span>|<span data-ttu-id="c87dd-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c87dd-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c87dd-107">OnMemoryNotification Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c87dd-107">OnMemoryNotification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md)|<span data-ttu-id="c87dd-108">Ortak dil çalışma zamanı (CLR) bilgisayardaki Bellek Yükü bildirir.</span><span class="sxs-lookup"><span data-stu-id="c87dd-108">Notifies the common language runtime (CLR) of the memory load on the computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c87dd-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c87dd-109">Remarks</span></span>  
 <span data-ttu-id="c87dd-110">Konağın kullandığı `ICLRMemoryNotificationCallback` CLR bellek kaynaklarını serbest istemek için arabirim.</span><span class="sxs-lookup"><span data-stu-id="c87dd-110">The host uses the `ICLRMemoryNotificationCallback` interface to request that the CLR free memory resources.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c87dd-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c87dd-111">Requirements</span></span>  
 <span data-ttu-id="c87dd-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c87dd-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c87dd-113">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c87dd-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c87dd-114">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="c87dd-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c87dd-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c87dd-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c87dd-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c87dd-116">See Also</span></span>  
 [<span data-ttu-id="c87dd-117">IHostMemoryManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c87dd-117">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 [<span data-ttu-id="c87dd-118">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c87dd-118">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
