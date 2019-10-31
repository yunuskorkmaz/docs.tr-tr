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
ms.openlocfilehash: 8ae66e0bf96138e5bc2f33e4c14ad86e7dabc6b8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124548"
---
# <a name="iclrtask2endpreventasyncabort-method"></a><span data-ttu-id="58321-102">ICLRTask2::EndPreventAsyncAbort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="58321-102">ICLRTask2::EndPreventAsyncAbort Method</span></span>
<span data-ttu-id="58321-103">Geçerli iş parçacığında iş parçacığı iptaline neden olan yeni veya bekleyen iş parçacığı iptali isteklerinin yapılmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="58321-103">Allows new or pending thread abort requests to result in thread aborts on the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58321-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="58321-104">Syntax</span></span>  
  
```cpp  
HRESULT EndPreventAsyncAbort();  
```  
  
## <a name="return-value"></a><span data-ttu-id="58321-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="58321-105">Return Value</span></span>  
 <span data-ttu-id="58321-106">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="58321-106">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="58321-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="58321-107">HRESULT</span></span>|<span data-ttu-id="58321-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="58321-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="58321-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="58321-109">S_OK</span></span>|<span data-ttu-id="58321-110">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="58321-110">The method completed successfully.</span></span>|  
|<span data-ttu-id="58321-111">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="58321-111">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="58321-112">Yöntem, geçerli iş parçacığı olmayan bir iş parçacığında çağrıldı.</span><span class="sxs-lookup"><span data-stu-id="58321-112">The method was called on a thread which is not the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="58321-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="58321-113">Remarks</span></span>  
 <span data-ttu-id="58321-114">Bu yöntemin çağrılması, geçerli iş parçacığı için gecikme iş parçacığı iptali sayacını bir azaltır.</span><span class="sxs-lookup"><span data-stu-id="58321-114">Calling this method decrements the delay-thread-abort counter for the current thread by one.</span></span>  
  
 <span data-ttu-id="58321-115">[ICLRTask2:: Beginkoruyucu Tasyncabort](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-beginpreventasyncabort-method.md) ve `EndPreventAsyncAbort` çağrıları iç içe olabilir.</span><span class="sxs-lookup"><span data-stu-id="58321-115">Calls to [ICLRTask2::BeginPreventAsyncAbort](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-beginpreventasyncabort-method.md) and `EndPreventAsyncAbort` can be nested.</span></span> <span data-ttu-id="58321-116">Sayaç sıfırdan büyük olduğu sürece, geçerli iş parçacığı için iş parçacığı iptal işlemi gecikiyor.</span><span class="sxs-lookup"><span data-stu-id="58321-116">As long as the counter is greater than zero, thread aborts for the current thread are delayed.</span></span>  
  
 <span data-ttu-id="58321-117">Bu özellik tarafından açığa çıkarılan işlevsellik, sanal makine (VM) tarafından dahili olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="58321-117">The functionality that is exposed by this feature is used internally by the virtual machine (VM).</span></span> <span data-ttu-id="58321-118">Bu yöntemlerin kötüye kullanılması, sanal makinede belirtilmeyen davranışa neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="58321-118">Misuse of these methods may cause unspecified behavior in the VM.</span></span> <span data-ttu-id="58321-119">Örneğin, önce `BeginPreventAsyncAbort` çağrılmadan `EndPreventAsyncAbort` çağırmak, VM daha önce artmışsa sayacı sıfıra ayarlayabilir.</span><span class="sxs-lookup"><span data-stu-id="58321-119">For example, calling `EndPreventAsyncAbort` without first calling `BeginPreventAsyncAbort` could set the counter to zero when the VM has previously incremented it.</span></span> <span data-ttu-id="58321-120">Benzer şekilde, iç sayaç taşma için denetlenmez.</span><span class="sxs-lookup"><span data-stu-id="58321-120">Similarly, the internal counter is not checked for overflow.</span></span> <span data-ttu-id="58321-121">Hem konak hem de VM tarafından arttırılacağından, tam sayı sınırını aşarsa, ortaya çıkan davranış belirtilmemiş olur.</span><span class="sxs-lookup"><span data-stu-id="58321-121">If it exceeds its integral limit because it is incremented by both the host and the VM, the resulting behavior is unspecified.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58321-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="58321-122">Requirements</span></span>  
 <span data-ttu-id="58321-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="58321-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58321-124">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="58321-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="58321-125">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="58321-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="58321-126">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58321-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58321-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="58321-127">See also</span></span>

- [<span data-ttu-id="58321-128">BeginPreventAsyncAbort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="58321-128">BeginPreventAsyncAbort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-beginpreventasyncabort-method.md)
- [<span data-ttu-id="58321-129">ICLRTask2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="58321-129">ICLRTask2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)
- [<span data-ttu-id="58321-130">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="58321-130">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="58321-131">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="58321-131">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="58321-132">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="58321-132">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="58321-133">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="58321-133">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
