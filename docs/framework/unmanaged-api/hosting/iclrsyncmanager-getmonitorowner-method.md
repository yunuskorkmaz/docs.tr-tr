---
description: ': ICLRSyncManager:: Getmonitortorowner yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 67fb966c415009236cabef5e6b4d27cbb90d50ac
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785035"
---
# <a name="iclrsyncmanagergetmonitorowner-method"></a><span data-ttu-id="74099-103">ICLRSyncManager::GetMonitorOwner Metodu</span><span class="sxs-lookup"><span data-stu-id="74099-103">ICLRSyncManager::GetMonitorOwner Method</span></span>

<span data-ttu-id="74099-104">Belirtilen tanımlama bilgisi tarafından tanımlanan izleyicinin sahibi olan [IHostTask](ihosttask-interface.md) örneğini alır.</span><span class="sxs-lookup"><span data-stu-id="74099-104">Gets the [IHostTask](ihosttask-interface.md) instance that owns the monitor identified by the specified cookie.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74099-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="74099-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMonitorOwner (  
    [in]  SIZE_T     cookie,  
    [out] IHostTask *ppOwnerHostTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="74099-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="74099-106">Parameters</span></span>  

 `cookie`  
 <span data-ttu-id="74099-107">'ndaki İzleyiciyle ilişkili tanımlama bilgisi.</span><span class="sxs-lookup"><span data-stu-id="74099-107">[in] The cookie associated with the monitor.</span></span>  
  
 `ppOwnerHostTask`  
 <span data-ttu-id="74099-108">dışı `IHostTask` Şu anda izleyicisine sahip olan bir işaretçi veya hiçbir görevin sahipliği yoksa null.</span><span class="sxs-lookup"><span data-stu-id="74099-108">[out] A pointer to the `IHostTask` that currently owns the monitor, or null if no task has ownership.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="74099-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="74099-109">Return Value</span></span>  
  
|<span data-ttu-id="74099-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="74099-110">HRESULT</span></span>|<span data-ttu-id="74099-111">Description</span><span class="sxs-lookup"><span data-stu-id="74099-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="74099-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="74099-112">S_OK</span></span>|<span data-ttu-id="74099-113">`GetMonitorOwner` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="74099-113">`GetMonitorOwner` returned successfully.</span></span>|  
|<span data-ttu-id="74099-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="74099-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="74099-115">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="74099-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="74099-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="74099-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="74099-117">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="74099-117">The call timed out.</span></span>|  
|<span data-ttu-id="74099-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="74099-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="74099-119">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="74099-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="74099-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="74099-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="74099-121">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="74099-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="74099-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="74099-122">E_FAIL</span></span>|<span data-ttu-id="74099-123">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="74099-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="74099-124">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="74099-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="74099-125">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="74099-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="74099-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="74099-126">Remarks</span></span>  

 <span data-ttu-id="74099-127">Ana bilgisayar genellikle `GetMonitorOwner` kilitlenme algılama mekanizmanın bir parçası olarak çağırır.</span><span class="sxs-lookup"><span data-stu-id="74099-127">The host typically calls `GetMonitorOwner` as part of a deadlock-detection mechanism.</span></span> <span data-ttu-id="74099-128">Tanımlama bilgisi [IHostSyncManager:: CreateMonitorEvent](ihostsyncmanager-createmonitorevent-method.md)çağrısı kullanılarak oluşturulduğunda bir izleyici ile ilişkilendirilir.</span><span class="sxs-lookup"><span data-stu-id="74099-128">The cookie is associated with a monitor when it is created by using a call to [IHostSyncManager::CreateMonitorEvent](ihostsyncmanager-createmonitorevent-method.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="74099-129">İzlemeyi izleyen olayı serbest bırakma çağrısı, bu yönteme yönelik bir çağrı Şu anda bu izleyiciyle ilişkili tanımlama bilgisinde etkinse engelleyebilir, ancak kilitlenmeyecektir —.</span><span class="sxs-lookup"><span data-stu-id="74099-129">A call to release the event underlying the monitor might block—but will not deadlock—if a call to this method is currently in effect on the cookie associated with that monitor.</span></span> <span data-ttu-id="74099-130">Diğer görevler de bu izleyiciyi almayı deneseler de engelleyebilirler.</span><span class="sxs-lookup"><span data-stu-id="74099-130">Other tasks might also block if they attempt to acquire this monitor.</span></span>  
  
 <span data-ttu-id="74099-131">`GetMonitorOwner` her zaman hemen döndürür ve çağrısından sonra herhangi bir zaman çağrılabilir `CreateMonitorEvent` .</span><span class="sxs-lookup"><span data-stu-id="74099-131">`GetMonitorOwner` always returns immediately and can be called any time after a call to `CreateMonitorEvent`.</span></span> <span data-ttu-id="74099-132">Konağın, bir görevin olayda beklenene kadar beklemesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="74099-132">The host does not need to wait until a task is waiting on the event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74099-133">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="74099-133">Requirements</span></span>  

 <span data-ttu-id="74099-134">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74099-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74099-135">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="74099-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="74099-136">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="74099-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="74099-137">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74099-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74099-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="74099-138">See also</span></span>

- [<span data-ttu-id="74099-139">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="74099-139">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="74099-140">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="74099-140">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
