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
ms.openlocfilehash: 2a01779e6203ddfea32e72838b7e02996fd868c2
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67749616"
---
# <a name="ihosttaskmanagerenterruntime-method"></a><span data-ttu-id="0b544-102">IHostTaskManager::EnterRuntime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0b544-102">IHostTaskManager::EnterRuntime Method</span></span>
<span data-ttu-id="0b544-103">Konak, yönetilmeyen bir yönteme bir çağrı yöntemi, bir platform çağırma gibi ortak dil çalışma zamanı (CLR) yürütme denetimi döndürmektir bildirir.</span><span class="sxs-lookup"><span data-stu-id="0b544-103">Notifies the host that a call to an unmanaged method, such as a platform invoke method, is returning execution control to the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b544-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0b544-104">Syntax</span></span>  
  
```cpp  
HRESULT EnterRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="0b544-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0b544-105">Return Value</span></span>  
  
|<span data-ttu-id="0b544-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0b544-106">HRESULT</span></span>|<span data-ttu-id="0b544-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0b544-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0b544-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="0b544-108">S_OK</span></span>|<span data-ttu-id="0b544-109">`EnterRuntime` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="0b544-109">`EnterRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="0b544-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0b544-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0b544-111">CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="0b544-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0b544-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0b544-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0b544-113">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="0b544-113">The call timed out.</span></span>|  
|<span data-ttu-id="0b544-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0b544-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0b544-115">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="0b544-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0b544-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0b544-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0b544-117">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="0b544-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0b544-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0b544-118">E_FAIL</span></span>|<span data-ttu-id="0b544-119">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="0b544-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0b544-120">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="0b544-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0b544-121">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="0b544-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="0b544-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="0b544-122">E_OUTOFMEMORY</span></span>|<span data-ttu-id="0b544-123">İstenen ayırma tamamlamak yeterli bellek yoktu.</span><span class="sxs-lookup"><span data-stu-id="0b544-123">Not enough memory was available to complete the requested allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0b544-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0b544-124">Remarks</span></span>  
 <span data-ttu-id="0b544-125">`EnterRuntime` ana bilgisayara bildirmek için çağırılır, kendisi için yönetilmeyen bir işlev çağrısında [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md) yöntemi yapıldı, yürütülmesi tamamlandı ve yürütme denetimi çalışma zamanına döndürüyor.</span><span class="sxs-lookup"><span data-stu-id="0b544-125">`EnterRuntime` is called to notify the host that an unmanaged function, for which an earlier call to the [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md) method was made, has finished executing, and is returning execution control to the runtime.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0b544-126">[ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md) ana bilgisayara bildirmek için çağırılır, kendisi için yönetilmeyen bir işlev çağrısında `LeaveRuntime` yapıldı, yönetilen kod çağrısı yapıyor.</span><span class="sxs-lookup"><span data-stu-id="0b544-126">[ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md) is called to notify the host that an unmanaged function, for which an earlier call to `LeaveRuntime` was made, is making a call into managed code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b544-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0b544-127">Requirements</span></span>  
 <span data-ttu-id="0b544-128">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b544-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b544-129">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0b544-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0b544-130">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="0b544-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0b544-131">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b544-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b544-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0b544-132">See also</span></span>

- [<span data-ttu-id="0b544-133">Gelişmiş COM birlikte çalışabilirliği</span><span class="sxs-lookup"><span data-stu-id="0b544-133">Advanced COM Interoperability</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx)
- [<span data-ttu-id="0b544-134">Nasıl yapılır: PInvoke Kullanarak Yönetilen Koddan Yerel DLL'leri Çağırma</span><span class="sxs-lookup"><span data-stu-id="0b544-134">How to: Call Native DLLs from Managed Code Using PInvoke</span></span>](/cpp/dotnet/how-to-call-native-dlls-from-managed-code-using-pinvoke)
- [<span data-ttu-id="0b544-135">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0b544-135">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="0b544-136">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0b544-136">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="0b544-137">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0b544-137">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="0b544-138">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0b544-138">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="0b544-139">LeaveRuntime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0b544-139">LeaveRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)
