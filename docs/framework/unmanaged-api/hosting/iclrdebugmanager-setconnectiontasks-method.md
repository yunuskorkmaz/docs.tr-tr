---
description: ': ICLRDebugManager:: SetConnectionTasks yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 851b3f54cc5599781596314dfb70296a3d86491a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99728749"
---
# <a name="iclrdebugmanagersetconnectiontasks-method"></a><span data-ttu-id="5d6d0-103">ICLRDebugManager::SetConnectionTasks Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5d6d0-103">ICLRDebugManager::SetConnectionTasks Method</span></span>

<span data-ttu-id="5d6d0-104">[ICLRTask](iclrtask-interface.md) örneklerinin listesini bir tanımlayıcı ve kolay bir ad ile ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="5d6d0-104">Associates a list of [ICLRTask](iclrtask-interface.md) instances with an identifier and a friendly name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d6d0-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5d6d0-105">Syntax</span></span>  
  
```cpp  
HRESULT SetConnectionTasks (  
    [in] CONNID id,  
    [in] DWORD dwCount,  
    [in, size_is(dwCount)] ICLRTask **ppCLRTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5d6d0-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5d6d0-106">Parameters</span></span>  

 `id`  
 <span data-ttu-id="5d6d0-107">'ndaki Dizinin ilişkilendirileceği bağlantı için konağa özgü tanımlayıcı `ppCLRTask` .</span><span class="sxs-lookup"><span data-stu-id="5d6d0-107">[in] The host-specific identifier for the connection with which to associate the `ppCLRTask` array.</span></span>  
  
 `dwCount`  
 <span data-ttu-id="5d6d0-108">'ndaki Üyelerinin sayısı `ppCLRTask` .</span><span class="sxs-lookup"><span data-stu-id="5d6d0-108">[in] The number of members of `ppCLRTask`.</span></span> <span data-ttu-id="5d6d0-109">Bu sayı sıfırdan büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5d6d0-109">This number must be greater than zero.</span></span>  
  
 `ppCLRTask`  
 <span data-ttu-id="5d6d0-110">'ndaki `ICLRTask` Tarafından tanımlanan bağlantıyla ilişkilendirilecek işaretçiler dizisi `id` .</span><span class="sxs-lookup"><span data-stu-id="5d6d0-110">[in] An array of `ICLRTask` pointers to associate with the connection identified by `id`.</span></span> <span data-ttu-id="5d6d0-111">Bu dizi en az bir üye içermelidir.</span><span class="sxs-lookup"><span data-stu-id="5d6d0-111">This array must contain at least one member.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5d6d0-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5d6d0-112">Return Value</span></span>  
  
|<span data-ttu-id="5d6d0-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5d6d0-113">HRESULT</span></span>|<span data-ttu-id="5d6d0-114">Description</span><span class="sxs-lookup"><span data-stu-id="5d6d0-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5d6d0-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="5d6d0-115">S_OK</span></span>|<span data-ttu-id="5d6d0-116">`SetConnectionTasks` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="5d6d0-116">`SetConnectionTasks` returned successfully.</span></span>|  
|<span data-ttu-id="5d6d0-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5d6d0-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5d6d0-118">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="5d6d0-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5d6d0-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5d6d0-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5d6d0-120">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="5d6d0-120">The call timed out.</span></span>|  
|<span data-ttu-id="5d6d0-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5d6d0-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5d6d0-122">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="5d6d0-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5d6d0-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5d6d0-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5d6d0-124">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="5d6d0-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5d6d0-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5d6d0-125">E_FAIL</span></span>|<span data-ttu-id="5d6d0-126">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="5d6d0-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5d6d0-127">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="5d6d0-127">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5d6d0-128">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="5d6d0-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="5d6d0-129">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="5d6d0-129">E_INVALIDARG</span></span>|<span data-ttu-id="5d6d0-130">[BeginConnection](iclrdebugmanager-beginconnection-method.md) bu değeri `id` veya `dwCount` ya da sıfır veya `id` öğelerinden biri null olan bu değer kullanılarak çağrılmadı `ppCLRTask` .</span><span class="sxs-lookup"><span data-stu-id="5d6d0-130">[BeginConnection](iclrdebugmanager-beginconnection-method.md) has not been called using this value of `id`, or `dwCount` or `id` is zero, or one of the elements of `ppCLRTask` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5d6d0-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5d6d0-131">Remarks</span></span>  

 <span data-ttu-id="5d6d0-132">[ICLRDebugManager](iclrdebugmanager-interface.md) , `BeginConnection` `SetConnectionTasks` görev listelerinin tanımlayıcılar ve kolay adlarla ilişkilendirilmesi için üç yöntem,, ve [EndConnection](iclrdebugmanager-endconnection-method.md)sağlar.</span><span class="sxs-lookup"><span data-stu-id="5d6d0-132">[ICLRDebugManager](iclrdebugmanager-interface.md) provides three methods, `BeginConnection`, `SetConnectionTasks`, and [EndConnection](iclrdebugmanager-endconnection-method.md), for associating task lists with identifiers and friendly names.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="5d6d0-133">Bu üç yöntemin her görev kümesi için belirli bir sırada çağrılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="5d6d0-133">These three methods must be called in a specific order for each set of tasks.</span></span> <span data-ttu-id="5d6d0-134">`BeginConnection` İlk olarak yeni bir bağlantı kurmak için çağırılır.</span><span class="sxs-lookup"><span data-stu-id="5d6d0-134">`BeginConnection` is called first to establish a new connection.</span></span> <span data-ttu-id="5d6d0-135">`SetConnectionTasks` ileri, bu bağlantıyla ilişkilendirilecek görev kümesini sağlamak için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="5d6d0-135">`SetConnectionTasks` is called next to provide the set of tasks to be associated with that connection.</span></span> <span data-ttu-id="5d6d0-136">`EndConnection` , görev listesi ile tanımlayıcı ve kolay ad arasındaki ilişkiyi kaldırmak için son olarak adlandırılır. Ancak, farklı bağlantılara yönelik çağrılar iç içe olabilir.</span><span class="sxs-lookup"><span data-stu-id="5d6d0-136">`EndConnection` is called last to remove the association between the task list and the identifier and friendly name.However, calls for different connections can be nested.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d6d0-137">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5d6d0-137">Requirements</span></span>  

 <span data-ttu-id="5d6d0-138">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d6d0-138">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d6d0-139">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="5d6d0-139">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5d6d0-140">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="5d6d0-140">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5d6d0-141">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d6d0-141">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d6d0-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5d6d0-142">See also</span></span>

- [<span data-ttu-id="5d6d0-143">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5d6d0-143">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="5d6d0-144">ICLRDebugManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5d6d0-144">ICLRDebugManager Interface</span></span>](iclrdebugmanager-interface.md)
- [<span data-ttu-id="5d6d0-145">BeginConnection Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5d6d0-145">BeginConnection Method</span></span>](iclrdebugmanager-beginconnection-method.md)
- [<span data-ttu-id="5d6d0-146">EndConnection Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5d6d0-146">EndConnection Method</span></span>](iclrdebugmanager-endconnection-method.md)
- [<span data-ttu-id="5d6d0-147">IHostControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5d6d0-147">IHostControl Interface</span></span>](ihostcontrol-interface.md)
