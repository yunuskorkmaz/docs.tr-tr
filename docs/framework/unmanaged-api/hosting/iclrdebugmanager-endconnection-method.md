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
ms.openlocfilehash: f524cadf77caec0823411784c68f339207433601
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615799"
---
# <a name="iclrdebugmanagerendconnection-method"></a><span data-ttu-id="f5392-102">ICLRDebugManager::EndConnection Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f5392-102">ICLRDebugManager::EndConnection Method</span></span>
<span data-ttu-id="f5392-103">Bir görev listesi ve tanımlayıcı ve kolay ad arasındaki ilişkiyi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="f5392-103">Removes the association between a list of tasks and an identifier and a friendly name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5392-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="f5392-104">Syntax</span></span>  
  
```cpp  
HRESULT EndConnection (  
    [in] CONNID dwConnectionId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f5392-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f5392-105">Parameters</span></span>  
 `dwConnectionId`  
 <span data-ttu-id="f5392-106">'ndaki Bağlantı için konağa özgü tanımlayıcı ve ortak dil çalışma zamanı (CLR) görevlerinin ilişkili listesi.</span><span class="sxs-lookup"><span data-stu-id="f5392-106">[in] The host-specific identifier for the connection and the associated list of common language runtime (CLR) tasks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f5392-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f5392-107">Return Value</span></span>  
  
|<span data-ttu-id="f5392-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f5392-108">HRESULT</span></span>|<span data-ttu-id="f5392-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f5392-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f5392-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="f5392-110">S_OK</span></span>|<span data-ttu-id="f5392-111">`EndConnection`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="f5392-111">`EndConnection` returned successfully.</span></span>|  
|<span data-ttu-id="f5392-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f5392-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f5392-113">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="f5392-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f5392-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f5392-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f5392-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="f5392-115">The call timed out.</span></span>|  
|<span data-ttu-id="f5392-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f5392-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f5392-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="f5392-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f5392-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f5392-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f5392-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="f5392-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f5392-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f5392-120">E_FAIL</span></span>|<span data-ttu-id="f5392-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="f5392-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f5392-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="f5392-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f5392-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="f5392-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="f5392-124">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="f5392-124">E_INVALIDARG</span></span>|<span data-ttu-id="f5392-125">[BeginConnection](iclrdebugmanager-beginconnection-method.md) hiçbir şekilde hiçbir şekilde çağrılmadı `dwConnectionId` veya `dwConnectionId` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="f5392-125">[BeginConnection](iclrdebugmanager-beginconnection-method.md) was never called using `dwConnectionId`, or `dwConnectionId` was zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f5392-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f5392-126">Remarks</span></span>  
 <span data-ttu-id="f5392-127">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) , `BeginConnection` görev listelerinin tanımlayıcılar ve kolay adlarla ilişkilendirilmesi için, [SetConnectionTasks](iclrdebugmanager-setconnectiontasks-method.md)ve olmak üzere üç yöntem sağlar `EndConnection` .</span><span class="sxs-lookup"><span data-stu-id="f5392-127">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) provides three methods, `BeginConnection`, [SetConnectionTasks](iclrdebugmanager-setconnectiontasks-method.md), and `EndConnection`, for associating task lists with identifiers and friendly names.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="f5392-128">Bu üç yöntemin her görev kümesi için belirli bir sırada çağrılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f5392-128">These three methods must be called in a specific order for each set of tasks.</span></span> <span data-ttu-id="f5392-129">`BeginConnection`İlk olarak yeni bir bağlantı kurmak için çağırılır.</span><span class="sxs-lookup"><span data-stu-id="f5392-129">`BeginConnection` is called first to establish a new connection.</span></span> <span data-ttu-id="f5392-130">`SetConnectionTasks`ileri, bu bağlantıyla ilişkilendirilecek görev kümesini sağlamak için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="f5392-130">`SetConnectionTasks` is called next to provide the set of tasks to be associated with that connection.</span></span> <span data-ttu-id="f5392-131">`EndConnection`, görev listesi ile tanımlayıcı ve kolay ad arasındaki ilişkiyi kaldırmak için son olarak adlandırılır. Ancak, farklı bağlantılara yönelik çağrılar iç içe olabilir.</span><span class="sxs-lookup"><span data-stu-id="f5392-131">`EndConnection` is called last to remove the association between the task list and the identifier and friendly name.However, calls for different connections can be nested.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5392-132">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f5392-132">Requirements</span></span>  
 <span data-ttu-id="f5392-133">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5392-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5392-134">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f5392-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f5392-135">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="f5392-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f5392-136">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5392-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5392-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f5392-137">See also</span></span>

- [<span data-ttu-id="f5392-138">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f5392-138">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="f5392-139">ICLRDebugManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f5392-139">ICLRDebugManager Interface</span></span>](iclrdebugmanager-interface.md)
- [<span data-ttu-id="f5392-140">BeginConnection Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f5392-140">BeginConnection Method</span></span>](iclrdebugmanager-beginconnection-method.md)
- [<span data-ttu-id="f5392-141">SetConnectionTasks Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f5392-141">SetConnectionTasks Method</span></span>](iclrdebugmanager-setconnectiontasks-method.md)
- [<span data-ttu-id="f5392-142">IHostControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f5392-142">IHostControl Interface</span></span>](ihostcontrol-interface.md)
