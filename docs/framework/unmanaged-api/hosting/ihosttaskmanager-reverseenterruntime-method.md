---
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
ms.openlocfilehash: 390a29760c0f3680ca082561607ab678e8bd1e8b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133003"
---
# <a name="ihosttaskmanagerreverseenterruntime-method"></a><span data-ttu-id="96cc5-102">IHostTaskManager::ReverseEnterRuntime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="96cc5-102">IHostTaskManager::ReverseEnterRuntime Method</span></span>
<span data-ttu-id="96cc5-103">Ana bilgisayara, yönetilmeyen koddan ortak dil çalışma zamanı (CLR) için bir çağrının yapıldığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="96cc5-103">Notifies the host that a call is being made into the common language runtime (CLR) from unmanaged code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96cc5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="96cc5-104">Syntax</span></span>  
  
```cpp  
HRESULT ReverseEnterRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="96cc5-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="96cc5-105">Return Value</span></span>  
  
|<span data-ttu-id="96cc5-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="96cc5-106">HRESULT</span></span>|<span data-ttu-id="96cc5-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="96cc5-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="96cc5-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="96cc5-108">S_OK</span></span>|<span data-ttu-id="96cc5-109">`ReverseEnterRuntime` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="96cc5-109">`ReverseEnterRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="96cc5-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="96cc5-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="96cc5-111">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="96cc5-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="96cc5-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="96cc5-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="96cc5-113">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="96cc5-113">The call timed out.</span></span>|  
|<span data-ttu-id="96cc5-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="96cc5-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="96cc5-115">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="96cc5-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="96cc5-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="96cc5-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="96cc5-117">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="96cc5-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="96cc5-118">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="96cc5-118">E_FAIL</span></span>|<span data-ttu-id="96cc5-119">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="96cc5-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="96cc5-120">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="96cc5-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="96cc5-121">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="96cc5-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="96cc5-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="96cc5-122">E_OUTOFMEMORY</span></span>|<span data-ttu-id="96cc5-123">İstenen kaynak ayırmayı tamamlamaya yetecek miktarda bellek yok.</span><span class="sxs-lookup"><span data-stu-id="96cc5-123">Not enough memory is available to complete the requested resource allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="96cc5-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="96cc5-124">Remarks</span></span>  
 <span data-ttu-id="96cc5-125">CLR 'ye yapılan çağrı yönetilen kodda oluşturulan bir dizinden yapılırsa, `ReverseEnterRuntime` her bir çağrı, [ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md)çağrısına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="96cc5-125">If the call into the CLR is made from a sequence that originated in managed code, each call to `ReverseEnterRuntime` corresponds to a call to [ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="96cc5-126">Çağrılar, iç içe kalmadan yönetilmeyen koddan kaynaklanamaz.</span><span class="sxs-lookup"><span data-stu-id="96cc5-126">Calls can originate from unmanaged code without being nested.</span></span> <span data-ttu-id="96cc5-127">Bu durumda, [EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)veya `ReverseLeaveRuntime`çağrısı yoktur ve `ReverseEnterRuntime` yapılan çağrıların sayısı `ReverseLeaveRuntime`çağrısı sayısına eşit değildir.</span><span class="sxs-lookup"><span data-stu-id="96cc5-127">In this case, there is no call to [EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md), or `ReverseLeaveRuntime`, and the number of calls to `ReverseEnterRuntime` does not equal the number of calls to `ReverseLeaveRuntime`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96cc5-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="96cc5-128">Requirements</span></span>  
 <span data-ttu-id="96cc5-129">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96cc5-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96cc5-130">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="96cc5-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="96cc5-131">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="96cc5-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="96cc5-132">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96cc5-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96cc5-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="96cc5-133">See also</span></span>

- [<span data-ttu-id="96cc5-134">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="96cc5-134">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="96cc5-135">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="96cc5-135">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="96cc5-136">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="96cc5-136">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="96cc5-137">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="96cc5-137">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
