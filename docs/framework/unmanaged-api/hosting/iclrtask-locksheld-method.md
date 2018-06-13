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
ms.openlocfilehash: b49590fba64fc0372d671c009ad587b441e85343
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434235"
---
# <a name="iclrtasklocksheld-method"></a><span data-ttu-id="71c1e-102">ICLRTask::LocksHeld Yöntemi</span><span class="sxs-lookup"><span data-stu-id="71c1e-102">ICLRTask::LocksHeld Method</span></span>
<span data-ttu-id="71c1e-103">Şu anda görevi tutulan kilitleri sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="71c1e-103">Gets the number of locks currently held on the task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71c1e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="71c1e-104">Syntax</span></span>  
  
```  
HRESULT LocksHeld (  
    [out] SIZE_T *pLockCount  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="71c1e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="71c1e-105">Parameters</span></span>  
 `pLockCount`  
 <span data-ttu-id="71c1e-106">[out] Görevi yöntem çağrısının aynı anda tutulan kilit sayısı.</span><span class="sxs-lookup"><span data-stu-id="71c1e-106">[out] The number of locks held on the task at the time of the method call.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="71c1e-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="71c1e-107">Return Value</span></span>  
  
|<span data-ttu-id="71c1e-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="71c1e-108">HRESULT</span></span>|<span data-ttu-id="71c1e-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="71c1e-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="71c1e-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="71c1e-110">S_OK</span></span>|<span data-ttu-id="71c1e-111">`LocksHeld` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="71c1e-111">`LocksHeld` returned successfully.</span></span>|  
|<span data-ttu-id="71c1e-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="71c1e-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="71c1e-113">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="71c1e-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="71c1e-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="71c1e-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="71c1e-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="71c1e-115">The call timed out.</span></span>|  
|<span data-ttu-id="71c1e-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="71c1e-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="71c1e-117">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="71c1e-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="71c1e-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="71c1e-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="71c1e-119">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="71c1e-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="71c1e-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="71c1e-120">E_FAIL</span></span>|<span data-ttu-id="71c1e-121">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="71c1e-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="71c1e-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="71c1e-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="71c1e-123">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="71c1e-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="71c1e-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="71c1e-124">Requirements</span></span>  
 <span data-ttu-id="71c1e-125">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="71c1e-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71c1e-126">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="71c1e-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="71c1e-127">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="71c1e-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="71c1e-128">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="71c1e-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71c1e-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="71c1e-129">See Also</span></span>  
 [<span data-ttu-id="71c1e-130">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="71c1e-130">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="71c1e-131">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="71c1e-131">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="71c1e-132">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="71c1e-132">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="71c1e-133">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="71c1e-133">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
