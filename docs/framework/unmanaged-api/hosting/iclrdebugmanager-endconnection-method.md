---
description: ': ICLRDebugManager:: EndConnection yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 06dc9e20ec02c3e3040090babcc443a2ae59848b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746060"
---
# <a name="iclrdebugmanagerendconnection-method"></a><span data-ttu-id="d652f-103">ICLRDebugManager::EndConnection Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d652f-103">ICLRDebugManager::EndConnection Method</span></span>

<span data-ttu-id="d652f-104">Bir görev listesi ve tanımlayıcı ve kolay ad arasındaki ilişkiyi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="d652f-104">Removes the association between a list of tasks and an identifier and a friendly name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d652f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d652f-105">Syntax</span></span>  
  
```cpp  
HRESULT EndConnection (  
    [in] CONNID dwConnectionId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d652f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d652f-106">Parameters</span></span>  

 `dwConnectionId`  
 <span data-ttu-id="d652f-107">'ndaki Bağlantı için konağa özgü tanımlayıcı ve ortak dil çalışma zamanı (CLR) görevlerinin ilişkili listesi.</span><span class="sxs-lookup"><span data-stu-id="d652f-107">[in] The host-specific identifier for the connection and the associated list of common language runtime (CLR) tasks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d652f-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d652f-108">Return Value</span></span>  
  
|<span data-ttu-id="d652f-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d652f-109">HRESULT</span></span>|<span data-ttu-id="d652f-110">Description</span><span class="sxs-lookup"><span data-stu-id="d652f-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d652f-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="d652f-111">S_OK</span></span>|<span data-ttu-id="d652f-112">`EndConnection` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="d652f-112">`EndConnection` returned successfully.</span></span>|  
|<span data-ttu-id="d652f-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d652f-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d652f-114">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="d652f-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d652f-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d652f-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d652f-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="d652f-116">The call timed out.</span></span>|  
|<span data-ttu-id="d652f-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d652f-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d652f-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="d652f-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d652f-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d652f-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d652f-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="d652f-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d652f-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d652f-121">E_FAIL</span></span>|<span data-ttu-id="d652f-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="d652f-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d652f-123">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="d652f-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d652f-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="d652f-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="d652f-125">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="d652f-125">E_INVALIDARG</span></span>|<span data-ttu-id="d652f-126">[BeginConnection](iclrdebugmanager-beginconnection-method.md) hiçbir şekilde hiçbir şekilde çağrılmadı `dwConnectionId` veya `dwConnectionId` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="d652f-126">[BeginConnection](iclrdebugmanager-beginconnection-method.md) was never called using `dwConnectionId`, or `dwConnectionId` was zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d652f-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d652f-127">Remarks</span></span>  

 <span data-ttu-id="d652f-128">[ICLRDebugManager](iclrdebugmanager-interface.md) , `BeginConnection` görev listelerinin tanımlayıcılar ve kolay adlarla ilişkilendirilmesi için, [SetConnectionTasks](iclrdebugmanager-setconnectiontasks-method.md)ve olmak üzere üç yöntem sağlar `EndConnection` .</span><span class="sxs-lookup"><span data-stu-id="d652f-128">[ICLRDebugManager](iclrdebugmanager-interface.md) provides three methods, `BeginConnection`, [SetConnectionTasks](iclrdebugmanager-setconnectiontasks-method.md), and `EndConnection`, for associating task lists with identifiers and friendly names.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d652f-129">Bu üç yöntemin her görev kümesi için belirli bir sırada çağrılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d652f-129">These three methods must be called in a specific order for each set of tasks.</span></span> <span data-ttu-id="d652f-130">`BeginConnection` İlk olarak yeni bir bağlantı kurmak için çağırılır.</span><span class="sxs-lookup"><span data-stu-id="d652f-130">`BeginConnection` is called first to establish a new connection.</span></span> <span data-ttu-id="d652f-131">`SetConnectionTasks` ileri, bu bağlantıyla ilişkilendirilecek görev kümesini sağlamak için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="d652f-131">`SetConnectionTasks` is called next to provide the set of tasks to be associated with that connection.</span></span> <span data-ttu-id="d652f-132">`EndConnection` , görev listesi ile tanımlayıcı ve kolay ad arasındaki ilişkiyi kaldırmak için son olarak adlandırılır. Ancak, farklı bağlantılara yönelik çağrılar iç içe olabilir.</span><span class="sxs-lookup"><span data-stu-id="d652f-132">`EndConnection` is called last to remove the association between the task list and the identifier and friendly name.However, calls for different connections can be nested.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d652f-133">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d652f-133">Requirements</span></span>  

 <span data-ttu-id="d652f-134">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d652f-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d652f-135">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d652f-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d652f-136">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="d652f-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d652f-137">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d652f-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d652f-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d652f-138">See also</span></span>

- [<span data-ttu-id="d652f-139">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d652f-139">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="d652f-140">ICLRDebugManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d652f-140">ICLRDebugManager Interface</span></span>](iclrdebugmanager-interface.md)
- [<span data-ttu-id="d652f-141">BeginConnection Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d652f-141">BeginConnection Method</span></span>](iclrdebugmanager-beginconnection-method.md)
- [<span data-ttu-id="d652f-142">SetConnectionTasks Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d652f-142">SetConnectionTasks Method</span></span>](iclrdebugmanager-setconnectiontasks-method.md)
- [<span data-ttu-id="d652f-143">IHostControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d652f-143">IHostControl Interface</span></span>](ihostcontrol-interface.md)
