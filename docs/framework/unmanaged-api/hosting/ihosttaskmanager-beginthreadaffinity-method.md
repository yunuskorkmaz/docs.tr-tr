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
ms.openlocfilehash: 67a133604e269b8c20dc8640b91e378c498cf038
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54745590"
---
# <a name="ihosttaskmanagerbeginthreadaffinity-method"></a><span data-ttu-id="77682-102">IHostTaskManager::BeginThreadAffinity Yöntemi</span><span class="sxs-lookup"><span data-stu-id="77682-102">IHostTaskManager::BeginThreadAffinity Method</span></span>
<span data-ttu-id="77682-103">Yönetilen kod ana bilgisayar, bir süre içinde geçerli görev için başka bir işletim sistemi iş parçacığı taşınmalıdır değil giriyor bildirir.</span><span class="sxs-lookup"><span data-stu-id="77682-103">Notifies the host that managed code is entering a period in which the current task must not be moved to another operating system thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77682-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="77682-104">Syntax</span></span>  
  
```  
HRESULT BeginThreadAffinity ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="77682-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="77682-105">Return Value</span></span>  
  
|<span data-ttu-id="77682-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="77682-106">HRESULT</span></span>|<span data-ttu-id="77682-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="77682-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="77682-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="77682-108">S_OK</span></span>|<span data-ttu-id="77682-109">`BeginThreadAffinity` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="77682-109">`BeginThreadAffinity` returned successfully.</span></span>|  
|<span data-ttu-id="77682-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="77682-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="77682-111">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="77682-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="77682-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="77682-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="77682-113">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="77682-113">The call timed out.</span></span>|  
|<span data-ttu-id="77682-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="77682-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="77682-115">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="77682-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="77682-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="77682-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="77682-117">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="77682-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="77682-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="77682-118">E_FAIL</span></span>|<span data-ttu-id="77682-119">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="77682-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="77682-120">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="77682-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="77682-121">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="77682-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="77682-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="77682-122">Remarks</span></span>  
 <span data-ttu-id="77682-123">CLR genellikle çağrıları `IHostTaskManager::BeginThreadAffinity` çağrı bağlamında <xref:System.Threading.Thread.BeginThreadAffinity%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="77682-123">The CLR typically calls `IHostTaskManager::BeginThreadAffinity` in the context of a call to <xref:System.Threading.Thread.BeginThreadAffinity%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="77682-124">Karşılık gelen bir çağrı yapılır kadar geçerli görevin zamanlanması gerekir değil [Ihosttaskmanager::endthreadaffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md).</span><span class="sxs-lookup"><span data-stu-id="77682-124">The current task must not be rescheduled until a corresponding call is made to [IHostTaskManager::EndThreadAffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md).</span></span> <span data-ttu-id="77682-125">Görevler, out değiştirilebilir, ancak geri geçiş yaparken, bunlar dışarı geçiş aynı işletim sistemi iş parçacığına atanmalıdır. Yuvalanmış çağrıları `BeginThreadAffinity` çağrı geçerli göreve başvurduğundan, etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="77682-125">Tasks can be switched out, but when they are switched back in, they must be assigned to the same operating system thread from which they were switched out. Nested calls to `BeginThreadAffinity` have no effect, because the call refers to the current task.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77682-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="77682-126">Requirements</span></span>  
 <span data-ttu-id="77682-127">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77682-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77682-128">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="77682-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="77682-129">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="77682-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="77682-130">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77682-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77682-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="77682-131">See also</span></span>
- [<span data-ttu-id="77682-132">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="77682-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="77682-133">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="77682-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="77682-134">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="77682-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="77682-135">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="77682-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
