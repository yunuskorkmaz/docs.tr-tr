---
description: ': ICLRMemoryNotificationCallback arabirimi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 46e53cdf0b7f797b8945237d47fc3b521b08ddb7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689249"
---
# <a name="iclrmemorynotificationcallback-interface"></a><span data-ttu-id="ebeb5-103">ICLRMemoryNotificationCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ebeb5-103">ICLRMemoryNotificationCallback Interface</span></span>

<span data-ttu-id="ebeb5-104">Konağın, Win32 işlevine benzer bir yaklaşım kullanarak bellek baskısı koşullarını rapor etmesine olanak tanır `CreateMemoryResourceNotification` .</span><span class="sxs-lookup"><span data-stu-id="ebeb5-104">Allows the host to report memory pressure conditions using an approach similar to that of the Win32 `CreateMemoryResourceNotification` function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ebeb5-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="ebeb5-105">Methods</span></span>  
  
|<span data-ttu-id="ebeb5-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="ebeb5-106">Method</span></span>|<span data-ttu-id="ebeb5-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ebeb5-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ebeb5-108">OnMemoryNotification Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ebeb5-108">OnMemoryNotification Method</span></span>](iclrmemorynotificationcallback-onmemorynotification-method.md)|<span data-ttu-id="ebeb5-109">Bilgisayardaki bellek yükünün ortak dil çalışma zamanına (CLR) bildirir.</span><span class="sxs-lookup"><span data-stu-id="ebeb5-109">Notifies the common language runtime (CLR) of the memory load on the computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ebeb5-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ebeb5-110">Remarks</span></span>  

 <span data-ttu-id="ebeb5-111">Ana bilgisayar, `ICLRMemoryNotificationCallback` clr boş bellek kaynaklarını istemek için arabirimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="ebeb5-111">The host uses the `ICLRMemoryNotificationCallback` interface to request that the CLR free memory resources.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ebeb5-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ebeb5-112">Requirements</span></span>  

 <span data-ttu-id="ebeb5-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ebeb5-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ebeb5-114">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ebeb5-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ebeb5-115">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="ebeb5-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ebeb5-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ebeb5-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebeb5-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ebeb5-117">See also</span></span>

- [<span data-ttu-id="ebeb5-118">IHostMemoryManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ebeb5-118">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
- [<span data-ttu-id="ebeb5-119">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ebeb5-119">Hosting Interfaces</span></span>](hosting-interfaces.md)
