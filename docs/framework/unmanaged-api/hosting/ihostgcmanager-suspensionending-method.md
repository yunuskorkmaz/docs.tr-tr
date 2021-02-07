---
description: 'Daha fazla bilgi edinin: IHostGCManager:: SuspensionEnding yöntemi'
title: IHostGCManager::SuspensionEnding Yöntemi
ms.date: 03/30/2017
api_name:
- IHostGCManager.SuspensionEnding
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostGCManager::SuspensionEnding
helpviewer_keywords:
- SuspensionEnding method, IHostGCManager interface [.NET Framework hosting]
- IHostGCManager::SuspensionEnding method [.NET Framework hosting]
ms.assetid: 8849a1db-17f0-44b7-880a-bd36d431eb91
topic_type:
- apiref
ms.openlocfilehash: 43ec3db76e6e6448719f9c40ef2476da4e2ccf9c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708630"
---
# <a name="ihostgcmanagersuspensionending-method"></a><span data-ttu-id="a51cb-103">IHostGCManager::SuspensionEnding Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a51cb-103">IHostGCManager::SuspensionEnding Method</span></span>

<span data-ttu-id="a51cb-104">Ana bilgisayara ortak dil çalışma zamanının (CLR) bir çöp toplama işlemi için askıya alınmış iş parçacıklarında görevlerin yürütülmesini sürdürmesinin devam ettirdiğinizi bildirir.</span><span class="sxs-lookup"><span data-stu-id="a51cb-104">Notifies the host that the common language runtime (CLR) is resuming execution of tasks on threads that had been suspended for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a51cb-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a51cb-105">Syntax</span></span>  
  
```cpp  
HRESULT SuspensionEnding (  
    [in] DWORD generation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a51cb-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a51cb-106">Parameters</span></span>  

 `generation`  
 <span data-ttu-id="a51cb-107">'ndaki İş parçacığının devam etmesinden önce son kullanılan çöp toplama oluşturma.</span><span class="sxs-lookup"><span data-stu-id="a51cb-107">[in] The garbage collection generation that is just finishing, from which the thread is resuming.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a51cb-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a51cb-108">Return Value</span></span>  
  
|<span data-ttu-id="a51cb-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a51cb-109">HRESULT</span></span>|<span data-ttu-id="a51cb-110">Description</span><span class="sxs-lookup"><span data-stu-id="a51cb-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a51cb-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="a51cb-111">S_OK</span></span>|<span data-ttu-id="a51cb-112">`SuspensionEnding` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="a51cb-112">`SuspensionEnding` returned successfully.</span></span>|  
|<span data-ttu-id="a51cb-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a51cb-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a51cb-114">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="a51cb-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a51cb-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a51cb-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a51cb-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="a51cb-116">The call timed out.</span></span>|  
|<span data-ttu-id="a51cb-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a51cb-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a51cb-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="a51cb-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a51cb-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a51cb-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a51cb-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="a51cb-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a51cb-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a51cb-121">E_FAIL</span></span>|<span data-ttu-id="a51cb-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="a51cb-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a51cb-123">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="a51cb-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a51cb-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="a51cb-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a51cb-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a51cb-125">Remarks</span></span>  

 <span data-ttu-id="a51cb-126">CLR, `SuspensionEnding` bir atık toplama gerçekleştirdikten sonra, Konağı iş parçacığının yürütmeyi sürdürmesini bildirmek için çağırır.</span><span class="sxs-lookup"><span data-stu-id="a51cb-126">The CLR calls `SuspensionEnding` after it performs a garbage collection, to inform the host that the thread is resuming execution.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a51cb-127">Yöntem çağrısının yapıldığı iş parçacığını yeniden zamanlamayın.</span><span class="sxs-lookup"><span data-stu-id="a51cb-127">Do not reschedule the thread the method call was made from.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a51cb-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a51cb-128">Requirements</span></span>  

 <span data-ttu-id="a51cb-129">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a51cb-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a51cb-130">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a51cb-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a51cb-131">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="a51cb-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a51cb-132">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a51cb-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a51cb-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a51cb-133">See also</span></span>

- [<span data-ttu-id="a51cb-134">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a51cb-134">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="a51cb-135">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a51cb-135">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="a51cb-136">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a51cb-136">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="a51cb-137">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a51cb-137">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="a51cb-138">IHostGCManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a51cb-138">IHostGCManager Interface</span></span>](ihostgcmanager-interface.md)
