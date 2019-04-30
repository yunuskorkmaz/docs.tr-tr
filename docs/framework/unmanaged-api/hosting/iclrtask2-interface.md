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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 518248651de6d8afdf25692c5f48da52b11eb0f7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763405"
---
# <a name="iclrtask2-interface"></a><span data-ttu-id="6963f-102">ICLRTask2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6963f-102">ICLRTask2 Interface</span></span>
<span data-ttu-id="6963f-103">Tüm işlevlerini sağlar [Iclrtask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) arabirim; Ayrıca, iş parçacığı iptalleri geçerli iş parçacığında geciktirileceği tanıyan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="6963f-103">Provides all the functionality of the [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) interface; in addition, provides methods that allow thread aborts to be delayed on the current thread.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6963f-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="6963f-104">Methods</span></span>  
  
|<span data-ttu-id="6963f-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="6963f-105">Method</span></span>|<span data-ttu-id="6963f-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6963f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6963f-107">BeginPreventAsyncAbort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6963f-107">BeginPreventAsyncAbort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-beginpreventasyncabort-method.md)|<span data-ttu-id="6963f-108">Gecikmeler yeni iş parçacığı geçerli iş parçacığı isteklerinde durdurur.</span><span class="sxs-lookup"><span data-stu-id="6963f-108">Delays new thread abort requests on the current thread.</span></span>|  
|[<span data-ttu-id="6963f-109">EndPreventAsyncAbort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6963f-109">EndPreventAsyncAbort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-endpreventasyncabort-method.md)|<span data-ttu-id="6963f-110">Yeni izin verir veya bekleyen iş parçacığı elde etmek iş parçacığı durdurma isteği geçerli iş parçacığı üzerinde durdurur.</span><span class="sxs-lookup"><span data-stu-id="6963f-110">Allows new or pending thread abort requests to result in thread aborts on the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6963f-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6963f-111">Remarks</span></span>  
 <span data-ttu-id="6963f-112">`ICLRTask2` Arabirimi devralır `ICLRTask` arabirim ve konak değil başarısız olması gereken bir bölgesine korumak için iş parçacığı iptalleri, gecikme sağlayan bir yöntem ekler.</span><span class="sxs-lookup"><span data-stu-id="6963f-112">The `ICLRTask2` interface inherits the `ICLRTask` interface and adds methods that allow the host to delay thread aborts, to protect a region of code that must not fail.</span></span> <span data-ttu-id="6963f-113">Çağırma `BeginPreventAsyncAbort` geçerli iş parçacığı ve arama için gecikme iş parçacığı iptal sayaç artırılır `EndPreventAsyncAbort` azaltır.</span><span class="sxs-lookup"><span data-stu-id="6963f-113">Calling `BeginPreventAsyncAbort` increments the delay-thread-abort counter for the current thread, and calling `EndPreventAsyncAbort` decrements it.</span></span> <span data-ttu-id="6963f-114">Çağrılar `BeginPreventAsyncAbort` ve `EndPreventAsyncAbort` yuvalanabilir.</span><span class="sxs-lookup"><span data-stu-id="6963f-114">Calls to `BeginPreventAsyncAbort` and `EndPreventAsyncAbort` can be nested.</span></span> <span data-ttu-id="6963f-115">Sayaç sıfırdan büyük olduğu sürece, geçerli iş parçacığı için iş parçacığı iptalleri gecikir.</span><span class="sxs-lookup"><span data-stu-id="6963f-115">As long as the counter is greater than zero, thread aborts for the current thread are delayed.</span></span>  
  
 <span data-ttu-id="6963f-116">Varsa çağrılar `BeginPreventAsyncAbort` ve `EndPreventAsyncAbort` olan eşleştirilmedi, hangi iş parçacığı iptalleri olamaz teslim edilemiyor geçerli iş parçacığına bir durumuna ulaşmasını sağlamak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="6963f-116">If calls to `BeginPreventAsyncAbort` and `EndPreventAsyncAbort` are not paired, it is possible to reach a state in which thread aborts cannot be delivered to the current thread.</span></span>  
  
 <span data-ttu-id="6963f-117">Gecikme kendisini iptal ettiğinde bir iş parçacığı için uygulanır değil.</span><span class="sxs-lookup"><span data-stu-id="6963f-117">The delay is not honored for a thread that aborts itself.</span></span>  
  
 <span data-ttu-id="6963f-118">Bu özellik tarafından sunulan işlevselliği, sanal makine (VM) tarafından dahili olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6963f-118">The functionality that is exposed by this feature is used internally by the virtual machine (VM).</span></span> <span data-ttu-id="6963f-119">Bu yöntemlerin kötüye, VM'yi belirsiz davranışa neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="6963f-119">Misuse of these methods may cause unspecified behavior in the VM.</span></span> <span data-ttu-id="6963f-120">Örneğin, çağırma `EndPreventAsyncAbort` ilk çağırmadan `BeginPreventAsyncAbort` sayaç VM daha önce artan olduğunda sıfır olarak ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6963f-120">For example, calling `EndPreventAsyncAbort` without first calling `BeginPreventAsyncAbort` could set the counter to zero when the VM has previously incremented it.</span></span> <span data-ttu-id="6963f-121">Benzer şekilde, iç sayaç için taşma işaretlenmemiştir.</span><span class="sxs-lookup"><span data-stu-id="6963f-121">Similarly, the internal counter is not checked for overflow.</span></span> <span data-ttu-id="6963f-122">Hem konak hem de VM tarafından artar çünkü tam sayı sınırını aşarsa, sonuçta ortaya çıkan davranış belirtilmemiş.</span><span class="sxs-lookup"><span data-stu-id="6963f-122">If it exceeds its integral limit because it is incremented by both the host and the VM, the resulting behavior is unspecified.</span></span>  
  
 <span data-ttu-id="6963f-123">Devralınan üyeleri hakkında bilgi için `ICLRTask` ve diğer kullanımlar bu arabirimin hakkında [Iclrtask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="6963f-123">For information about members inherited from `ICLRTask` and about the other uses of this interface, see the [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6963f-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6963f-124">Requirements</span></span>  
 <span data-ttu-id="6963f-125">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6963f-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6963f-126">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6963f-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6963f-127">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="6963f-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6963f-128">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6963f-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6963f-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6963f-129">See also</span></span>

- [<span data-ttu-id="6963f-130">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6963f-130">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="6963f-131">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6963f-131">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="6963f-132">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6963f-132">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="6963f-133">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6963f-133">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="6963f-134">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="6963f-134">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
