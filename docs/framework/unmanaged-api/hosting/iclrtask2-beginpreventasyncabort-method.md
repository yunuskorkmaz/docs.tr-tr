---
description: 'Şu konuda daha fazla bilgi edinin: ICLRTask2:: Beginkoruyucu Tasyncabort yöntemi'
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
ms.openlocfilehash: 1e25cb0e6157d77efc6a04016dc49d9d5d0bf116
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99728657"
---
# <a name="iclrtask2beginpreventasyncabort-method"></a><span data-ttu-id="5c657-103">ICLRTask2::BeginPreventAsyncAbort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5c657-103">ICLRTask2::BeginPreventAsyncAbort Method</span></span>

<span data-ttu-id="5c657-104">Geçerli iş parçacığında iş parçacığı iptaline neden olan yeni iş parçacığı iptali isteklerini geciktirir.</span><span class="sxs-lookup"><span data-stu-id="5c657-104">Delays new thread abort requests from resulting in thread aborts on the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c657-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="5c657-105">Syntax</span></span>  
  
```cpp  
HRESULT BeginPreventAsyncAbort();  
```  
  
## <a name="return-value"></a><span data-ttu-id="5c657-106">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5c657-106">Return Value</span></span>  

 <span data-ttu-id="5c657-107">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="5c657-107">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="5c657-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5c657-108">HRESULT</span></span>|<span data-ttu-id="5c657-109">Description</span><span class="sxs-lookup"><span data-stu-id="5c657-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5c657-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="5c657-110">S_OK</span></span>|<span data-ttu-id="5c657-111">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="5c657-111">The method completed successfully.</span></span>|  
|<span data-ttu-id="5c657-112">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="5c657-112">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="5c657-113">Yöntem, geçerli iş parçacığı olmayan bir iş parçacığında çağrıldı.</span><span class="sxs-lookup"><span data-stu-id="5c657-113">The method was called on a thread which is not the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5c657-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5c657-114">Remarks</span></span>  

 <span data-ttu-id="5c657-115">Bu yöntemi çağırmak, geçerli iş parçacığı için gecikme-iş parçacığı iptali sayacını bir artırır.</span><span class="sxs-lookup"><span data-stu-id="5c657-115">Calling this method increments the delay-thread-abort counter for the current thread by one.</span></span>  
  
 <span data-ttu-id="5c657-116">`BeginPreventAsyncAbort`Ve [ICLRTask2:: Endkoruyucu Tasyncabort](iclrtask2-endpreventasyncabort-method.md) çağrıları iç içe olabilir.</span><span class="sxs-lookup"><span data-stu-id="5c657-116">Calls to `BeginPreventAsyncAbort` and [ICLRTask2::EndPreventAsyncAbort](iclrtask2-endpreventasyncabort-method.md) can be nested.</span></span> <span data-ttu-id="5c657-117">Sayaç sıfırdan büyük olduğu sürece, geçerli iş parçacığı için iş parçacığı iptal işlemi gecikiyor.</span><span class="sxs-lookup"><span data-stu-id="5c657-117">As long as the counter is greater than zero, thread aborts for the current thread are delayed.</span></span> <span data-ttu-id="5c657-118">Bu çağrı, yöntemi çağrısıyla eşlenmezse `EndPreventAsyncAbort` , iş parçacığının iptal edilmesi durumunda geçerli iş parçacığına teslim edilemez durumuna ulaşmak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="5c657-118">If this call is not paired with a call to the `EndPreventAsyncAbort` method, it is possible to reach a state in which thread aborts cannot be delivered to the current thread.</span></span>  
  
 <span data-ttu-id="5c657-119">Gecikme, kendisini iptal eden bir iş parçacığı için kabul edilmez.</span><span class="sxs-lookup"><span data-stu-id="5c657-119">The delay is not honored for a thread that aborts itself.</span></span>  
  
 <span data-ttu-id="5c657-120">Bu özellik tarafından açığa çıkarılan işlevsellik, sanal makine (VM) tarafından dahili olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5c657-120">The functionality that is exposed by this feature is used internally by the virtual machine (VM).</span></span> <span data-ttu-id="5c657-121">Bu yöntemlerin kötüye kullanılması, sanal makinede belirtilmeyen davranışa neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="5c657-121">Misuse of these methods may cause unspecified behavior in the VM.</span></span> <span data-ttu-id="5c657-122">Örneğin, `EndPreventAsyncAbort` ilk çağrılmadan çağırmak, `BeginPreventAsyncAbort` VM daha önce artmışsa sayacı sıfıra ayarlar.</span><span class="sxs-lookup"><span data-stu-id="5c657-122">For example, calling `EndPreventAsyncAbort` without first calling `BeginPreventAsyncAbort` could set the counter to zero when the VM has previously incremented it.</span></span> <span data-ttu-id="5c657-123">Benzer şekilde, iç sayaç taşma için denetlenmez.</span><span class="sxs-lookup"><span data-stu-id="5c657-123">Similarly, the internal counter is not checked for overflow.</span></span> <span data-ttu-id="5c657-124">Hem konak hem de VM tarafından arttırılacağından, tam sayı sınırını aşarsa, ortaya çıkan davranış belirtilmemiş olur.</span><span class="sxs-lookup"><span data-stu-id="5c657-124">If it exceeds its integral limit because it is incremented by both the host and the VM, the resulting behavior is unspecified.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c657-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5c657-125">Requirements</span></span>  

 <span data-ttu-id="5c657-126">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5c657-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c657-127">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="5c657-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5c657-128">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="5c657-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5c657-129">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c657-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c657-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5c657-130">See also</span></span>

- [<span data-ttu-id="5c657-131">EndPreventAsyncAbort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5c657-131">EndPreventAsyncAbort Method</span></span>](iclrtask2-endpreventasyncabort-method.md)
- [<span data-ttu-id="5c657-132">ICLRTask2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5c657-132">ICLRTask2 Interface</span></span>](iclrtask2-interface.md)
- [<span data-ttu-id="5c657-133">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5c657-133">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="5c657-134">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5c657-134">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="5c657-135">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5c657-135">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="5c657-136">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="5c657-136">Hosting Interfaces</span></span>](hosting-interfaces.md)
