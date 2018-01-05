---
title: "IHostTaskManager::EnterRuntime Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTaskManager.EnterRuntime
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTaskManager::EnterRuntime
helpviewer_keywords:
- IHostTaskManager::EnterRuntime method [.NET Framework hosting]
- EnterRuntime method [.NET Framework hosting]
ms.assetid: 1aa7a4b1-636a-4f5e-b834-b406d72f7120
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0617ce6960c5afbdad77c28de8284531ae976f3b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ihosttaskmanagerenterruntime-method"></a><span data-ttu-id="7272f-102">IHostTaskManager::EnterRuntime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7272f-102">IHostTaskManager::EnterRuntime Method</span></span>
<span data-ttu-id="7272f-103">Konak bir yönetilmeyen yöntemine yapılan bir çağrı yöntemi, bir platform çağırma gibi ortak dil çalışma zamanı (CLR) yürütme denetimi döndürmektir bildirir.</span><span class="sxs-lookup"><span data-stu-id="7272f-103">Notifies the host that a call to an unmanaged method, such as a platform invoke method, is returning execution control to the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7272f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7272f-104">Syntax</span></span>  
  
```  
HRESULT EnterRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="7272f-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7272f-105">Return Value</span></span>  
  
|<span data-ttu-id="7272f-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7272f-106">HRESULT</span></span>|<span data-ttu-id="7272f-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7272f-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7272f-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="7272f-108">S_OK</span></span>|<span data-ttu-id="7272f-109">`EnterRuntime`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="7272f-109">`EnterRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="7272f-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7272f-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7272f-111">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="7272f-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7272f-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7272f-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7272f-113">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="7272f-113">The call timed out.</span></span>|  
|<span data-ttu-id="7272f-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7272f-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7272f-115">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="7272f-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7272f-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7272f-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7272f-117">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="7272f-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7272f-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7272f-118">E_FAIL</span></span>|<span data-ttu-id="7272f-119">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="7272f-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7272f-120">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="7272f-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7272f-121">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="7272f-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="7272f-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="7272f-122">E_OUTOFMEMORY</span></span>|<span data-ttu-id="7272f-123">İstenen ayırma tamamlamak yeterli bellek yoktu.</span><span class="sxs-lookup"><span data-stu-id="7272f-123">Not enough memory was available to complete the requested allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7272f-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7272f-124">Remarks</span></span>  
 <span data-ttu-id="7272f-125">`EnterRuntime`konak bildirmek için çağrılır, kendisi için yönetilmeyen bir işleve önceki bir çağrı [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md) yöntemi yapıldığı, yürütülmesi tamamlandı ve çalışma zamanı yürütme denetimi döndürüyor.</span><span class="sxs-lookup"><span data-stu-id="7272f-125">`EnterRuntime` is called to notify the host that an unmanaged function, for which an earlier call to the [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md) method was made, has finished executing, and is returning execution control to the runtime.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7272f-126">[ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md) konak bildirmek üzere çağrılır, kendisi için yönetilmeyen bir işleve önceki bir çağrı `LeaveRuntime` yapıldı, yönetilen koda çağrı yapma.</span><span class="sxs-lookup"><span data-stu-id="7272f-126">[ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md) is called to notify the host that an unmanaged function, for which an earlier call to `LeaveRuntime` was made, is making a call into managed code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7272f-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7272f-127">Requirements</span></span>  
 <span data-ttu-id="7272f-128">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7272f-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7272f-129">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7272f-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7272f-130">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="7272f-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7272f-131">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7272f-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7272f-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7272f-132">See Also</span></span>  
 [<span data-ttu-id="7272f-133">Gelişmiş COM birlikte çalışabilirliği</span><span class="sxs-lookup"><span data-stu-id="7272f-133">Advanced COM Interoperability</span></span>](http://msdn.microsoft.com/en-us/3ada36e5-2390-4d70-b490-6ad8de92f2fb)  
 [<span data-ttu-id="7272f-134">Nasıl yapılır: Yönetilen Koddan PInvoke Kullanarak Yerel DLL'leri Çağırma</span><span class="sxs-lookup"><span data-stu-id="7272f-134">How to: Call Native DLLs from Managed Code Using PInvoke</span></span>](/cpp/dotnet/how-to-call-native-dlls-from-managed-code-using-pinvoke)  
 [<span data-ttu-id="7272f-135">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7272f-135">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="7272f-136">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7272f-136">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="7272f-137">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7272f-137">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="7272f-138">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7272f-138">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="7272f-139">LeaveRuntime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7272f-139">LeaveRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)
