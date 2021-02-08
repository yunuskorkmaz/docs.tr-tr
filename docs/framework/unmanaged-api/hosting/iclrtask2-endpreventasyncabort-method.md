---
description: 'Şu konuda daha fazla bilgi edinin: ICLRTask2:: Endkoruyucu Tasyncabort yöntemi'
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
ms.openlocfilehash: 964a68c1ad6d5aa6a95560d2870e135640283590
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799505"
---
# <a name="iclrtask2endpreventasyncabort-method"></a><span data-ttu-id="6d09e-103">ICLRTask2::EndPreventAsyncAbort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6d09e-103">ICLRTask2::EndPreventAsyncAbort Method</span></span>

<span data-ttu-id="6d09e-104">Geçerli iş parçacığında iş parçacığı iptaline neden olan yeni veya bekleyen iş parçacığı iptali isteklerinin yapılmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="6d09e-104">Allows new or pending thread abort requests to result in thread aborts on the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d09e-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="6d09e-105">Syntax</span></span>  
  
```cpp  
HRESULT EndPreventAsyncAbort();  
```  
  
## <a name="return-value"></a><span data-ttu-id="6d09e-106">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="6d09e-106">Return Value</span></span>  

 <span data-ttu-id="6d09e-107">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="6d09e-107">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="6d09e-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6d09e-108">HRESULT</span></span>|<span data-ttu-id="6d09e-109">Description</span><span class="sxs-lookup"><span data-stu-id="6d09e-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6d09e-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="6d09e-110">S_OK</span></span>|<span data-ttu-id="6d09e-111">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="6d09e-111">The method completed successfully.</span></span>|  
|<span data-ttu-id="6d09e-112">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="6d09e-112">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="6d09e-113">Yöntem, geçerli iş parçacığı olmayan bir iş parçacığında çağrıldı.</span><span class="sxs-lookup"><span data-stu-id="6d09e-113">The method was called on a thread which is not the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6d09e-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6d09e-114">Remarks</span></span>  

 <span data-ttu-id="6d09e-115">Bu yöntemin çağrılması, geçerli iş parçacığı için gecikme iş parçacığı iptali sayacını bir azaltır.</span><span class="sxs-lookup"><span data-stu-id="6d09e-115">Calling this method decrements the delay-thread-abort counter for the current thread by one.</span></span>  
  
 <span data-ttu-id="6d09e-116">[ICLRTask2:: Beginkoruyucu Tasyncabort](iclrtask2-beginpreventasyncabort-method.md) çağrısı yapın ve `EndPreventAsyncAbort` iç içe olabilir.</span><span class="sxs-lookup"><span data-stu-id="6d09e-116">Calls to [ICLRTask2::BeginPreventAsyncAbort](iclrtask2-beginpreventasyncabort-method.md) and `EndPreventAsyncAbort` can be nested.</span></span> <span data-ttu-id="6d09e-117">Sayaç sıfırdan büyük olduğu sürece, geçerli iş parçacığı için iş parçacığı iptal işlemi gecikiyor.</span><span class="sxs-lookup"><span data-stu-id="6d09e-117">As long as the counter is greater than zero, thread aborts for the current thread are delayed.</span></span>  
  
 <span data-ttu-id="6d09e-118">Bu özellik tarafından açığa çıkarılan işlevsellik, sanal makine (VM) tarafından dahili olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6d09e-118">The functionality that is exposed by this feature is used internally by the virtual machine (VM).</span></span> <span data-ttu-id="6d09e-119">Bu yöntemlerin kötüye kullanılması, sanal makinede belirtilmeyen davranışa neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="6d09e-119">Misuse of these methods may cause unspecified behavior in the VM.</span></span> <span data-ttu-id="6d09e-120">Örneğin, `EndPreventAsyncAbort` ilk çağrılmadan çağırmak, `BeginPreventAsyncAbort` VM daha önce artmışsa sayacı sıfıra ayarlar.</span><span class="sxs-lookup"><span data-stu-id="6d09e-120">For example, calling `EndPreventAsyncAbort` without first calling `BeginPreventAsyncAbort` could set the counter to zero when the VM has previously incremented it.</span></span> <span data-ttu-id="6d09e-121">Benzer şekilde, iç sayaç taşma için denetlenmez.</span><span class="sxs-lookup"><span data-stu-id="6d09e-121">Similarly, the internal counter is not checked for overflow.</span></span> <span data-ttu-id="6d09e-122">Hem konak hem de VM tarafından arttırılacağından, tam sayı sınırını aşarsa, ortaya çıkan davranış belirtilmemiş olur.</span><span class="sxs-lookup"><span data-stu-id="6d09e-122">If it exceeds its integral limit because it is incremented by both the host and the VM, the resulting behavior is unspecified.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d09e-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6d09e-123">Requirements</span></span>  

 <span data-ttu-id="6d09e-124">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d09e-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d09e-125">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6d09e-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6d09e-126">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="6d09e-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6d09e-127">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d09e-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d09e-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6d09e-128">See also</span></span>

- [<span data-ttu-id="6d09e-129">BeginPreventAsyncAbort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6d09e-129">BeginPreventAsyncAbort Method</span></span>](iclrtask2-beginpreventasyncabort-method.md)
- [<span data-ttu-id="6d09e-130">ICLRTask2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6d09e-130">ICLRTask2 Interface</span></span>](iclrtask2-interface.md)
- [<span data-ttu-id="6d09e-131">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6d09e-131">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="6d09e-132">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6d09e-132">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="6d09e-133">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6d09e-133">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="6d09e-134">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="6d09e-134">Hosting Interfaces</span></span>](hosting-interfaces.md)
