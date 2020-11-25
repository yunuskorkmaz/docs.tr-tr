---
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
ms.openlocfilehash: e2624f5fce168662fac8fd5f4324617c7acf802c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729557"
---
# <a name="ihostgcmanagersuspensionending-method"></a><span data-ttu-id="ac53e-102">IHostGCManager::SuspensionEnding Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ac53e-102">IHostGCManager::SuspensionEnding Method</span></span>

<span data-ttu-id="ac53e-103">Ana bilgisayara ortak dil çalışma zamanının (CLR) bir çöp toplama işlemi için askıya alınmış iş parçacıklarında görevlerin yürütülmesini sürdürmesinin devam ettirdiğinizi bildirir.</span><span class="sxs-lookup"><span data-stu-id="ac53e-103">Notifies the host that the common language runtime (CLR) is resuming execution of tasks on threads that had been suspended for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac53e-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="ac53e-104">Syntax</span></span>  
  
```cpp  
HRESULT SuspensionEnding (  
    [in] DWORD generation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ac53e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ac53e-105">Parameters</span></span>  

 `generation`  
 <span data-ttu-id="ac53e-106">'ndaki İş parçacığının devam etmesinden önce son kullanılan çöp toplama oluşturma.</span><span class="sxs-lookup"><span data-stu-id="ac53e-106">[in] The garbage collection generation that is just finishing, from which the thread is resuming.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ac53e-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ac53e-107">Return Value</span></span>  
  
|<span data-ttu-id="ac53e-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ac53e-108">HRESULT</span></span>|<span data-ttu-id="ac53e-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ac53e-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ac53e-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="ac53e-110">S_OK</span></span>|<span data-ttu-id="ac53e-111">`SuspensionEnding` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="ac53e-111">`SuspensionEnding` returned successfully.</span></span>|  
|<span data-ttu-id="ac53e-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ac53e-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ac53e-113">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="ac53e-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ac53e-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ac53e-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ac53e-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="ac53e-115">The call timed out.</span></span>|  
|<span data-ttu-id="ac53e-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ac53e-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ac53e-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="ac53e-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ac53e-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ac53e-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ac53e-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="ac53e-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ac53e-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ac53e-120">E_FAIL</span></span>|<span data-ttu-id="ac53e-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="ac53e-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ac53e-122">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="ac53e-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ac53e-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="ac53e-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ac53e-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ac53e-124">Remarks</span></span>  

 <span data-ttu-id="ac53e-125">CLR, `SuspensionEnding` bir atık toplama gerçekleştirdikten sonra, Konağı iş parçacığının yürütmeyi sürdürmesini bildirmek için çağırır.</span><span class="sxs-lookup"><span data-stu-id="ac53e-125">The CLR calls `SuspensionEnding` after it performs a garbage collection, to inform the host that the thread is resuming execution.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="ac53e-126">Yöntem çağrısının yapıldığı iş parçacığını yeniden zamanlamayın.</span><span class="sxs-lookup"><span data-stu-id="ac53e-126">Do not reschedule the thread the method call was made from.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac53e-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ac53e-127">Requirements</span></span>  

 <span data-ttu-id="ac53e-128">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac53e-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac53e-129">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ac53e-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ac53e-130">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="ac53e-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ac53e-131">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac53e-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac53e-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ac53e-132">See also</span></span>

- [<span data-ttu-id="ac53e-133">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ac53e-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="ac53e-134">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ac53e-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="ac53e-135">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ac53e-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="ac53e-136">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ac53e-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="ac53e-137">IHostGCManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ac53e-137">IHostGCManager Interface</span></span>](ihostgcmanager-interface.md)
