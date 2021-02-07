---
description: 'Daha fazla bilgi edinin: IHostThreadPoolManager Arabirimi'
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
ms.openlocfilehash: 0361b7a08f781a8748e43959f65ce0e9f21bbac1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99728431"
---
# <a name="ihostthreadpoolmanager-interface"></a><span data-ttu-id="1b775-103">IHostThreadPoolManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1b775-103">IHostThreadPoolManager Interface</span></span>

<span data-ttu-id="1b775-104">Ortak dil çalışma zamanını (CLR) iş parçacığı havuzunu yapılandırmak ve iş öğelerini iş parçacığı havuzuna sıraya almak için etkinleştiren yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="1b775-104">Provides methods that enable the common language runtime (CLR) to configure the thread pool and to queue work items to the thread pool.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1b775-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="1b775-105">Methods</span></span>  
  
|<span data-ttu-id="1b775-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="1b775-106">Method</span></span>|<span data-ttu-id="1b775-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1b775-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1b775-108">GetAvailableThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1b775-108">GetAvailableThreads Method</span></span>](ihostthreadpoolmanager-getavailablethreads-method.md)|<span data-ttu-id="1b775-109">İş öğelerini işlemeyen iş parçacığı havuzundaki iş parçacığı sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="1b775-109">Gets the number of threads in the thread pool that are not currently processing work items.</span></span>|  
|[<span data-ttu-id="1b775-110">GetMaxThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1b775-110">GetMaxThreads Method</span></span>](ihostthreadpoolmanager-getmaxthreads-method.md)|<span data-ttu-id="1b775-111">Konağın iş parçacığı havuzunda eşzamanlı olarak tuttuğu en fazla iş parçacığı sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="1b775-111">Gets the maximum number of threads that the host maintains concurrently in the thread pool.</span></span>|  
|[<span data-ttu-id="1b775-112">GetMinThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1b775-112">GetMinThreads Method</span></span>](ihostthreadpoolmanager-getminthreads-method.md)|<span data-ttu-id="1b775-113">Olasılığına for isteklerinde konağın sakladığı en az boştaki iş parçacığı sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="1b775-113">Gets the minimum number of idle threads that the host maintains in anticipation of requests.</span></span>|  
|[<span data-ttu-id="1b775-114">QueueUserWorkItem Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1b775-114">QueueUserWorkItem Method</span></span>](ihostthreadpoolmanager-queueuserworkitem-method.md)|<span data-ttu-id="1b775-115">Yürütme için bir işlevi sıraya alır ve işlev tarafından kullanılacak verileri içeren bir nesne sağlar.</span><span class="sxs-lookup"><span data-stu-id="1b775-115">Queues a function for execution, and provides an object containing data to be used by the function.</span></span>|  
|[<span data-ttu-id="1b775-116">SetMaxThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1b775-116">SetMaxThreads Method</span></span>](ihostthreadpoolmanager-setmaxthreads-method.md)|<span data-ttu-id="1b775-117">Konağın iş parçacığı havuzunda koruyabileceği en fazla iş parçacığı sayısını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="1b775-117">Sets the maximum number of threads that the host can maintain in the thread pool.</span></span>|  
|[<span data-ttu-id="1b775-118">SetMinThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1b775-118">SetMinThreads Method</span></span>](ihostthreadpoolmanager-setminthreads-method.md)|<span data-ttu-id="1b775-119">Konağın olasılığına isteklerinde saklanması gereken en az boş iş parçacığı sayısını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="1b775-119">Sets the minimum number of idle threads that the host must maintain in anticipation of requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1b775-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1b775-120">Remarks</span></span>  

 <span data-ttu-id="1b775-121">Ana bilgisayar, ve yöntemlerine yapılan çağrılarında belirtilen değerleri kullanarak iş parçacığı havuzunu yapılandırmak için gerekli değildir `SetMaxThreads` `SetMinThreads` .</span><span class="sxs-lookup"><span data-stu-id="1b775-121">The host is not required to configure the thread pool by using the values specified in calls to the `SetMaxThreads` and `SetMinThreads` methods.</span></span> <span data-ttu-id="1b775-122">Bu durumda, ana bilgisayar bu yöntemlerden bir E_NOTIMPL HRESULT değeri döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="1b775-122">In this case, the host should return an HRESULT value of E_NOTIMPL from these methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b775-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1b775-123">Requirements</span></span>  

 <span data-ttu-id="1b775-124">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b775-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b775-125">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="1b775-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1b775-126">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="1b775-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1b775-127">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b775-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b775-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1b775-128">See also</span></span>

- <xref:System.Threading>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="1b775-129">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="1b775-129">Hosting Interfaces</span></span>](hosting-interfaces.md)
