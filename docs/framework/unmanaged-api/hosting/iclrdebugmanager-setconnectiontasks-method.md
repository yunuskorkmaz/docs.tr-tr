---
title: ICLRDebugManager::SetConnectionTasks Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRDebugManager.SetConnectionTasks
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::SetConnectionTasks
helpviewer_keywords:
- SetConnectionTasks method [.NET Framework hosting]
- ICLRDebugManager::SetConnectionTasks method [.NET Framework hosting]
ms.assetid: b38bbc9a-872c-41a9-b8c3-ca011d25456a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 85746f89347c908e60b77435be1fc4bb097c606a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435601"
---
# <a name="iclrdebugmanagersetconnectiontasks-method"></a><span data-ttu-id="037d6-102">ICLRDebugManager::SetConnectionTasks Yöntemi</span><span class="sxs-lookup"><span data-stu-id="037d6-102">ICLRDebugManager::SetConnectionTasks Method</span></span>
<span data-ttu-id="037d6-103">Listesini ilişkilendirir [Iclrtask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) tanımlayıcı ve kolay bir ad ile örnekleri.</span><span class="sxs-lookup"><span data-stu-id="037d6-103">Associates a list of [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instances with an identifier and a friendly name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="037d6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="037d6-104">Syntax</span></span>  
  
```  
HRESULT SetConnectionTasks (  
    [in] CONNID id,  
    [in] DWORD dwCount,  
    [in, size_is(dwCount)] ICLRTask **ppCLRTask  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="037d6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="037d6-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="037d6-106">[in] İle ilişkilendirmek bağlantı için ana bilgisayar özgü tanımlayıcıyı `ppCLRTask` dizi.</span><span class="sxs-lookup"><span data-stu-id="037d6-106">[in] The host-specific identifier for the connection with which to associate the `ppCLRTask` array.</span></span>  
  
 `dwCount`  
 <span data-ttu-id="037d6-107">[in] Üye sayısı `ppCLRTask`.</span><span class="sxs-lookup"><span data-stu-id="037d6-107">[in] The number of members of `ppCLRTask`.</span></span> <span data-ttu-id="037d6-108">Bu sayı sıfırdan büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="037d6-108">This number must be greater than zero.</span></span>  
  
 `ppCLRTask`  
 <span data-ttu-id="037d6-109">[in] Bir dizi `ICLRTask` tarafından tanımlanan bağlantı ilişkilendirmek için işaretçileri `id`.</span><span class="sxs-lookup"><span data-stu-id="037d6-109">[in] An array of `ICLRTask` pointers to associate with the connection identified by `id`.</span></span> <span data-ttu-id="037d6-110">Bu dizi en az bir üye içermelidir.</span><span class="sxs-lookup"><span data-stu-id="037d6-110">This array must contain at least one member.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="037d6-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="037d6-111">Return Value</span></span>  
  
|<span data-ttu-id="037d6-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="037d6-112">HRESULT</span></span>|<span data-ttu-id="037d6-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="037d6-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="037d6-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="037d6-114">S_OK</span></span>|<span data-ttu-id="037d6-115">`SetConnectionTasks` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="037d6-115">`SetConnectionTasks` returned successfully.</span></span>|  
|<span data-ttu-id="037d6-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="037d6-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="037d6-117">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="037d6-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="037d6-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="037d6-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="037d6-119">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="037d6-119">The call timed out.</span></span>|  
|<span data-ttu-id="037d6-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="037d6-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="037d6-121">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="037d6-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="037d6-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="037d6-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="037d6-123">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="037d6-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="037d6-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="037d6-124">E_FAIL</span></span>|<span data-ttu-id="037d6-125">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="037d6-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="037d6-126">CLR, artık bir yöntem E_FAIL döndükten sonra işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="037d6-126">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="037d6-127">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="037d6-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="037d6-128">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="037d6-128">E_INVALIDARG</span></span>|<span data-ttu-id="037d6-129">[BeginConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) bu değeri kullanılarak çağrılmadı `id`, veya `dwCount` veya `id` sıfır ya da öğelerinden biri `ppCLRTask` null.</span><span class="sxs-lookup"><span data-stu-id="037d6-129">[BeginConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) has not been called using this value of `id`, or `dwCount` or `id` is zero, or one of the elements of `ppCLRTask` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="037d6-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="037d6-130">Remarks</span></span>  
 <span data-ttu-id="037d6-131">[Iclrdebugmanager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) üç yöntem sunar `BeginConnection`, `SetConnectionTasks`, ve [EndConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md), görev listeleri tanımlayıcıları ve kolay adlar ile ilişkilendirme.</span><span class="sxs-lookup"><span data-stu-id="037d6-131">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) provides three methods, `BeginConnection`, `SetConnectionTasks`, and [EndConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md), for associating task lists with identifiers and friendly names.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="037d6-132">Bu üç yöntem, her bir dizi görevi için belirli bir sırayla çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="037d6-132">These three methods must be called in a specific order for each set of tasks.</span></span> <span data-ttu-id="037d6-133">`BeginConnection` Yeni bir bağlantı kurmak için önce çağrılır.</span><span class="sxs-lookup"><span data-stu-id="037d6-133">`BeginConnection` is called first to establish a new connection.</span></span> <span data-ttu-id="037d6-134">`SetConnectionTasks` ardından bu bağlantı ile ilişkili görevleri kümesi sağlamak için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="037d6-134">`SetConnectionTasks` is called next to provide the set of tasks to be associated with that connection.</span></span> <span data-ttu-id="037d6-135">`EndConnection` Görev listesi ve tanımlayıcısı ve kolay ad arasındaki ilişkiyi kaldırmak için son çağrılır. Ancak, çağrıları farklı bağlantılar için iç içe.</span><span class="sxs-lookup"><span data-stu-id="037d6-135">`EndConnection` is called last to remove the association between the task list and the identifier and friendly name.However, calls for different connections can be nested.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="037d6-136">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="037d6-136">Requirements</span></span>  
 <span data-ttu-id="037d6-137">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="037d6-137">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="037d6-138">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="037d6-138">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="037d6-139">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="037d6-139">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="037d6-140">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="037d6-140">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="037d6-141">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="037d6-141">See Also</span></span>  
 [<span data-ttu-id="037d6-142">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="037d6-142">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="037d6-143">ICLRDebugManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="037d6-143">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)  
 [<span data-ttu-id="037d6-144">BeginConnection Yöntemi</span><span class="sxs-lookup"><span data-stu-id="037d6-144">BeginConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)  
 [<span data-ttu-id="037d6-145">EndConnection Yöntemi</span><span class="sxs-lookup"><span data-stu-id="037d6-145">EndConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)  
 [<span data-ttu-id="037d6-146">IHostControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="037d6-146">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
