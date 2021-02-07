---
description: 'Şu konuda daha fazla bilgi edinin: ıhostiocompletionmanager arabirimi'
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
ms.openlocfilehash: 30cb0ecbfd9645bc0374e3570751832d6fa8eced
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708326"
---
# <a name="ihostiocompletionmanager-interface"></a><span data-ttu-id="594ab-103">IHostIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="594ab-103">IHostIoCompletionManager Interface</span></span>

<span data-ttu-id="594ab-104">Ortak dil çalışma zamanının (CLR) konak tarafından sağlanan g/ç tamamlama bağlantı noktalarıyla etkileşime girmesine izin veren yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="594ab-104">Provides methods that allow the common language runtime (CLR) to interact with I/O completion ports provided by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="594ab-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="594ab-105">Methods</span></span>  
  
|<span data-ttu-id="594ab-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="594ab-106">Method</span></span>|<span data-ttu-id="594ab-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="594ab-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="594ab-108">Bind Yöntemi</span><span class="sxs-lookup"><span data-stu-id="594ab-108">Bind Method</span></span>](ihostiocompletionmanager-bind-method.md)|<span data-ttu-id="594ab-109">Bir tanıtıcıyı g/ç tamamlama bağlantı noktasına bağlar.</span><span class="sxs-lookup"><span data-stu-id="594ab-109">Binds a handle to an I/O completion port.</span></span>|  
|[<span data-ttu-id="594ab-110">CloseIoCompletionPort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="594ab-110">CloseIoCompletionPort Method</span></span>](ihostiocompletionmanager-closeiocompletionport-method.md)|<span data-ttu-id="594ab-111">Daha önceki bir çağrısıyla oluşturulmuş bir bağlantı noktasını kapatır `CreateIoCompletionPort` .</span><span class="sxs-lookup"><span data-stu-id="594ab-111">Closes a port that was created through an earlier call to `CreateIoCompletionPort`.</span></span>|  
|[<span data-ttu-id="594ab-112">CreateIoCompletionPort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="594ab-112">CreateIoCompletionPort Method</span></span>](ihostiocompletionmanager-createiocompletionport-method.md)|<span data-ttu-id="594ab-113">Konağın yeni bir g/ç tamamlama bağlantı noktası oluşturmasını ister.</span><span class="sxs-lookup"><span data-stu-id="594ab-113">Requests that the host create a new I/O completion port.</span></span>|  
|[<span data-ttu-id="594ab-114">GetAvailableThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="594ab-114">GetAvailableThreads Method</span></span>](ihostiocompletionmanager-getavailablethreads-method.md)|<span data-ttu-id="594ab-115">Şu anda istek işlemekte olan g/ç Tamamlama iş parçacığı sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="594ab-115">Gets the number of I/O completion threads that are not currently processing requests.</span></span>|  
|[<span data-ttu-id="594ab-116">GetHostOverlappedSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="594ab-116">GetHostOverlappedSize Method</span></span>](ihostiocompletionmanager-gethostoverlappedsize-method.md)|<span data-ttu-id="594ab-117">Ana bilgisayarın g/ç isteklerine eklenmesini amaçladığı tüm özel verilerin boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="594ab-117">Gets the size of any custom data the host intends to append to I/O requests.</span></span>|  
|[<span data-ttu-id="594ab-118">GetMaxThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="594ab-118">GetMaxThreads Method</span></span>](ihostiocompletionmanager-getmaxthreads-method.md)|<span data-ttu-id="594ab-119">Ana bilgisayarın g/ç isteklerine hizmet vermek için lot olarak barındırabileceği en fazla iş parçacığı sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="594ab-119">Gets the maximum number of threads that the host can allot to service I/O requests.</span></span>|  
|[<span data-ttu-id="594ab-120">GetMinThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="594ab-120">GetMinThreads Method</span></span>](ihostiocompletionmanager-getminthreads-method.md)|<span data-ttu-id="594ab-121">Hizmetin g/ç isteklerine hizmet vermek için sağladığı en az iş parçacığı sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="594ab-121">Gets the minimum number of threads that the host provides to service I/O requests.</span></span>|  
|[<span data-ttu-id="594ab-122">InitializeHostOverlapped Yöntemi</span><span class="sxs-lookup"><span data-stu-id="594ab-122">InitializeHostOverlapped Method</span></span>](ihostiocompletionmanager-initializehostoverlapped-method.md)|<span data-ttu-id="594ab-123">Bir g/ç isteğiyle ilgili özel verileri başlatmak için ana bilgisayara bir fırsat sağlar.</span><span class="sxs-lookup"><span data-stu-id="594ab-123">Provides the host with an opportunity to initialize any custom data about an I/O request.</span></span>|  
|[<span data-ttu-id="594ab-124">SetCLRIoCompletionManager Yöntemi</span><span class="sxs-lookup"><span data-stu-id="594ab-124">SetCLRIoCompletionManager Method</span></span>](ihostiocompletionmanager-setclriocompletionmanager-method.md)|<span data-ttu-id="594ab-125">CLR tarafından uygulanan bir [ıclriocompletionmanager](iclriocompletionmanager-interface.md) örneğine yönelik arabirim işaretçisi ile konağa sağlar.</span><span class="sxs-lookup"><span data-stu-id="594ab-125">Provides the host with an interface pointer to an [ICLRIoCompletionManager](iclriocompletionmanager-interface.md) instance implemented by the CLR.</span></span>|  
|[<span data-ttu-id="594ab-126">SetMaxThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="594ab-126">SetMaxThreads Method</span></span>](ihostiocompletionmanager-setmaxthreads-method.md)|<span data-ttu-id="594ab-127">Ana bilgisayar tarafından g/ç isteklerine hizmet vermek için ayrılan iş parçacığı sayısı üst sınırını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="594ab-127">Sets the maximum number of threads that the host allots to service I/O requests.</span></span>|  
|[<span data-ttu-id="594ab-128">SetMinThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="594ab-128">SetMinThreads Method</span></span>](ihostiocompletionmanager-setminthreads-method.md)|<span data-ttu-id="594ab-129">Ana bilgisayarın g/ç tamamlama için en az sayıda iş parçacığı sayısını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="594ab-129">Sets the minimum number of threads that the host should allot to I/O completion.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="594ab-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="594ab-130">Remarks</span></span>  

 <span data-ttu-id="594ab-131">`IHostIoCompletionManager``ICLRIoCompletionManager`clr tarafından uygulanan arabirime karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="594ab-131">`IHostIoCompletionManager` corresponds to the `ICLRIoCompletionManager` interface implemented by the CLR.</span></span> <span data-ttu-id="594ab-132">CLR, `IHostIoCompletionManager` tutamaçları konağın sağladığı bağlantı noktalarına bağlamak için yöntemini çağırır ve konak `ICLRIoCompletionManager` g/ç isteklerinin tamamlanmasını raporlamak için yöntemlerini çağırır.</span><span class="sxs-lookup"><span data-stu-id="594ab-132">The CLR calls the methods of `IHostIoCompletionManager` to bind handles to the ports that the host provides, and the host calls the methods of `ICLRIoCompletionManager` to report the completion of I/O requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="594ab-133">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="594ab-133">Requirements</span></span>  

 <span data-ttu-id="594ab-134">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="594ab-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="594ab-135">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="594ab-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="594ab-136">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="594ab-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="594ab-137">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="594ab-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="594ab-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="594ab-138">See also</span></span>

- [<span data-ttu-id="594ab-139">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="594ab-139">Hosting Interfaces</span></span>](hosting-interfaces.md)
