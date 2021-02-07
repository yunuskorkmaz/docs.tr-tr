---
description: 'Daha fazla bilgi edinin: ICLRTask2 Interface'
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
ms.openlocfilehash: 835b01e1c808c071e9393c5117d5e38415ec8eba
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99728658"
---
# <a name="iclrtask2-interface"></a><span data-ttu-id="00892-103">ICLRTask2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00892-103">ICLRTask2 Interface</span></span>

<span data-ttu-id="00892-104">[ICLRTask](iclrtask-interface.md) arabiriminin tüm işlevlerini sağlar; Ayrıca, geçerli iş parçacığında iş parçacığı iptal vermesinin ertelenmesini sağlayan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="00892-104">Provides all the functionality of the [ICLRTask](iclrtask-interface.md) interface; in addition, provides methods that allow thread aborts to be delayed on the current thread.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="00892-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="00892-105">Methods</span></span>  
  
|<span data-ttu-id="00892-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="00892-106">Method</span></span>|<span data-ttu-id="00892-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="00892-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="00892-108">BeginPreventAsyncAbort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="00892-108">BeginPreventAsyncAbort Method</span></span>](iclrtask2-beginpreventasyncabort-method.md)|<span data-ttu-id="00892-109">Geçerli iş parçacığında yeni iş parçacığı iptali isteklerini geciktirir.</span><span class="sxs-lookup"><span data-stu-id="00892-109">Delays new thread abort requests on the current thread.</span></span>|  
|[<span data-ttu-id="00892-110">EndPreventAsyncAbort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="00892-110">EndPreventAsyncAbort Method</span></span>](iclrtask2-endpreventasyncabort-method.md)|<span data-ttu-id="00892-111">Geçerli iş parçacığında iş parçacığı iptaline neden olan yeni veya bekleyen iş parçacığı iptali isteklerinin yapılmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="00892-111">Allows new or pending thread abort requests to result in thread aborts on the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="00892-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="00892-112">Remarks</span></span>  

 <span data-ttu-id="00892-113">`ICLRTask2`Arabirim, arabirimi devralır `ICLRTask` ve başarısız olması gereken bir kod bölgesini korumak için konağın iş parçacığı iptal işlemini geciktirmesini sağlayan yöntemler ekler.</span><span class="sxs-lookup"><span data-stu-id="00892-113">The `ICLRTask2` interface inherits the `ICLRTask` interface and adds methods that allow the host to delay thread aborts, to protect a region of code that must not fail.</span></span> <span data-ttu-id="00892-114">Çağırma, `BeginPreventAsyncAbort` geçerli iş parçacığı için gecikme-iş parçacığı iptali sayacını artırır ve bu çağrıyı `EndPreventAsyncAbort` azaltır.</span><span class="sxs-lookup"><span data-stu-id="00892-114">Calling `BeginPreventAsyncAbort` increments the delay-thread-abort counter for the current thread, and calling `EndPreventAsyncAbort` decrements it.</span></span> <span data-ttu-id="00892-115">Ve için `BeginPreventAsyncAbort` çağrıları `EndPreventAsyncAbort` iç içe olabilir.</span><span class="sxs-lookup"><span data-stu-id="00892-115">Calls to `BeginPreventAsyncAbort` and `EndPreventAsyncAbort` can be nested.</span></span> <span data-ttu-id="00892-116">Sayaç sıfırdan büyük olduğu sürece, geçerli iş parçacığı için iş parçacığı iptal işlemi gecikiyor.</span><span class="sxs-lookup"><span data-stu-id="00892-116">As long as the counter is greater than zero, thread aborts for the current thread are delayed.</span></span>  
  
 <span data-ttu-id="00892-117">Ve ' a `BeginPreventAsyncAbort` çağrıları `EndPreventAsyncAbort` eşlenmediğinde, iş parçacığı durdurulduğunda geçerli iş parçacığına teslim edilemeyen bir duruma ulaşmak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="00892-117">If calls to `BeginPreventAsyncAbort` and `EndPreventAsyncAbort` are not paired, it is possible to reach a state in which thread aborts cannot be delivered to the current thread.</span></span>  
  
 <span data-ttu-id="00892-118">Gecikme, kendisini iptal eden bir iş parçacığı için kabul edilmez.</span><span class="sxs-lookup"><span data-stu-id="00892-118">The delay is not honored for a thread that aborts itself.</span></span>  
  
 <span data-ttu-id="00892-119">Bu özellik tarafından açığa çıkarılan işlevsellik, sanal makine (VM) tarafından dahili olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="00892-119">The functionality that is exposed by this feature is used internally by the virtual machine (VM).</span></span> <span data-ttu-id="00892-120">Bu yöntemlerin kötüye kullanılması, sanal makinede belirtilmeyen davranışa neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="00892-120">Misuse of these methods may cause unspecified behavior in the VM.</span></span> <span data-ttu-id="00892-121">Örneğin, `EndPreventAsyncAbort` ilk çağrılmadan çağırmak, `BeginPreventAsyncAbort` VM daha önce artmışsa sayacı sıfıra ayarlar.</span><span class="sxs-lookup"><span data-stu-id="00892-121">For example, calling `EndPreventAsyncAbort` without first calling `BeginPreventAsyncAbort` could set the counter to zero when the VM has previously incremented it.</span></span> <span data-ttu-id="00892-122">Benzer şekilde, iç sayaç taşma için denetlenmez.</span><span class="sxs-lookup"><span data-stu-id="00892-122">Similarly, the internal counter is not checked for overflow.</span></span> <span data-ttu-id="00892-123">Hem konak hem de VM tarafından arttırılacağından, tam sayı sınırını aşarsa, ortaya çıkan davranış belirtilmemiş olur.</span><span class="sxs-lookup"><span data-stu-id="00892-123">If it exceeds its integral limit because it is incremented by both the host and the VM, the resulting behavior is unspecified.</span></span>  
  
 <span data-ttu-id="00892-124">Kaynağından devralınan Üyeler `ICLRTask` ve bu arabirimin diğer kullanımları hakkında daha fazla bilgi Için [ICLRTask](iclrtask-interface.md) arabirimine bakın.</span><span class="sxs-lookup"><span data-stu-id="00892-124">For information about members inherited from `ICLRTask` and about the other uses of this interface, see the [ICLRTask](iclrtask-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00892-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="00892-125">Requirements</span></span>  

 <span data-ttu-id="00892-126">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00892-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00892-127">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="00892-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="00892-128">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="00892-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="00892-129">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00892-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00892-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="00892-130">See also</span></span>

- [<span data-ttu-id="00892-131">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00892-131">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="00892-132">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00892-132">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="00892-133">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00892-133">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="00892-134">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00892-134">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="00892-135">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="00892-135">Hosting Interfaces</span></span>](hosting-interfaces.md)
