---
title: "ICLRTask::LocksHeld Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRTask.LocksHeld
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRTask::LocksHeld
helpviewer_keywords:
- LocksHeld method [.NET Framework hosting]
- ICLRTask::LocksHeld method [.NET Framework hosting]
ms.assetid: e88a4dc3-02cc-4703-a474-292b71c40657
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2d51fded9f2e475759f2912aea659d272ce08855
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrtasklocksheld-method"></a><span data-ttu-id="54903-102">ICLRTask::LocksHeld Yöntemi</span><span class="sxs-lookup"><span data-stu-id="54903-102">ICLRTask::LocksHeld Method</span></span>
<span data-ttu-id="54903-103">Şu anda görevi tutulan kilitleri sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="54903-103">Gets the number of locks currently held on the task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54903-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="54903-104">Syntax</span></span>  
  
```  
HRESULT LocksHeld (  
    [out] SIZE_T *pLockCount  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="54903-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="54903-105">Parameters</span></span>  
 `pLockCount`  
 <span data-ttu-id="54903-106">[out] Görevi yöntem çağrısının aynı anda tutulan kilit sayısı.</span><span class="sxs-lookup"><span data-stu-id="54903-106">[out] The number of locks held on the task at the time of the method call.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="54903-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="54903-107">Return Value</span></span>  
  
|<span data-ttu-id="54903-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="54903-108">HRESULT</span></span>|<span data-ttu-id="54903-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="54903-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="54903-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="54903-110">S_OK</span></span>|<span data-ttu-id="54903-111">`LocksHeld`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="54903-111">`LocksHeld` returned successfully.</span></span>|  
|<span data-ttu-id="54903-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="54903-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="54903-113">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="54903-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="54903-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="54903-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="54903-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="54903-115">The call timed out.</span></span>|  
|<span data-ttu-id="54903-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="54903-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="54903-117">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="54903-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="54903-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="54903-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="54903-119">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="54903-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="54903-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="54903-120">E_FAIL</span></span>|<span data-ttu-id="54903-121">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="54903-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="54903-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="54903-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="54903-123">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="54903-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="54903-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="54903-124">Requirements</span></span>  
 <span data-ttu-id="54903-125">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="54903-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54903-126">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="54903-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="54903-127">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="54903-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="54903-128">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54903-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54903-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="54903-129">See Also</span></span>  
 [<span data-ttu-id="54903-130">Iclrtask arabirimi</span><span class="sxs-lookup"><span data-stu-id="54903-130">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="54903-131">Iclrtaskmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="54903-131">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="54903-132">Ihosttask arabirimi</span><span class="sxs-lookup"><span data-stu-id="54903-132">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="54903-133">Ihosttaskmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="54903-133">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
