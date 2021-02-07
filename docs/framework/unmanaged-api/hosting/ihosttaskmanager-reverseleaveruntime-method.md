---
description: ': IHostTaskManager:: ReverseLeaveRuntime yöntemi hakkında daha fazla bilgi'
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
ms.openlocfilehash: 2fed157f6ea05243270b957cacdb00ba5a47a88f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99680874"
---
# <a name="ihosttaskmanagerreverseleaveruntime-method"></a><span data-ttu-id="55714-103">IHostTaskManager::ReverseLeaveRuntime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="55714-103">IHostTaskManager::ReverseLeaveRuntime Method</span></span>

<span data-ttu-id="55714-104">Denetimin ortak dil çalışma zamanını (CLR) terk eden ve sırasıyla yönetilen koddan çağrılan yönetilmeyen bir işlev girerek konağa bildirir.</span><span class="sxs-lookup"><span data-stu-id="55714-104">Notifies the host that control is leaving the common language runtime (CLR) and entering an unmanaged function that was, in turn, called from managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55714-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="55714-105">Syntax</span></span>  
  
```cpp  
HRESULT ReverseLeaveRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="55714-106">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="55714-106">Return Value</span></span>  
  
|<span data-ttu-id="55714-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="55714-107">HRESULT</span></span>|<span data-ttu-id="55714-108">Description</span><span class="sxs-lookup"><span data-stu-id="55714-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="55714-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="55714-109">S_OK</span></span>|<span data-ttu-id="55714-110">`ReverseLeaveRuntime` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="55714-110">`ReverseLeaveRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="55714-111">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="55714-111">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="55714-112">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="55714-112">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="55714-113">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="55714-113">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="55714-114">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="55714-114">The call timed out.</span></span>|  
|<span data-ttu-id="55714-115">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="55714-115">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="55714-116">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="55714-116">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="55714-117">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="55714-117">HOST_E_ABANDONED</span></span>|<span data-ttu-id="55714-118">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="55714-118">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="55714-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="55714-119">E_FAIL</span></span>|<span data-ttu-id="55714-120">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="55714-120">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="55714-121">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="55714-121">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="55714-122">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="55714-122">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="55714-123">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="55714-123">E_OUTOFMEMORY</span></span>|<span data-ttu-id="55714-124">İstenen kaynak ayırmayı tamamlamaya yetecek miktarda bellek yok.</span><span class="sxs-lookup"><span data-stu-id="55714-124">Not enough memory is available to complete the requested resource allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="55714-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="55714-125">Remarks</span></span>  

 <span data-ttu-id="55714-126">CLR, `ReverseLeaveRuntime` ana bilgisayarı şu anda yürütülmekte olan görevin, platform Invoke aracılığıyla yönetilen koddan çağrılan yönetilmeyen bir işleve bir denetim döndüğünü bilgilendirmek için çağırır.</span><span class="sxs-lookup"><span data-stu-id="55714-126">The CLR calls `ReverseLeaveRuntime` to inform the host that the currently executing task is returning control to an unmanaged function that was, in turn, called from managed code through platform invoke.</span></span> <span data-ttu-id="55714-127">Her çağrısı, `ReverseLeaveRuntime` bir [Smarenterruntime](ihosttaskmanager-reverseenterruntime-method.md)öğesine karşılık gelen çağrısıyla eşleşir.</span><span class="sxs-lookup"><span data-stu-id="55714-127">Each call to `ReverseLeaveRuntime` matches a corresponding call to [ReverseEnterRuntime](ihosttaskmanager-reverseenterruntime-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="55714-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="55714-128">Requirements</span></span>  

 <span data-ttu-id="55714-129">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="55714-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55714-130">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="55714-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="55714-131">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="55714-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="55714-132">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55714-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55714-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="55714-133">See also</span></span>

- [<span data-ttu-id="55714-134">CallNeedsHostHook Yöntemi</span><span class="sxs-lookup"><span data-stu-id="55714-134">CallNeedsHostHook Method</span></span>](ihosttaskmanager-callneedshosthook-method.md)
- [<span data-ttu-id="55714-135">EnterRuntime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="55714-135">EnterRuntime Method</span></span>](ihosttaskmanager-enterruntime-method.md)
- [<span data-ttu-id="55714-136">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="55714-136">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="55714-137">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="55714-137">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="55714-138">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="55714-138">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="55714-139">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="55714-139">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="55714-140">LeaveRuntime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="55714-140">LeaveRuntime Method</span></span>](ihosttaskmanager-leaveruntime-method.md)
- <span data-ttu-id="55714-141">[Platform çağırma ' ye daha yakından bakış](/previous-versions/dotnet/netframework-4.0/0h9e9t7d(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="55714-141">[A Closer Look at Platform Invoke](/previous-versions/dotnet/netframework-4.0/0h9e9t7d(v=vs.100))</span></span>
