---
title: ICLRSyncManager::GetMonitorOwner Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRSyncManager.GetMonitorOwner
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRSyncManager::GetMonitorOwner
helpviewer_keywords:
- ICLRSyncManager::GetMonitorOwner method [.NET Framework hosting]
- GetMonitorOwner method [.NET Framework hosting]
ms.assetid: 840983a4-396d-47b4-86a0-d35f9b437cdb
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 90fbba9a5aead27d79c5355d69bc12481e826b65
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrsyncmanagergetmonitorowner-method"></a><span data-ttu-id="21b74-102">ICLRSyncManager::GetMonitorOwner Metodu</span><span class="sxs-lookup"><span data-stu-id="21b74-102">ICLRSyncManager::GetMonitorOwner Method</span></span>
<span data-ttu-id="21b74-103">Alır [Ihosttask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) belirtilen tanımlama bilgisi tarafından tanımlanan İzleyici sahibi örneği.</span><span class="sxs-lookup"><span data-stu-id="21b74-103">Gets the [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance that owns the monitor identified by the specified cookie.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21b74-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="21b74-104">Syntax</span></span>  
  
```  
HRESULT GetMonitorOwner (  
    [in]  SIZE_T     cookie,  
    [out] IHostTask *ppOwnerHostTask  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="21b74-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="21b74-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="21b74-106">[in] İzleme ile ilişkili tanımlama.</span><span class="sxs-lookup"><span data-stu-id="21b74-106">[in] The cookie associated with the monitor.</span></span>  
  
 `ppOwnerHostTask`  
 <span data-ttu-id="21b74-107">[out] Bir işaretçi `IHostTask` , şu anda sahibi İzleyici ya da null hiçbir görev sahipliği varsa.</span><span class="sxs-lookup"><span data-stu-id="21b74-107">[out] A pointer to the `IHostTask` that currently owns the monitor, or null if no task has ownership.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="21b74-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="21b74-108">Return Value</span></span>  
  
|<span data-ttu-id="21b74-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="21b74-109">HRESULT</span></span>|<span data-ttu-id="21b74-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="21b74-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="21b74-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="21b74-111">S_OK</span></span>|<span data-ttu-id="21b74-112">`GetMonitorOwner`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="21b74-112">`GetMonitorOwner` returned successfully.</span></span>|  
|<span data-ttu-id="21b74-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="21b74-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="21b74-114">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="21b74-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="21b74-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="21b74-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="21b74-116">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="21b74-116">The call timed out.</span></span>|  
|<span data-ttu-id="21b74-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="21b74-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="21b74-118">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="21b74-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="21b74-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="21b74-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="21b74-120">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="21b74-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="21b74-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="21b74-121">E_FAIL</span></span>|<span data-ttu-id="21b74-122">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="21b74-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="21b74-123">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="21b74-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="21b74-124">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="21b74-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="21b74-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="21b74-125">Remarks</span></span>  
 <span data-ttu-id="21b74-126">Konak genellikle çağırır `GetMonitorOwner` kilitlenme algılama mekanizmasının bir parçası olarak.</span><span class="sxs-lookup"><span data-stu-id="21b74-126">The host typically calls `GetMonitorOwner` as part of a deadlock-detection mechanism.</span></span> <span data-ttu-id="21b74-127">Bir çağrı kullanılarak oluşturulduğunda tanımlama bilgisinin bir izleyici ile ilişkilendirilen [Ihostsyncmanager::createmonitorevent](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmonitorevent-method.md).</span><span class="sxs-lookup"><span data-stu-id="21b74-127">The cookie is associated with a monitor when it is created by using a call to [IHostSyncManager::CreateMonitorEvent](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmonitorevent-method.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="21b74-128">İzleyici temel olay serbest bırakmak için bir çağrı engelleyebilecek — ancak değil kilitlenme — bu yöntem çağrısı şu anda etkin izleyen ile ilişkili tanımlama açıksa.</span><span class="sxs-lookup"><span data-stu-id="21b74-128">A call to release the event underlying the monitor might block—but will not deadlock—if a call to this method is currently in effect on the cookie associated with that monitor.</span></span> <span data-ttu-id="21b74-129">Bu İzleyici edinmeye çalışırsanız başka görevler de engelleyebilir.</span><span class="sxs-lookup"><span data-stu-id="21b74-129">Other tasks might also block if they attempt to acquire this monitor.</span></span>  
  
 <span data-ttu-id="21b74-130">`GetMonitorOwner`her zaman hemen döndürür ve bir çağrı sonra her zaman çağrılabilir `CreateMonitorEvent`.</span><span class="sxs-lookup"><span data-stu-id="21b74-130">`GetMonitorOwner` always returns immediately and can be called any time after a call to `CreateMonitorEvent`.</span></span> <span data-ttu-id="21b74-131">Ana bilgisayar olayda bekliyor. bir görev beklemeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="21b74-131">The host does not need to wait until a task is waiting on the event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21b74-132">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="21b74-132">Requirements</span></span>  
 <span data-ttu-id="21b74-133">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21b74-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21b74-134">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="21b74-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="21b74-135">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="21b74-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="21b74-136">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21b74-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21b74-137">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="21b74-137">See Also</span></span>  
 [<span data-ttu-id="21b74-138">Iclrsyncmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="21b74-138">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="21b74-139">Ihostsyncmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="21b74-139">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
