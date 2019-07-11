---
title: ICLRTask::SwitchOut Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRTask.SwitchOut
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::SwitchOut
helpviewer_keywords:
- ICLRTask::SwitchOut method [.NET Framework hosting]
- SwitchOut method [.NET Framework hosting]
ms.assetid: b6fb168c-b24b-4ecf-a390-2b5ba3317ae6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 21e77b781c382cbcab79a93a0c58edd4f07690b2
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67770395"
---
# <a name="iclrtaskswitchout-method"></a><span data-ttu-id="88055-102">ICLRTask::SwitchOut Yöntemi</span><span class="sxs-lookup"><span data-stu-id="88055-102">ICLRTask::SwitchOut Method</span></span>
<span data-ttu-id="88055-103">Görev geçerli tarafından temsil edilen ortak dil çalışma zamanı (CLR) bildirir [Iclrtask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) örneği duruma dönerken artık değildir.</span><span class="sxs-lookup"><span data-stu-id="88055-103">Notifies the common language runtime (CLR) that the task represented by the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance is no longer in an operable state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88055-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="88055-104">Syntax</span></span>  
  
```cpp  
HRESULT SwitchOut ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="88055-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="88055-105">Return Value</span></span>  
  
|<span data-ttu-id="88055-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="88055-106">HRESULT</span></span>|<span data-ttu-id="88055-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="88055-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="88055-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="88055-108">S_OK</span></span>|<span data-ttu-id="88055-109">`SwitchOut` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="88055-109">`SwitchOut` returned successfully.</span></span>|  
|<span data-ttu-id="88055-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="88055-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="88055-111">CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="88055-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="88055-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="88055-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="88055-113">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="88055-113">The call timed out.</span></span>|  
|<span data-ttu-id="88055-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="88055-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="88055-115">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="88055-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="88055-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="88055-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="88055-117">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="88055-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="88055-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="88055-118">E_FAIL</span></span>|<span data-ttu-id="88055-119">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="88055-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="88055-120">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="88055-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="88055-121">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="88055-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="88055-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="88055-122">Remarks</span></span>  
 <span data-ttu-id="88055-123">Bir konak çağırır `SwitchOut` CLR, geçici olarak görev yürütülürken durduruldu olduğunu bildirmek için geçerli `ICLRTask` örneğinin temsil ettiği ve görevi yeniden zamanlanır.</span><span class="sxs-lookup"><span data-stu-id="88055-123">A host calls `SwitchOut` to inform the CLR that it has temporarily stopped executing the task that the current `ICLRTask` instance represents, and will reschedule the task.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88055-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="88055-124">Requirements</span></span>  
 <span data-ttu-id="88055-125">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="88055-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88055-126">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="88055-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="88055-127">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="88055-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="88055-128">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="88055-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88055-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="88055-129">See also</span></span>

- [<span data-ttu-id="88055-130">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="88055-130">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="88055-131">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="88055-131">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="88055-132">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="88055-132">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="88055-133">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="88055-133">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
