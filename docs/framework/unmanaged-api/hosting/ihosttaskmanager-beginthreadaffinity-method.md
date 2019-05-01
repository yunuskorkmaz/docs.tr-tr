---
title: IHostTaskManager::BeginThreadAffinity Yöntemi
ms.date: 03/30/2017
api_name:
- IHostTaskManager.BeginThreadAffinity
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::BeginThreadAffinity
helpviewer_keywords:
- IHostTaskManager::BeginThreadAffinity method [.NET Framework hosting]
- BeginThreadAffinity method [.NET Framework hosting]
ms.assetid: fea3ab88-ce41-4c5a-847b-bb78cd748da6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7eb5c7ec85c0adb301fb722155caaed3c14e0e19
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789473"
---
# <a name="ihosttaskmanagerbeginthreadaffinity-method"></a><span data-ttu-id="e61f5-102">IHostTaskManager::BeginThreadAffinity Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e61f5-102">IHostTaskManager::BeginThreadAffinity Method</span></span>
<span data-ttu-id="e61f5-103">Yönetilen kod ana bilgisayar, bir süre içinde geçerli görev için başka bir işletim sistemi iş parçacığı taşınmalıdır değil giriyor bildirir.</span><span class="sxs-lookup"><span data-stu-id="e61f5-103">Notifies the host that managed code is entering a period in which the current task must not be moved to another operating system thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e61f5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e61f5-104">Syntax</span></span>  
  
```  
HRESULT BeginThreadAffinity ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="e61f5-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e61f5-105">Return Value</span></span>  
  
|<span data-ttu-id="e61f5-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e61f5-106">HRESULT</span></span>|<span data-ttu-id="e61f5-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e61f5-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e61f5-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="e61f5-108">S_OK</span></span>|<span data-ttu-id="e61f5-109">`BeginThreadAffinity` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="e61f5-109">`BeginThreadAffinity` returned successfully.</span></span>|  
|<span data-ttu-id="e61f5-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e61f5-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e61f5-111">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="e61f5-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e61f5-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e61f5-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e61f5-113">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="e61f5-113">The call timed out.</span></span>|  
|<span data-ttu-id="e61f5-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e61f5-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e61f5-115">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="e61f5-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e61f5-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e61f5-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e61f5-117">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="e61f5-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e61f5-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e61f5-118">E_FAIL</span></span>|<span data-ttu-id="e61f5-119">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="e61f5-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e61f5-120">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="e61f5-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e61f5-121">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="e61f5-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e61f5-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e61f5-122">Remarks</span></span>  
 <span data-ttu-id="e61f5-123">CLR genellikle çağrıları `IHostTaskManager::BeginThreadAffinity` çağrı bağlamında <xref:System.Threading.Thread.BeginThreadAffinity%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e61f5-123">The CLR typically calls `IHostTaskManager::BeginThreadAffinity` in the context of a call to <xref:System.Threading.Thread.BeginThreadAffinity%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e61f5-124">Karşılık gelen bir çağrı yapılır kadar geçerli görevin zamanlanması gerekir değil [Ihosttaskmanager::endthreadaffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md).</span><span class="sxs-lookup"><span data-stu-id="e61f5-124">The current task must not be rescheduled until a corresponding call is made to [IHostTaskManager::EndThreadAffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md).</span></span> <span data-ttu-id="e61f5-125">Görevler, out değiştirilebilir, ancak geri geçiş yaparken, bunlar dışarı geçiş aynı işletim sistemi iş parçacığına atanmalıdır. Yuvalanmış çağrıları `BeginThreadAffinity` çağrı geçerli göreve başvurduğundan, etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="e61f5-125">Tasks can be switched out, but when they are switched back in, they must be assigned to the same operating system thread from which they were switched out. Nested calls to `BeginThreadAffinity` have no effect, because the call refers to the current task.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e61f5-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e61f5-126">Requirements</span></span>  
 <span data-ttu-id="e61f5-127">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e61f5-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e61f5-128">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e61f5-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e61f5-129">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="e61f5-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e61f5-130">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e61f5-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e61f5-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e61f5-131">See also</span></span>

- [<span data-ttu-id="e61f5-132">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e61f5-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="e61f5-133">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e61f5-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="e61f5-134">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e61f5-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="e61f5-135">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e61f5-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
