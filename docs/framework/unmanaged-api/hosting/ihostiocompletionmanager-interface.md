---
title: IHostIoCompletionManager Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostIoCompletionManager
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostIoCompletionManager
helpviewer_keywords: IHostIoCompletionManager interface [.NET Framework hosting]
ms.assetid: c28d1983-83f7-46e2-990f-dbb9dc07c818
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cbb4b87b57d4f5e11a9dab04d20dfb73170bb4a5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostiocompletionmanager-interface"></a><span data-ttu-id="7d25c-102">IHostIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7d25c-102">IHostIoCompletionManager Interface</span></span>
<span data-ttu-id="7d25c-103">Ortak dil çalışma zamanı (CLR) ana bilgisayar tarafından sağlanan g/ç tamamlama bağlantı noktaları ile etkileşim kurmasına izin yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="7d25c-103">Provides methods that allow the common language runtime (CLR) to interact with I/O completion ports provided by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7d25c-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="7d25c-104">Methods</span></span>  
  
|<span data-ttu-id="7d25c-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="7d25c-105">Method</span></span>|<span data-ttu-id="7d25c-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7d25c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7d25c-107">Bind Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7d25c-107">Bind Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md)|<span data-ttu-id="7d25c-108">Bir tanıtıcı bir g/ç tamamlama bağlantı noktasına bağlar.</span><span class="sxs-lookup"><span data-stu-id="7d25c-108">Binds a handle to an I/O completion port.</span></span>|  
|[<span data-ttu-id="7d25c-109">CloseIoCompletionPort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7d25c-109">CloseIoCompletionPort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-closeiocompletionport-method.md)|<span data-ttu-id="7d25c-110">Önceki bir çağrı aracılığıyla oluşturulan bir bağlantı noktasını kapatır `CreateIoCompletionPort`.</span><span class="sxs-lookup"><span data-stu-id="7d25c-110">Closes a port that was created through an earlier call to `CreateIoCompletionPort`.</span></span>|  
|[<span data-ttu-id="7d25c-111">CreateIoCompletionPort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7d25c-111">CreateIoCompletionPort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md)|<span data-ttu-id="7d25c-112">Ana bilgisayar yeni bir g/ç tamamlama bağlantı noktasını oluşturmak istek sayısı.</span><span class="sxs-lookup"><span data-stu-id="7d25c-112">Requests that the host create a new I/O completion port.</span></span>|  
|[<span data-ttu-id="7d25c-113">GetAvailableThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7d25c-113">GetAvailableThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getavailablethreads-method.md)|<span data-ttu-id="7d25c-114">Şu anda istekleri işlemeyi olmayan g/ç Tamamlama iş parçacığı sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="7d25c-114">Gets the number of I/O completion threads that are not currently processing requests.</span></span>|  
|[<span data-ttu-id="7d25c-115">GetHostOverlappedSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7d25c-115">GetHostOverlappedSize Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-gethostoverlappedsize-method.md)|<span data-ttu-id="7d25c-116">G/ç istekleri eklemek için ana bilgisayar oranla herhangi bir özel veri boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="7d25c-116">Gets the size of any custom data the host intends to append to I/O requests.</span></span>|  
|[<span data-ttu-id="7d25c-117">GetMaxThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7d25c-117">GetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getmaxthreads-method.md)|<span data-ttu-id="7d25c-118">G/ç istekleri konak paylaştırmak iş parçacığı sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="7d25c-118">Gets the maximum number of threads that the host can allot to service I/O requests.</span></span>|  
|[<span data-ttu-id="7d25c-119">GetMinThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7d25c-119">GetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getminthreads-method.md)|<span data-ttu-id="7d25c-120">Ana bilgisayarının sağladığı iş parçacıklarının en az sayıda g/ç istekleri alır.</span><span class="sxs-lookup"><span data-stu-id="7d25c-120">Gets the minimum number of threads that the host provides to service I/O requests.</span></span>|  
|[<span data-ttu-id="7d25c-121">InitializeHostOverlapped Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7d25c-121">InitializeHostOverlapped Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-initializehostoverlapped-method.md)|<span data-ttu-id="7d25c-122">Konak bir g/ç isteği hakkında herhangi bir özel veri başlatmak için bir fırsat sunar.</span><span class="sxs-lookup"><span data-stu-id="7d25c-122">Provides the host with an opportunity to initialize any custom data about an I/O request.</span></span>|  
|[<span data-ttu-id="7d25c-123">SetCLRIoCompletionManager Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7d25c-123">SetCLRIoCompletionManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setclriocompletionmanager-method.md)|<span data-ttu-id="7d25c-124">Ana bilgisayar için bir arabirim işaretçisi sağlayan bir [Iclrıocompletionmanager](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md) CLR tarafından uygulanan örneği.</span><span class="sxs-lookup"><span data-stu-id="7d25c-124">Provides the host with an interface pointer to an [ICLRIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md) instance implemented by the CLR.</span></span>|  
|[<span data-ttu-id="7d25c-125">SetMaxThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7d25c-125">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setmaxthreads-method.md)|<span data-ttu-id="7d25c-126">G/ç istekleri konak allots iş parçacığı sayısını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="7d25c-126">Sets the maximum number of threads that the host allots to service I/O requests.</span></span>|  
|[<span data-ttu-id="7d25c-127">SetMinThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7d25c-127">SetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setminthreads-method.md)|<span data-ttu-id="7d25c-128">Konak tahsis et iş parçacıklarının en az sayıda g/ç tamamlama ayarlar.</span><span class="sxs-lookup"><span data-stu-id="7d25c-128">Sets the minimum number of threads that the host should allot to I/O completion.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7d25c-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7d25c-129">Remarks</span></span>  
 <span data-ttu-id="7d25c-130">`IHostIoCompletionManager`karşılık gelen `ICLRIoCompletionManager` CLR tarafından uygulanan arabirimi.</span><span class="sxs-lookup"><span data-stu-id="7d25c-130">`IHostIoCompletionManager` corresponds to the `ICLRIoCompletionManager` interface implemented by the CLR.</span></span> <span data-ttu-id="7d25c-131">CLR yöntemlerini çağıran `IHostIoCompletionManager` tanıtıcıları konak sağlayan ve ana bilgisayar yöntemlerini çağıran bağlantı noktalarına bağlanması için `ICLRIoCompletionManager` tamamlandığında g/ç istekleri, rapor için.</span><span class="sxs-lookup"><span data-stu-id="7d25c-131">The CLR calls the methods of `IHostIoCompletionManager` to bind handles to the ports that the host provides, and the host calls the methods of `ICLRIoCompletionManager` to report the completion of I/O requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d25c-132">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7d25c-132">Requirements</span></span>  
 <span data-ttu-id="7d25c-133">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d25c-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d25c-134">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7d25c-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7d25c-135">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="7d25c-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7d25c-136">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d25c-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d25c-137">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7d25c-137">See Also</span></span>  
 [<span data-ttu-id="7d25c-138">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="7d25c-138">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
