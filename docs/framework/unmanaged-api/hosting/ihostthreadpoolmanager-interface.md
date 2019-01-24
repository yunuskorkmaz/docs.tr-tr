---
title: IHostThreadPoolManager Arabirimi
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager
helpviewer_keywords:
- IHostThreadPoolManager interface [.NET Framework hosting]
ms.assetid: c3a2cd90-7c4e-4374-bb87-b41befb8344f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b7fc0a271a9c62406d2942f387a5458e21211116
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54522732"
---
# <a name="ihostthreadpoolmanager-interface"></a><span data-ttu-id="6523a-102">IHostThreadPoolManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6523a-102">IHostThreadPoolManager Interface</span></span>
<span data-ttu-id="6523a-103">Ortak dil çalışma zamanı (CLR) iş parçacığı havuzu yapılandırmak ve iş parçacığı havuzu iş öğelerine kuyruğuna olanak tanıyan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="6523a-103">Provides methods that enable the common language runtime (CLR) to configure the thread pool and to queue work items to the thread pool.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6523a-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="6523a-104">Methods</span></span>  
  
|<span data-ttu-id="6523a-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="6523a-105">Method</span></span>|<span data-ttu-id="6523a-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6523a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6523a-107">GetAvailableThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6523a-107">GetAvailableThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getavailablethreads-method.md)|<span data-ttu-id="6523a-108">İş öğeleri şu anda işleme değil iş parçacığı havuzundaki iş parçacığı sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="6523a-108">Gets the number of threads in the thread pool that are not currently processing work items.</span></span>|  
|[<span data-ttu-id="6523a-109">GetMaxThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6523a-109">GetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getmaxthreads-method.md)|<span data-ttu-id="6523a-110">Konak tutan iş parçacığı sayısı, iş parçacığı havuzundaki eşzamanlı olarak alır.</span><span class="sxs-lookup"><span data-stu-id="6523a-110">Gets the maximum number of threads that the host maintains concurrently in the thread pool.</span></span>|  
|[<span data-ttu-id="6523a-111">GetMinThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6523a-111">GetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getminthreads-method.md)|<span data-ttu-id="6523a-112">En az sayıda konak tutar boşta iş parçacıkları istekleri olasılığına alır.</span><span class="sxs-lookup"><span data-stu-id="6523a-112">Gets the minimum number of idle threads that the host maintains in anticipation of requests.</span></span>|  
|[<span data-ttu-id="6523a-113">QueueUserWorkItem Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6523a-113">QueueUserWorkItem Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md)|<span data-ttu-id="6523a-114">Bir işlev yürütme için sıralar ve işlev tarafından kullanılan veri içeren bir nesne sağlar.</span><span class="sxs-lookup"><span data-stu-id="6523a-114">Queues a function for execution, and provides an object containing data to be used by the function.</span></span>|  
|[<span data-ttu-id="6523a-115">SetMaxThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6523a-115">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setmaxthreads-method.md)|<span data-ttu-id="6523a-116">Ana iş parçacığı havuzundaki koruyabilirsiniz iş parçacığı sayısını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="6523a-116">Sets the maximum number of threads that the host can maintain in the thread pool.</span></span>|  
|[<span data-ttu-id="6523a-117">SetMinThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6523a-117">SetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setminthreads-method.md)|<span data-ttu-id="6523a-118">En az sayıda konak korumalıdır boşta iş parçacıkları istekleri olasılığına ayarlar.</span><span class="sxs-lookup"><span data-stu-id="6523a-118">Sets the minimum number of idle threads that the host must maintain in anticipation of requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6523a-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6523a-119">Remarks</span></span>  
 <span data-ttu-id="6523a-120">Ana iş parçacığı havuzu yapılan çağrıda belirtilen değerleri kullanarak yapılandırmak için gerekli değildir `SetMaxThreads` ve `SetMinThreads` yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="6523a-120">The host is not required to configure the thread pool by using the values specified in calls to the `SetMaxThreads` and `SetMinThreads` methods.</span></span> <span data-ttu-id="6523a-121">Bu durumda, konak, bu yöntemlerden E_NOTIMPL bir HRESULT değerini döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="6523a-121">In this case, the host should return an HRESULT value of E_NOTIMPL from these methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6523a-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6523a-122">Requirements</span></span>  
 <span data-ttu-id="6523a-123">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6523a-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6523a-124">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6523a-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6523a-125">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="6523a-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6523a-126">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6523a-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6523a-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6523a-127">See also</span></span>
- <xref:System.Threading>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="6523a-128">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="6523a-128">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
