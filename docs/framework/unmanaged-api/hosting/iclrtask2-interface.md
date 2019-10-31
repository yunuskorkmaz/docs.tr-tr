---
title: ICLRTask2 Arabirimi
ms.date: 03/30/2017
api_name:
- ICLRTask2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask2
helpviewer_keywords:
- ICLRTask2 interface [.NET Framework hosting]
ms.assetid: b5a22ebc-0582-49de-91f9-97a3d9789290
topic_type:
- apiref
ms.openlocfilehash: 47c6dd9045636bcfbe07c909fec3fda515d28ee8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124520"
---
# <a name="iclrtask2-interface"></a><span data-ttu-id="cccaf-102">ICLRTask2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cccaf-102">ICLRTask2 Interface</span></span>
<span data-ttu-id="cccaf-103">[ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) arabiriminin tüm işlevlerini sağlar; Ayrıca, geçerli iş parçacığında iş parçacığı iptal vermesinin ertelenmesini sağlayan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="cccaf-103">Provides all the functionality of the [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) interface; in addition, provides methods that allow thread aborts to be delayed on the current thread.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cccaf-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="cccaf-104">Methods</span></span>  
  
|<span data-ttu-id="cccaf-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="cccaf-105">Method</span></span>|<span data-ttu-id="cccaf-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cccaf-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cccaf-107">BeginPreventAsyncAbort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cccaf-107">BeginPreventAsyncAbort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-beginpreventasyncabort-method.md)|<span data-ttu-id="cccaf-108">Geçerli iş parçacığında yeni iş parçacığı iptali isteklerini geciktirir.</span><span class="sxs-lookup"><span data-stu-id="cccaf-108">Delays new thread abort requests on the current thread.</span></span>|  
|[<span data-ttu-id="cccaf-109">EndPreventAsyncAbort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cccaf-109">EndPreventAsyncAbort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-endpreventasyncabort-method.md)|<span data-ttu-id="cccaf-110">Geçerli iş parçacığında iş parçacığı iptaline neden olan yeni veya bekleyen iş parçacığı iptali isteklerinin yapılmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="cccaf-110">Allows new or pending thread abort requests to result in thread aborts on the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cccaf-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cccaf-111">Remarks</span></span>  
 <span data-ttu-id="cccaf-112">`ICLRTask2` arabirimi `ICLRTask` arabirimini devralır ve başarısız olması gereken bir kod bölgesini korumak için konağın iş parçacığı iptal işlemini geciktirmesini sağlayan yöntemler ekler.</span><span class="sxs-lookup"><span data-stu-id="cccaf-112">The `ICLRTask2` interface inherits the `ICLRTask` interface and adds methods that allow the host to delay thread aborts, to protect a region of code that must not fail.</span></span> <span data-ttu-id="cccaf-113">`BeginPreventAsyncAbort` çağrısı, geçerli iş parçacığı için Gecikmeli iş parçacığı iptali sayacını artırır ve çağırma `EndPreventAsyncAbort` çağırır.</span><span class="sxs-lookup"><span data-stu-id="cccaf-113">Calling `BeginPreventAsyncAbort` increments the delay-thread-abort counter for the current thread, and calling `EndPreventAsyncAbort` decrements it.</span></span> <span data-ttu-id="cccaf-114">`BeginPreventAsyncAbort` ve `EndPreventAsyncAbort` çağrıları iç içe olabilir.</span><span class="sxs-lookup"><span data-stu-id="cccaf-114">Calls to `BeginPreventAsyncAbort` and `EndPreventAsyncAbort` can be nested.</span></span> <span data-ttu-id="cccaf-115">Sayaç sıfırdan büyük olduğu sürece, geçerli iş parçacığı için iş parçacığı iptal işlemi gecikiyor.</span><span class="sxs-lookup"><span data-stu-id="cccaf-115">As long as the counter is greater than zero, thread aborts for the current thread are delayed.</span></span>  
  
 <span data-ttu-id="cccaf-116">`BeginPreventAsyncAbort` ve `EndPreventAsyncAbort` çağrıları eşlenmezse, iş parçacığının iptal edilmesi durumunda geçerli iş parçacığına teslim edilemez durumuna ulaşmak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="cccaf-116">If calls to `BeginPreventAsyncAbort` and `EndPreventAsyncAbort` are not paired, it is possible to reach a state in which thread aborts cannot be delivered to the current thread.</span></span>  
  
 <span data-ttu-id="cccaf-117">Gecikme, kendisini iptal eden bir iş parçacığı için kabul edilmez.</span><span class="sxs-lookup"><span data-stu-id="cccaf-117">The delay is not honored for a thread that aborts itself.</span></span>  
  
 <span data-ttu-id="cccaf-118">Bu özellik tarafından açığa çıkarılan işlevsellik, sanal makine (VM) tarafından dahili olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cccaf-118">The functionality that is exposed by this feature is used internally by the virtual machine (VM).</span></span> <span data-ttu-id="cccaf-119">Bu yöntemlerin kötüye kullanılması, sanal makinede belirtilmeyen davranışa neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="cccaf-119">Misuse of these methods may cause unspecified behavior in the VM.</span></span> <span data-ttu-id="cccaf-120">Örneğin, önce `BeginPreventAsyncAbort` çağrılmadan `EndPreventAsyncAbort` çağırmak, VM daha önce artmışsa sayacı sıfıra ayarlayabilir.</span><span class="sxs-lookup"><span data-stu-id="cccaf-120">For example, calling `EndPreventAsyncAbort` without first calling `BeginPreventAsyncAbort` could set the counter to zero when the VM has previously incremented it.</span></span> <span data-ttu-id="cccaf-121">Benzer şekilde, iç sayaç taşma için denetlenmez.</span><span class="sxs-lookup"><span data-stu-id="cccaf-121">Similarly, the internal counter is not checked for overflow.</span></span> <span data-ttu-id="cccaf-122">Hem konak hem de VM tarafından arttırılacağından, tam sayı sınırını aşarsa, ortaya çıkan davranış belirtilmemiş olur.</span><span class="sxs-lookup"><span data-stu-id="cccaf-122">If it exceeds its integral limit because it is incremented by both the host and the VM, the resulting behavior is unspecified.</span></span>  
  
 <span data-ttu-id="cccaf-123">`ICLRTask` devralınan Üyeler ve bu arabirimin diğer kullanımları hakkında daha fazla bilgi için [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) arabirimine bakın.</span><span class="sxs-lookup"><span data-stu-id="cccaf-123">For information about members inherited from `ICLRTask` and about the other uses of this interface, see the [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cccaf-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cccaf-124">Requirements</span></span>  
 <span data-ttu-id="cccaf-125">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cccaf-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cccaf-126">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="cccaf-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cccaf-127">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="cccaf-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cccaf-128">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cccaf-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cccaf-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cccaf-129">See also</span></span>

- [<span data-ttu-id="cccaf-130">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cccaf-130">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="cccaf-131">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cccaf-131">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="cccaf-132">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cccaf-132">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="cccaf-133">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cccaf-133">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="cccaf-134">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="cccaf-134">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
