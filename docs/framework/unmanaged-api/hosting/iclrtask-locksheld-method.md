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
ms.openlocfilehash: 3f548d8b19a76aaccbae276dd63f091e4488690b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59106814"
---
# <a name="iclrtasklocksheld-method"></a><span data-ttu-id="3f1ec-102">ICLRTask::LocksHeld Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3f1ec-102">ICLRTask::LocksHeld Method</span></span>
<span data-ttu-id="3f1ec-103">Şu anda görevi tutulan kilitlerin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="3f1ec-103">Gets the number of locks currently held on the task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f1ec-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3f1ec-104">Syntax</span></span>  
  
```  
HRESULT LocksHeld (  
    [out] SIZE_T *pLockCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3f1ec-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3f1ec-105">Parameters</span></span>  
 `pLockCount`  
 <span data-ttu-id="3f1ec-106">[out] Yöntem çağrısının yapıldığı sırada görevi tutulan kilitlerin sayısı.</span><span class="sxs-lookup"><span data-stu-id="3f1ec-106">[out] The number of locks held on the task at the time of the method call.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3f1ec-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3f1ec-107">Return Value</span></span>  
  
|<span data-ttu-id="3f1ec-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3f1ec-108">HRESULT</span></span>|<span data-ttu-id="3f1ec-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3f1ec-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3f1ec-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="3f1ec-110">S_OK</span></span>|`LocksHeld` <span data-ttu-id="3f1ec-111">başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="3f1ec-111">returned successfully.</span></span>|  
|<span data-ttu-id="3f1ec-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3f1ec-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3f1ec-113">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="3f1ec-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3f1ec-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3f1ec-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3f1ec-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="3f1ec-115">The call timed out.</span></span>|  
|<span data-ttu-id="3f1ec-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3f1ec-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3f1ec-117">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="3f1ec-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3f1ec-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3f1ec-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3f1ec-119">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="3f1ec-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3f1ec-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3f1ec-120">E_FAIL</span></span>|<span data-ttu-id="3f1ec-121">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="3f1ec-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3f1ec-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="3f1ec-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3f1ec-123">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="3f1ec-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3f1ec-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3f1ec-124">Requirements</span></span>  
 <span data-ttu-id="3f1ec-125">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f1ec-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f1ec-126">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3f1ec-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3f1ec-127">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="3f1ec-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="3f1ec-128">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="3f1ec-128">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3f1ec-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3f1ec-129">See also</span></span>

- [<span data-ttu-id="3f1ec-130">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3f1ec-130">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="3f1ec-131">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3f1ec-131">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="3f1ec-132">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3f1ec-132">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="3f1ec-133">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3f1ec-133">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
