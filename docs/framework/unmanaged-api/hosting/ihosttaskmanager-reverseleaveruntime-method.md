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
ms.openlocfilehash: 8e0981415c03120cc30e6349daced51e79216938
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95669971"
---
# <a name="ihosttaskmanagerreverseleaveruntime-method"></a><span data-ttu-id="98fce-102">IHostTaskManager::ReverseLeaveRuntime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="98fce-102">IHostTaskManager::ReverseLeaveRuntime Method</span></span>

<span data-ttu-id="98fce-103">Denetimin ortak dil çalışma zamanını (CLR) terk eden ve sırasıyla yönetilen koddan çağrılan yönetilmeyen bir işlev girerek konağa bildirir.</span><span class="sxs-lookup"><span data-stu-id="98fce-103">Notifies the host that control is leaving the common language runtime (CLR) and entering an unmanaged function that was, in turn, called from managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98fce-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="98fce-104">Syntax</span></span>  
  
```cpp  
HRESULT ReverseLeaveRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="98fce-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="98fce-105">Return Value</span></span>  
  
|<span data-ttu-id="98fce-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="98fce-106">HRESULT</span></span>|<span data-ttu-id="98fce-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="98fce-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="98fce-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="98fce-108">S_OK</span></span>|<span data-ttu-id="98fce-109">`ReverseLeaveRuntime` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="98fce-109">`ReverseLeaveRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="98fce-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="98fce-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="98fce-111">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="98fce-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="98fce-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="98fce-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="98fce-113">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="98fce-113">The call timed out.</span></span>|  
|<span data-ttu-id="98fce-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="98fce-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="98fce-115">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="98fce-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="98fce-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="98fce-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="98fce-117">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="98fce-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="98fce-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="98fce-118">E_FAIL</span></span>|<span data-ttu-id="98fce-119">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="98fce-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="98fce-120">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="98fce-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="98fce-121">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="98fce-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="98fce-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="98fce-122">E_OUTOFMEMORY</span></span>|<span data-ttu-id="98fce-123">İstenen kaynak ayırmayı tamamlamaya yetecek miktarda bellek yok.</span><span class="sxs-lookup"><span data-stu-id="98fce-123">Not enough memory is available to complete the requested resource allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="98fce-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="98fce-124">Remarks</span></span>  

 <span data-ttu-id="98fce-125">CLR, `ReverseLeaveRuntime` ana bilgisayarı şu anda yürütülmekte olan görevin, platform Invoke aracılığıyla yönetilen koddan çağrılan yönetilmeyen bir işleve bir denetim döndüğünü bilgilendirmek için çağırır.</span><span class="sxs-lookup"><span data-stu-id="98fce-125">The CLR calls `ReverseLeaveRuntime` to inform the host that the currently executing task is returning control to an unmanaged function that was, in turn, called from managed code through platform invoke.</span></span> <span data-ttu-id="98fce-126">Her çağrısı, `ReverseLeaveRuntime` bir [Smarenterruntime](ihosttaskmanager-reverseenterruntime-method.md)öğesine karşılık gelen çağrısıyla eşleşir.</span><span class="sxs-lookup"><span data-stu-id="98fce-126">Each call to `ReverseLeaveRuntime` matches a corresponding call to [ReverseEnterRuntime](ihosttaskmanager-reverseenterruntime-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98fce-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="98fce-127">Requirements</span></span>  

 <span data-ttu-id="98fce-128">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="98fce-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98fce-129">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="98fce-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="98fce-130">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="98fce-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="98fce-131">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98fce-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98fce-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="98fce-132">See also</span></span>

- [<span data-ttu-id="98fce-133">CallNeedsHostHook Yöntemi</span><span class="sxs-lookup"><span data-stu-id="98fce-133">CallNeedsHostHook Method</span></span>](ihosttaskmanager-callneedshosthook-method.md)
- [<span data-ttu-id="98fce-134">EnterRuntime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="98fce-134">EnterRuntime Method</span></span>](ihosttaskmanager-enterruntime-method.md)
- [<span data-ttu-id="98fce-135">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="98fce-135">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="98fce-136">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="98fce-136">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="98fce-137">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="98fce-137">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="98fce-138">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="98fce-138">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="98fce-139">LeaveRuntime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="98fce-139">LeaveRuntime Method</span></span>](ihosttaskmanager-leaveruntime-method.md)
- <span data-ttu-id="98fce-140">[Platform çağırma ' ye daha yakından bakış](/previous-versions/dotnet/netframework-4.0/0h9e9t7d(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="98fce-140">[A Closer Look at Platform Invoke](/previous-versions/dotnet/netframework-4.0/0h9e9t7d(v=vs.100))</span></span>
