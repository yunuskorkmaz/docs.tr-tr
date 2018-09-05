---
title: IHostTaskManager::EnterRuntime Yöntemi
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8625f893c30700a47cc2db7b960715f748ccb299
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43533555"
---
# <a name="ihosttaskmanagerenterruntime-method"></a><span data-ttu-id="d8190-102">IHostTaskManager::EnterRuntime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d8190-102">IHostTaskManager::EnterRuntime Method</span></span>
<span data-ttu-id="d8190-103">Konak, yönetilmeyen bir yönteme bir çağrı yöntemi, bir platform çağırma gibi ortak dil çalışma zamanı (CLR) yürütme denetimi döndürmektir bildirir.</span><span class="sxs-lookup"><span data-stu-id="d8190-103">Notifies the host that a call to an unmanaged method, such as a platform invoke method, is returning execution control to the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8190-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d8190-104">Syntax</span></span>  
  
```  
HRESULT EnterRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="d8190-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d8190-105">Return Value</span></span>  
  
|<span data-ttu-id="d8190-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d8190-106">HRESULT</span></span>|<span data-ttu-id="d8190-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d8190-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d8190-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="d8190-108">S_OK</span></span>|<span data-ttu-id="d8190-109">`EnterRuntime` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="d8190-109">`EnterRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="d8190-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d8190-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d8190-111">CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="d8190-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d8190-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d8190-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d8190-113">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="d8190-113">The call timed out.</span></span>|  
|<span data-ttu-id="d8190-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d8190-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d8190-115">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="d8190-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d8190-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d8190-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d8190-117">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="d8190-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d8190-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d8190-118">E_FAIL</span></span>|<span data-ttu-id="d8190-119">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="d8190-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d8190-120">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="d8190-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d8190-121">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="d8190-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="d8190-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="d8190-122">E_OUTOFMEMORY</span></span>|<span data-ttu-id="d8190-123">İstenen ayırma tamamlamak yeterli bellek yoktu.</span><span class="sxs-lookup"><span data-stu-id="d8190-123">Not enough memory was available to complete the requested allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d8190-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d8190-124">Remarks</span></span>  
 <span data-ttu-id="d8190-125">`EnterRuntime` ana bilgisayara bildirmek için çağırılır, kendisi için yönetilmeyen bir işlev çağrısında [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md) yöntemi yapıldı, yürütülmesi tamamlandı ve yürütme denetimi çalışma zamanına döndürüyor.</span><span class="sxs-lookup"><span data-stu-id="d8190-125">`EnterRuntime` is called to notify the host that an unmanaged function, for which an earlier call to the [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md) method was made, has finished executing, and is returning execution control to the runtime.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d8190-126">[ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md) ana bilgisayara bildirmek için çağırılır, kendisi için yönetilmeyen bir işlev çağrısında `LeaveRuntime` yapıldı, yönetilen kod çağrısı yapıyor.</span><span class="sxs-lookup"><span data-stu-id="d8190-126">[ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md) is called to notify the host that an unmanaged function, for which an earlier call to `LeaveRuntime` was made, is making a call into managed code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8190-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d8190-127">Requirements</span></span>  
 <span data-ttu-id="d8190-128">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8190-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8190-129">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d8190-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d8190-130">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="d8190-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d8190-131">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8190-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8190-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d8190-132">See Also</span></span>  
 [<span data-ttu-id="d8190-133">Gelişmiş COM birlikte çalışabilirliği</span><span class="sxs-lookup"><span data-stu-id="d8190-133">Advanced COM Interoperability</span></span>](https://msdn.microsoft.com/library/3ada36e5-2390-4d70-b490-6ad8de92f2fb)  
 [<span data-ttu-id="d8190-134">Nasıl yapılır: Yönetilen Koddan PInvoke Kullanarak Yerel DLL'leri Çağırma</span><span class="sxs-lookup"><span data-stu-id="d8190-134">How to: Call Native DLLs from Managed Code Using PInvoke</span></span>](/cpp/dotnet/how-to-call-native-dlls-from-managed-code-using-pinvoke)  
 [<span data-ttu-id="d8190-135">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d8190-135">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="d8190-136">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d8190-136">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="d8190-137">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d8190-137">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="d8190-138">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d8190-138">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="d8190-139">LeaveRuntime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d8190-139">LeaveRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)
