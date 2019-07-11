---
title: ICLRTaskManager::CreateTask Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRTaskManager.CreateTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager::CreateTask
helpviewer_keywords:
- ICLRTaskManager::CreateTask method [.NET Framework hosting]
- CreateTask method, ICLRTaskManager interface [.NET Framework hosting]
ms.assetid: eea570d9-2e53-4320-9ea0-eb777bf9dcf3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 804a295cf74067eb23ed8e8c860252a1f2fcf5d5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67770195"
---
# <a name="iclrtaskmanagercreatetask-method"></a><span data-ttu-id="b3c32-102">ICLRTaskManager::CreateTask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b3c32-102">ICLRTaskManager::CreateTask Method</span></span>
<span data-ttu-id="b3c32-103">Açıkça ortak dil çalışma zamanı (CLR) yeni bir görev oluşturmasını ister.</span><span class="sxs-lookup"><span data-stu-id="b3c32-103">Requests explicitly that the common language runtime (CLR) create a new task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3c32-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b3c32-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateTask (  
    [out] ICLRTask **pTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b3c32-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b3c32-105">Parameters</span></span>  
 `pTask`  
 <span data-ttu-id="b3c32-106">[out] Yeni oluşturulan adresini bir işaretçiye [Iclrtask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md), ya da görev oluşturulamadı yoksa null.</span><span class="sxs-lookup"><span data-stu-id="b3c32-106">[out] A pointer to the address of a newly created [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md), or null, if the task could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b3c32-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b3c32-107">Return Value</span></span>  
  
|<span data-ttu-id="b3c32-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b3c32-108">HRESULT</span></span>|<span data-ttu-id="b3c32-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b3c32-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b3c32-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="b3c32-110">S_OK</span></span>|<span data-ttu-id="b3c32-111">Yöntemi başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="b3c32-111">The method returned successfully.</span></span>|  
|<span data-ttu-id="b3c32-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b3c32-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b3c32-113">CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="b3c32-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b3c32-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b3c32-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b3c32-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="b3c32-115">The call timed out.</span></span>|  
|<span data-ttu-id="b3c32-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b3c32-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b3c32-117">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="b3c32-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b3c32-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b3c32-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b3c32-119">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="b3c32-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b3c32-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b3c32-120">E_FAIL</span></span>|<span data-ttu-id="b3c32-121">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="b3c32-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b3c32-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="b3c32-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b3c32-123">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="b3c32-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="b3c32-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="b3c32-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="b3c32-125">İstenen kaynağı ayırmak yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="b3c32-125">Not enough memory is available to allocate the requested resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b3c32-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b3c32-126">Remarks</span></span>  
 <span data-ttu-id="b3c32-127">Kullanıcı kodu bir iş parçacığı türleri kullanarak CLR başlatma sırasında otomatik olarak yeni bir görev oluşturur <xref:System.Threading> ad alanı veya iş parçacığı havuzunun boyutunu zaman yükseltilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b3c32-127">The CLR creates a new task automatically upon initialization, when user code creates a thread by using types in the <xref:System.Threading> namespace, or when the size of the thread pool is increased.</span></span> <span data-ttu-id="b3c32-128">Yönetilmeyen kod için yönetilen bir işleve bir çağrı yaptığında görevleri de oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b3c32-128">It also creates tasks when unmanaged code makes a call to a managed function.</span></span>  
  
 <span data-ttu-id="b3c32-129">`CreateTask` CLR yeni bir görev oluşturma açık bir istekte bulunmak konak sağlar.</span><span class="sxs-lookup"><span data-stu-id="b3c32-129">`CreateTask` allows the host to make an explicit request that the CLR create a new task.</span></span> <span data-ttu-id="b3c32-130">Örneğin, ana veri yapılarını preinitialize için bu yöntemi çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b3c32-130">For example, the host can invoke this method to preinitialize data structures.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b3c32-131">Yeni görevin askıya alınmış durumda döndürülür ve konak açıkça çağıran kadar askıda kalır [Ihosttask::Start](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md).</span><span class="sxs-lookup"><span data-stu-id="b3c32-131">The new task is returned in a suspended state and remains suspended until the host explicitly calls [IHostTask::Start](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3c32-132">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b3c32-132">Requirements</span></span>  
 <span data-ttu-id="b3c32-133">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b3c32-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3c32-134">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b3c32-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b3c32-135">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="b3c32-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b3c32-136">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3c32-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3c32-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b3c32-137">See also</span></span>

- [<span data-ttu-id="b3c32-138">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b3c32-138">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="b3c32-139">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b3c32-139">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="b3c32-140">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b3c32-140">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="b3c32-141">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b3c32-141">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
