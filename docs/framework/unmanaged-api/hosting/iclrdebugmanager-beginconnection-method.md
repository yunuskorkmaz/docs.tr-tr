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
ms.openlocfilehash: 2ac2b0dde97b883313e1bca17c5e99855484e4aa
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126569"
---
# <a name="iclrdebugmanagerbeginconnection-method"></a><span data-ttu-id="1e865-102">ICLRDebugManager::BeginConnection Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1e865-102">ICLRDebugManager::BeginConnection Method</span></span>
<span data-ttu-id="1e865-103">Bir görev listesini tanımlayıcı ve kolay bir ad ile ilişkilendirmek için ana bilgisayar ile hata ayıklayıcı arasında yeni bir bağlantı kurar.</span><span class="sxs-lookup"><span data-stu-id="1e865-103">Establishes a new connection between the host and the debugger to associate a list of tasks with an identifier and a friendly name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e865-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1e865-104">Syntax</span></span>  
  
```cpp  
HRESULT BeginConnection (  
    [in] CONNID dwConnectionId,  
    [in, string] wchar_t* szConnectionName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1e865-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1e865-105">Parameters</span></span>  
 `dwConnectionId`  
 <span data-ttu-id="1e865-106">'ndaki Ortak dil çalışma zamanı (CLR) görevlerinin listesiyle ilişkilendirilecek tanımlayıcı.</span><span class="sxs-lookup"><span data-stu-id="1e865-106">[in] An identifier to associate with the list of common language runtime (CLR) tasks.</span></span>  
  
 `szConnectionName`  
 <span data-ttu-id="1e865-107">'ndaki CLR görevlerinin listesiyle ilişkilendirilecek kolay ad.</span><span class="sxs-lookup"><span data-stu-id="1e865-107">[in] A friendly name to associate with the list of CLR tasks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1e865-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1e865-108">Return Value</span></span>  
  
|<span data-ttu-id="1e865-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1e865-109">HRESULT</span></span>|<span data-ttu-id="1e865-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1e865-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1e865-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="1e865-111">S_OK</span></span>|<span data-ttu-id="1e865-112">`BeginConnection` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="1e865-112">`BeginConnection` returned successfully.</span></span>|  
|<span data-ttu-id="1e865-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1e865-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1e865-114">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="1e865-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1e865-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1e865-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1e865-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="1e865-116">The call timed out.</span></span>|  
|<span data-ttu-id="1e865-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1e865-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1e865-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="1e865-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1e865-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1e865-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1e865-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="1e865-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1e865-121">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="1e865-121">E_FAIL</span></span>|<span data-ttu-id="1e865-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="1e865-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1e865-123">Bir yöntem E_FAıL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="1e865-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1e865-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="1e865-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="1e865-125">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="1e865-125">E_INVALIDARG</span></span>|<span data-ttu-id="1e865-126">`dwConnectionId` sıfır veya `BeginConnection` zaten bu `dwConnectionId` değeri kullanılarak çağırıldı veya `szConnectionName` null.</span><span class="sxs-lookup"><span data-stu-id="1e865-126">`dwConnectionId` was zero, or `BeginConnection` was already called using this `dwConnectionId` value, or `szConnectionName` was null.</span></span>|  
|<span data-ttu-id="1e865-127">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="1e865-127">E_OUTOFMEMORY</span></span>|<span data-ttu-id="1e865-128">Bu bağlantıyla ilişkili görevlerin listesini tutmak için yeterli bellek ayrılamadı.</span><span class="sxs-lookup"><span data-stu-id="1e865-128">Not enough memory could be allocated to hold the list of tasks associated with this connection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1e865-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1e865-129">Remarks</span></span>  
 <span data-ttu-id="1e865-130">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) , görev listelerinin tanımlayıcılar ve kolay adlarla ilişkilendirilmesi için üç yöntem, `BeginConnection`, [SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)ve [EndConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)sağlar.</span><span class="sxs-lookup"><span data-stu-id="1e865-130">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) provides three methods, `BeginConnection`, [SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md), and [EndConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md), for associating task lists with identifiers and friendly names.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="1e865-131">Bu üç yöntemin her görev kümesi için belirli bir sırada çağrılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1e865-131">These three methods must be called in a specific order for each set of tasks.</span></span> <span data-ttu-id="1e865-132">`BeginConnection` yeni bir bağlantı kurmak için ilk olarak çağırılır.</span><span class="sxs-lookup"><span data-stu-id="1e865-132">`BeginConnection` is called first to establish a new connection.</span></span> <span data-ttu-id="1e865-133">`SetConnectionTasks`, bu bağlantıyla ilişkilendirilecek görev kümesini sağlamak için ileri çağırılır.</span><span class="sxs-lookup"><span data-stu-id="1e865-133">`SetConnectionTasks` is called next to provide the set of tasks to be associated with that connection.</span></span> <span data-ttu-id="1e865-134">`EndConnection` görev listesi ve tanımlayıcı ve kolay ad arasındaki ilişkiyi kaldırmak için son olarak adlandırılır. Ancak, farklı bağlantılara yönelik çağrılar iç içe olabilir.</span><span class="sxs-lookup"><span data-stu-id="1e865-134">`EndConnection` is called last to remove the association between the task list and the identifier and friendly name.However, calls for different connections can be nested.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1e865-135">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1e865-135">Requirements</span></span>  
 <span data-ttu-id="1e865-136">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1e865-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e865-137">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="1e865-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1e865-138">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="1e865-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1e865-139">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e865-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e865-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1e865-140">See also</span></span>

- [<span data-ttu-id="1e865-141">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1e865-141">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="1e865-142">ICLRDebugManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1e865-142">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)
- [<span data-ttu-id="1e865-143">EndConnection Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1e865-143">EndConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)
- [<span data-ttu-id="1e865-144">SetConnectionTasks Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1e865-144">SetConnectionTasks Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)
- [<span data-ttu-id="1e865-145">IHostControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1e865-145">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
