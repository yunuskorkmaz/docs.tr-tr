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
ms.openlocfilehash: f63b761497b3e9a19a9b939b45acf60d5a7d37b0
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504244"
---
# <a name="iclrdebugmanagersetconnectiontasks-method"></a><span data-ttu-id="a1458-102">ICLRDebugManager::SetConnectionTasks Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a1458-102">ICLRDebugManager::SetConnectionTasks Method</span></span>
<span data-ttu-id="a1458-103">[ICLRTask](iclrtask-interface.md) örneklerinin listesini bir tanımlayıcı ve kolay bir ad ile ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="a1458-103">Associates a list of [ICLRTask](iclrtask-interface.md) instances with an identifier and a friendly name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1458-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="a1458-104">Syntax</span></span>  
  
```cpp  
HRESULT SetConnectionTasks (  
    [in] CONNID id,  
    [in] DWORD dwCount,  
    [in, size_is(dwCount)] ICLRTask **ppCLRTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a1458-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a1458-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="a1458-106">'ndaki Dizinin ilişkilendirileceği bağlantı için konağa özgü tanımlayıcı `ppCLRTask` .</span><span class="sxs-lookup"><span data-stu-id="a1458-106">[in] The host-specific identifier for the connection with which to associate the `ppCLRTask` array.</span></span>  
  
 `dwCount`  
 <span data-ttu-id="a1458-107">'ndaki Üyelerinin sayısı `ppCLRTask` .</span><span class="sxs-lookup"><span data-stu-id="a1458-107">[in] The number of members of `ppCLRTask`.</span></span> <span data-ttu-id="a1458-108">Bu sayı sıfırdan büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a1458-108">This number must be greater than zero.</span></span>  
  
 `ppCLRTask`  
 <span data-ttu-id="a1458-109">'ndaki `ICLRTask`Tarafından tanımlanan bağlantıyla ilişkilendirilecek işaretçiler dizisi `id` .</span><span class="sxs-lookup"><span data-stu-id="a1458-109">[in] An array of `ICLRTask` pointers to associate with the connection identified by `id`.</span></span> <span data-ttu-id="a1458-110">Bu dizi en az bir üye içermelidir.</span><span class="sxs-lookup"><span data-stu-id="a1458-110">This array must contain at least one member.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a1458-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a1458-111">Return Value</span></span>  
  
|<span data-ttu-id="a1458-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a1458-112">HRESULT</span></span>|<span data-ttu-id="a1458-113">Description</span><span class="sxs-lookup"><span data-stu-id="a1458-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a1458-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="a1458-114">S_OK</span></span>|<span data-ttu-id="a1458-115">`SetConnectionTasks`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="a1458-115">`SetConnectionTasks` returned successfully.</span></span>|  
|<span data-ttu-id="a1458-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a1458-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a1458-117">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="a1458-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a1458-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a1458-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a1458-119">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="a1458-119">The call timed out.</span></span>|  
|<span data-ttu-id="a1458-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a1458-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a1458-121">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="a1458-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a1458-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a1458-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a1458-123">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="a1458-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a1458-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a1458-124">E_FAIL</span></span>|<span data-ttu-id="a1458-125">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="a1458-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a1458-126">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="a1458-126">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a1458-127">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="a1458-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="a1458-128">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="a1458-128">E_INVALIDARG</span></span>|<span data-ttu-id="a1458-129">[BeginConnection](iclrdebugmanager-beginconnection-method.md) bu değeri `id` veya `dwCount` ya da sıfır veya `id` öğelerinden biri null olan bu değer kullanılarak çağrılmadı `ppCLRTask` .</span><span class="sxs-lookup"><span data-stu-id="a1458-129">[BeginConnection](iclrdebugmanager-beginconnection-method.md) has not been called using this value of `id`, or `dwCount` or `id` is zero, or one of the elements of `ppCLRTask` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a1458-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a1458-130">Remarks</span></span>  
 <span data-ttu-id="a1458-131">[ICLRDebugManager](iclrdebugmanager-interface.md) , `BeginConnection` `SetConnectionTasks` görev listelerinin tanımlayıcılar ve kolay adlarla ilişkilendirilmesi için üç yöntem,, ve [EndConnection](iclrdebugmanager-endconnection-method.md)sağlar.</span><span class="sxs-lookup"><span data-stu-id="a1458-131">[ICLRDebugManager](iclrdebugmanager-interface.md) provides three methods, `BeginConnection`, `SetConnectionTasks`, and [EndConnection](iclrdebugmanager-endconnection-method.md), for associating task lists with identifiers and friendly names.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a1458-132">Bu üç yöntemin her görev kümesi için belirli bir sırada çağrılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a1458-132">These three methods must be called in a specific order for each set of tasks.</span></span> <span data-ttu-id="a1458-133">`BeginConnection`İlk olarak yeni bir bağlantı kurmak için çağırılır.</span><span class="sxs-lookup"><span data-stu-id="a1458-133">`BeginConnection` is called first to establish a new connection.</span></span> <span data-ttu-id="a1458-134">`SetConnectionTasks`ileri, bu bağlantıyla ilişkilendirilecek görev kümesini sağlamak için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="a1458-134">`SetConnectionTasks` is called next to provide the set of tasks to be associated with that connection.</span></span> <span data-ttu-id="a1458-135">`EndConnection`, görev listesi ile tanımlayıcı ve kolay ad arasındaki ilişkiyi kaldırmak için son olarak adlandırılır. Ancak, farklı bağlantılara yönelik çağrılar iç içe olabilir.</span><span class="sxs-lookup"><span data-stu-id="a1458-135">`EndConnection` is called last to remove the association between the task list and the identifier and friendly name.However, calls for different connections can be nested.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1458-136">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a1458-136">Requirements</span></span>  
 <span data-ttu-id="a1458-137">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1458-137">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1458-138">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a1458-138">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a1458-139">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="a1458-139">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a1458-140">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1458-140">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1458-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a1458-141">See also</span></span>

- [<span data-ttu-id="a1458-142">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a1458-142">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="a1458-143">ICLRDebugManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a1458-143">ICLRDebugManager Interface</span></span>](iclrdebugmanager-interface.md)
- [<span data-ttu-id="a1458-144">BeginConnection Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a1458-144">BeginConnection Method</span></span>](iclrdebugmanager-beginconnection-method.md)
- [<span data-ttu-id="a1458-145">EndConnection Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a1458-145">EndConnection Method</span></span>](iclrdebugmanager-endconnection-method.md)
- [<span data-ttu-id="a1458-146">IHostControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a1458-146">IHostControl Interface</span></span>](ihostcontrol-interface.md)
