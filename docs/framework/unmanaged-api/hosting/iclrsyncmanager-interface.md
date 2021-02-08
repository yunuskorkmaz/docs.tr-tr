---
description: ': ICLRSyncManager Arabirimi hakkında daha fazla bilgi'
title: ICLRSyncManager Arabirimi
ms.date: 03/30/2017
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
ms.openlocfilehash: 188d1c913d75666aea09b17244012401d377fa10
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785022"
---
# <a name="iclrsyncmanager-interface"></a><span data-ttu-id="bbc1b-103">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bbc1b-103">ICLRSyncManager Interface</span></span>

<span data-ttu-id="bbc1b-104">Konağın istenen görevler hakkında bilgi almasını ve eşitleme uygulamasında kilitlenmeleri algılamasını sağlayan yöntemleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bbc1b-104">Defines methods that allow the host to get information about requested tasks and to detect deadlocks in its synchronization implementation.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bbc1b-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="bbc1b-105">Methods</span></span>  
  
|<span data-ttu-id="bbc1b-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="bbc1b-106">Method</span></span>|<span data-ttu-id="bbc1b-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bbc1b-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bbc1b-108">CreateRWLockOwnerIterator Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bbc1b-108">CreateRWLockOwnerIterator Method</span></span>](iclrsyncmanager-createrwlockowneriterator-method.md)|<span data-ttu-id="bbc1b-109">Ortak dil çalışma zamanının (CLR), bir okuyucu-yazıcı kilidinde bekleyen görev kümesini belirlemede kullanacağı konak için bir yineleyici oluşturmasını ister.</span><span class="sxs-lookup"><span data-stu-id="bbc1b-109">Requests that the common language runtime (CLR) create an iterator for the host to use to determine the set of tasks waiting on a reader-writer lock.</span></span>|  
|[<span data-ttu-id="bbc1b-110">DeleteRWLockOwnerIterator Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bbc1b-110">DeleteRWLockOwnerIterator Method</span></span>](iclrsyncmanager-deleterwlockowneriterator-method.md)|<span data-ttu-id="bbc1b-111">CLR 'nin bir çağrısıyla oluşturulmuş bir yineleyiciyi yok ettiğini ister `CreateRWLockOwnerIterator` .</span><span class="sxs-lookup"><span data-stu-id="bbc1b-111">Requests that the CLR destroy an iterator that was created by a call to `CreateRWLockOwnerIterator`.</span></span>|  
|[<span data-ttu-id="bbc1b-112">GetMonitorOwner Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bbc1b-112">GetMonitorOwner Method</span></span>](iclrsyncmanager-getmonitorowner-method.md)|<span data-ttu-id="bbc1b-113">Belirtilen izleyicinin sahibi olan görevi alır.</span><span class="sxs-lookup"><span data-stu-id="bbc1b-113">Gets the task that owns the specified monitor.</span></span>|  
|[<span data-ttu-id="bbc1b-114">GetRWLockOwnerNext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bbc1b-114">GetRWLockOwnerNext Method</span></span>](iclrsyncmanager-getrwlockownernext-method.md)|<span data-ttu-id="bbc1b-115">Geçerli okuyucu-yazıcı kilidinde bekleyen bir sonraki görevi alır.</span><span class="sxs-lookup"><span data-stu-id="bbc1b-115">Gets the next task that is waiting on the current reader-writer lock.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bbc1b-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bbc1b-116">Requirements</span></span>  

 <span data-ttu-id="bbc1b-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bbc1b-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bbc1b-118">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="bbc1b-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bbc1b-119">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="bbc1b-119">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bbc1b-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bbc1b-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbc1b-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bbc1b-121">See also</span></span>

- <xref:System.Threading.Thread>
- [<span data-ttu-id="bbc1b-122">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bbc1b-122">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
- <span data-ttu-id="bbc1b-123">[Yönetilen ve yönetilmeyen Iş parçacığı](/previous-versions/dotnet/netframework-4.0/5s8ee185(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="bbc1b-123">[Managed and Unmanaged Threading](/previous-versions/dotnet/netframework-4.0/5s8ee185(v=vs.100))</span></span>
- [<span data-ttu-id="bbc1b-124">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="bbc1b-124">Hosting Interfaces</span></span>](hosting-interfaces.md)
