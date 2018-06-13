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
ms.openlocfilehash: 5e1b5c0f5636748b96cc7d9667155581f1595a4e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33438411"
---
# <a name="iclrtask2beginpreventasyncabort-method"></a><span data-ttu-id="15562-102">ICLRTask2::BeginPreventAsyncAbort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="15562-102">ICLRTask2::BeginPreventAsyncAbort Method</span></span>
<span data-ttu-id="15562-103">Geçerli iş parçacığında iş parçacığı iptalleri sonuçlanmasını gecikmeler yeni iş parçacığı iptal istekleri.</span><span class="sxs-lookup"><span data-stu-id="15562-103">Delays new thread abort requests from resulting in thread aborts on the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15562-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="15562-104">Syntax</span></span>  
  
```  
HRESULT BeginPreventAsyncAbort();  
```  
  
## <a name="return-value"></a><span data-ttu-id="15562-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="15562-105">Return Value</span></span>  
 <span data-ttu-id="15562-106">Bu yöntem aşağıdaki belirli HRESULTs yanı sıra HRESULT yöntem hatası olduğunu gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="15562-106">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="15562-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="15562-107">HRESULT</span></span>|<span data-ttu-id="15562-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="15562-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="15562-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="15562-109">S_OK</span></span>|<span data-ttu-id="15562-110">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="15562-110">The method completed successfully.</span></span>|  
|<span data-ttu-id="15562-111">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="15562-111">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="15562-112">Yöntemi, geçerli iş parçacığının olmayan bir iş parçacığında çağrıldı.</span><span class="sxs-lookup"><span data-stu-id="15562-112">The method was called on a thread which is not the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="15562-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="15562-113">Remarks</span></span>  
 <span data-ttu-id="15562-114">Bu yöntemin çağrılması geçerli iş parçacığının gecikme iş parçacığı iptal sayaç bire artırır.</span><span class="sxs-lookup"><span data-stu-id="15562-114">Calling this method increments the delay-thread-abort counter for the current thread by one.</span></span>  
  
 <span data-ttu-id="15562-115">Çağrılar `BeginPreventAsyncAbort` ve [Iclrtask2::endpreventasyncabort](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-endpreventasyncabort-method.md) iç içe olamaz.</span><span class="sxs-lookup"><span data-stu-id="15562-115">Calls to `BeginPreventAsyncAbort` and [ICLRTask2::EndPreventAsyncAbort](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-endpreventasyncabort-method.md) can be nested.</span></span> <span data-ttu-id="15562-116">Sayaç sıfırdan büyük olduğu sürece, geçerli iş parçacığı için iş parçacığı iptalleri gecikir.</span><span class="sxs-lookup"><span data-stu-id="15562-116">As long as the counter is greater than zero, thread aborts for the current thread are delayed.</span></span> <span data-ttu-id="15562-117">Bu çağrı çağrısıyla eşleştirilmiş değil, `EndPreventAsyncAbort` yöntemi, hangi iş parçacığı iptalleri olamaz teslim edilemiyor geçerli iş parçacığına bir duruma mümkün.</span><span class="sxs-lookup"><span data-stu-id="15562-117">If this call is not paired with a call to the `EndPreventAsyncAbort` method, it is possible to reach a state in which thread aborts cannot be delivered to the current thread.</span></span>  
  
 <span data-ttu-id="15562-118">Gecikme kendisini durdurur bir iş parçacığı için dikkate alınır değil.</span><span class="sxs-lookup"><span data-stu-id="15562-118">The delay is not honored for a thread that aborts itself.</span></span>  
  
 <span data-ttu-id="15562-119">Bu özellik tarafından sunulan işlevselliği sanal makine (VM) tarafından dahili olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="15562-119">The functionality that is exposed by this feature is used internally by the virtual machine (VM).</span></span> <span data-ttu-id="15562-120">Bu yöntemlerin kötüye VM'yi belirtilmeyen davranışlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="15562-120">Misuse of these methods may cause unspecified behavior in the VM.</span></span> <span data-ttu-id="15562-121">Örneğin, arama `EndPreventAsyncAbort` ilk çağırmadan `BeginPreventAsyncAbort` VM daha önce onu artar olduğunda Sayaç sıfıra ayarlanamıyor.</span><span class="sxs-lookup"><span data-stu-id="15562-121">For example, calling `EndPreventAsyncAbort` without first calling `BeginPreventAsyncAbort` could set the counter to zero when the VM has previously incremented it.</span></span> <span data-ttu-id="15562-122">Benzer şekilde, iç sayaç için taşma işaretlenmemiştir.</span><span class="sxs-lookup"><span data-stu-id="15562-122">Similarly, the internal counter is not checked for overflow.</span></span> <span data-ttu-id="15562-123">Konak ve VM tarafından artırılır çünkü tam sayı sınırını aşarsa, bunun sonucunda oluşan davranışı belirtilmemiş.</span><span class="sxs-lookup"><span data-stu-id="15562-123">If it exceeds its integral limit because it is incremented by both the host and the VM, the resulting behavior is unspecified.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15562-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="15562-124">Requirements</span></span>  
 <span data-ttu-id="15562-125">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15562-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15562-126">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="15562-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="15562-127">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="15562-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="15562-128">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15562-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15562-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="15562-129">See Also</span></span>  
 [<span data-ttu-id="15562-130">EndPreventAsyncAbort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="15562-130">EndPreventAsyncAbort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-endpreventasyncabort-method.md)  
 [<span data-ttu-id="15562-131">ICLRTask2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="15562-131">ICLRTask2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)  
 [<span data-ttu-id="15562-132">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="15562-132">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="15562-133">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="15562-133">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="15562-134">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="15562-134">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="15562-135">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="15562-135">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
