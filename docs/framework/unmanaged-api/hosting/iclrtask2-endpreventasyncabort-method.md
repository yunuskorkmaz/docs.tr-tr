---
title: ICLRTask2::EndPreventAsyncAbort Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRTask2.EndPreventAsyncAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask2::EndPreventAsyncAbort
helpviewer_keywords:
- EndPreventAsyncAbort method [.NET Framework hosting]
- ICLRTask2::EndPreventAsyncAbort method [.NET Framework hosting]
ms.assetid: d8013659-e3df-44b3-814f-a6b534ce62f8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 60997717baf70e10366e7f0ba6a06daa1f35f8cd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59121673"
---
# <a name="iclrtask2endpreventasyncabort-method"></a><span data-ttu-id="bb9c6-102">ICLRTask2::EndPreventAsyncAbort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bb9c6-102">ICLRTask2::EndPreventAsyncAbort Method</span></span>
<span data-ttu-id="bb9c6-103">Yeni izin verir veya bekleyen iş parçacığı elde etmek iş parçacığı durdurma isteği geçerli iş parçacığı üzerinde durdurur.</span><span class="sxs-lookup"><span data-stu-id="bb9c6-103">Allows new or pending thread abort requests to result in thread aborts on the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb9c6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bb9c6-104">Syntax</span></span>  
  
```  
HRESULT EndPreventAsyncAbort();  
```  
  
## <a name="return-value"></a><span data-ttu-id="bb9c6-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="bb9c6-105">Return Value</span></span>  
 <span data-ttu-id="bb9c6-106">Bu yöntem aşağıdaki özel HRESULT'ları yanı sıra HRESULT döndürür yöntemi hatayı gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="bb9c6-106">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="bb9c6-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bb9c6-107">HRESULT</span></span>|<span data-ttu-id="bb9c6-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bb9c6-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bb9c6-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="bb9c6-109">S_OK</span></span>|<span data-ttu-id="bb9c6-110">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="bb9c6-110">The method completed successfully.</span></span>|  
|<span data-ttu-id="bb9c6-111">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="bb9c6-111">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="bb9c6-112">Yöntem, geçerli iş parçacığı olmayan bir iş parçacığında çağrıldı.</span><span class="sxs-lookup"><span data-stu-id="bb9c6-112">The method was called on a thread which is not the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bb9c6-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bb9c6-113">Remarks</span></span>  
 <span data-ttu-id="bb9c6-114">Bu yöntem azaltır gecikme iş parçacığı iptal sayaç için geçerli iş parçacığı tarafından çağrılıyor.</span><span class="sxs-lookup"><span data-stu-id="bb9c6-114">Calling this method decrements the delay-thread-abort counter for the current thread by one.</span></span>  
  
 <span data-ttu-id="bb9c6-115">Çağrılar [Iclrtask2::beginpreventasyncabort](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-beginpreventasyncabort-method.md) ve `EndPreventAsyncAbort` yuvalanabilir.</span><span class="sxs-lookup"><span data-stu-id="bb9c6-115">Calls to [ICLRTask2::BeginPreventAsyncAbort](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-beginpreventasyncabort-method.md) and `EndPreventAsyncAbort` can be nested.</span></span> <span data-ttu-id="bb9c6-116">Sayaç sıfırdan büyük olduğu sürece, geçerli iş parçacığı için iş parçacığı iptalleri gecikir.</span><span class="sxs-lookup"><span data-stu-id="bb9c6-116">As long as the counter is greater than zero, thread aborts for the current thread are delayed.</span></span>  
  
 <span data-ttu-id="bb9c6-117">Bu özellik tarafından sunulan işlevselliği, sanal makine (VM) tarafından dahili olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bb9c6-117">The functionality that is exposed by this feature is used internally by the virtual machine (VM).</span></span> <span data-ttu-id="bb9c6-118">Bu yöntemlerin kötüye, VM'yi belirsiz davranışa neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="bb9c6-118">Misuse of these methods may cause unspecified behavior in the VM.</span></span> <span data-ttu-id="bb9c6-119">Örneğin, çağırma `EndPreventAsyncAbort` ilk çağırmadan `BeginPreventAsyncAbort` sayaç VM daha önce artan olduğunda sıfır olarak ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bb9c6-119">For example, calling `EndPreventAsyncAbort` without first calling `BeginPreventAsyncAbort` could set the counter to zero when the VM has previously incremented it.</span></span> <span data-ttu-id="bb9c6-120">Benzer şekilde, iç sayaç için taşma işaretlenmemiştir.</span><span class="sxs-lookup"><span data-stu-id="bb9c6-120">Similarly, the internal counter is not checked for overflow.</span></span> <span data-ttu-id="bb9c6-121">Hem konak hem de VM tarafından artar çünkü tam sayı sınırını aşarsa, sonuçta ortaya çıkan davranış belirtilmemiş.</span><span class="sxs-lookup"><span data-stu-id="bb9c6-121">If it exceeds its integral limit because it is incremented by both the host and the VM, the resulting behavior is unspecified.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb9c6-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bb9c6-122">Requirements</span></span>  
 <span data-ttu-id="bb9c6-123">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb9c6-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb9c6-124">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="bb9c6-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bb9c6-125">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="bb9c6-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bb9c6-126">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb9c6-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb9c6-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bb9c6-127">See also</span></span>

- [<span data-ttu-id="bb9c6-128">BeginPreventAsyncAbort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bb9c6-128">BeginPreventAsyncAbort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-beginpreventasyncabort-method.md)
- [<span data-ttu-id="bb9c6-129">ICLRTask2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bb9c6-129">ICLRTask2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)
- [<span data-ttu-id="bb9c6-130">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bb9c6-130">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="bb9c6-131">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bb9c6-131">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="bb9c6-132">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bb9c6-132">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="bb9c6-133">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="bb9c6-133">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
