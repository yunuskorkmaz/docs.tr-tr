---
title: ICLRTask2::BeginPreventAsyncAbort Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRTask2.BeginPreventAsyncAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask2::BeginPreventAsyncAbort
helpviewer_keywords:
- ICLRTask2::BeginPreventAsyncAbort method [.NET Framework hosting]
- BeginPreventAsyncAbort method [.NET Framework hosting]
ms.assetid: 75754c2f-38c7-4707-85fe-559db4542729
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 85a43fef7f6dfa6dbe0bb9f1c4caec2c9c224b93
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59213590"
---
# <a name="iclrtask2beginpreventasyncabort-method"></a><span data-ttu-id="85f12-102">ICLRTask2::BeginPreventAsyncAbort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="85f12-102">ICLRTask2::BeginPreventAsyncAbort Method</span></span>
<span data-ttu-id="85f12-103">Yeni iş parçacığı gecikmeler geçerli iş parçacığında iş parçacığı iptalleri výsledek isteklerinin durdurur.</span><span class="sxs-lookup"><span data-stu-id="85f12-103">Delays new thread abort requests from resulting in thread aborts on the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85f12-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="85f12-104">Syntax</span></span>  
  
```  
HRESULT BeginPreventAsyncAbort();  
```  
  
## <a name="return-value"></a><span data-ttu-id="85f12-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="85f12-105">Return Value</span></span>  
 <span data-ttu-id="85f12-106">Bu yöntem aşağıdaki özel HRESULT'ları yanı sıra HRESULT döndürür yöntemi hatayı gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="85f12-106">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="85f12-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="85f12-107">HRESULT</span></span>|<span data-ttu-id="85f12-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="85f12-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="85f12-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="85f12-109">S_OK</span></span>|<span data-ttu-id="85f12-110">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="85f12-110">The method completed successfully.</span></span>|  
|<span data-ttu-id="85f12-111">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="85f12-111">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="85f12-112">Yöntem, geçerli iş parçacığı olmayan bir iş parçacığında çağrıldı.</span><span class="sxs-lookup"><span data-stu-id="85f12-112">The method was called on a thread which is not the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="85f12-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="85f12-113">Remarks</span></span>  
 <span data-ttu-id="85f12-114">Bu yöntemi çağırmadan geçerli iş parçacığına gecikme iş parçacığı iptal sayaç bire artırır.</span><span class="sxs-lookup"><span data-stu-id="85f12-114">Calling this method increments the delay-thread-abort counter for the current thread by one.</span></span>  
  
 <span data-ttu-id="85f12-115">Çağrılar `BeginPreventAsyncAbort` ve [Iclrtask2::endpreventasyncabort](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-endpreventasyncabort-method.md) yuvalanabilir.</span><span class="sxs-lookup"><span data-stu-id="85f12-115">Calls to `BeginPreventAsyncAbort` and [ICLRTask2::EndPreventAsyncAbort](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-endpreventasyncabort-method.md) can be nested.</span></span> <span data-ttu-id="85f12-116">Sayaç sıfırdan büyük olduğu sürece, geçerli iş parçacığı için iş parçacığı iptalleri gecikir.</span><span class="sxs-lookup"><span data-stu-id="85f12-116">As long as the counter is greater than zero, thread aborts for the current thread are delayed.</span></span> <span data-ttu-id="85f12-117">Bu çağrı bir çağrı ile eşleştirilmiş değil, `EndPreventAsyncAbort` yöntemi mümkündür hangi iş parçacığı iptalleri olamaz teslim edilemiyor geçerli iş parçacığına bir duruma ulaşmak.</span><span class="sxs-lookup"><span data-stu-id="85f12-117">If this call is not paired with a call to the `EndPreventAsyncAbort` method, it is possible to reach a state in which thread aborts cannot be delivered to the current thread.</span></span>  
  
 <span data-ttu-id="85f12-118">Gecikme kendisini iptal ettiğinde bir iş parçacığı için uygulanır değil.</span><span class="sxs-lookup"><span data-stu-id="85f12-118">The delay is not honored for a thread that aborts itself.</span></span>  
  
 <span data-ttu-id="85f12-119">Bu özellik tarafından sunulan işlevselliği, sanal makine (VM) tarafından dahili olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="85f12-119">The functionality that is exposed by this feature is used internally by the virtual machine (VM).</span></span> <span data-ttu-id="85f12-120">Bu yöntemlerin kötüye, VM'yi belirsiz davranışa neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="85f12-120">Misuse of these methods may cause unspecified behavior in the VM.</span></span> <span data-ttu-id="85f12-121">Örneğin, çağırma `EndPreventAsyncAbort` ilk çağırmadan `BeginPreventAsyncAbort` sayaç VM daha önce artan olduğunda sıfır olarak ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="85f12-121">For example, calling `EndPreventAsyncAbort` without first calling `BeginPreventAsyncAbort` could set the counter to zero when the VM has previously incremented it.</span></span> <span data-ttu-id="85f12-122">Benzer şekilde, iç sayaç için taşma işaretlenmemiştir.</span><span class="sxs-lookup"><span data-stu-id="85f12-122">Similarly, the internal counter is not checked for overflow.</span></span> <span data-ttu-id="85f12-123">Hem konak hem de VM tarafından artar çünkü tam sayı sınırını aşarsa, sonuçta ortaya çıkan davranış belirtilmemiş.</span><span class="sxs-lookup"><span data-stu-id="85f12-123">If it exceeds its integral limit because it is incremented by both the host and the VM, the resulting behavior is unspecified.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85f12-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="85f12-124">Requirements</span></span>  
 <span data-ttu-id="85f12-125">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="85f12-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85f12-126">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="85f12-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="85f12-127">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="85f12-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="85f12-128">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85f12-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85f12-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="85f12-129">See also</span></span>

- [<span data-ttu-id="85f12-130">EndPreventAsyncAbort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="85f12-130">EndPreventAsyncAbort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-endpreventasyncabort-method.md)
- [<span data-ttu-id="85f12-131">ICLRTask2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="85f12-131">ICLRTask2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)
- [<span data-ttu-id="85f12-132">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="85f12-132">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="85f12-133">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="85f12-133">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="85f12-134">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="85f12-134">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="85f12-135">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="85f12-135">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
