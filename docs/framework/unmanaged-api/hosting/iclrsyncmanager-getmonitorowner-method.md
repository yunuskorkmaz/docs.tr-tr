---
title: ICLRSyncManager::GetMonitorOwner Metodu
ms.date: 03/30/2017
api_name:
- ICLRSyncManager.GetMonitorOwner
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRSyncManager::GetMonitorOwner
helpviewer_keywords:
- ICLRSyncManager::GetMonitorOwner method [.NET Framework hosting]
- GetMonitorOwner method [.NET Framework hosting]
ms.assetid: 840983a4-396d-47b4-86a0-d35f9b437cdb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4b14421bbe71b68ca677cf712512a7f10aa30583
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763632"
---
# <a name="iclrsyncmanagergetmonitorowner-method"></a><span data-ttu-id="2cec0-102">ICLRSyncManager::GetMonitorOwner Metodu</span><span class="sxs-lookup"><span data-stu-id="2cec0-102">ICLRSyncManager::GetMonitorOwner Method</span></span>
<span data-ttu-id="2cec0-103">Alır [Ihosttask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) sahibi tarafından belirtilen tanımlama bilgisinin tanımlanan izleme örneği.</span><span class="sxs-lookup"><span data-stu-id="2cec0-103">Gets the [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance that owns the monitor identified by the specified cookie.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2cec0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2cec0-104">Syntax</span></span>  
  
```  
HRESULT GetMonitorOwner (  
    [in]  SIZE_T     cookie,  
    [out] IHostTask *ppOwnerHostTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2cec0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2cec0-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="2cec0-106">[in] İzleyiciyle ilişkili tanımlama.</span><span class="sxs-lookup"><span data-stu-id="2cec0-106">[in] The cookie associated with the monitor.</span></span>  
  
 `ppOwnerHostTask`  
 <span data-ttu-id="2cec0-107">[out] Bir işaretçi `IHostTask` şu anda sahip olan İzleyici ya da null görev sahipliği varsa.</span><span class="sxs-lookup"><span data-stu-id="2cec0-107">[out] A pointer to the `IHostTask` that currently owns the monitor, or null if no task has ownership.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2cec0-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2cec0-108">Return Value</span></span>  
  
|<span data-ttu-id="2cec0-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2cec0-109">HRESULT</span></span>|<span data-ttu-id="2cec0-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2cec0-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2cec0-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="2cec0-111">S_OK</span></span>|<span data-ttu-id="2cec0-112">`GetMonitorOwner` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="2cec0-112">`GetMonitorOwner` returned successfully.</span></span>|  
|<span data-ttu-id="2cec0-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2cec0-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2cec0-114">CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="2cec0-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2cec0-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2cec0-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2cec0-116">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="2cec0-116">The call timed out.</span></span>|  
|<span data-ttu-id="2cec0-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2cec0-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2cec0-118">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="2cec0-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2cec0-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2cec0-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2cec0-120">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="2cec0-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2cec0-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2cec0-121">E_FAIL</span></span>|<span data-ttu-id="2cec0-122">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="2cec0-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2cec0-123">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="2cec0-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2cec0-124">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="2cec0-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2cec0-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2cec0-125">Remarks</span></span>  
 <span data-ttu-id="2cec0-126">Ana bilgisayar genellikle çağrıları `GetMonitorOwner` kilitlenme algılaması mekanizması bir parçası olarak.</span><span class="sxs-lookup"><span data-stu-id="2cec0-126">The host typically calls `GetMonitorOwner` as part of a deadlock-detection mechanism.</span></span> <span data-ttu-id="2cec0-127">Tanımlama bilgisi için bir çağrı kullanılarak oluşturulduğunda bir izleyiciyle ilişkili [Ihostsyncmanager::createmonitorevent](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmonitorevent-method.md).</span><span class="sxs-lookup"><span data-stu-id="2cec0-127">The cookie is associated with a monitor when it is created by using a call to [IHostSyncManager::CreateMonitorEvent](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmonitorevent-method.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2cec0-128">İzleyici temel olay serbest bırakmak için bir çağrı engelleyebilecek — ancak değil kilitlenme — bu yönteme bir çağrı şu anda yürürlükte izleyen ile ilişkili tanımlama açıksa.</span><span class="sxs-lookup"><span data-stu-id="2cec0-128">A call to release the event underlying the monitor might block—but will not deadlock—if a call to this method is currently in effect on the cookie associated with that monitor.</span></span> <span data-ttu-id="2cec0-129">Bu İzleyici almayı denerseniz diğer görevleri de engelleyebilir.</span><span class="sxs-lookup"><span data-stu-id="2cec0-129">Other tasks might also block if they attempt to acquire this monitor.</span></span>  
  
 <span data-ttu-id="2cec0-130">`GetMonitorOwner` her zaman hemen döndürür ve çağrısı yapıldıktan sonra istediğiniz zaman çağrılabilir `CreateMonitorEvent`.</span><span class="sxs-lookup"><span data-stu-id="2cec0-130">`GetMonitorOwner` always returns immediately and can be called any time after a call to `CreateMonitorEvent`.</span></span> <span data-ttu-id="2cec0-131">Ana görevi, olayda bekleyen beklemeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="2cec0-131">The host does not need to wait until a task is waiting on the event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2cec0-132">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2cec0-132">Requirements</span></span>  
 <span data-ttu-id="2cec0-133">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2cec0-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2cec0-134">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2cec0-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2cec0-135">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="2cec0-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2cec0-136">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2cec0-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cec0-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2cec0-137">See also</span></span>

- [<span data-ttu-id="2cec0-138">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2cec0-138">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="2cec0-139">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2cec0-139">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
