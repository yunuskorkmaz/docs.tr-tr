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
ms.openlocfilehash: 3ea36c56ef9ccf5886ba96191627e5283da186f7
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762861"
---
# <a name="iclrtask2endpreventasyncabort-method"></a><span data-ttu-id="9faae-102">ICLRTask2::EndPreventAsyncAbort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9faae-102">ICLRTask2::EndPreventAsyncAbort Method</span></span>
<span data-ttu-id="9faae-103">Geçerli iş parçacığında iş parçacığı iptaline neden olan yeni veya bekleyen iş parçacığı iptali isteklerinin yapılmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="9faae-103">Allows new or pending thread abort requests to result in thread aborts on the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9faae-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="9faae-104">Syntax</span></span>  
  
```cpp  
HRESULT EndPreventAsyncAbort();  
```  
  
## <a name="return-value"></a><span data-ttu-id="9faae-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9faae-105">Return Value</span></span>  
 <span data-ttu-id="9faae-106">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="9faae-106">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="9faae-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9faae-107">HRESULT</span></span>|<span data-ttu-id="9faae-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9faae-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9faae-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="9faae-109">S_OK</span></span>|<span data-ttu-id="9faae-110">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="9faae-110">The method completed successfully.</span></span>|  
|<span data-ttu-id="9faae-111">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="9faae-111">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="9faae-112">Yöntem, geçerli iş parçacığı olmayan bir iş parçacığında çağrıldı.</span><span class="sxs-lookup"><span data-stu-id="9faae-112">The method was called on a thread which is not the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9faae-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9faae-113">Remarks</span></span>  
 <span data-ttu-id="9faae-114">Bu yöntemin çağrılması, geçerli iş parçacığı için gecikme iş parçacığı iptali sayacını bir azaltır.</span><span class="sxs-lookup"><span data-stu-id="9faae-114">Calling this method decrements the delay-thread-abort counter for the current thread by one.</span></span>  
  
 <span data-ttu-id="9faae-115">[ICLRTask2:: Beginkoruyucu Tasyncabort](iclrtask2-beginpreventasyncabort-method.md) çağrısı yapın ve `EndPreventAsyncAbort` iç içe olabilir.</span><span class="sxs-lookup"><span data-stu-id="9faae-115">Calls to [ICLRTask2::BeginPreventAsyncAbort](iclrtask2-beginpreventasyncabort-method.md) and `EndPreventAsyncAbort` can be nested.</span></span> <span data-ttu-id="9faae-116">Sayaç sıfırdan büyük olduğu sürece, geçerli iş parçacığı için iş parçacığı iptal işlemi gecikiyor.</span><span class="sxs-lookup"><span data-stu-id="9faae-116">As long as the counter is greater than zero, thread aborts for the current thread are delayed.</span></span>  
  
 <span data-ttu-id="9faae-117">Bu özellik tarafından açığa çıkarılan işlevsellik, sanal makine (VM) tarafından dahili olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9faae-117">The functionality that is exposed by this feature is used internally by the virtual machine (VM).</span></span> <span data-ttu-id="9faae-118">Bu yöntemlerin kötüye kullanılması, sanal makinede belirtilmeyen davranışa neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="9faae-118">Misuse of these methods may cause unspecified behavior in the VM.</span></span> <span data-ttu-id="9faae-119">Örneğin, `EndPreventAsyncAbort` ilk çağrılmadan çağırmak, `BeginPreventAsyncAbort` VM daha önce artmışsa sayacı sıfıra ayarlar.</span><span class="sxs-lookup"><span data-stu-id="9faae-119">For example, calling `EndPreventAsyncAbort` without first calling `BeginPreventAsyncAbort` could set the counter to zero when the VM has previously incremented it.</span></span> <span data-ttu-id="9faae-120">Benzer şekilde, iç sayaç taşma için denetlenmez.</span><span class="sxs-lookup"><span data-stu-id="9faae-120">Similarly, the internal counter is not checked for overflow.</span></span> <span data-ttu-id="9faae-121">Hem konak hem de VM tarafından arttırılacağından, tam sayı sınırını aşarsa, ortaya çıkan davranış belirtilmemiş olur.</span><span class="sxs-lookup"><span data-stu-id="9faae-121">If it exceeds its integral limit because it is incremented by both the host and the VM, the resulting behavior is unspecified.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9faae-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9faae-122">Requirements</span></span>  
 <span data-ttu-id="9faae-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9faae-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9faae-124">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9faae-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9faae-125">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="9faae-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9faae-126">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9faae-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9faae-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9faae-127">See also</span></span>

- [<span data-ttu-id="9faae-128">BeginPreventAsyncAbort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9faae-128">BeginPreventAsyncAbort Method</span></span>](iclrtask2-beginpreventasyncabort-method.md)
- [<span data-ttu-id="9faae-129">ICLRTask2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9faae-129">ICLRTask2 Interface</span></span>](iclrtask2-interface.md)
- [<span data-ttu-id="9faae-130">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9faae-130">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="9faae-131">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9faae-131">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="9faae-132">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9faae-132">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="9faae-133">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="9faae-133">Hosting Interfaces</span></span>](hosting-interfaces.md)
