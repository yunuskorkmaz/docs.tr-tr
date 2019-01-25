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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 61aa68aff5c55586b9de227a72746b3c02234043
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54727436"
---
# <a name="ihosttaskmanagerbegindelayabort-method"></a><span data-ttu-id="e3e3b-102">IHostTaskManager::BeginDelayAbort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e3e3b-102">IHostTaskManager::BeginDelayAbort Method</span></span>
<span data-ttu-id="e3e3b-103">Yönetilen kod ana bilgisayar, bir süre içinde geçerli görevi iptal gerekir giriyor bildirir.</span><span class="sxs-lookup"><span data-stu-id="e3e3b-103">Notifies the host that managed code is entering a period in which the current task must not be aborted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3e3b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e3e3b-104">Syntax</span></span>  
  
```  
HRESULT BeginDelayAbort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="e3e3b-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e3e3b-105">Return Value</span></span>  
  
|<span data-ttu-id="e3e3b-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e3e3b-106">HRESULT</span></span>|<span data-ttu-id="e3e3b-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e3e3b-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e3e3b-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="e3e3b-108">S_OK</span></span>|<span data-ttu-id="e3e3b-109">`BeginDelayAbort` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="e3e3b-109">`BeginDelayAbort` returned successfully.</span></span>|  
|<span data-ttu-id="e3e3b-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e3e3b-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e3e3b-111">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="e3e3b-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e3e3b-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e3e3b-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e3e3b-113">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="e3e3b-113">The call timed out.</span></span>|  
|<span data-ttu-id="e3e3b-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e3e3b-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e3e3b-115">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="e3e3b-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e3e3b-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e3e3b-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e3e3b-117">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="e3e3b-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e3e3b-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e3e3b-118">E_FAIL</span></span>|<span data-ttu-id="e3e3b-119">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="e3e3b-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e3e3b-120">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="e3e3b-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e3e3b-121">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="e3e3b-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e3e3b-122">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="e3e3b-122">E_UNEXPECTED</span></span>|<span data-ttu-id="e3e3b-123">`BeginDelayAbort` zaten, ancak karşılık gelen çağrı çağrıldıktan [EndDelayAbort](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enddelayabort-method.md) henüz alınmamıştır.</span><span class="sxs-lookup"><span data-stu-id="e3e3b-123">`BeginDelayAbort` has already been called, but the corresponding call to [EndDelayAbort](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enddelayabort-method.md) has not yet been received.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e3e3b-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e3e3b-124">Remarks</span></span>  
 <span data-ttu-id="e3e3b-125">Ana kadar geçerli görevi iptal değil `EndDelayAbort` çağrılır.</span><span class="sxs-lookup"><span data-stu-id="e3e3b-125">The host must not abort the current task until `EndDelayAbort` is called.</span></span> <span data-ttu-id="e3e3b-126">Başka bir çağırırsanız `BeginDelayAbort` bir çağrı göndermelisiniz olmadan yapılan `EndDelayAbort`, konak gelen E_UNEXPECTED döndürmelidir `BeginDelayAbort`ve herhangi bir eylem yapması.</span><span class="sxs-lookup"><span data-stu-id="e3e3b-126">If another call to `BeginDelayAbort` is made without an intervening call to `EndDelayAbort`, the host should return E_UNEXPECTED from `BeginDelayAbort`, and should take no action.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3e3b-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e3e3b-127">Requirements</span></span>  
 <span data-ttu-id="e3e3b-128">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3e3b-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3e3b-129">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e3e3b-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e3e3b-130">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="e3e3b-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e3e3b-131">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3e3b-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3e3b-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e3e3b-132">See also</span></span>
- [<span data-ttu-id="e3e3b-133">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e3e3b-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="e3e3b-134">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e3e3b-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="e3e3b-135">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e3e3b-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="e3e3b-136">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e3e3b-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
