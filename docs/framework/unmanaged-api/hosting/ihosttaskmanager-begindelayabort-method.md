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
ms.openlocfilehash: ea3269d06fdd3f5a2e365465d45ba6e569127b0a
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842380"
---
# <a name="ihosttaskmanagerbegindelayabort-method"></a><span data-ttu-id="72da3-102">IHostTaskManager::BeginDelayAbort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="72da3-102">IHostTaskManager::BeginDelayAbort Method</span></span>
<span data-ttu-id="72da3-103">Ana bilgisayara, yönetilen kodun geçerli görevin durdurulmayan bir dönem girdiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="72da3-103">Notifies the host that managed code is entering a period in which the current task must not be aborted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72da3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="72da3-104">Syntax</span></span>  
  
```cpp  
HRESULT BeginDelayAbort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="72da3-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="72da3-105">Return Value</span></span>  
  
|<span data-ttu-id="72da3-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="72da3-106">HRESULT</span></span>|<span data-ttu-id="72da3-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="72da3-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="72da3-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="72da3-108">S_OK</span></span>|<span data-ttu-id="72da3-109">`BeginDelayAbort`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="72da3-109">`BeginDelayAbort` returned successfully.</span></span>|  
|<span data-ttu-id="72da3-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="72da3-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="72da3-111">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="72da3-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="72da3-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="72da3-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="72da3-113">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="72da3-113">The call timed out.</span></span>|  
|<span data-ttu-id="72da3-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="72da3-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="72da3-115">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="72da3-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="72da3-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="72da3-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="72da3-117">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="72da3-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="72da3-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="72da3-118">E_FAIL</span></span>|<span data-ttu-id="72da3-119">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="72da3-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="72da3-120">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="72da3-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="72da3-121">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="72da3-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="72da3-122">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="72da3-122">E_UNEXPECTED</span></span>|<span data-ttu-id="72da3-123">`BeginDelayAbort`zaten çağrılmış, ancak buna karşılık gelen [EndDelayAbort](ihosttaskmanager-enddelayabort-method.md) çağrısı henüz alınmadı.</span><span class="sxs-lookup"><span data-stu-id="72da3-123">`BeginDelayAbort` has already been called, but the corresponding call to [EndDelayAbort](ihosttaskmanager-enddelayabort-method.md) has not yet been received.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="72da3-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="72da3-124">Remarks</span></span>  
 <span data-ttu-id="72da3-125">Ana bilgisayar, çağrılana kadar geçerli görevi iptal etmelidir `EndDelayAbort` .</span><span class="sxs-lookup"><span data-stu-id="72da3-125">The host must not abort the current task until `EndDelayAbort` is called.</span></span> <span data-ttu-id="72da3-126">`BeginDelayAbort`Üzerinde araya giren bir çağrı olmadan başka bir çağrı yapılırsa `EndDelayAbort` , ana bilgisayar öğesinden E_UNEXPECTED döndürmelidir `BeginDelayAbort` ve hiçbir işlem yapması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="72da3-126">If another call to `BeginDelayAbort` is made without an intervening call to `EndDelayAbort`, the host should return E_UNEXPECTED from `BeginDelayAbort`, and should take no action.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72da3-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="72da3-127">Requirements</span></span>  
 <span data-ttu-id="72da3-128">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72da3-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72da3-129">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="72da3-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="72da3-130">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="72da3-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="72da3-131">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72da3-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72da3-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="72da3-132">See also</span></span>

- [<span data-ttu-id="72da3-133">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="72da3-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="72da3-134">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="72da3-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="72da3-135">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="72da3-135">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
