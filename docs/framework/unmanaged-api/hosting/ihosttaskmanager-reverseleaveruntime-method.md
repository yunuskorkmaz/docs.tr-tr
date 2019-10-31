---
title: IHostTaskManager::ReverseLeaveRuntime Yöntemi
ms.date: 03/30/2017
api_name:
- IHostTaskManager.ReverseLeaveRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::ReverseLeaveRuntime
helpviewer_keywords:
- IHostTaskManager::ReverseLeaveRuntime method [.NET Framework hosting]
- ReverseLeaveRuntime method [.NET Framework hosting]
ms.assetid: 4837d398-16a1-4e32-902c-022cd1aad3ca
topic_type:
- apiref
ms.openlocfilehash: 362239c584f469c9bd88f9f937bb3cdae7235429
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132950"
---
# <a name="ihosttaskmanagerreverseleaveruntime-method"></a><span data-ttu-id="65578-102">IHostTaskManager::ReverseLeaveRuntime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="65578-102">IHostTaskManager::ReverseLeaveRuntime Method</span></span>
<span data-ttu-id="65578-103">Denetimin ortak dil çalışma zamanını (CLR) terk eden ve sırasıyla yönetilen koddan çağrılan yönetilmeyen bir işlev girerek konağa bildirir.</span><span class="sxs-lookup"><span data-stu-id="65578-103">Notifies the host that control is leaving the common language runtime (CLR) and entering an unmanaged function that was, in turn, called from managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65578-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="65578-104">Syntax</span></span>  
  
```cpp  
HRESULT ReverseLeaveRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="65578-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="65578-105">Return Value</span></span>  
  
|<span data-ttu-id="65578-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="65578-106">HRESULT</span></span>|<span data-ttu-id="65578-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="65578-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="65578-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="65578-108">S_OK</span></span>|<span data-ttu-id="65578-109">`ReverseLeaveRuntime` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="65578-109">`ReverseLeaveRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="65578-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="65578-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="65578-111">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="65578-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="65578-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="65578-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="65578-113">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="65578-113">The call timed out.</span></span>|  
|<span data-ttu-id="65578-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="65578-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="65578-115">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="65578-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="65578-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="65578-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="65578-117">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="65578-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="65578-118">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="65578-118">E_FAIL</span></span>|<span data-ttu-id="65578-119">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="65578-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="65578-120">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="65578-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="65578-121">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="65578-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="65578-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="65578-122">E_OUTOFMEMORY</span></span>|<span data-ttu-id="65578-123">İstenen kaynak ayırmayı tamamlamaya yetecek miktarda bellek yok.</span><span class="sxs-lookup"><span data-stu-id="65578-123">Not enough memory is available to complete the requested resource allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="65578-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="65578-124">Remarks</span></span>  
 <span data-ttu-id="65578-125">CLR, ana bilgisayarı şu anda yürütülmekte olan görevin, platform Invoke aracılığıyla yönetilen koddan çağrılan yönetilmeyen bir işleve bir denetim döndüğünü bildirmek için `ReverseLeaveRuntime` çağırır.</span><span class="sxs-lookup"><span data-stu-id="65578-125">The CLR calls `ReverseLeaveRuntime` to inform the host that the currently executing task is returning control to an unmanaged function that was, in turn, called from managed code through platform invoke.</span></span> <span data-ttu-id="65578-126">Her `ReverseLeaveRuntime` çağrısı, bir [Smarenterruntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md)öğesine karşılık gelen bir çağrıyla eşleşir.</span><span class="sxs-lookup"><span data-stu-id="65578-126">Each call to `ReverseLeaveRuntime` matches a corresponding call to [ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65578-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="65578-127">Requirements</span></span>  
 <span data-ttu-id="65578-128">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65578-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65578-129">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="65578-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="65578-130">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="65578-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="65578-131">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65578-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65578-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="65578-132">See also</span></span>

- [<span data-ttu-id="65578-133">CallNeedsHostHook Yöntemi</span><span class="sxs-lookup"><span data-stu-id="65578-133">CallNeedsHostHook Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-callneedshosthook-method.md)
- [<span data-ttu-id="65578-134">EnterRuntime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="65578-134">EnterRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md)
- [<span data-ttu-id="65578-135">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="65578-135">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="65578-136">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="65578-136">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="65578-137">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="65578-137">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="65578-138">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="65578-138">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="65578-139">LeaveRuntime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="65578-139">LeaveRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)
- <span data-ttu-id="65578-140">[Platform çağırma ' ye daha yakından bakış](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0h9e9t7d(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="65578-140">[A Closer Look at Platform Invoke](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0h9e9t7d(v=vs.100))</span></span>
