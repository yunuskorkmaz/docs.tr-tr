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
ms.openlocfilehash: 5762a354bec485cb382b5460dfd2a337f79bee1a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95689543"
---
# <a name="iclrmemorynotificationcallback-interface"></a><span data-ttu-id="8282f-102">ICLRMemoryNotificationCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8282f-102">ICLRMemoryNotificationCallback Interface</span></span>

<span data-ttu-id="8282f-103">Konağın, Win32 işlevine benzer bir yaklaşım kullanarak bellek baskısı koşullarını rapor etmesine olanak tanır `CreateMemoryResourceNotification` .</span><span class="sxs-lookup"><span data-stu-id="8282f-103">Allows the host to report memory pressure conditions using an approach similar to that of the Win32 `CreateMemoryResourceNotification` function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8282f-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="8282f-104">Methods</span></span>  
  
|<span data-ttu-id="8282f-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="8282f-105">Method</span></span>|<span data-ttu-id="8282f-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8282f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8282f-107">OnMemoryNotification Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8282f-107">OnMemoryNotification Method</span></span>](iclrmemorynotificationcallback-onmemorynotification-method.md)|<span data-ttu-id="8282f-108">Bilgisayardaki bellek yükünün ortak dil çalışma zamanına (CLR) bildirir.</span><span class="sxs-lookup"><span data-stu-id="8282f-108">Notifies the common language runtime (CLR) of the memory load on the computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8282f-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8282f-109">Remarks</span></span>  

 <span data-ttu-id="8282f-110">Ana bilgisayar, `ICLRMemoryNotificationCallback` clr boş bellek kaynaklarını istemek için arabirimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="8282f-110">The host uses the `ICLRMemoryNotificationCallback` interface to request that the CLR free memory resources.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8282f-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8282f-111">Requirements</span></span>  

 <span data-ttu-id="8282f-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8282f-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8282f-113">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8282f-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8282f-114">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="8282f-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8282f-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8282f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8282f-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8282f-116">See also</span></span>

- [<span data-ttu-id="8282f-117">IHostMemoryManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8282f-117">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
- [<span data-ttu-id="8282f-118">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8282f-118">Hosting Interfaces</span></span>](hosting-interfaces.md)
