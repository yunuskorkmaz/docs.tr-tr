---
title: IHostManualEvent Arabirimi
ms.date: 03/30/2017
api_name:
- IHostManualEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostManualEvent
helpviewer_keywords:
- IHostManualEvent interface [.NET Framework hosting]
ms.assetid: 300c2661-b7d1-4c39-b080-9ebdef0fd523
topic_type:
- apiref
ms.openlocfilehash: 7c46f00063cdf9281a5f1080594e8d6dbc6c101e
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804592"
---
# <a name="ihostmanualevent-interface"></a><span data-ttu-id="40eea-102">IHostManualEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="40eea-102">IHostManualEvent Interface</span></span>
<span data-ttu-id="40eea-103">Konağın el ile sıfırlama olayının temsili için bir uygulama sağlar.</span><span class="sxs-lookup"><span data-stu-id="40eea-103">Provides the host's implementation of a representation of a manual reset event.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="40eea-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="40eea-104">Methods</span></span>  
  
|<span data-ttu-id="40eea-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="40eea-105">Method</span></span>|<span data-ttu-id="40eea-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="40eea-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="40eea-107">Reset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="40eea-107">Reset Method</span></span>](ihostmanualevent-reset-method.md)|<span data-ttu-id="40eea-108">Geçerli örneği, `IHostManualEvent` sinyal olmayan bir duruma sıfırlar.</span><span class="sxs-lookup"><span data-stu-id="40eea-108">Resets the current `IHostManualEvent` instance to a non-signaled state.</span></span>|  
|[<span data-ttu-id="40eea-109">Set Yöntemi</span><span class="sxs-lookup"><span data-stu-id="40eea-109">Set Method</span></span>](ihostmanualevent-set-method.md)|<span data-ttu-id="40eea-110">Geçerli `IHostManualEvent` örneği bir sinyal durumuna ayarlar.</span><span class="sxs-lookup"><span data-stu-id="40eea-110">Sets the current `IHostManualEvent` instance to a signaled state.</span></span>|  
|[<span data-ttu-id="40eea-111">Wait Yöntemi</span><span class="sxs-lookup"><span data-stu-id="40eea-111">Wait Method</span></span>](ihostmanualevent-wait-method.md)|<span data-ttu-id="40eea-112">Geçerli örneğin, `IHostManualEvent` sahip olana kadar beklemesini veya belirli bir süre geçtikten sonra gelmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="40eea-112">Causes the current `IHostManualEvent` instance to wait until it is owned, or a specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="40eea-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="40eea-113">Requirements</span></span>  
 <span data-ttu-id="40eea-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40eea-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40eea-115">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="40eea-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="40eea-116">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="40eea-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="40eea-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40eea-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40eea-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="40eea-118">See also</span></span>

- [<span data-ttu-id="40eea-119">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="40eea-119">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="40eea-120">IHostAutoEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="40eea-120">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="40eea-121">IHostSemaphore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="40eea-121">IHostSemaphore Interface</span></span>](ihostsemaphore-interface.md)
- [<span data-ttu-id="40eea-122">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="40eea-122">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
- [<span data-ttu-id="40eea-123">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="40eea-123">Hosting Interfaces</span></span>](hosting-interfaces.md)
