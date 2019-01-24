---
title: ICLRDebugManager::EndConnection Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRDebugManager.EndConnection
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::EndConnection
helpviewer_keywords:
- ICLRDebugManager::EndConnection method [.NET Framework hosting]
- EndConnection method [.NET Framework hosting]
ms.assetid: 89dc7363-2f29-4eb2-8f23-fccdda6a76a6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 914b1710bee3ce6e2aaaf756ae4e32d8041d064f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54601733"
---
# <a name="iclrdebugmanagerendconnection-method"></a><span data-ttu-id="e46fb-102">ICLRDebugManager::EndConnection Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e46fb-102">ICLRDebugManager::EndConnection Method</span></span>
<span data-ttu-id="e46fb-103">Görevlerin bir listesi ve tanımlayıcı bir kolay ad arasındaki ilişkiyi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="e46fb-103">Removes the association between a list of tasks and an identifier and a friendly name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e46fb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e46fb-104">Syntax</span></span>  
  
```  
HRESULT EndConnection (  
    [in] CONNID dwConnectionId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e46fb-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e46fb-105">Parameters</span></span>  
 `dwConnectionId`  
 <span data-ttu-id="e46fb-106">[in] Bağlantı ve ilişkili ortak dil çalışma zamanı (CLR) görev listesi konağa özgü tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="e46fb-106">[in] The host-specific identifier for the connection and the associated list of common language runtime (CLR) tasks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e46fb-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e46fb-107">Return Value</span></span>  
  
|<span data-ttu-id="e46fb-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e46fb-108">HRESULT</span></span>|<span data-ttu-id="e46fb-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e46fb-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e46fb-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="e46fb-110">S_OK</span></span>|<span data-ttu-id="e46fb-111">`EndConnection` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="e46fb-111">`EndConnection` returned successfully.</span></span>|  
|<span data-ttu-id="e46fb-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e46fb-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e46fb-113">CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="e46fb-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e46fb-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e46fb-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e46fb-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="e46fb-115">The call timed out.</span></span>|  
|<span data-ttu-id="e46fb-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e46fb-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e46fb-117">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="e46fb-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e46fb-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e46fb-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e46fb-119">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="e46fb-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e46fb-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e46fb-120">E_FAIL</span></span>|<span data-ttu-id="e46fb-121">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="e46fb-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e46fb-122">CLR, artık E_FAIL bir yöntemin dönüşünün ardından, işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="e46fb-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e46fb-123">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="e46fb-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e46fb-124">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="e46fb-124">E_INVALIDARG</span></span>|<span data-ttu-id="e46fb-125">[BeginConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) kullanarak asla çağrıldı `dwConnectionId`, veya `dwConnectionId` sıfırdan küçük.</span><span class="sxs-lookup"><span data-stu-id="e46fb-125">[BeginConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) was never called using `dwConnectionId`, or `dwConnectionId` was zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e46fb-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e46fb-126">Remarks</span></span>  
 <span data-ttu-id="e46fb-127">[Iclrdebugmanager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) üç yöntem sunar `BeginConnection`, [SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md), ve `EndConnection`, görev listeleri kolay adları ve tanımlayıcıları ile ilişkilendirme.</span><span class="sxs-lookup"><span data-stu-id="e46fb-127">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) provides three methods, `BeginConnection`, [SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md), and `EndConnection`, for associating task lists with identifiers and friendly names.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e46fb-128">Bu üç yöntem, her bir dizi görevi için belirli bir sırayla çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e46fb-128">These three methods must be called in a specific order for each set of tasks.</span></span> <span data-ttu-id="e46fb-129">`BeginConnection` Yeni bir bağlantı kurmak için önce çağrılır.</span><span class="sxs-lookup"><span data-stu-id="e46fb-129">`BeginConnection` is called first to establish a new connection.</span></span> <span data-ttu-id="e46fb-130">`SetConnectionTasks` sonraki görevlerin bu bağlantıyla ilişkili olmasını sağlamak için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="e46fb-130">`SetConnectionTasks` is called next to provide the set of tasks to be associated with that connection.</span></span> <span data-ttu-id="e46fb-131">`EndConnection` Son görev listesi ve tanımlayıcı ile kolay ad arasındaki ilişkiyi kaldırmak için çağrılır. Ancak, farklı bağlantı çağrıları yuvalanabilir.</span><span class="sxs-lookup"><span data-stu-id="e46fb-131">`EndConnection` is called last to remove the association between the task list and the identifier and friendly name.However, calls for different connections can be nested.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e46fb-132">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e46fb-132">Requirements</span></span>  
 <span data-ttu-id="e46fb-133">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e46fb-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e46fb-134">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e46fb-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e46fb-135">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="e46fb-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e46fb-136">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e46fb-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e46fb-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e46fb-137">See also</span></span>
- [<span data-ttu-id="e46fb-138">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e46fb-138">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="e46fb-139">ICLRDebugManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e46fb-139">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)
- [<span data-ttu-id="e46fb-140">BeginConnection Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e46fb-140">BeginConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)
- [<span data-ttu-id="e46fb-141">SetConnectionTasks Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e46fb-141">SetConnectionTasks Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)
- [<span data-ttu-id="e46fb-142">IHostControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e46fb-142">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
