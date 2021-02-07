---
description: ': IHostTaskManager:: EnterRuntime Yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 924fa18c9acbf02d8c614ffd9bf95657fd73ed14
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753841"
---
# <a name="ihosttaskmanagerenterruntime-method"></a><span data-ttu-id="5e1d0-103">IHostTaskManager::EnterRuntime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5e1d0-103">IHostTaskManager::EnterRuntime Method</span></span>

<span data-ttu-id="5e1d0-104">Ana bilgisayara platform çağırma yöntemi gibi yönetilmeyen bir yönteme yapılan çağrının, ortak dil çalışma zamanına (CLR) yürütme denetimi döndürdüğünü bildirir.</span><span class="sxs-lookup"><span data-stu-id="5e1d0-104">Notifies the host that a call to an unmanaged method, such as a platform invoke method, is returning execution control to the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e1d0-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="5e1d0-105">Syntax</span></span>  
  
```cpp  
HRESULT EnterRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="5e1d0-106">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5e1d0-106">Return Value</span></span>  
  
|<span data-ttu-id="5e1d0-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5e1d0-107">HRESULT</span></span>|<span data-ttu-id="5e1d0-108">Description</span><span class="sxs-lookup"><span data-stu-id="5e1d0-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5e1d0-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="5e1d0-109">S_OK</span></span>|<span data-ttu-id="5e1d0-110">`EnterRuntime` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="5e1d0-110">`EnterRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="5e1d0-111">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5e1d0-111">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5e1d0-112">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="5e1d0-112">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5e1d0-113">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5e1d0-113">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5e1d0-114">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="5e1d0-114">The call timed out.</span></span>|  
|<span data-ttu-id="5e1d0-115">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5e1d0-115">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5e1d0-116">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="5e1d0-116">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5e1d0-117">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5e1d0-117">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5e1d0-118">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="5e1d0-118">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5e1d0-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5e1d0-119">E_FAIL</span></span>|<span data-ttu-id="5e1d0-120">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="5e1d0-120">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5e1d0-121">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="5e1d0-121">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5e1d0-122">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="5e1d0-122">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="5e1d0-123">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="5e1d0-123">E_OUTOFMEMORY</span></span>|<span data-ttu-id="5e1d0-124">İstenen ayırmayı tamamlamaya yetecek miktarda bellek yoktu.</span><span class="sxs-lookup"><span data-stu-id="5e1d0-124">Not enough memory was available to complete the requested allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5e1d0-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5e1d0-125">Remarks</span></span>  

 <span data-ttu-id="5e1d0-126">`EnterRuntime` , bir yönetilmeyen işlevin, [LeaveRuntime](ihosttaskmanager-leaveruntime-method.md) yöntemine daha önceki bir çağrı yapıldığını, yürütmeyi bitirmekte olduğunu ve çalışma zamanına yürütme denetimi döndüğünü bildirmek için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="5e1d0-126">`EnterRuntime` is called to notify the host that an unmanaged function, for which an earlier call to the [LeaveRuntime](ihosttaskmanager-leaveruntime-method.md) method was made, has finished executing, and is returning execution control to the runtime.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5e1d0-127">Daha önce yapılan bir çağrının oluşturulduğu yönetilmeyen bir işlevin, yönetilen koda çağrı yaptığını konağa bildirmek için [Smarenterruntime](ihosttaskmanager-reverseenterruntime-method.md) çağırılır `LeaveRuntime` .</span><span class="sxs-lookup"><span data-stu-id="5e1d0-127">[ReverseEnterRuntime](ihosttaskmanager-reverseenterruntime-method.md) is called to notify the host that an unmanaged function, for which an earlier call to `LeaveRuntime` was made, is making a call into managed code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e1d0-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5e1d0-128">Requirements</span></span>  

 <span data-ttu-id="5e1d0-129">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e1d0-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e1d0-130">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="5e1d0-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5e1d0-131">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="5e1d0-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5e1d0-132">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e1d0-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e1d0-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5e1d0-133">See also</span></span>

- <span data-ttu-id="5e1d0-134">[Gelişmiş COM birlikte çalışabilirlik](/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="5e1d0-134">[Advanced COM Interoperability](/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span></span>
- [<span data-ttu-id="5e1d0-135">Nasıl yapılır: yönetilen koddan PInvoke kullanarak yerel dll 'Leri çağırma</span><span class="sxs-lookup"><span data-stu-id="5e1d0-135">How to: Call Native DLLs from Managed Code Using PInvoke</span></span>](/cpp/dotnet/how-to-call-native-dlls-from-managed-code-using-pinvoke)
- [<span data-ttu-id="5e1d0-136">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5e1d0-136">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="5e1d0-137">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5e1d0-137">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="5e1d0-138">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5e1d0-138">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="5e1d0-139">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5e1d0-139">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="5e1d0-140">LeaveRuntime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5e1d0-140">LeaveRuntime Method</span></span>](ihosttaskmanager-leaveruntime-method.md)
