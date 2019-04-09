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
ms.openlocfilehash: a215189461bd22011462842bf02ff6c0109119fa
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59090062"
---
# <a name="iclrtaskswitchout-method"></a><span data-ttu-id="d455f-102">ICLRTask::SwitchOut Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d455f-102">ICLRTask::SwitchOut Method</span></span>
<span data-ttu-id="d455f-103">Görev geçerli tarafından temsil edilen ortak dil çalışma zamanı (CLR) bildirir [Iclrtask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) örneği duruma dönerken artık değildir.</span><span class="sxs-lookup"><span data-stu-id="d455f-103">Notifies the common language runtime (CLR) that the task represented by the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance is no longer in an operable state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d455f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d455f-104">Syntax</span></span>  
  
```  
HRESULT SwitchOut ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="d455f-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d455f-105">Return Value</span></span>  
  
|<span data-ttu-id="d455f-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d455f-106">HRESULT</span></span>|<span data-ttu-id="d455f-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d455f-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d455f-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="d455f-108">S_OK</span></span>|`SwitchOut` <span data-ttu-id="d455f-109">başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="d455f-109">returned successfully.</span></span>|  
|<span data-ttu-id="d455f-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d455f-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d455f-111">CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="d455f-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d455f-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d455f-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d455f-113">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="d455f-113">The call timed out.</span></span>|  
|<span data-ttu-id="d455f-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d455f-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d455f-115">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="d455f-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d455f-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d455f-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d455f-117">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="d455f-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d455f-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d455f-118">E_FAIL</span></span>|<span data-ttu-id="d455f-119">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="d455f-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d455f-120">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="d455f-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d455f-121">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="d455f-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d455f-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d455f-122">Remarks</span></span>  
 <span data-ttu-id="d455f-123">Bir konak çağırır `SwitchOut` CLR, geçici olarak görev yürütülürken durduruldu olduğunu bildirmek için geçerli `ICLRTask` örneğinin temsil ettiği ve görevi yeniden zamanlanır.</span><span class="sxs-lookup"><span data-stu-id="d455f-123">A host calls `SwitchOut` to inform the CLR that it has temporarily stopped executing the task that the current `ICLRTask` instance represents, and will reschedule the task.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d455f-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d455f-124">Requirements</span></span>  
 <span data-ttu-id="d455f-125">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d455f-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d455f-126">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d455f-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d455f-127">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="d455f-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="d455f-128">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="d455f-128">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d455f-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d455f-129">See also</span></span>

- [<span data-ttu-id="d455f-130">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d455f-130">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="d455f-131">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d455f-131">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="d455f-132">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d455f-132">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="d455f-133">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d455f-133">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
