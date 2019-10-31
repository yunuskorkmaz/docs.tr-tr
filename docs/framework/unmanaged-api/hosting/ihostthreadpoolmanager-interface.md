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
ms.openlocfilehash: 8aef78c7cf70e6b2d97af9c47d57908b86729ff7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122079"
---
# <a name="ihostthreadpoolmanager-interface"></a><span data-ttu-id="ad02a-102">IHostThreadPoolManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ad02a-102">IHostThreadPoolManager Interface</span></span>
<span data-ttu-id="ad02a-103">Ortak dil çalışma zamanını (CLR) iş parçacığı havuzunu yapılandırmak ve iş öğelerini iş parçacığı havuzuna sıraya almak için etkinleştiren yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="ad02a-103">Provides methods that enable the common language runtime (CLR) to configure the thread pool and to queue work items to the thread pool.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ad02a-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="ad02a-104">Methods</span></span>  
  
|<span data-ttu-id="ad02a-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="ad02a-105">Method</span></span>|<span data-ttu-id="ad02a-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ad02a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ad02a-107">GetAvailableThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ad02a-107">GetAvailableThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getavailablethreads-method.md)|<span data-ttu-id="ad02a-108">İş öğelerini işlemeyen iş parçacığı havuzundaki iş parçacığı sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="ad02a-108">Gets the number of threads in the thread pool that are not currently processing work items.</span></span>|  
|[<span data-ttu-id="ad02a-109">GetMaxThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ad02a-109">GetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getmaxthreads-method.md)|<span data-ttu-id="ad02a-110">Konağın iş parçacığı havuzunda eşzamanlı olarak tuttuğu en fazla iş parçacığı sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="ad02a-110">Gets the maximum number of threads that the host maintains concurrently in the thread pool.</span></span>|  
|[<span data-ttu-id="ad02a-111">GetMinThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ad02a-111">GetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getminthreads-method.md)|<span data-ttu-id="ad02a-112">Olasılığına for isteklerinde konağın sakladığı en az boştaki iş parçacığı sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="ad02a-112">Gets the minimum number of idle threads that the host maintains in anticipation of requests.</span></span>|  
|[<span data-ttu-id="ad02a-113">QueueUserWorkItem Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ad02a-113">QueueUserWorkItem Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md)|<span data-ttu-id="ad02a-114">Yürütme için bir işlevi sıraya alır ve işlev tarafından kullanılacak verileri içeren bir nesne sağlar.</span><span class="sxs-lookup"><span data-stu-id="ad02a-114">Queues a function for execution, and provides an object containing data to be used by the function.</span></span>|  
|[<span data-ttu-id="ad02a-115">SetMaxThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ad02a-115">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setmaxthreads-method.md)|<span data-ttu-id="ad02a-116">Konağın iş parçacığı havuzunda koruyabileceği en fazla iş parçacığı sayısını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="ad02a-116">Sets the maximum number of threads that the host can maintain in the thread pool.</span></span>|  
|[<span data-ttu-id="ad02a-117">SetMinThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ad02a-117">SetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setminthreads-method.md)|<span data-ttu-id="ad02a-118">Konağın olasılığına isteklerinde saklanması gereken en az boş iş parçacığı sayısını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="ad02a-118">Sets the minimum number of idle threads that the host must maintain in anticipation of requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ad02a-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ad02a-119">Remarks</span></span>  
 <span data-ttu-id="ad02a-120">Ana bilgisayar, `SetMaxThreads` çağrılarında ve `SetMinThreads` metotlarında belirtilen değerleri kullanarak iş parçacığı havuzunu yapılandırmak için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="ad02a-120">The host is not required to configure the thread pool by using the values specified in calls to the `SetMaxThreads` and `SetMinThreads` methods.</span></span> <span data-ttu-id="ad02a-121">Bu durumda, ana bilgisayar bu yöntemlerden bir HRESULT değeri E_NOTIMPL döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="ad02a-121">In this case, the host should return an HRESULT value of E_NOTIMPL from these methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad02a-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ad02a-122">Requirements</span></span>  
 <span data-ttu-id="ad02a-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad02a-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad02a-124">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ad02a-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ad02a-125">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="ad02a-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ad02a-126">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad02a-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad02a-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ad02a-127">See also</span></span>

- <xref:System.Threading>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="ad02a-128">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ad02a-128">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
