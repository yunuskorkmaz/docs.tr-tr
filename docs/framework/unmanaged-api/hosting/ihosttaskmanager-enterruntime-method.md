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
ms.openlocfilehash: 11515bbb5717222a0030c1953b4eab4eb1b83bb2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731650"
---
# <a name="ihosttaskmanagerenterruntime-method"></a><span data-ttu-id="680c2-102">IHostTaskManager::EnterRuntime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="680c2-102">IHostTaskManager::EnterRuntime Method</span></span>

<span data-ttu-id="680c2-103">Ana bilgisayara platform çağırma yöntemi gibi yönetilmeyen bir yönteme yapılan çağrının, ortak dil çalışma zamanına (CLR) yürütme denetimi döndürdüğünü bildirir.</span><span class="sxs-lookup"><span data-stu-id="680c2-103">Notifies the host that a call to an unmanaged method, such as a platform invoke method, is returning execution control to the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="680c2-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="680c2-104">Syntax</span></span>  
  
```cpp  
HRESULT EnterRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="680c2-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="680c2-105">Return Value</span></span>  
  
|<span data-ttu-id="680c2-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="680c2-106">HRESULT</span></span>|<span data-ttu-id="680c2-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="680c2-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="680c2-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="680c2-108">S_OK</span></span>|<span data-ttu-id="680c2-109">`EnterRuntime` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="680c2-109">`EnterRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="680c2-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="680c2-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="680c2-111">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="680c2-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="680c2-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="680c2-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="680c2-113">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="680c2-113">The call timed out.</span></span>|  
|<span data-ttu-id="680c2-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="680c2-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="680c2-115">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="680c2-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="680c2-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="680c2-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="680c2-117">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="680c2-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="680c2-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="680c2-118">E_FAIL</span></span>|<span data-ttu-id="680c2-119">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="680c2-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="680c2-120">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="680c2-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="680c2-121">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="680c2-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="680c2-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="680c2-122">E_OUTOFMEMORY</span></span>|<span data-ttu-id="680c2-123">İstenen ayırmayı tamamlamaya yetecek miktarda bellek yoktu.</span><span class="sxs-lookup"><span data-stu-id="680c2-123">Not enough memory was available to complete the requested allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="680c2-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="680c2-124">Remarks</span></span>  

 <span data-ttu-id="680c2-125">`EnterRuntime` , bir yönetilmeyen işlevin, [LeaveRuntime](ihosttaskmanager-leaveruntime-method.md) yöntemine daha önceki bir çağrı yapıldığını, yürütmeyi bitirmekte olduğunu ve çalışma zamanına yürütme denetimi döndüğünü bildirmek için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="680c2-125">`EnterRuntime` is called to notify the host that an unmanaged function, for which an earlier call to the [LeaveRuntime](ihosttaskmanager-leaveruntime-method.md) method was made, has finished executing, and is returning execution control to the runtime.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="680c2-126">Daha önce yapılan bir çağrının oluşturulduğu yönetilmeyen bir işlevin, yönetilen koda çağrı yaptığını konağa bildirmek için [Smarenterruntime](ihosttaskmanager-reverseenterruntime-method.md) çağırılır `LeaveRuntime` .</span><span class="sxs-lookup"><span data-stu-id="680c2-126">[ReverseEnterRuntime](ihosttaskmanager-reverseenterruntime-method.md) is called to notify the host that an unmanaged function, for which an earlier call to `LeaveRuntime` was made, is making a call into managed code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="680c2-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="680c2-127">Requirements</span></span>  

 <span data-ttu-id="680c2-128">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="680c2-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="680c2-129">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="680c2-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="680c2-130">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="680c2-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="680c2-131">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="680c2-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="680c2-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="680c2-132">See also</span></span>

- <span data-ttu-id="680c2-133">[Gelişmiş COM birlikte çalışabilirlik](/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="680c2-133">[Advanced COM Interoperability](/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span></span>
- [<span data-ttu-id="680c2-134">Nasıl yapılır: yönetilen koddan PInvoke kullanarak yerel dll 'Leri çağırma</span><span class="sxs-lookup"><span data-stu-id="680c2-134">How to: Call Native DLLs from Managed Code Using PInvoke</span></span>](/cpp/dotnet/how-to-call-native-dlls-from-managed-code-using-pinvoke)
- [<span data-ttu-id="680c2-135">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="680c2-135">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="680c2-136">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="680c2-136">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="680c2-137">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="680c2-137">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="680c2-138">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="680c2-138">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="680c2-139">LeaveRuntime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="680c2-139">LeaveRuntime Method</span></span>](ihosttaskmanager-leaveruntime-method.md)
