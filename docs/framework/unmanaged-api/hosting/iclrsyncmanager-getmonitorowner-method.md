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
ms.openlocfilehash: 3aec11674275769bb5c4b68521a40a72a1d68a22
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124677"
---
# <a name="iclrsyncmanagergetmonitorowner-method"></a><span data-ttu-id="64d9f-102">ICLRSyncManager::GetMonitorOwner Metodu</span><span class="sxs-lookup"><span data-stu-id="64d9f-102">ICLRSyncManager::GetMonitorOwner Method</span></span>
<span data-ttu-id="64d9f-103">Belirtilen tanımlama bilgisi tarafından tanımlanan izleyicinin sahibi olan [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) örneğini alır.</span><span class="sxs-lookup"><span data-stu-id="64d9f-103">Gets the [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance that owns the monitor identified by the specified cookie.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64d9f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="64d9f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMonitorOwner (  
    [in]  SIZE_T     cookie,  
    [out] IHostTask *ppOwnerHostTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="64d9f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="64d9f-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="64d9f-106">'ndaki İzleyiciyle ilişkili tanımlama bilgisi.</span><span class="sxs-lookup"><span data-stu-id="64d9f-106">[in] The cookie associated with the monitor.</span></span>  
  
 `ppOwnerHostTask`  
 <span data-ttu-id="64d9f-107">dışı Şu anda izleyicinin sahip olduğu `IHostTask` bir işaretçi veya hiçbir görevin sahiplik yoksa null.</span><span class="sxs-lookup"><span data-stu-id="64d9f-107">[out] A pointer to the `IHostTask` that currently owns the monitor, or null if no task has ownership.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="64d9f-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="64d9f-108">Return Value</span></span>  
  
|<span data-ttu-id="64d9f-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="64d9f-109">HRESULT</span></span>|<span data-ttu-id="64d9f-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="64d9f-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="64d9f-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="64d9f-111">S_OK</span></span>|<span data-ttu-id="64d9f-112">`GetMonitorOwner` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="64d9f-112">`GetMonitorOwner` returned successfully.</span></span>|  
|<span data-ttu-id="64d9f-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="64d9f-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="64d9f-114">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="64d9f-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="64d9f-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="64d9f-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="64d9f-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="64d9f-116">The call timed out.</span></span>|  
|<span data-ttu-id="64d9f-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="64d9f-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="64d9f-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="64d9f-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="64d9f-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="64d9f-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="64d9f-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="64d9f-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="64d9f-121">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="64d9f-121">E_FAIL</span></span>|<span data-ttu-id="64d9f-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="64d9f-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="64d9f-123">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="64d9f-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="64d9f-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="64d9f-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="64d9f-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="64d9f-125">Remarks</span></span>  
 <span data-ttu-id="64d9f-126">Konak genellikle kilitlenme algılama mekanizmasının bir parçası olarak `GetMonitorOwner` çağırır.</span><span class="sxs-lookup"><span data-stu-id="64d9f-126">The host typically calls `GetMonitorOwner` as part of a deadlock-detection mechanism.</span></span> <span data-ttu-id="64d9f-127">Tanımlama bilgisi [IHostSyncManager:: CreateMonitorEvent](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmonitorevent-method.md)çağrısı kullanılarak oluşturulduğunda bir izleyici ile ilişkilendirilir.</span><span class="sxs-lookup"><span data-stu-id="64d9f-127">The cookie is associated with a monitor when it is created by using a call to [IHostSyncManager::CreateMonitorEvent](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmonitorevent-method.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="64d9f-128">İzlemeyi izleyen olayı serbest bırakma çağrısı, bu yönteme yönelik bir çağrı Şu anda bu izleyiciyle ilişkili tanımlama bilgisinde etkinse engelleyebilir, ancak kilitlenmeyecektir —.</span><span class="sxs-lookup"><span data-stu-id="64d9f-128">A call to release the event underlying the monitor might block—but will not deadlock—if a call to this method is currently in effect on the cookie associated with that monitor.</span></span> <span data-ttu-id="64d9f-129">Diğer görevler de bu izleyiciyi almayı deneseler de engelleyebilirler.</span><span class="sxs-lookup"><span data-stu-id="64d9f-129">Other tasks might also block if they attempt to acquire this monitor.</span></span>  
  
 <span data-ttu-id="64d9f-130">`GetMonitorOwner` her zaman hemen döndürülür ve `CreateMonitorEvent`çağrısından sonra herhangi bir zaman çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="64d9f-130">`GetMonitorOwner` always returns immediately and can be called any time after a call to `CreateMonitorEvent`.</span></span> <span data-ttu-id="64d9f-131">Konağın, bir görevin olayda beklenene kadar beklemesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="64d9f-131">The host does not need to wait until a task is waiting on the event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64d9f-132">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="64d9f-132">Requirements</span></span>  
 <span data-ttu-id="64d9f-133">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="64d9f-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64d9f-134">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="64d9f-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="64d9f-135">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="64d9f-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="64d9f-136">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64d9f-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64d9f-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="64d9f-137">See also</span></span>

- [<span data-ttu-id="64d9f-138">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="64d9f-138">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="64d9f-139">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="64d9f-139">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
