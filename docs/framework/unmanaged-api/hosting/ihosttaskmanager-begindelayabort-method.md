---
title: IHostTaskManager::BeginDelayAbort Yöntemi
ms.date: 03/30/2017
api_name:
- IHostTaskManager.BeginDelayAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::BeginDelayAbort
helpviewer_keywords:
- BeginDelayAbort method [.NET Framework hosting]
- IHostTaskManager::BeginDelayAbort method [.NET Framework hosting]
ms.assetid: 75f42a8b-ed68-4718-a030-a179cfba7d72
topic_type:
- apiref
ms.openlocfilehash: f72cc15904d098e159dd7f75f673d43ae987998d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727334"
---
# <a name="ihosttaskmanagerbegindelayabort-method"></a><span data-ttu-id="b9466-102">IHostTaskManager::BeginDelayAbort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b9466-102">IHostTaskManager::BeginDelayAbort Method</span></span>

<span data-ttu-id="b9466-103">Ana bilgisayara, yönetilen kodun geçerli görevin durdurulmayan bir dönem girdiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="b9466-103">Notifies the host that managed code is entering a period in which the current task must not be aborted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9466-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="b9466-104">Syntax</span></span>  
  
```cpp  
HRESULT BeginDelayAbort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="b9466-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b9466-105">Return Value</span></span>  
  
|<span data-ttu-id="b9466-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b9466-106">HRESULT</span></span>|<span data-ttu-id="b9466-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b9466-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b9466-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="b9466-108">S_OK</span></span>|<span data-ttu-id="b9466-109">`BeginDelayAbort` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="b9466-109">`BeginDelayAbort` returned successfully.</span></span>|  
|<span data-ttu-id="b9466-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b9466-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b9466-111">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="b9466-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b9466-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b9466-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b9466-113">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="b9466-113">The call timed out.</span></span>|  
|<span data-ttu-id="b9466-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b9466-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b9466-115">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="b9466-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b9466-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b9466-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b9466-117">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="b9466-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b9466-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b9466-118">E_FAIL</span></span>|<span data-ttu-id="b9466-119">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="b9466-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b9466-120">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="b9466-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b9466-121">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="b9466-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="b9466-122">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="b9466-122">E_UNEXPECTED</span></span>|<span data-ttu-id="b9466-123">`BeginDelayAbort` zaten çağrılmış, ancak buna karşılık gelen [EndDelayAbort](ihosttaskmanager-enddelayabort-method.md) çağrısı henüz alınmadı.</span><span class="sxs-lookup"><span data-stu-id="b9466-123">`BeginDelayAbort` has already been called, but the corresponding call to [EndDelayAbort](ihosttaskmanager-enddelayabort-method.md) has not yet been received.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b9466-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b9466-124">Remarks</span></span>  

 <span data-ttu-id="b9466-125">Ana bilgisayar, çağrılana kadar geçerli görevi iptal etmelidir `EndDelayAbort` .</span><span class="sxs-lookup"><span data-stu-id="b9466-125">The host must not abort the current task until `EndDelayAbort` is called.</span></span> <span data-ttu-id="b9466-126">`BeginDelayAbort`Üzerinde araya giren bir çağrı olmadan başka bir çağrı yapılırsa `EndDelayAbort` , ana bilgisayar öğesinden E_UNEXPECTED döndürmelidir `BeginDelayAbort` ve hiçbir işlem yapması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="b9466-126">If another call to `BeginDelayAbort` is made without an intervening call to `EndDelayAbort`, the host should return E_UNEXPECTED from `BeginDelayAbort`, and should take no action.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9466-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b9466-127">Requirements</span></span>  

 <span data-ttu-id="b9466-128">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9466-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9466-129">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b9466-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b9466-130">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="b9466-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b9466-131">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9466-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9466-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b9466-132">See also</span></span>

- [<span data-ttu-id="b9466-133">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b9466-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="b9466-134">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b9466-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="b9466-135">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b9466-135">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
