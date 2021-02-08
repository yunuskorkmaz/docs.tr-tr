---
description: ': IHostTaskManager:: BeginDelayAbort yöntemi hakkında daha fazla bilgi'
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
ms.openlocfilehash: f991690af4f7e634c8d845bdbd09f690b4ea3af7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784619"
---
# <a name="ihosttaskmanagerbegindelayabort-method"></a><span data-ttu-id="fd187-103">IHostTaskManager::BeginDelayAbort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fd187-103">IHostTaskManager::BeginDelayAbort Method</span></span>

<span data-ttu-id="fd187-104">Ana bilgisayara, yönetilen kodun geçerli görevin durdurulmayan bir dönem girdiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="fd187-104">Notifies the host that managed code is entering a period in which the current task must not be aborted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd187-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="fd187-105">Syntax</span></span>  
  
```cpp  
HRESULT BeginDelayAbort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="fd187-106">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="fd187-106">Return Value</span></span>  
  
|<span data-ttu-id="fd187-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fd187-107">HRESULT</span></span>|<span data-ttu-id="fd187-108">Description</span><span class="sxs-lookup"><span data-stu-id="fd187-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fd187-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="fd187-109">S_OK</span></span>|<span data-ttu-id="fd187-110">`BeginDelayAbort` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="fd187-110">`BeginDelayAbort` returned successfully.</span></span>|  
|<span data-ttu-id="fd187-111">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fd187-111">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fd187-112">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="fd187-112">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fd187-113">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fd187-113">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="fd187-114">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="fd187-114">The call timed out.</span></span>|  
|<span data-ttu-id="fd187-115">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="fd187-115">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="fd187-116">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="fd187-116">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="fd187-117">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="fd187-117">HOST_E_ABANDONED</span></span>|<span data-ttu-id="fd187-118">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="fd187-118">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="fd187-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fd187-119">E_FAIL</span></span>|<span data-ttu-id="fd187-120">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="fd187-120">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fd187-121">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="fd187-121">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="fd187-122">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="fd187-122">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="fd187-123">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="fd187-123">E_UNEXPECTED</span></span>|<span data-ttu-id="fd187-124">`BeginDelayAbort` zaten çağrılmış, ancak buna karşılık gelen [EndDelayAbort](ihosttaskmanager-enddelayabort-method.md) çağrısı henüz alınmadı.</span><span class="sxs-lookup"><span data-stu-id="fd187-124">`BeginDelayAbort` has already been called, but the corresponding call to [EndDelayAbort](ihosttaskmanager-enddelayabort-method.md) has not yet been received.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fd187-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fd187-125">Remarks</span></span>  

 <span data-ttu-id="fd187-126">Ana bilgisayar, çağrılana kadar geçerli görevi iptal etmelidir `EndDelayAbort` .</span><span class="sxs-lookup"><span data-stu-id="fd187-126">The host must not abort the current task until `EndDelayAbort` is called.</span></span> <span data-ttu-id="fd187-127">`BeginDelayAbort`Üzerinde araya giren bir çağrı olmadan başka bir çağrı yapılırsa `EndDelayAbort` , ana bilgisayar öğesinden E_UNEXPECTED döndürmelidir `BeginDelayAbort` ve hiçbir işlem yapması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="fd187-127">If another call to `BeginDelayAbort` is made without an intervening call to `EndDelayAbort`, the host should return E_UNEXPECTED from `BeginDelayAbort`, and should take no action.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd187-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fd187-128">Requirements</span></span>  

 <span data-ttu-id="fd187-129">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fd187-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd187-130">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="fd187-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fd187-131">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="fd187-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fd187-132">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd187-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd187-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fd187-133">See also</span></span>

- [<span data-ttu-id="fd187-134">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fd187-134">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="fd187-135">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fd187-135">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="fd187-136">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fd187-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
