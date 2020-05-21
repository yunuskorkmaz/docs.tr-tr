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
ms.openlocfilehash: 0da18c6850f393808d05dff8b1f19ac12b05bb86
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762896"
---
# <a name="iclrtask2beginpreventasyncabort-method"></a><span data-ttu-id="0d375-102">ICLRTask2::BeginPreventAsyncAbort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0d375-102">ICLRTask2::BeginPreventAsyncAbort Method</span></span>
<span data-ttu-id="0d375-103">Geçerli iş parçacığında iş parçacığı iptaline neden olan yeni iş parçacığı iptali isteklerini geciktirir.</span><span class="sxs-lookup"><span data-stu-id="0d375-103">Delays new thread abort requests from resulting in thread aborts on the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d375-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="0d375-104">Syntax</span></span>  
  
```cpp  
HRESULT BeginPreventAsyncAbort();  
```  
  
## <a name="return-value"></a><span data-ttu-id="0d375-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0d375-105">Return Value</span></span>  
 <span data-ttu-id="0d375-106">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="0d375-106">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="0d375-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0d375-107">HRESULT</span></span>|<span data-ttu-id="0d375-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0d375-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0d375-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="0d375-109">S_OK</span></span>|<span data-ttu-id="0d375-110">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="0d375-110">The method completed successfully.</span></span>|  
|<span data-ttu-id="0d375-111">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="0d375-111">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="0d375-112">Yöntem, geçerli iş parçacığı olmayan bir iş parçacığında çağrıldı.</span><span class="sxs-lookup"><span data-stu-id="0d375-112">The method was called on a thread which is not the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0d375-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0d375-113">Remarks</span></span>  
 <span data-ttu-id="0d375-114">Bu yöntemi çağırmak, geçerli iş parçacığı için gecikme-iş parçacığı iptali sayacını bir artırır.</span><span class="sxs-lookup"><span data-stu-id="0d375-114">Calling this method increments the delay-thread-abort counter for the current thread by one.</span></span>  
  
 <span data-ttu-id="0d375-115">`BeginPreventAsyncAbort`Ve [ICLRTask2:: Endkoruyucu Tasyncabort](iclrtask2-endpreventasyncabort-method.md) çağrıları iç içe olabilir.</span><span class="sxs-lookup"><span data-stu-id="0d375-115">Calls to `BeginPreventAsyncAbort` and [ICLRTask2::EndPreventAsyncAbort](iclrtask2-endpreventasyncabort-method.md) can be nested.</span></span> <span data-ttu-id="0d375-116">Sayaç sıfırdan büyük olduğu sürece, geçerli iş parçacığı için iş parçacığı iptal işlemi gecikiyor.</span><span class="sxs-lookup"><span data-stu-id="0d375-116">As long as the counter is greater than zero, thread aborts for the current thread are delayed.</span></span> <span data-ttu-id="0d375-117">Bu çağrı, yöntemi çağrısıyla eşlenmezse `EndPreventAsyncAbort` , iş parçacığının iptal edilmesi durumunda geçerli iş parçacığına teslim edilemez durumuna ulaşmak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="0d375-117">If this call is not paired with a call to the `EndPreventAsyncAbort` method, it is possible to reach a state in which thread aborts cannot be delivered to the current thread.</span></span>  
  
 <span data-ttu-id="0d375-118">Gecikme, kendisini iptal eden bir iş parçacığı için kabul edilmez.</span><span class="sxs-lookup"><span data-stu-id="0d375-118">The delay is not honored for a thread that aborts itself.</span></span>  
  
 <span data-ttu-id="0d375-119">Bu özellik tarafından açığa çıkarılan işlevsellik, sanal makine (VM) tarafından dahili olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0d375-119">The functionality that is exposed by this feature is used internally by the virtual machine (VM).</span></span> <span data-ttu-id="0d375-120">Bu yöntemlerin kötüye kullanılması, sanal makinede belirtilmeyen davranışa neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="0d375-120">Misuse of these methods may cause unspecified behavior in the VM.</span></span> <span data-ttu-id="0d375-121">Örneğin, `EndPreventAsyncAbort` ilk çağrılmadan çağırmak, `BeginPreventAsyncAbort` VM daha önce artmışsa sayacı sıfıra ayarlar.</span><span class="sxs-lookup"><span data-stu-id="0d375-121">For example, calling `EndPreventAsyncAbort` without first calling `BeginPreventAsyncAbort` could set the counter to zero when the VM has previously incremented it.</span></span> <span data-ttu-id="0d375-122">Benzer şekilde, iç sayaç taşma için denetlenmez.</span><span class="sxs-lookup"><span data-stu-id="0d375-122">Similarly, the internal counter is not checked for overflow.</span></span> <span data-ttu-id="0d375-123">Hem konak hem de VM tarafından arttırılacağından, tam sayı sınırını aşarsa, ortaya çıkan davranış belirtilmemiş olur.</span><span class="sxs-lookup"><span data-stu-id="0d375-123">If it exceeds its integral limit because it is incremented by both the host and the VM, the resulting behavior is unspecified.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d375-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0d375-124">Requirements</span></span>  
 <span data-ttu-id="0d375-125">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d375-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d375-126">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0d375-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0d375-127">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="0d375-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0d375-128">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d375-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d375-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0d375-129">See also</span></span>

- [<span data-ttu-id="0d375-130">EndPreventAsyncAbort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0d375-130">EndPreventAsyncAbort Method</span></span>](iclrtask2-endpreventasyncabort-method.md)
- [<span data-ttu-id="0d375-131">ICLRTask2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0d375-131">ICLRTask2 Interface</span></span>](iclrtask2-interface.md)
- [<span data-ttu-id="0d375-132">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0d375-132">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="0d375-133">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0d375-133">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="0d375-134">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0d375-134">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="0d375-135">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="0d375-135">Hosting Interfaces</span></span>](hosting-interfaces.md)
