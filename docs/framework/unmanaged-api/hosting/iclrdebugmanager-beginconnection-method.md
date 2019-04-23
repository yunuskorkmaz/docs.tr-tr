---
title: ICLRDebugManager::BeginConnection Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRDebugManager.BeginConnection
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::BeginConnection
helpviewer_keywords:
- ICLRDebugManager::BeginConnection method [.NET Framework hosting]
- BeginConnection method [.NET Framework hosting]
ms.assetid: bdd98146-ff4d-4150-a264-a4c1a32d31f3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b365aaa13b3070662a74ebcfc914f5ed3d291d76
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59133997"
---
# <a name="iclrdebugmanagerbeginconnection-method"></a><span data-ttu-id="b2914-102">ICLRDebugManager::BeginConnection Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b2914-102">ICLRDebugManager::BeginConnection Method</span></span>
<span data-ttu-id="b2914-103">Konak ve hata ayıklayıcı görevlerinin listesi bir tanımlayıcı ve kolay bir ad ile ilişkilendirmek için arasında yeni bir bağlantı kurar.</span><span class="sxs-lookup"><span data-stu-id="b2914-103">Establishes a new connection between the host and the debugger to associate a list of tasks with an identifier and a friendly name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2914-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b2914-104">Syntax</span></span>  
  
```  
HRESULT BeginConnection (  
    [in] CONNID dwConnectionId,  
    [in, string] wchar_t* szConnectionName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b2914-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b2914-105">Parameters</span></span>  
 `dwConnectionId`  
 <span data-ttu-id="b2914-106">[in] Ortak dil çalışma zamanı (CLR) görev listesi ile ilişkilendirmek için bir tanımlayıcı.</span><span class="sxs-lookup"><span data-stu-id="b2914-106">[in] An identifier to associate with the list of common language runtime (CLR) tasks.</span></span>  
  
 `szConnectionName`  
 <span data-ttu-id="b2914-107">[in] CLR görevlerin listesi ile ilişkilendirmek için bir kolay ad.</span><span class="sxs-lookup"><span data-stu-id="b2914-107">[in] A friendly name to associate with the list of CLR tasks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b2914-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b2914-108">Return Value</span></span>  
  
|<span data-ttu-id="b2914-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b2914-109">HRESULT</span></span>|<span data-ttu-id="b2914-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b2914-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b2914-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="b2914-111">S_OK</span></span>|<span data-ttu-id="b2914-112">`BeginConnection` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="b2914-112">`BeginConnection` returned successfully.</span></span>|  
|<span data-ttu-id="b2914-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b2914-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b2914-114">CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="b2914-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b2914-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b2914-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b2914-116">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="b2914-116">The call timed out.</span></span>|  
|<span data-ttu-id="b2914-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b2914-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b2914-118">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="b2914-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b2914-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b2914-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b2914-120">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="b2914-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b2914-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b2914-121">E_FAIL</span></span>|<span data-ttu-id="b2914-122">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="b2914-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b2914-123">CLR, artık E_FAIL bir yöntemin dönüşünün ardından, işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="b2914-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b2914-124">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="b2914-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="b2914-125">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="b2914-125">E_INVALIDARG</span></span>|<span data-ttu-id="b2914-126">`dwConnectionId` sıfırdan küçük, veya `BeginConnection` bu kullanarak zaten çağrıldı `dwConnectionId` değeri veya `szConnectionName` null idi.</span><span class="sxs-lookup"><span data-stu-id="b2914-126">`dwConnectionId` was zero, or `BeginConnection` was already called using this `dwConnectionId` value, or `szConnectionName` was null.</span></span>|  
|<span data-ttu-id="b2914-127">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="b2914-127">E_OUTOFMEMORY</span></span>|<span data-ttu-id="b2914-128">Bu bağlantıyla ilişkili Görevler listesini tutmak için yeterli bellek ayrılamadı.</span><span class="sxs-lookup"><span data-stu-id="b2914-128">Not enough memory could be allocated to hold the list of tasks associated with this connection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b2914-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b2914-129">Remarks</span></span>  
 <span data-ttu-id="b2914-130">[Iclrdebugmanager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) üç yöntem sunar `BeginConnection`, [SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md), ve [EndConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md), görev listeleri kolay adları ve tanımlayıcıları ile ilişkilendirme.</span><span class="sxs-lookup"><span data-stu-id="b2914-130">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) provides three methods, `BeginConnection`, [SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md), and [EndConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md), for associating task lists with identifiers and friendly names.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b2914-131">Bu üç yöntem, her bir dizi görevi için belirli bir sırayla çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b2914-131">These three methods must be called in a specific order for each set of tasks.</span></span> <span data-ttu-id="b2914-132">`BeginConnection` Yeni bir bağlantı kurmak için önce çağrılır.</span><span class="sxs-lookup"><span data-stu-id="b2914-132">`BeginConnection` is called first to establish a new connection.</span></span> <span data-ttu-id="b2914-133">`SetConnectionTasks` sonraki görevlerin bu bağlantıyla ilişkili olmasını sağlamak için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="b2914-133">`SetConnectionTasks` is called next to provide the set of tasks to be associated with that connection.</span></span> <span data-ttu-id="b2914-134">`EndConnection` Son görev listesi ve tanımlayıcı ile kolay ad arasındaki ilişkiyi kaldırmak için çağrılır. Ancak, farklı bağlantı çağrıları yuvalanabilir.</span><span class="sxs-lookup"><span data-stu-id="b2914-134">`EndConnection` is called last to remove the association between the task list and the identifier and friendly name.However, calls for different connections can be nested.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2914-135">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b2914-135">Requirements</span></span>  
 <span data-ttu-id="b2914-136">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2914-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2914-137">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b2914-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b2914-138">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="b2914-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b2914-139">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2914-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2914-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b2914-140">See also</span></span>

- [<span data-ttu-id="b2914-141">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b2914-141">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="b2914-142">ICLRDebugManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b2914-142">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)
- [<span data-ttu-id="b2914-143">EndConnection Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b2914-143">EndConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)
- [<span data-ttu-id="b2914-144">SetConnectionTasks Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b2914-144">SetConnectionTasks Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)
- [<span data-ttu-id="b2914-145">IHostControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b2914-145">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
