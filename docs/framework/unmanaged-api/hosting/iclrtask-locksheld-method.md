---
title: ICLRTask::LocksHeld Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRTask.LocksHeld
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::LocksHeld
helpviewer_keywords:
- LocksHeld method [.NET Framework hosting]
- ICLRTask::LocksHeld method [.NET Framework hosting]
ms.assetid: e88a4dc3-02cc-4703-a474-292b71c40657
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 931395a1bb5f516000097f964ce0372a69420d85
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54679636"
---
# <a name="iclrtasklocksheld-method"></a><span data-ttu-id="2041a-102">ICLRTask::LocksHeld Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2041a-102">ICLRTask::LocksHeld Method</span></span>
<span data-ttu-id="2041a-103">Şu anda görevi tutulan kilitlerin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="2041a-103">Gets the number of locks currently held on the task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2041a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2041a-104">Syntax</span></span>  
  
```  
HRESULT LocksHeld (  
    [out] SIZE_T *pLockCount  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2041a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2041a-105">Parameters</span></span>  
 `pLockCount`  
 <span data-ttu-id="2041a-106">[out] Yöntem çağrısının yapıldığı sırada görevi tutulan kilitlerin sayısı.</span><span class="sxs-lookup"><span data-stu-id="2041a-106">[out] The number of locks held on the task at the time of the method call.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2041a-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2041a-107">Return Value</span></span>  
  
|<span data-ttu-id="2041a-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2041a-108">HRESULT</span></span>|<span data-ttu-id="2041a-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2041a-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2041a-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="2041a-110">S_OK</span></span>|<span data-ttu-id="2041a-111">`LocksHeld` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="2041a-111">`LocksHeld` returned successfully.</span></span>|  
|<span data-ttu-id="2041a-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2041a-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2041a-113">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="2041a-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2041a-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2041a-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2041a-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="2041a-115">The call timed out.</span></span>|  
|<span data-ttu-id="2041a-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2041a-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2041a-117">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="2041a-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2041a-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2041a-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2041a-119">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="2041a-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2041a-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2041a-120">E_FAIL</span></span>|<span data-ttu-id="2041a-121">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="2041a-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2041a-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="2041a-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2041a-123">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="2041a-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2041a-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2041a-124">Requirements</span></span>  
 <span data-ttu-id="2041a-125">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2041a-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2041a-126">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2041a-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2041a-127">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="2041a-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2041a-128">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2041a-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2041a-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2041a-129">See also</span></span>
- [<span data-ttu-id="2041a-130">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2041a-130">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="2041a-131">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2041a-131">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="2041a-132">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2041a-132">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="2041a-133">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2041a-133">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
