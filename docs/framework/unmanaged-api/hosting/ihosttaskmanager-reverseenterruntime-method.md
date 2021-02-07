---
description: ': IHostTaskManager:: Smarenterruntime yöntemi hakkında daha fazla bilgi edinin'
title: IHostTaskManager::ReverseEnterRuntime Yöntemi
ms.date: 03/30/2017
api_name:
- IHostTaskManager.ReverseEnterRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::ReverseEnterRuntime
helpviewer_keywords:
- IHostTaskManager::ReverseEnterRuntime method [.NET Framework hosting]
- ReverseEnterRuntime method [.NET Framework hosting]
ms.assetid: b1e26bff-d3ea-436e-9867-29720df999f4
topic_type:
- apiref
ms.openlocfilehash: 1c2d2d7d60bd110999591ed5e94c86d680560d12
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707557"
---
# <a name="ihosttaskmanagerreverseenterruntime-method"></a><span data-ttu-id="99760-103">IHostTaskManager::ReverseEnterRuntime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="99760-103">IHostTaskManager::ReverseEnterRuntime Method</span></span>

<span data-ttu-id="99760-104">Ana bilgisayara, yönetilmeyen koddan ortak dil çalışma zamanı (CLR) için bir çağrının yapıldığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="99760-104">Notifies the host that a call is being made into the common language runtime (CLR) from unmanaged code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99760-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="99760-105">Syntax</span></span>  
  
```cpp  
HRESULT ReverseEnterRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="99760-106">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="99760-106">Return Value</span></span>  
  
|<span data-ttu-id="99760-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="99760-107">HRESULT</span></span>|<span data-ttu-id="99760-108">Description</span><span class="sxs-lookup"><span data-stu-id="99760-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="99760-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="99760-109">S_OK</span></span>|<span data-ttu-id="99760-110">`ReverseEnterRuntime` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="99760-110">`ReverseEnterRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="99760-111">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="99760-111">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="99760-112">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="99760-112">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="99760-113">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="99760-113">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="99760-114">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="99760-114">The call timed out.</span></span>|  
|<span data-ttu-id="99760-115">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="99760-115">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="99760-116">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="99760-116">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="99760-117">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="99760-117">HOST_E_ABANDONED</span></span>|<span data-ttu-id="99760-118">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="99760-118">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="99760-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="99760-119">E_FAIL</span></span>|<span data-ttu-id="99760-120">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="99760-120">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="99760-121">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="99760-121">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="99760-122">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="99760-122">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="99760-123">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="99760-123">E_OUTOFMEMORY</span></span>|<span data-ttu-id="99760-124">İstenen kaynak ayırmayı tamamlamaya yetecek miktarda bellek yok.</span><span class="sxs-lookup"><span data-stu-id="99760-124">Not enough memory is available to complete the requested resource allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="99760-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="99760-125">Remarks</span></span>  

 <span data-ttu-id="99760-126">CLR 'ye yapılan çağrı yönetilen kodda oluşturulan bir sıra tarafından yapılırsa, her `ReverseEnterRuntime` bir çağrı bir [ReverseLeaveRuntime](ihosttaskmanager-reverseleaveruntime-method.md)çağrısına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="99760-126">If the call into the CLR is made from a sequence that originated in managed code, each call to `ReverseEnterRuntime` corresponds to a call to [ReverseLeaveRuntime](ihosttaskmanager-reverseleaveruntime-method.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="99760-127">Çağrılar, iç içe kalmadan yönetilmeyen koddan kaynaklanamaz.</span><span class="sxs-lookup"><span data-stu-id="99760-127">Calls can originate from unmanaged code without being nested.</span></span> <span data-ttu-id="99760-128">Bu durumda, bir [EnterRuntime](ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](ihosttaskmanager-leaveruntime-method.md)veya ve çağrısı sayısı ile yapılan çağrı `ReverseLeaveRuntime` `ReverseEnterRuntime` sayısına eşit değildir `ReverseLeaveRuntime` .</span><span class="sxs-lookup"><span data-stu-id="99760-128">In this case, there is no call to [EnterRuntime](ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](ihosttaskmanager-leaveruntime-method.md), or `ReverseLeaveRuntime`, and the number of calls to `ReverseEnterRuntime` does not equal the number of calls to `ReverseLeaveRuntime`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99760-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="99760-129">Requirements</span></span>  

 <span data-ttu-id="99760-130">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="99760-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99760-131">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="99760-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="99760-132">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="99760-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="99760-133">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99760-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99760-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="99760-134">See also</span></span>

- [<span data-ttu-id="99760-135">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="99760-135">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="99760-136">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="99760-136">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="99760-137">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="99760-137">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="99760-138">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="99760-138">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
