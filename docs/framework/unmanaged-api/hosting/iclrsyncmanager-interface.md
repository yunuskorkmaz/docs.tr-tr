---
title: ICLRSyncManager Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRSyncManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRSyncManager
helpviewer_keywords:
- ICLRSyncManager interface [.NET Framework hosting]
ms.assetid: a49f9d80-1c76-4ddd-8c49-34f913a5c596
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f75a9b532e91966d6b0be9ac6602080eac896ed8
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="iclrsyncmanager-interface"></a><span data-ttu-id="27d67-102">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="27d67-102">ICLRSyncManager Interface</span></span>
<span data-ttu-id="27d67-103">İstenen görevler hakkında bilgi almak ve kendi eşitleme uygulamasında kilitlenmeleri algılamak için konak izin yöntemleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="27d67-103">Defines methods that allow the host to get information about requested tasks and to detect deadlocks in its synchronization implementation.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="27d67-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="27d67-104">Methods</span></span>  
  
|<span data-ttu-id="27d67-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="27d67-105">Method</span></span>|<span data-ttu-id="27d67-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="27d67-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="27d67-107">CreateRWLockOwnerIterator Yöntemi</span><span class="sxs-lookup"><span data-stu-id="27d67-107">CreateRWLockOwnerIterator Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md)|<span data-ttu-id="27d67-108">Ortak dil çalışma zamanı (CLR) oluşturma yineleyici Okuyucu-Yazıcı kilit Bekleyen Görevler belirlemek için kullanılacak ana bilgisayar için istek sayısı.</span><span class="sxs-lookup"><span data-stu-id="27d67-108">Requests that the common language runtime (CLR) create an iterator for the host to use to determine the set of tasks waiting on a reader-writer lock.</span></span>|  
|[<span data-ttu-id="27d67-109">DeleteRWLockOwnerIterator Yöntemi</span><span class="sxs-lookup"><span data-stu-id="27d67-109">DeleteRWLockOwnerIterator Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md)|<span data-ttu-id="27d67-110">CLR yapılan bir çağrı tarafından oluşturulan bir yineleyici destroy istekleri `CreateRWLockOwnerIterator`.</span><span class="sxs-lookup"><span data-stu-id="27d67-110">Requests that the CLR destroy an iterator that was created by a call to `CreateRWLockOwnerIterator`.</span></span>|  
|[<span data-ttu-id="27d67-111">GetMonitorOwner Yöntemi</span><span class="sxs-lookup"><span data-stu-id="27d67-111">GetMonitorOwner Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getmonitorowner-method.md)|<span data-ttu-id="27d67-112">Belirtilen İzleyici sahibi görev alır.</span><span class="sxs-lookup"><span data-stu-id="27d67-112">Gets the task that owns the specified monitor.</span></span>|  
|[<span data-ttu-id="27d67-113">GetRWLockOwnerNext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="27d67-113">GetRWLockOwnerNext Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getrwlockownernext-method.md)|<span data-ttu-id="27d67-114">Geçerli Okuyucu-Yazıcı kilidi beklerken sonraki görev alır.</span><span class="sxs-lookup"><span data-stu-id="27d67-114">Gets the next task that is waiting on the current reader-writer lock.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="27d67-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="27d67-115">Requirements</span></span>  
 <span data-ttu-id="27d67-116">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="27d67-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27d67-117">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="27d67-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="27d67-118">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="27d67-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="27d67-119">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27d67-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27d67-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="27d67-120">See Also</span></span>  
 <xref:System.Threading.Thread>  
 [<span data-ttu-id="27d67-121">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="27d67-121">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 [<span data-ttu-id="27d67-122">Yönetilen ve yönetilmeyen iş parçacığı oluşturma</span><span class="sxs-lookup"><span data-stu-id="27d67-122">Managed and Unmanaged Threading</span></span>](http://msdn.microsoft.com/library/db425c20-4b2f-4433-bf96-76071c7881e5)  
 [<span data-ttu-id="27d67-123">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="27d67-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
