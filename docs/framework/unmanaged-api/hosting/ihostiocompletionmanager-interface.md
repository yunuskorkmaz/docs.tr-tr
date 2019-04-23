---
title: IHostIoCompletionManager Arabirimi
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager
helpviewer_keywords:
- IHostIoCompletionManager interface [.NET Framework hosting]
ms.assetid: c28d1983-83f7-46e2-990f-dbb9dc07c818
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3c3bebe8eabd4d5fd5faec21e0b0efc408353bc2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59197275"
---
# <a name="ihostiocompletionmanager-interface"></a><span data-ttu-id="9e0db-102">IHostIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e0db-102">IHostIoCompletionManager Interface</span></span>
<span data-ttu-id="9e0db-103">Ortak dil çalışma zamanı (CLR) ana bilgisayar tarafından sağlanan g/ç tamamlama bağlantı noktaları ile etkileşim kurmak için izin vermek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e0db-103">Provides methods that allow the common language runtime (CLR) to interact with I/O completion ports provided by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9e0db-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="9e0db-104">Methods</span></span>  
  
|<span data-ttu-id="9e0db-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="9e0db-105">Method</span></span>|<span data-ttu-id="9e0db-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9e0db-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9e0db-107">Bind Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9e0db-107">Bind Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md)|<span data-ttu-id="9e0db-108">Bir tanıtıcı bir g/ç tamamlama bağlantı noktasına bağlar.</span><span class="sxs-lookup"><span data-stu-id="9e0db-108">Binds a handle to an I/O completion port.</span></span>|  
|[<span data-ttu-id="9e0db-109">CloseIoCompletionPort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9e0db-109">CloseIoCompletionPort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-closeiocompletionport-method.md)|<span data-ttu-id="9e0db-110">Önceki bir çağrı aracılığıyla oluşturulmuş olan bir bağlantı noktasını kapatır `CreateIoCompletionPort`.</span><span class="sxs-lookup"><span data-stu-id="9e0db-110">Closes a port that was created through an earlier call to `CreateIoCompletionPort`.</span></span>|  
|[<span data-ttu-id="9e0db-111">CreateIoCompletionPort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9e0db-111">CreateIoCompletionPort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md)|<span data-ttu-id="9e0db-112">Ana bilgisayar yeni bir g/ç tamamlama bağlantı oluşturma isteği.</span><span class="sxs-lookup"><span data-stu-id="9e0db-112">Requests that the host create a new I/O completion port.</span></span>|  
|[<span data-ttu-id="9e0db-113">GetAvailableThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9e0db-113">GetAvailableThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getavailablethreads-method.md)|<span data-ttu-id="9e0db-114">Şu anda istekleri işleme olmayan g/ç Tamamlama iş parçacığı sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="9e0db-114">Gets the number of I/O completion threads that are not currently processing requests.</span></span>|  
|[<span data-ttu-id="9e0db-115">GetHostOverlappedSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9e0db-115">GetHostOverlappedSize Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-gethostoverlappedsize-method.md)|<span data-ttu-id="9e0db-116">G/ç istekleri eklenecek konak düşünüyor herhangi bir özel veri boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="9e0db-116">Gets the size of any custom data the host intends to append to I/O requests.</span></span>|  
|[<span data-ttu-id="9e0db-117">GetMaxThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9e0db-117">GetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getmaxthreads-method.md)|<span data-ttu-id="9e0db-118">G/ç isteklerine hizmet konağı paylaştırmak iş parçacığı sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="9e0db-118">Gets the maximum number of threads that the host can allot to service I/O requests.</span></span>|  
|[<span data-ttu-id="9e0db-119">GetMinThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9e0db-119">GetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getminthreads-method.md)|<span data-ttu-id="9e0db-120">G/ç isteklerine hizmet ana bilgisayarının sağladığı iş parçacıklarını en az sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="9e0db-120">Gets the minimum number of threads that the host provides to service I/O requests.</span></span>|  
|[<span data-ttu-id="9e0db-121">InitializeHostOverlapped Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9e0db-121">InitializeHostOverlapped Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-initializehostoverlapped-method.md)|<span data-ttu-id="9e0db-122">Konak bir g/ç isteği hakkında herhangi bir özel veri başlatmak üzere bir fırsat sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e0db-122">Provides the host with an opportunity to initialize any custom data about an I/O request.</span></span>|  
|[<span data-ttu-id="9e0db-123">SetCLRIoCompletionManager Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9e0db-123">SetCLRIoCompletionManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setclriocompletionmanager-method.md)|<span data-ttu-id="9e0db-124">Bir arabirim işaretçisi ile ana bilgisayarının sağladığı bir [Iclrıocompletionmanager](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md) CLR tarafından uygulanan örnek.</span><span class="sxs-lookup"><span data-stu-id="9e0db-124">Provides the host with an interface pointer to an [ICLRIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md) instance implemented by the CLR.</span></span>|  
|[<span data-ttu-id="9e0db-125">SetMaxThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9e0db-125">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setmaxthreads-method.md)|<span data-ttu-id="9e0db-126">G/ç isteklerine hizmet konak allots iş parçacığı sayısını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="9e0db-126">Sets the maximum number of threads that the host allots to service I/O requests.</span></span>|  
|[<span data-ttu-id="9e0db-127">SetMinThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9e0db-127">SetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setminthreads-method.md)|<span data-ttu-id="9e0db-128">En az sayıda konak paylaştırmak iş parçacıkları için g/ç tamamlama ayarlar.</span><span class="sxs-lookup"><span data-stu-id="9e0db-128">Sets the minimum number of threads that the host should allot to I/O completion.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9e0db-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9e0db-129">Remarks</span></span>  
 <span data-ttu-id="9e0db-130">`IHostIoCompletionManager` karşılık gelen `ICLRIoCompletionManager` CLR tarafından uygulanan arabirimi.</span><span class="sxs-lookup"><span data-stu-id="9e0db-130">`IHostIoCompletionManager` corresponds to the `ICLRIoCompletionManager` interface implemented by the CLR.</span></span> <span data-ttu-id="9e0db-131">CLR yöntemlerini çağıran `IHostIoCompletionManager` tanıtıcıları konak sağlar ve konak yöntemlerini çağıran bağlantı noktalarına bağlamak için `ICLRIoCompletionManager` g/ç isteklerinin tamamlanmasından bildirmek için.</span><span class="sxs-lookup"><span data-stu-id="9e0db-131">The CLR calls the methods of `IHostIoCompletionManager` to bind handles to the ports that the host provides, and the host calls the methods of `ICLRIoCompletionManager` to report the completion of I/O requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e0db-132">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9e0db-132">Requirements</span></span>  
 <span data-ttu-id="9e0db-133">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e0db-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e0db-134">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9e0db-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9e0db-135">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="9e0db-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9e0db-136">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e0db-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e0db-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9e0db-137">See also</span></span>

- [<span data-ttu-id="9e0db-138">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="9e0db-138">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
