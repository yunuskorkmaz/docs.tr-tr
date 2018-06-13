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
ms.openlocfilehash: 92097cdf735630f3537296f188bd83ea8162add2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33441146"
---
# <a name="ihostthreadpoolmanager-interface"></a><span data-ttu-id="ac1cf-102">IHostThreadPoolManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ac1cf-102">IHostThreadPoolManager Interface</span></span>
<span data-ttu-id="ac1cf-103">Ortak dil çalışma zamanı (CLR) iş parçacığı havuzu yapılandırmak için ve iş parçacığı havuzu iş öğelerine kuyruğuna sağlayan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="ac1cf-103">Provides methods that enable the common language runtime (CLR) to configure the thread pool and to queue work items to the thread pool.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ac1cf-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="ac1cf-104">Methods</span></span>  
  
|<span data-ttu-id="ac1cf-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="ac1cf-105">Method</span></span>|<span data-ttu-id="ac1cf-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ac1cf-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ac1cf-107">GetAvailableThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ac1cf-107">GetAvailableThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getavailablethreads-method.md)|<span data-ttu-id="ac1cf-108">İş öğeleri şu anda işlenmiyor iş parçacığı havuzundaki iş parçacığı sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="ac1cf-108">Gets the number of threads in the thread pool that are not currently processing work items.</span></span>|  
|[<span data-ttu-id="ac1cf-109">GetMaxThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ac1cf-109">GetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getmaxthreads-method.md)|<span data-ttu-id="ac1cf-110">Konak tutar iş parçacığı sayısı, iş parçacığı havuzundaki eşzamanlı olarak alır.</span><span class="sxs-lookup"><span data-stu-id="ac1cf-110">Gets the maximum number of threads that the host maintains concurrently in the thread pool.</span></span>|  
|[<span data-ttu-id="ac1cf-111">GetMinThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ac1cf-111">GetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getminthreads-method.md)|<span data-ttu-id="ac1cf-112">Ana bilgisayar tutar boş iş parçacığı en az sayıda istekleri kapatıldığını içinde alır.</span><span class="sxs-lookup"><span data-stu-id="ac1cf-112">Gets the minimum number of idle threads that the host maintains in anticipation of requests.</span></span>|  
|[<span data-ttu-id="ac1cf-113">QueueUserWorkItem Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ac1cf-113">QueueUserWorkItem Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md)|<span data-ttu-id="ac1cf-114">Bir işlev yürütme için sıraya koyar ve işlev tarafından kullanılacak verilerini içeren bir nesne sağlar.</span><span class="sxs-lookup"><span data-stu-id="ac1cf-114">Queues a function for execution, and provides an object containing data to be used by the function.</span></span>|  
|[<span data-ttu-id="ac1cf-115">SetMaxThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ac1cf-115">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setmaxthreads-method.md)|<span data-ttu-id="ac1cf-116">Ana iş parçacığı havuzundaki koruyabilirsiniz iş parçacığı sayısını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="ac1cf-116">Sets the maximum number of threads that the host can maintain in the thread pool.</span></span>|  
|[<span data-ttu-id="ac1cf-117">SetMinThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ac1cf-117">SetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setminthreads-method.md)|<span data-ttu-id="ac1cf-118">Konak korumalıdır boş iş parçacığı sayısı alt sınırını istekleri kapatıldığını içinde ayarlar.</span><span class="sxs-lookup"><span data-stu-id="ac1cf-118">Sets the minimum number of idle threads that the host must maintain in anticipation of requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ac1cf-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ac1cf-119">Remarks</span></span>  
 <span data-ttu-id="ac1cf-120">Ana bilgisayar çağrıları belirtilen değerleri kullanarak iş parçacığı havuzu yapılandırmak için gerekli olmayan `SetMaxThreads` ve `SetMinThreads` yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="ac1cf-120">The host is not required to configure the thread pool by using the values specified in calls to the `SetMaxThreads` and `SetMinThreads` methods.</span></span> <span data-ttu-id="ac1cf-121">Bu durumda, ana bilgisayar bu yöntemlerden E_NOTIMPL HRESULT değerini döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="ac1cf-121">In this case, the host should return an HRESULT value of E_NOTIMPL from these methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac1cf-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ac1cf-122">Requirements</span></span>  
 <span data-ttu-id="ac1cf-123">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac1cf-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac1cf-124">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ac1cf-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ac1cf-125">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="ac1cf-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ac1cf-126">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac1cf-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac1cf-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ac1cf-127">See Also</span></span>  
 <xref:System.Threading>  
 <xref:System.Threading.ThreadPool>  
 [<span data-ttu-id="ac1cf-128">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ac1cf-128">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
