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
ms.openlocfilehash: 425f40da7a53aa4af1bd14964a8136add2f59f0b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73135210"
---
# <a name="iclrdebugmanagerendconnection-method"></a><span data-ttu-id="2034d-102">ICLRDebugManager::EndConnection Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2034d-102">ICLRDebugManager::EndConnection Method</span></span>
<span data-ttu-id="2034d-103">Bir görev listesi ve tanımlayıcı ve kolay ad arasındaki ilişkiyi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="2034d-103">Removes the association between a list of tasks and an identifier and a friendly name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2034d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2034d-104">Syntax</span></span>  
  
```cpp  
HRESULT EndConnection (  
    [in] CONNID dwConnectionId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2034d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2034d-105">Parameters</span></span>  
 `dwConnectionId`  
 <span data-ttu-id="2034d-106">'ndaki Bağlantı için konağa özgü tanımlayıcı ve ortak dil çalışma zamanı (CLR) görevlerinin ilişkili listesi.</span><span class="sxs-lookup"><span data-stu-id="2034d-106">[in] The host-specific identifier for the connection and the associated list of common language runtime (CLR) tasks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2034d-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2034d-107">Return Value</span></span>  
  
|<span data-ttu-id="2034d-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2034d-108">HRESULT</span></span>|<span data-ttu-id="2034d-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2034d-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2034d-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="2034d-110">S_OK</span></span>|<span data-ttu-id="2034d-111">`EndConnection` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="2034d-111">`EndConnection` returned successfully.</span></span>|  
|<span data-ttu-id="2034d-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2034d-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2034d-113">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="2034d-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2034d-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2034d-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2034d-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="2034d-115">The call timed out.</span></span>|  
|<span data-ttu-id="2034d-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2034d-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2034d-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="2034d-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2034d-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2034d-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2034d-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="2034d-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2034d-120">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="2034d-120">E_FAIL</span></span>|<span data-ttu-id="2034d-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="2034d-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2034d-122">Bir yöntem E_FAıL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="2034d-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2034d-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="2034d-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="2034d-124">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="2034d-124">E_INVALIDARG</span></span>|<span data-ttu-id="2034d-125">[BeginConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) `dwConnectionId`kullanılarak hiçbir şekilde çağrılmadı veya `dwConnectionId` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="2034d-125">[BeginConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) was never called using `dwConnectionId`, or `dwConnectionId` was zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2034d-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2034d-126">Remarks</span></span>  
 <span data-ttu-id="2034d-127">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) , görev listelerinin tanımlayıcılar ve kolay adlarla ilişkilendirilmesi için üç yöntem, `BeginConnection`, [setconnectiontasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)ve `EndConnection`sağlar.</span><span class="sxs-lookup"><span data-stu-id="2034d-127">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) provides three methods, `BeginConnection`, [SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md), and `EndConnection`, for associating task lists with identifiers and friendly names.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="2034d-128">Bu üç yöntemin her görev kümesi için belirli bir sırada çağrılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="2034d-128">These three methods must be called in a specific order for each set of tasks.</span></span> <span data-ttu-id="2034d-129">`BeginConnection` yeni bir bağlantı kurmak için ilk olarak çağırılır.</span><span class="sxs-lookup"><span data-stu-id="2034d-129">`BeginConnection` is called first to establish a new connection.</span></span> <span data-ttu-id="2034d-130">`SetConnectionTasks`, bu bağlantıyla ilişkilendirilecek görev kümesini sağlamak için ileri çağırılır.</span><span class="sxs-lookup"><span data-stu-id="2034d-130">`SetConnectionTasks` is called next to provide the set of tasks to be associated with that connection.</span></span> <span data-ttu-id="2034d-131">`EndConnection` görev listesi ve tanımlayıcı ve kolay ad arasındaki ilişkiyi kaldırmak için son olarak adlandırılır. Ancak, farklı bağlantılara yönelik çağrılar iç içe olabilir.</span><span class="sxs-lookup"><span data-stu-id="2034d-131">`EndConnection` is called last to remove the association between the task list and the identifier and friendly name.However, calls for different connections can be nested.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2034d-132">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2034d-132">Requirements</span></span>  
 <span data-ttu-id="2034d-133">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2034d-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2034d-134">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2034d-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2034d-135">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="2034d-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2034d-136">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2034d-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2034d-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2034d-137">See also</span></span>

- [<span data-ttu-id="2034d-138">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2034d-138">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="2034d-139">ICLRDebugManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2034d-139">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)
- [<span data-ttu-id="2034d-140">BeginConnection Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2034d-140">BeginConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)
- [<span data-ttu-id="2034d-141">SetConnectionTasks Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2034d-141">SetConnectionTasks Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)
- [<span data-ttu-id="2034d-142">IHostControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2034d-142">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
