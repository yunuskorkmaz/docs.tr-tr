---
title: ICLRSyncManager Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRSyncManager
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRSyncManager
helpviewer_keywords: ICLRSyncManager interface [.NET Framework hosting]
ms.assetid: a49f9d80-1c76-4ddd-8c49-34f913a5c596
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1e47f02a5a84b909b03c6be4e0a43c7166a1ddc9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrsyncmanager-interface"></a><span data-ttu-id="c61d9-102">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c61d9-102">ICLRSyncManager Interface</span></span>
<span data-ttu-id="c61d9-103">İstenen görevler hakkında bilgi almak ve kendi eşitleme uygulamasında kilitlenmeleri algılamak için konak izin yöntemleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c61d9-103">Defines methods that allow the host to get information about requested tasks and to detect deadlocks in its synchronization implementation.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c61d9-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="c61d9-104">Methods</span></span>  
  
|<span data-ttu-id="c61d9-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="c61d9-105">Method</span></span>|<span data-ttu-id="c61d9-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c61d9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c61d9-107">Createrwlockownerıterator yöntemi</span><span class="sxs-lookup"><span data-stu-id="c61d9-107">CreateRWLockOwnerIterator Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md)|<span data-ttu-id="c61d9-108">Ortak dil çalışma zamanı (CLR) oluşturma yineleyici Okuyucu-Yazıcı kilit Bekleyen Görevler belirlemek için kullanılacak ana bilgisayar için istek sayısı.</span><span class="sxs-lookup"><span data-stu-id="c61d9-108">Requests that the common language runtime (CLR) create an iterator for the host to use to determine the set of tasks waiting on a reader-writer lock.</span></span>|  
|[<span data-ttu-id="c61d9-109">Deleterwlockownerıterator yöntemi</span><span class="sxs-lookup"><span data-stu-id="c61d9-109">DeleteRWLockOwnerIterator Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md)|<span data-ttu-id="c61d9-110">CLR yapılan bir çağrı tarafından oluşturulan bir yineleyici destroy istekleri `CreateRWLockOwnerIterator`.</span><span class="sxs-lookup"><span data-stu-id="c61d9-110">Requests that the CLR destroy an iterator that was created by a call to `CreateRWLockOwnerIterator`.</span></span>|  
|[<span data-ttu-id="c61d9-111">GetMonitorOwner yöntemi</span><span class="sxs-lookup"><span data-stu-id="c61d9-111">GetMonitorOwner Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getmonitorowner-method.md)|<span data-ttu-id="c61d9-112">Belirtilen İzleyici sahibi görev alır.</span><span class="sxs-lookup"><span data-stu-id="c61d9-112">Gets the task that owns the specified monitor.</span></span>|  
|[<span data-ttu-id="c61d9-113">GetRWLockOwnerNext yöntemi</span><span class="sxs-lookup"><span data-stu-id="c61d9-113">GetRWLockOwnerNext Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getrwlockownernext-method.md)|<span data-ttu-id="c61d9-114">Geçerli Okuyucu-Yazıcı kilidi beklerken sonraki görev alır.</span><span class="sxs-lookup"><span data-stu-id="c61d9-114">Gets the next task that is waiting on the current reader-writer lock.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c61d9-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c61d9-115">Requirements</span></span>  
 <span data-ttu-id="c61d9-116">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c61d9-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c61d9-117">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c61d9-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c61d9-118">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="c61d9-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c61d9-119">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c61d9-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c61d9-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c61d9-120">See Also</span></span>  
 <xref:System.Threading.Thread>  
 [<span data-ttu-id="c61d9-121">Ihostsyncmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="c61d9-121">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 [<span data-ttu-id="c61d9-122">Yönetilen ve yönetilmeyen iş parçacığı oluşturma</span><span class="sxs-lookup"><span data-stu-id="c61d9-122">Managed and Unmanaged Threading</span></span>](http://msdn.microsoft.com/en-us/db425c20-4b2f-4433-bf96-76071c7881e5)  
 [<span data-ttu-id="c61d9-123">Barındırma arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c61d9-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
