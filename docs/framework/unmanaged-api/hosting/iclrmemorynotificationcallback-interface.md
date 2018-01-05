---
title: ICLRMemoryNotificationCallback Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRMemoryNotificationCallback
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRMemoryNotificationCallback
helpviewer_keywords: ICLRMemoryNotificationCallback interface [.NET Framework hosting]
ms.assetid: 873639e2-4837-4568-83b3-4493e67e4174
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cc09e3668dc814360de0256c2476ffa7b61462ed
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrmemorynotificationcallback-interface"></a><span data-ttu-id="5e8b3-102">ICLRMemoryNotificationCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5e8b3-102">ICLRMemoryNotificationCallback Interface</span></span>
<span data-ttu-id="5e8b3-103">Win32 için benzer bir yaklaşım kullanarak rapor bellek baskısı koşullarını konağa verir `CreateMemoryResourceNotification` işlevi.</span><span class="sxs-lookup"><span data-stu-id="5e8b3-103">Allows the host to report memory pressure conditions using an approach similar to that of the Win32 `CreateMemoryResourceNotification` function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5e8b3-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="5e8b3-104">Methods</span></span>  
  
|<span data-ttu-id="5e8b3-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="5e8b3-105">Method</span></span>|<span data-ttu-id="5e8b3-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5e8b3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5e8b3-107">OnMemoryNotification Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5e8b3-107">OnMemoryNotification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md)|<span data-ttu-id="5e8b3-108">Ortak dil çalışma zamanı (CLR) bilgisayardaki Bellek Yükü bildirir.</span><span class="sxs-lookup"><span data-stu-id="5e8b3-108">Notifies the common language runtime (CLR) of the memory load on the computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5e8b3-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5e8b3-109">Remarks</span></span>  
 <span data-ttu-id="5e8b3-110">Konağın kullandığı `ICLRMemoryNotificationCallback` CLR bellek kaynaklarını serbest istemek için arabirim.</span><span class="sxs-lookup"><span data-stu-id="5e8b3-110">The host uses the `ICLRMemoryNotificationCallback` interface to request that the CLR free memory resources.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e8b3-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5e8b3-111">Requirements</span></span>  
 <span data-ttu-id="5e8b3-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e8b3-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e8b3-113">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5e8b3-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5e8b3-114">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="5e8b3-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5e8b3-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e8b3-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e8b3-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5e8b3-116">See Also</span></span>  
 [<span data-ttu-id="5e8b3-117">IHostMemoryManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5e8b3-117">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 [<span data-ttu-id="5e8b3-118">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="5e8b3-118">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
