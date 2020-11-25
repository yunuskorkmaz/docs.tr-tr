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
ms.openlocfilehash: b6625b0ef4dc3de4067514a0b39849c7a958d5c4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730767"
---
# <a name="ihostthreadpoolmanager-interface"></a><span data-ttu-id="baf3f-102">IHostThreadPoolManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="baf3f-102">IHostThreadPoolManager Interface</span></span>

<span data-ttu-id="baf3f-103">Ortak dil çalışma zamanını (CLR) iş parçacığı havuzunu yapılandırmak ve iş öğelerini iş parçacığı havuzuna sıraya almak için etkinleştiren yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="baf3f-103">Provides methods that enable the common language runtime (CLR) to configure the thread pool and to queue work items to the thread pool.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="baf3f-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="baf3f-104">Methods</span></span>  
  
|<span data-ttu-id="baf3f-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="baf3f-105">Method</span></span>|<span data-ttu-id="baf3f-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="baf3f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="baf3f-107">GetAvailableThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="baf3f-107">GetAvailableThreads Method</span></span>](ihostthreadpoolmanager-getavailablethreads-method.md)|<span data-ttu-id="baf3f-108">İş öğelerini işlemeyen iş parçacığı havuzundaki iş parçacığı sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="baf3f-108">Gets the number of threads in the thread pool that are not currently processing work items.</span></span>|  
|[<span data-ttu-id="baf3f-109">GetMaxThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="baf3f-109">GetMaxThreads Method</span></span>](ihostthreadpoolmanager-getmaxthreads-method.md)|<span data-ttu-id="baf3f-110">Konağın iş parçacığı havuzunda eşzamanlı olarak tuttuğu en fazla iş parçacığı sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="baf3f-110">Gets the maximum number of threads that the host maintains concurrently in the thread pool.</span></span>|  
|[<span data-ttu-id="baf3f-111">GetMinThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="baf3f-111">GetMinThreads Method</span></span>](ihostthreadpoolmanager-getminthreads-method.md)|<span data-ttu-id="baf3f-112">Olasılığına for isteklerinde konağın sakladığı en az boştaki iş parçacığı sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="baf3f-112">Gets the minimum number of idle threads that the host maintains in anticipation of requests.</span></span>|  
|[<span data-ttu-id="baf3f-113">QueueUserWorkItem Yöntemi</span><span class="sxs-lookup"><span data-stu-id="baf3f-113">QueueUserWorkItem Method</span></span>](ihostthreadpoolmanager-queueuserworkitem-method.md)|<span data-ttu-id="baf3f-114">Yürütme için bir işlevi sıraya alır ve işlev tarafından kullanılacak verileri içeren bir nesne sağlar.</span><span class="sxs-lookup"><span data-stu-id="baf3f-114">Queues a function for execution, and provides an object containing data to be used by the function.</span></span>|  
|[<span data-ttu-id="baf3f-115">SetMaxThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="baf3f-115">SetMaxThreads Method</span></span>](ihostthreadpoolmanager-setmaxthreads-method.md)|<span data-ttu-id="baf3f-116">Konağın iş parçacığı havuzunda koruyabileceği en fazla iş parçacığı sayısını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="baf3f-116">Sets the maximum number of threads that the host can maintain in the thread pool.</span></span>|  
|[<span data-ttu-id="baf3f-117">SetMinThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="baf3f-117">SetMinThreads Method</span></span>](ihostthreadpoolmanager-setminthreads-method.md)|<span data-ttu-id="baf3f-118">Konağın olasılığına isteklerinde saklanması gereken en az boş iş parçacığı sayısını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="baf3f-118">Sets the minimum number of idle threads that the host must maintain in anticipation of requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="baf3f-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="baf3f-119">Remarks</span></span>  

 <span data-ttu-id="baf3f-120">Ana bilgisayar, ve yöntemlerine yapılan çağrılarında belirtilen değerleri kullanarak iş parçacığı havuzunu yapılandırmak için gerekli değildir `SetMaxThreads` `SetMinThreads` .</span><span class="sxs-lookup"><span data-stu-id="baf3f-120">The host is not required to configure the thread pool by using the values specified in calls to the `SetMaxThreads` and `SetMinThreads` methods.</span></span> <span data-ttu-id="baf3f-121">Bu durumda, ana bilgisayar bu yöntemlerden bir E_NOTIMPL HRESULT değeri döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="baf3f-121">In this case, the host should return an HRESULT value of E_NOTIMPL from these methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="baf3f-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="baf3f-122">Requirements</span></span>  

 <span data-ttu-id="baf3f-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="baf3f-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="baf3f-124">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="baf3f-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="baf3f-125">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="baf3f-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="baf3f-126">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="baf3f-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="baf3f-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="baf3f-127">See also</span></span>

- <xref:System.Threading>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="baf3f-128">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="baf3f-128">Hosting Interfaces</span></span>](hosting-interfaces.md)
