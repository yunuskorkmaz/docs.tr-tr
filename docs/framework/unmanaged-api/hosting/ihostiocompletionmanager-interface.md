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
ms.openlocfilehash: 095872f8d4bd4f7d3351b8b3e3f8f8445b615cd8
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501546"
---
# <a name="ihostiocompletionmanager-interface"></a><span data-ttu-id="0f883-102">IHostIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0f883-102">IHostIoCompletionManager Interface</span></span>
<span data-ttu-id="0f883-103">Ortak dil çalışma zamanının (CLR) konak tarafından sağlanan g/ç tamamlama bağlantı noktalarıyla etkileşime girmesine izin veren yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0f883-103">Provides methods that allow the common language runtime (CLR) to interact with I/O completion ports provided by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0f883-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="0f883-104">Methods</span></span>  
  
|<span data-ttu-id="0f883-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="0f883-105">Method</span></span>|<span data-ttu-id="0f883-106">Description</span><span class="sxs-lookup"><span data-stu-id="0f883-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0f883-107">Bind Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0f883-107">Bind Method</span></span>](ihostiocompletionmanager-bind-method.md)|<span data-ttu-id="0f883-108">Bir tanıtıcıyı g/ç tamamlama bağlantı noktasına bağlar.</span><span class="sxs-lookup"><span data-stu-id="0f883-108">Binds a handle to an I/O completion port.</span></span>|  
|[<span data-ttu-id="0f883-109">CloseIoCompletionPort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0f883-109">CloseIoCompletionPort Method</span></span>](ihostiocompletionmanager-closeiocompletionport-method.md)|<span data-ttu-id="0f883-110">Daha önceki bir çağrısıyla oluşturulmuş bir bağlantı noktasını kapatır `CreateIoCompletionPort` .</span><span class="sxs-lookup"><span data-stu-id="0f883-110">Closes a port that was created through an earlier call to `CreateIoCompletionPort`.</span></span>|  
|[<span data-ttu-id="0f883-111">CreateIoCompletionPort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0f883-111">CreateIoCompletionPort Method</span></span>](ihostiocompletionmanager-createiocompletionport-method.md)|<span data-ttu-id="0f883-112">Konağın yeni bir g/ç tamamlama bağlantı noktası oluşturmasını ister.</span><span class="sxs-lookup"><span data-stu-id="0f883-112">Requests that the host create a new I/O completion port.</span></span>|  
|[<span data-ttu-id="0f883-113">GetAvailableThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0f883-113">GetAvailableThreads Method</span></span>](ihostiocompletionmanager-getavailablethreads-method.md)|<span data-ttu-id="0f883-114">Şu anda istek işlemekte olan g/ç Tamamlama iş parçacığı sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="0f883-114">Gets the number of I/O completion threads that are not currently processing requests.</span></span>|  
|[<span data-ttu-id="0f883-115">GetHostOverlappedSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0f883-115">GetHostOverlappedSize Method</span></span>](ihostiocompletionmanager-gethostoverlappedsize-method.md)|<span data-ttu-id="0f883-116">Ana bilgisayarın g/ç isteklerine eklenmesini amaçladığı tüm özel verilerin boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="0f883-116">Gets the size of any custom data the host intends to append to I/O requests.</span></span>|  
|[<span data-ttu-id="0f883-117">GetMaxThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0f883-117">GetMaxThreads Method</span></span>](ihostiocompletionmanager-getmaxthreads-method.md)|<span data-ttu-id="0f883-118">Ana bilgisayarın g/ç isteklerine hizmet vermek için lot olarak barındırabileceği en fazla iş parçacığı sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="0f883-118">Gets the maximum number of threads that the host can allot to service I/O requests.</span></span>|  
|[<span data-ttu-id="0f883-119">GetMinThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0f883-119">GetMinThreads Method</span></span>](ihostiocompletionmanager-getminthreads-method.md)|<span data-ttu-id="0f883-120">Hizmetin g/ç isteklerine hizmet vermek için sağladığı en az iş parçacığı sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="0f883-120">Gets the minimum number of threads that the host provides to service I/O requests.</span></span>|  
|[<span data-ttu-id="0f883-121">InitializeHostOverlapped Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0f883-121">InitializeHostOverlapped Method</span></span>](ihostiocompletionmanager-initializehostoverlapped-method.md)|<span data-ttu-id="0f883-122">Bir g/ç isteğiyle ilgili özel verileri başlatmak için ana bilgisayara bir fırsat sağlar.</span><span class="sxs-lookup"><span data-stu-id="0f883-122">Provides the host with an opportunity to initialize any custom data about an I/O request.</span></span>|  
|[<span data-ttu-id="0f883-123">SetCLRIoCompletionManager Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0f883-123">SetCLRIoCompletionManager Method</span></span>](ihostiocompletionmanager-setclriocompletionmanager-method.md)|<span data-ttu-id="0f883-124">CLR tarafından uygulanan bir [ıclriocompletionmanager](iclriocompletionmanager-interface.md) örneğine yönelik arabirim işaretçisi ile konağa sağlar.</span><span class="sxs-lookup"><span data-stu-id="0f883-124">Provides the host with an interface pointer to an [ICLRIoCompletionManager](iclriocompletionmanager-interface.md) instance implemented by the CLR.</span></span>|  
|[<span data-ttu-id="0f883-125">SetMaxThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0f883-125">SetMaxThreads Method</span></span>](ihostiocompletionmanager-setmaxthreads-method.md)|<span data-ttu-id="0f883-126">Ana bilgisayar tarafından g/ç isteklerine hizmet vermek için ayrılan iş parçacığı sayısı üst sınırını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="0f883-126">Sets the maximum number of threads that the host allots to service I/O requests.</span></span>|  
|[<span data-ttu-id="0f883-127">SetMinThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0f883-127">SetMinThreads Method</span></span>](ihostiocompletionmanager-setminthreads-method.md)|<span data-ttu-id="0f883-128">Ana bilgisayarın g/ç tamamlama için en az sayıda iş parçacığı sayısını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="0f883-128">Sets the minimum number of threads that the host should allot to I/O completion.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0f883-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0f883-129">Remarks</span></span>  
 <span data-ttu-id="0f883-130">`IHostIoCompletionManager``ICLRIoCompletionManager`clr tarafından uygulanan arabirime karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="0f883-130">`IHostIoCompletionManager` corresponds to the `ICLRIoCompletionManager` interface implemented by the CLR.</span></span> <span data-ttu-id="0f883-131">CLR, `IHostIoCompletionManager` tutamaçları konağın sağladığı bağlantı noktalarına bağlamak için yöntemini çağırır ve konak `ICLRIoCompletionManager` g/ç isteklerinin tamamlanmasını raporlamak için yöntemlerini çağırır.</span><span class="sxs-lookup"><span data-stu-id="0f883-131">The CLR calls the methods of `IHostIoCompletionManager` to bind handles to the ports that the host provides, and the host calls the methods of `ICLRIoCompletionManager` to report the completion of I/O requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f883-132">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0f883-132">Requirements</span></span>  
 <span data-ttu-id="0f883-133">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f883-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f883-134">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0f883-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0f883-135">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="0f883-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0f883-136">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f883-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f883-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0f883-137">See also</span></span>

- [<span data-ttu-id="0f883-138">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="0f883-138">Hosting Interfaces</span></span>](hosting-interfaces.md)
