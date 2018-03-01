---
title: "IHostTaskManager::EnterRuntime Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IHostTaskManager.EnterRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::EnterRuntime
helpviewer_keywords:
- IHostTaskManager::EnterRuntime method [.NET Framework hosting]
- EnterRuntime method [.NET Framework hosting]
ms.assetid: 1aa7a4b1-636a-4f5e-b834-b406d72f7120
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 70c9e83311fd7427895e1957d3511a45c47434e6
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="ihosttaskmanagerenterruntime-method"></a><span data-ttu-id="a2d7d-102">IHostTaskManager::EnterRuntime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a2d7d-102">IHostTaskManager::EnterRuntime Method</span></span>
<span data-ttu-id="a2d7d-103">Konak bir yönetilmeyen yöntemine yapılan bir çağrı yöntemi, bir platform çağırma gibi ortak dil çalışma zamanı (CLR) yürütme denetimi döndürmektir bildirir.</span><span class="sxs-lookup"><span data-stu-id="a2d7d-103">Notifies the host that a call to an unmanaged method, such as a platform invoke method, is returning execution control to the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2d7d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a2d7d-104">Syntax</span></span>  
  
```  
HRESULT EnterRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="a2d7d-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a2d7d-105">Return Value</span></span>  
  
|<span data-ttu-id="a2d7d-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a2d7d-106">HRESULT</span></span>|<span data-ttu-id="a2d7d-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a2d7d-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a2d7d-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="a2d7d-108">S_OK</span></span>|<span data-ttu-id="a2d7d-109">`EnterRuntime`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="a2d7d-109">`EnterRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="a2d7d-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a2d7d-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a2d7d-111">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="a2d7d-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a2d7d-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a2d7d-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a2d7d-113">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="a2d7d-113">The call timed out.</span></span>|  
|<span data-ttu-id="a2d7d-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a2d7d-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a2d7d-115">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="a2d7d-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a2d7d-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a2d7d-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a2d7d-117">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="a2d7d-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a2d7d-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a2d7d-118">E_FAIL</span></span>|<span data-ttu-id="a2d7d-119">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="a2d7d-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a2d7d-120">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="a2d7d-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a2d7d-121">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="a2d7d-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="a2d7d-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="a2d7d-122">E_OUTOFMEMORY</span></span>|<span data-ttu-id="a2d7d-123">İstenen ayırma tamamlamak yeterli bellek yoktu.</span><span class="sxs-lookup"><span data-stu-id="a2d7d-123">Not enough memory was available to complete the requested allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a2d7d-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a2d7d-124">Remarks</span></span>  
 <span data-ttu-id="a2d7d-125">`EnterRuntime`konak bildirmek için çağrılır, kendisi için yönetilmeyen bir işleve önceki bir çağrı [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md) yöntemi yapıldığı, yürütülmesi tamamlandı ve çalışma zamanı yürütme denetimi döndürüyor.</span><span class="sxs-lookup"><span data-stu-id="a2d7d-125">`EnterRuntime` is called to notify the host that an unmanaged function, for which an earlier call to the [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md) method was made, has finished executing, and is returning execution control to the runtime.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a2d7d-126">[ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md) konak bildirmek üzere çağrılır, kendisi için yönetilmeyen bir işleve önceki bir çağrı `LeaveRuntime` yapıldı, yönetilen koda çağrı yapma.</span><span class="sxs-lookup"><span data-stu-id="a2d7d-126">[ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md) is called to notify the host that an unmanaged function, for which an earlier call to `LeaveRuntime` was made, is making a call into managed code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2d7d-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a2d7d-127">Requirements</span></span>  
 <span data-ttu-id="a2d7d-128">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a2d7d-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2d7d-129">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a2d7d-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a2d7d-130">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="a2d7d-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a2d7d-131">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2d7d-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2d7d-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a2d7d-132">See Also</span></span>  
 [<span data-ttu-id="a2d7d-133">Gelişmiş COM birlikte çalışabilirliği</span><span class="sxs-lookup"><span data-stu-id="a2d7d-133">Advanced COM Interoperability</span></span>](http://msdn.microsoft.com/library/3ada36e5-2390-4d70-b490-6ad8de92f2fb)  
 [<span data-ttu-id="a2d7d-134">Nasıl yapılır: Yönetilen Koddan PInvoke Kullanarak Yerel DLL'leri Çağırma</span><span class="sxs-lookup"><span data-stu-id="a2d7d-134">How to: Call Native DLLs from Managed Code Using PInvoke</span></span>](/cpp/dotnet/how-to-call-native-dlls-from-managed-code-using-pinvoke)  
 [<span data-ttu-id="a2d7d-135">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a2d7d-135">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="a2d7d-136">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a2d7d-136">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="a2d7d-137">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a2d7d-137">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="a2d7d-138">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a2d7d-138">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="a2d7d-139">LeaveRuntime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a2d7d-139">LeaveRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)
