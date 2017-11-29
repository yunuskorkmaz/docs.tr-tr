---
title: IHostThreadPoolManager Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostThreadPoolManager
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostThreadPoolManager
helpviewer_keywords: IHostThreadPoolManager interface [.NET Framework hosting]
ms.assetid: c3a2cd90-7c4e-4374-bb87-b41befb8344f
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2773042c695320ab1e90d4c5d341e2df5f0f778f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostthreadpoolmanager-interface"></a><span data-ttu-id="58690-102">IHostThreadPoolManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="58690-102">IHostThreadPoolManager Interface</span></span>
<span data-ttu-id="58690-103">Ortak dil çalışma zamanı (CLR) iş parçacığı havuzu yapılandırmak için ve iş parçacığı havuzu iş öğelerine kuyruğuna sağlayan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="58690-103">Provides methods that enable the common language runtime (CLR) to configure the thread pool and to queue work items to the thread pool.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="58690-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="58690-104">Methods</span></span>  
  
|<span data-ttu-id="58690-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="58690-105">Method</span></span>|<span data-ttu-id="58690-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="58690-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="58690-107">GetAvailableThreads yöntemi</span><span class="sxs-lookup"><span data-stu-id="58690-107">GetAvailableThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getavailablethreads-method.md)|<span data-ttu-id="58690-108">İş öğeleri şu anda işlenmiyor iş parçacığı havuzundaki iş parçacığı sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="58690-108">Gets the number of threads in the thread pool that are not currently processing work items.</span></span>|  
|[<span data-ttu-id="58690-109">GetMaxThreads yöntemi</span><span class="sxs-lookup"><span data-stu-id="58690-109">GetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getmaxthreads-method.md)|<span data-ttu-id="58690-110">Konak tutar iş parçacığı sayısı, iş parçacığı havuzundaki eşzamanlı olarak alır.</span><span class="sxs-lookup"><span data-stu-id="58690-110">Gets the maximum number of threads that the host maintains concurrently in the thread pool.</span></span>|  
|[<span data-ttu-id="58690-111">GetMinThreads yöntemi</span><span class="sxs-lookup"><span data-stu-id="58690-111">GetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getminthreads-method.md)|<span data-ttu-id="58690-112">Ana bilgisayar tutar boş iş parçacığı en az sayıda istekleri kapatıldığını içinde alır.</span><span class="sxs-lookup"><span data-stu-id="58690-112">Gets the minimum number of idle threads that the host maintains in anticipation of requests.</span></span>|  
|[<span data-ttu-id="58690-113">QueueUserWorkItem yöntemi</span><span class="sxs-lookup"><span data-stu-id="58690-113">QueueUserWorkItem Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md)|<span data-ttu-id="58690-114">Bir işlev yürütme için sıraya koyar ve işlev tarafından kullanılacak verilerini içeren bir nesne sağlar.</span><span class="sxs-lookup"><span data-stu-id="58690-114">Queues a function for execution, and provides an object containing data to be used by the function.</span></span>|  
|[<span data-ttu-id="58690-115">SetMaxThreads yöntemi</span><span class="sxs-lookup"><span data-stu-id="58690-115">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setmaxthreads-method.md)|<span data-ttu-id="58690-116">Ana iş parçacığı havuzundaki koruyabilirsiniz iş parçacığı sayısını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="58690-116">Sets the maximum number of threads that the host can maintain in the thread pool.</span></span>|  
|[<span data-ttu-id="58690-117">SetMinThreads yöntemi</span><span class="sxs-lookup"><span data-stu-id="58690-117">SetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setminthreads-method.md)|<span data-ttu-id="58690-118">Konak korumalıdır boş iş parçacığı sayısı alt sınırını istekleri kapatıldığını içinde ayarlar.</span><span class="sxs-lookup"><span data-stu-id="58690-118">Sets the minimum number of idle threads that the host must maintain in anticipation of requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="58690-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="58690-119">Remarks</span></span>  
 <span data-ttu-id="58690-120">Ana bilgisayar çağrıları belirtilen değerleri kullanarak iş parçacığı havuzu yapılandırmak için gerekli olmayan `SetMaxThreads` ve `SetMinThreads` yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="58690-120">The host is not required to configure the thread pool by using the values specified in calls to the `SetMaxThreads` and `SetMinThreads` methods.</span></span> <span data-ttu-id="58690-121">Bu durumda, ana bilgisayar bu yöntemlerden E_NOTIMPL HRESULT değerini döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="58690-121">In this case, the host should return an HRESULT value of E_NOTIMPL from these methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58690-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="58690-122">Requirements</span></span>  
 <span data-ttu-id="58690-123">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="58690-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58690-124">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="58690-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="58690-125">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="58690-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="58690-126">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58690-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58690-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="58690-127">See Also</span></span>  
 <xref:System.Threading>  
 <xref:System.Threading.ThreadPool>  
 [<span data-ttu-id="58690-128">Barındırma arabirimleri</span><span class="sxs-lookup"><span data-stu-id="58690-128">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
