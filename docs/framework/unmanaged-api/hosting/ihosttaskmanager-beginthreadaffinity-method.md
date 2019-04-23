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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59137728"
---
# <a name="ihosttaskmanagerbeginthreadaffinity-method"></a><span data-ttu-id="9bd73-102">IHostTaskManager::BeginThreadAffinity Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9bd73-102">IHostTaskManager::BeginThreadAffinity Method</span></span>
<span data-ttu-id="9bd73-103">Yönetilen kod ana bilgisayar, bir süre içinde geçerli görev için başka bir işletim sistemi iş parçacığı taşınmalıdır değil giriyor bildirir.</span><span class="sxs-lookup"><span data-stu-id="9bd73-103">Notifies the host that managed code is entering a period in which the current task must not be moved to another operating system thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9bd73-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9bd73-104">Syntax</span></span>  
  
```  
HRESULT BeginThreadAffinity ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="9bd73-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9bd73-105">Return Value</span></span>  
  
|<span data-ttu-id="9bd73-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9bd73-106">HRESULT</span></span>|<span data-ttu-id="9bd73-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9bd73-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9bd73-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="9bd73-108">S_OK</span></span>|<span data-ttu-id="9bd73-109">`BeginThreadAffinity` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="9bd73-109">`BeginThreadAffinity` returned successfully.</span></span>|  
|<span data-ttu-id="9bd73-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9bd73-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9bd73-111">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="9bd73-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9bd73-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9bd73-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9bd73-113">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="9bd73-113">The call timed out.</span></span>|  
|<span data-ttu-id="9bd73-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9bd73-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9bd73-115">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="9bd73-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9bd73-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9bd73-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9bd73-117">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="9bd73-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9bd73-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9bd73-118">E_FAIL</span></span>|<span data-ttu-id="9bd73-119">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="9bd73-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9bd73-120">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="9bd73-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9bd73-121">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="9bd73-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9bd73-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9bd73-122">Remarks</span></span>  
 <span data-ttu-id="9bd73-123">CLR genellikle çağrıları `IHostTaskManager::BeginThreadAffinity` çağrı bağlamında <xref:System.Threading.Thread.BeginThreadAffinity%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9bd73-123">The CLR typically calls `IHostTaskManager::BeginThreadAffinity` in the context of a call to <xref:System.Threading.Thread.BeginThreadAffinity%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="9bd73-124">Karşılık gelen bir çağrı yapılır kadar geçerli görevin zamanlanması gerekir değil [Ihosttaskmanager::endthreadaffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md).</span><span class="sxs-lookup"><span data-stu-id="9bd73-124">The current task must not be rescheduled until a corresponding call is made to [IHostTaskManager::EndThreadAffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md).</span></span> <span data-ttu-id="9bd73-125">Görevler, out değiştirilebilir, ancak geri geçiş yaparken, bunlar dışarı geçiş aynı işletim sistemi iş parçacığına atanmalıdır. Yuvalanmış çağrıları `BeginThreadAffinity` çağrı geçerli göreve başvurduğundan, etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="9bd73-125">Tasks can be switched out, but when they are switched back in, they must be assigned to the same operating system thread from which they were switched out. Nested calls to `BeginThreadAffinity` have no effect, because the call refers to the current task.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9bd73-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9bd73-126">Requirements</span></span>  
 <span data-ttu-id="9bd73-127">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9bd73-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9bd73-128">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9bd73-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9bd73-129">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="9bd73-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9bd73-130">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9bd73-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bd73-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9bd73-131">See also</span></span>

- [<span data-ttu-id="9bd73-132">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9bd73-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="9bd73-133">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9bd73-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="9bd73-134">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9bd73-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="9bd73-135">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9bd73-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
