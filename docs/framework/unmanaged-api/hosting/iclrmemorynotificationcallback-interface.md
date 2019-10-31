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
ms.openlocfilehash: e980356ad592e137df7d08dadd77431b0e295380
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140995"
---
# <a name="iclrmemorynotificationcallback-interface"></a><span data-ttu-id="7c5c4-102">ICLRMemoryNotificationCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7c5c4-102">ICLRMemoryNotificationCallback Interface</span></span>
<span data-ttu-id="7c5c4-103">Konağın, Win32 `CreateMemoryResourceNotification` işleviyle benzer bir yaklaşım kullanarak bellek baskısı koşullarını rapor etmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="7c5c4-103">Allows the host to report memory pressure conditions using an approach similar to that of the Win32 `CreateMemoryResourceNotification` function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7c5c4-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="7c5c4-104">Methods</span></span>  
  
|<span data-ttu-id="7c5c4-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="7c5c4-105">Method</span></span>|<span data-ttu-id="7c5c4-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7c5c4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7c5c4-107">OnMemoryNotification Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7c5c4-107">OnMemoryNotification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md)|<span data-ttu-id="7c5c4-108">Bilgisayardaki bellek yükünün ortak dil çalışma zamanına (CLR) bildirir.</span><span class="sxs-lookup"><span data-stu-id="7c5c4-108">Notifies the common language runtime (CLR) of the memory load on the computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7c5c4-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7c5c4-109">Remarks</span></span>  
 <span data-ttu-id="7c5c4-110">Konak, CLR boş bellek kaynakları istemek için `ICLRMemoryNotificationCallback` arabirimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="7c5c4-110">The host uses the `ICLRMemoryNotificationCallback` interface to request that the CLR free memory resources.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c5c4-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7c5c4-111">Requirements</span></span>  
 <span data-ttu-id="7c5c4-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c5c4-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c5c4-113">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="7c5c4-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7c5c4-114">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="7c5c4-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7c5c4-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c5c4-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c5c4-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7c5c4-116">See also</span></span>

- [<span data-ttu-id="7c5c4-117">IHostMemoryManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7c5c4-117">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="7c5c4-118">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="7c5c4-118">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
