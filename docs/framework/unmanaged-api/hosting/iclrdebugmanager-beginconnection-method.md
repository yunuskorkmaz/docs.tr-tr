---
description: ': ICLRDebugManager:: BeginConnection yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 9b4ee64ad96bddfd5d7d650b657c6691b27d8c69
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746145"
---
# <a name="iclrdebugmanagerbeginconnection-method"></a><span data-ttu-id="7f126-103">ICLRDebugManager::BeginConnection Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7f126-103">ICLRDebugManager::BeginConnection Method</span></span>

<span data-ttu-id="7f126-104">Bir görev listesini tanımlayıcı ve kolay bir ad ile ilişkilendirmek için ana bilgisayar ile hata ayıklayıcı arasında yeni bir bağlantı kurar.</span><span class="sxs-lookup"><span data-stu-id="7f126-104">Establishes a new connection between the host and the debugger to associate a list of tasks with an identifier and a friendly name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f126-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7f126-105">Syntax</span></span>  
  
```cpp  
HRESULT BeginConnection (  
    [in] CONNID dwConnectionId,  
    [in, string] wchar_t* szConnectionName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7f126-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7f126-106">Parameters</span></span>  

 `dwConnectionId`  
 <span data-ttu-id="7f126-107">'ndaki Ortak dil çalışma zamanı (CLR) görevlerinin listesiyle ilişkilendirilecek tanımlayıcı.</span><span class="sxs-lookup"><span data-stu-id="7f126-107">[in] An identifier to associate with the list of common language runtime (CLR) tasks.</span></span>  
  
 `szConnectionName`  
 <span data-ttu-id="7f126-108">'ndaki CLR görevlerinin listesiyle ilişkilendirilecek kolay ad.</span><span class="sxs-lookup"><span data-stu-id="7f126-108">[in] A friendly name to associate with the list of CLR tasks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7f126-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7f126-109">Return Value</span></span>  
  
|<span data-ttu-id="7f126-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7f126-110">HRESULT</span></span>|<span data-ttu-id="7f126-111">Description</span><span class="sxs-lookup"><span data-stu-id="7f126-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7f126-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="7f126-112">S_OK</span></span>|<span data-ttu-id="7f126-113">`BeginConnection` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="7f126-113">`BeginConnection` returned successfully.</span></span>|  
|<span data-ttu-id="7f126-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7f126-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7f126-115">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="7f126-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7f126-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7f126-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7f126-117">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="7f126-117">The call timed out.</span></span>|  
|<span data-ttu-id="7f126-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7f126-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7f126-119">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="7f126-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7f126-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7f126-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7f126-121">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="7f126-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7f126-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7f126-122">E_FAIL</span></span>|<span data-ttu-id="7f126-123">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="7f126-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7f126-124">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="7f126-124">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7f126-125">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="7f126-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="7f126-126">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="7f126-126">E_INVALIDARG</span></span>|<span data-ttu-id="7f126-127">`dwConnectionId` sıfır veya `BeginConnection` Bu değeri kullanarak zaten çağırıldı ya da `dwConnectionId` `szConnectionName` null idi.</span><span class="sxs-lookup"><span data-stu-id="7f126-127">`dwConnectionId` was zero, or `BeginConnection` was already called using this `dwConnectionId` value, or `szConnectionName` was null.</span></span>|  
|<span data-ttu-id="7f126-128">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="7f126-128">E_OUTOFMEMORY</span></span>|<span data-ttu-id="7f126-129">Bu bağlantıyla ilişkili görevlerin listesini tutmak için yeterli bellek ayrılamadı.</span><span class="sxs-lookup"><span data-stu-id="7f126-129">Not enough memory could be allocated to hold the list of tasks associated with this connection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7f126-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7f126-130">Remarks</span></span>  

 <span data-ttu-id="7f126-131">[ICLRDebugManager](iclrdebugmanager-interface.md) , `BeginConnection` görev listelerinin tanımlayıcılar ve kolay adlarla ilişkilendirilmesi için, [SetConnectionTasks](iclrdebugmanager-setconnectiontasks-method.md)ve [EndConnection](iclrdebugmanager-endconnection-method.md)olmak üzere üç yöntem sunar.</span><span class="sxs-lookup"><span data-stu-id="7f126-131">[ICLRDebugManager](iclrdebugmanager-interface.md) provides three methods, `BeginConnection`, [SetConnectionTasks](iclrdebugmanager-setconnectiontasks-method.md), and [EndConnection](iclrdebugmanager-endconnection-method.md), for associating task lists with identifiers and friendly names.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="7f126-132">Bu üç yöntemin her görev kümesi için belirli bir sırada çağrılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="7f126-132">These three methods must be called in a specific order for each set of tasks.</span></span> <span data-ttu-id="7f126-133">`BeginConnection` İlk olarak yeni bir bağlantı kurmak için çağırılır.</span><span class="sxs-lookup"><span data-stu-id="7f126-133">`BeginConnection` is called first to establish a new connection.</span></span> <span data-ttu-id="7f126-134">`SetConnectionTasks` ileri, bu bağlantıyla ilişkilendirilecek görev kümesini sağlamak için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="7f126-134">`SetConnectionTasks` is called next to provide the set of tasks to be associated with that connection.</span></span> <span data-ttu-id="7f126-135">`EndConnection` , görev listesi ile tanımlayıcı ve kolay ad arasındaki ilişkiyi kaldırmak için son olarak adlandırılır. Ancak, farklı bağlantılara yönelik çağrılar iç içe olabilir.</span><span class="sxs-lookup"><span data-stu-id="7f126-135">`EndConnection` is called last to remove the association between the task list and the identifier and friendly name.However, calls for different connections can be nested.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f126-136">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7f126-136">Requirements</span></span>  

 <span data-ttu-id="7f126-137">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f126-137">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f126-138">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="7f126-138">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7f126-139">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="7f126-139">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7f126-140">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f126-140">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f126-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7f126-141">See also</span></span>

- [<span data-ttu-id="7f126-142">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7f126-142">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="7f126-143">ICLRDebugManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7f126-143">ICLRDebugManager Interface</span></span>](iclrdebugmanager-interface.md)
- [<span data-ttu-id="7f126-144">EndConnection Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7f126-144">EndConnection Method</span></span>](iclrdebugmanager-endconnection-method.md)
- [<span data-ttu-id="7f126-145">SetConnectionTasks Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7f126-145">SetConnectionTasks Method</span></span>](iclrdebugmanager-setconnectiontasks-method.md)
- [<span data-ttu-id="7f126-146">IHostControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7f126-146">IHostControl Interface</span></span>](ihostcontrol-interface.md)
