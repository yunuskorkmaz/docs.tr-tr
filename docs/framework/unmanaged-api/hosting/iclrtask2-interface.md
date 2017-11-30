---
title: ICLRTask2 Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRTask2
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRTask2
helpviewer_keywords: ICLRTask2 interface [.NET Framework hosting]
ms.assetid: b5a22ebc-0582-49de-91f9-97a3d9789290
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5f2312d193031eae556f55b061a36259531d013b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrtask2-interface"></a><span data-ttu-id="c4d98-102">ICLRTask2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c4d98-102">ICLRTask2 Interface</span></span>
<span data-ttu-id="c4d98-103">Tüm işlevselliğini sağlar [Iclrtask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) arabirim; Ayrıca, iş parçacığı iptalleri geçerli iş parçacığı üzerinde Gecikmeli için izin yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="c4d98-103">Provides all the functionality of the [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) interface; in addition, provides methods that allow thread aborts to be delayed on the current thread.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c4d98-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="c4d98-104">Methods</span></span>  
  
|<span data-ttu-id="c4d98-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="c4d98-105">Method</span></span>|<span data-ttu-id="c4d98-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c4d98-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c4d98-107">BeginPreventAsyncAbort yöntemi</span><span class="sxs-lookup"><span data-stu-id="c4d98-107">BeginPreventAsyncAbort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-beginpreventasyncabort-method.md)|<span data-ttu-id="c4d98-108">Yeni bir iş parçacığı gecikmeler geçerli iş parçacığının isteklerinde durdur.</span><span class="sxs-lookup"><span data-stu-id="c4d98-108">Delays new thread abort requests on the current thread.</span></span>|  
|[<span data-ttu-id="c4d98-109">EndPreventAsyncAbort yöntemi</span><span class="sxs-lookup"><span data-stu-id="c4d98-109">EndPreventAsyncAbort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-endpreventasyncabort-method.md)|<span data-ttu-id="c4d98-110">Yeni izin verir veya bekleyen iş parçacığı elde etmek iş parçacığı durdurma isteği geçerli iş parçacığı üzerinde durdurur.</span><span class="sxs-lookup"><span data-stu-id="c4d98-110">Allows new or pending thread abort requests to result in thread aborts on the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c4d98-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c4d98-111">Remarks</span></span>  
 <span data-ttu-id="c4d98-112">`ICLRTask2` Arabirimi devralır `ICLRTask` arabirim ve bir bölge başarısız gerekir kodu korumak için iş parçacığı iptalleri gecikme konağının yöntemleri ekler.</span><span class="sxs-lookup"><span data-stu-id="c4d98-112">The `ICLRTask2` interface inherits the `ICLRTask` interface and adds methods that allow the host to delay thread aborts, to protect a region of code that must not fail.</span></span> <span data-ttu-id="c4d98-113">Çağırma `BeginPreventAsyncAbort` geçerli iş parçacığının ve arama için gecikme iş parçacığı iptal sayaç artırılır `EndPreventAsyncAbort` azaltır.</span><span class="sxs-lookup"><span data-stu-id="c4d98-113">Calling `BeginPreventAsyncAbort` increments the delay-thread-abort counter for the current thread, and calling `EndPreventAsyncAbort` decrements it.</span></span> <span data-ttu-id="c4d98-114">Çağrılar `BeginPreventAsyncAbort` ve `EndPreventAsyncAbort` iç içe olamaz.</span><span class="sxs-lookup"><span data-stu-id="c4d98-114">Calls to `BeginPreventAsyncAbort` and `EndPreventAsyncAbort` can be nested.</span></span> <span data-ttu-id="c4d98-115">Sayaç sıfırdan büyük olduğu sürece, geçerli iş parçacığı için iş parçacığı iptalleri gecikir.</span><span class="sxs-lookup"><span data-stu-id="c4d98-115">As long as the counter is greater than zero, thread aborts for the current thread are delayed.</span></span>  
  
 <span data-ttu-id="c4d98-116">Varsa çağrılar `BeginPreventAsyncAbort` ve `EndPreventAsyncAbort` olan eşleştirilmiş değil, hangi iş parçacığı iptalleri olamaz teslim edilemiyor geçerli iş parçacığına durumuna ulaşması mümkündür.</span><span class="sxs-lookup"><span data-stu-id="c4d98-116">If calls to `BeginPreventAsyncAbort` and `EndPreventAsyncAbort` are not paired, it is possible to reach a state in which thread aborts cannot be delivered to the current thread.</span></span>  
  
 <span data-ttu-id="c4d98-117">Gecikme kendisini durdurur bir iş parçacığı için dikkate alınır değil.</span><span class="sxs-lookup"><span data-stu-id="c4d98-117">The delay is not honored for a thread that aborts itself.</span></span>  
  
 <span data-ttu-id="c4d98-118">Bu özellik tarafından sunulan işlevselliği sanal makine (VM) tarafından dahili olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c4d98-118">The functionality that is exposed by this feature is used internally by the virtual machine (VM).</span></span> <span data-ttu-id="c4d98-119">Bu yöntemlerin kötüye VM'yi belirtilmeyen davranışlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="c4d98-119">Misuse of these methods may cause unspecified behavior in the VM.</span></span> <span data-ttu-id="c4d98-120">Örneğin, arama `EndPreventAsyncAbort` ilk çağırmadan `BeginPreventAsyncAbort` VM daha önce onu artar olduğunda Sayaç sıfıra ayarlanamıyor.</span><span class="sxs-lookup"><span data-stu-id="c4d98-120">For example, calling `EndPreventAsyncAbort` without first calling `BeginPreventAsyncAbort` could set the counter to zero when the VM has previously incremented it.</span></span> <span data-ttu-id="c4d98-121">Benzer şekilde, iç sayaç için taşma işaretlenmemiştir.</span><span class="sxs-lookup"><span data-stu-id="c4d98-121">Similarly, the internal counter is not checked for overflow.</span></span> <span data-ttu-id="c4d98-122">Konak ve VM tarafından artırılır çünkü tam sayı sınırını aşarsa, bunun sonucunda oluşan davranışı belirtilmemiş.</span><span class="sxs-lookup"><span data-stu-id="c4d98-122">If it exceeds its integral limit because it is incremented by both the host and the VM, the resulting behavior is unspecified.</span></span>  
  
 <span data-ttu-id="c4d98-123">Devralınan üyeleri hakkında bilgi için `ICLRTask` ve diğer kullanımlar bu arabirimin hakkında bkz: [Iclrtask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="c4d98-123">For information about members inherited from `ICLRTask` and about the other uses of this interface, see the [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4d98-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c4d98-124">Requirements</span></span>  
 <span data-ttu-id="c4d98-125">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4d98-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4d98-126">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c4d98-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c4d98-127">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="c4d98-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c4d98-128">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4d98-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4d98-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c4d98-129">See Also</span></span>  
 [<span data-ttu-id="c4d98-130">Iclrtask arabirimi</span><span class="sxs-lookup"><span data-stu-id="c4d98-130">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="c4d98-131">Iclrtaskmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="c4d98-131">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="c4d98-132">Ihosttask arabirimi</span><span class="sxs-lookup"><span data-stu-id="c4d98-132">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="c4d98-133">Ihosttaskmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="c4d98-133">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="c4d98-134">Barındırma arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c4d98-134">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
