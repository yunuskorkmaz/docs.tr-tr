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
ms.openlocfilehash: aa756c98dc082774f7a8a6e050209525420b359f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913724"
---
# <a name="ihosttaskmanagerenterruntime-method"></a><span data-ttu-id="0be6a-102">IHostTaskManager::EnterRuntime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0be6a-102">IHostTaskManager::EnterRuntime Method</span></span>
<span data-ttu-id="0be6a-103">Ana bilgisayara platform çağırma yöntemi gibi yönetilmeyen bir yönteme yapılan çağrının, ortak dil çalışma zamanına (CLR) yürütme denetimi döndürdüğünü bildirir.</span><span class="sxs-lookup"><span data-stu-id="0be6a-103">Notifies the host that a call to an unmanaged method, such as a platform invoke method, is returning execution control to the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0be6a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0be6a-104">Syntax</span></span>  
  
```cpp  
HRESULT EnterRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="0be6a-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0be6a-105">Return Value</span></span>  
  
|<span data-ttu-id="0be6a-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0be6a-106">HRESULT</span></span>|<span data-ttu-id="0be6a-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0be6a-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0be6a-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="0be6a-108">S_OK</span></span>|<span data-ttu-id="0be6a-109">`EnterRuntime`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="0be6a-109">`EnterRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="0be6a-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0be6a-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0be6a-111">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="0be6a-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0be6a-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0be6a-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0be6a-113">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="0be6a-113">The call timed out.</span></span>|  
|<span data-ttu-id="0be6a-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0be6a-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0be6a-115">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="0be6a-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0be6a-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0be6a-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0be6a-117">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="0be6a-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0be6a-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0be6a-118">E_FAIL</span></span>|<span data-ttu-id="0be6a-119">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="0be6a-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0be6a-120">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="0be6a-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0be6a-121">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="0be6a-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="0be6a-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="0be6a-122">E_OUTOFMEMORY</span></span>|<span data-ttu-id="0be6a-123">İstenen ayırmayı tamamlamaya yetecek miktarda bellek yoktu.</span><span class="sxs-lookup"><span data-stu-id="0be6a-123">Not enough memory was available to complete the requested allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0be6a-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0be6a-124">Remarks</span></span>  
 <span data-ttu-id="0be6a-125">`EnterRuntime`, bir yönetilmeyen işlevin, [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md) yöntemine daha önceki bir çağrı yapıldığını, yürütmeyi bitirmekte olduğunu ve çalışma zamanına yürütme denetimi döndüğünü bildirmek için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="0be6a-125">`EnterRuntime` is called to notify the host that an unmanaged function, for which an earlier call to the [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md) method was made, has finished executing, and is returning execution control to the runtime.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0be6a-126">Daha önce yapılan bir çağrının `LeaveRuntime` oluşturulduğu yönetilmeyen bir işlevin, yönetilen koda çağrı yaptığını konağa bildirmek için [smarenterruntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md) çağırılır.</span><span class="sxs-lookup"><span data-stu-id="0be6a-126">[ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md) is called to notify the host that an unmanaged function, for which an earlier call to `LeaveRuntime` was made, is making a call into managed code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0be6a-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0be6a-127">Requirements</span></span>  
 <span data-ttu-id="0be6a-128">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0be6a-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0be6a-129">**Üst bilgi** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0be6a-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0be6a-130">**Kitaplığı** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="0be6a-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0be6a-131">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0be6a-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0be6a-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0be6a-132">See also</span></span>

- [<span data-ttu-id="0be6a-133">Gelişmiş COM birlikte çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="0be6a-133">Advanced COM Interoperability</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx)
- [<span data-ttu-id="0be6a-134">Nasıl yapılır: PInvoke Kullanarak Yönetilen Koddan Yerel DLL'leri Çağırma</span><span class="sxs-lookup"><span data-stu-id="0be6a-134">How to: Call Native DLLs from Managed Code Using PInvoke</span></span>](/cpp/dotnet/how-to-call-native-dlls-from-managed-code-using-pinvoke)
- [<span data-ttu-id="0be6a-135">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0be6a-135">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="0be6a-136">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0be6a-136">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="0be6a-137">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0be6a-137">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="0be6a-138">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0be6a-138">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="0be6a-139">LeaveRuntime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0be6a-139">LeaveRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)
