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
ms.openlocfilehash: 98e4efe149cab1b822c9993e4df28806f773c61d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504257"
---
# <a name="iclrdebugmanagerbeginconnection-method"></a><span data-ttu-id="6c7b3-102">ICLRDebugManager::BeginConnection Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6c7b3-102">ICLRDebugManager::BeginConnection Method</span></span>
<span data-ttu-id="6c7b3-103">Bir görev listesini tanımlayıcı ve kolay bir ad ile ilişkilendirmek için ana bilgisayar ile hata ayıklayıcı arasında yeni bir bağlantı kurar.</span><span class="sxs-lookup"><span data-stu-id="6c7b3-103">Establishes a new connection between the host and the debugger to associate a list of tasks with an identifier and a friendly name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c7b3-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="6c7b3-104">Syntax</span></span>  
  
```cpp  
HRESULT BeginConnection (  
    [in] CONNID dwConnectionId,  
    [in, string] wchar_t* szConnectionName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6c7b3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6c7b3-105">Parameters</span></span>  
 `dwConnectionId`  
 <span data-ttu-id="6c7b3-106">'ndaki Ortak dil çalışma zamanı (CLR) görevlerinin listesiyle ilişkilendirilecek tanımlayıcı.</span><span class="sxs-lookup"><span data-stu-id="6c7b3-106">[in] An identifier to associate with the list of common language runtime (CLR) tasks.</span></span>  
  
 `szConnectionName`  
 <span data-ttu-id="6c7b3-107">'ndaki CLR görevlerinin listesiyle ilişkilendirilecek kolay ad.</span><span class="sxs-lookup"><span data-stu-id="6c7b3-107">[in] A friendly name to associate with the list of CLR tasks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6c7b3-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="6c7b3-108">Return Value</span></span>  
  
|<span data-ttu-id="6c7b3-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6c7b3-109">HRESULT</span></span>|<span data-ttu-id="6c7b3-110">Description</span><span class="sxs-lookup"><span data-stu-id="6c7b3-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6c7b3-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="6c7b3-111">S_OK</span></span>|<span data-ttu-id="6c7b3-112">`BeginConnection`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="6c7b3-112">`BeginConnection` returned successfully.</span></span>|  
|<span data-ttu-id="6c7b3-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6c7b3-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6c7b3-114">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="6c7b3-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6c7b3-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6c7b3-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6c7b3-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="6c7b3-116">The call timed out.</span></span>|  
|<span data-ttu-id="6c7b3-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6c7b3-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6c7b3-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="6c7b3-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6c7b3-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6c7b3-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6c7b3-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="6c7b3-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6c7b3-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6c7b3-121">E_FAIL</span></span>|<span data-ttu-id="6c7b3-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="6c7b3-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6c7b3-123">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="6c7b3-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6c7b3-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="6c7b3-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="6c7b3-125">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="6c7b3-125">E_INVALIDARG</span></span>|<span data-ttu-id="6c7b3-126">`dwConnectionId`sıfır veya `BeginConnection` Bu değeri kullanarak zaten çağırıldı ya da `dwConnectionId` `szConnectionName` null idi.</span><span class="sxs-lookup"><span data-stu-id="6c7b3-126">`dwConnectionId` was zero, or `BeginConnection` was already called using this `dwConnectionId` value, or `szConnectionName` was null.</span></span>|  
|<span data-ttu-id="6c7b3-127">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="6c7b3-127">E_OUTOFMEMORY</span></span>|<span data-ttu-id="6c7b3-128">Bu bağlantıyla ilişkili görevlerin listesini tutmak için yeterli bellek ayrılamadı.</span><span class="sxs-lookup"><span data-stu-id="6c7b3-128">Not enough memory could be allocated to hold the list of tasks associated with this connection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6c7b3-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6c7b3-129">Remarks</span></span>  
 <span data-ttu-id="6c7b3-130">[ICLRDebugManager](iclrdebugmanager-interface.md) , `BeginConnection` görev listelerinin tanımlayıcılar ve kolay adlarla ilişkilendirilmesi için, [SetConnectionTasks](iclrdebugmanager-setconnectiontasks-method.md)ve [EndConnection](iclrdebugmanager-endconnection-method.md)olmak üzere üç yöntem sunar.</span><span class="sxs-lookup"><span data-stu-id="6c7b3-130">[ICLRDebugManager](iclrdebugmanager-interface.md) provides three methods, `BeginConnection`, [SetConnectionTasks](iclrdebugmanager-setconnectiontasks-method.md), and [EndConnection](iclrdebugmanager-endconnection-method.md), for associating task lists with identifiers and friendly names.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="6c7b3-131">Bu üç yöntemin her görev kümesi için belirli bir sırada çağrılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6c7b3-131">These three methods must be called in a specific order for each set of tasks.</span></span> <span data-ttu-id="6c7b3-132">`BeginConnection`İlk olarak yeni bir bağlantı kurmak için çağırılır.</span><span class="sxs-lookup"><span data-stu-id="6c7b3-132">`BeginConnection` is called first to establish a new connection.</span></span> <span data-ttu-id="6c7b3-133">`SetConnectionTasks`ileri, bu bağlantıyla ilişkilendirilecek görev kümesini sağlamak için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="6c7b3-133">`SetConnectionTasks` is called next to provide the set of tasks to be associated with that connection.</span></span> <span data-ttu-id="6c7b3-134">`EndConnection`, görev listesi ile tanımlayıcı ve kolay ad arasındaki ilişkiyi kaldırmak için son olarak adlandırılır. Ancak, farklı bağlantılara yönelik çağrılar iç içe olabilir.</span><span class="sxs-lookup"><span data-stu-id="6c7b3-134">`EndConnection` is called last to remove the association between the task list and the identifier and friendly name.However, calls for different connections can be nested.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c7b3-135">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6c7b3-135">Requirements</span></span>  
 <span data-ttu-id="6c7b3-136">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c7b3-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c7b3-137">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6c7b3-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6c7b3-138">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="6c7b3-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6c7b3-139">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c7b3-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c7b3-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6c7b3-140">See also</span></span>

- [<span data-ttu-id="6c7b3-141">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6c7b3-141">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="6c7b3-142">ICLRDebugManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6c7b3-142">ICLRDebugManager Interface</span></span>](iclrdebugmanager-interface.md)
- [<span data-ttu-id="6c7b3-143">EndConnection Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6c7b3-143">EndConnection Method</span></span>](iclrdebugmanager-endconnection-method.md)
- [<span data-ttu-id="6c7b3-144">SetConnectionTasks Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6c7b3-144">SetConnectionTasks Method</span></span>](iclrdebugmanager-setconnectiontasks-method.md)
- [<span data-ttu-id="6c7b3-145">IHostControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6c7b3-145">IHostControl Interface</span></span>](ihostcontrol-interface.md)
