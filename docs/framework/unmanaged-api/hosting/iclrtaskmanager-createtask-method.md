---
title: "ICLRTaskManager::CreateTask Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRTaskManager.CreateTask
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRTaskManager::CreateTask
helpviewer_keywords:
- ICLRTaskManager::CreateTask method [.NET Framework hosting]
- CreateTask method, ICLRTaskManager interface [.NET Framework hosting]
ms.assetid: eea570d9-2e53-4320-9ea0-eb777bf9dcf3
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e9e78db6e43397709f913f8f79a617221f98db87
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrtaskmanagercreatetask-method"></a><span data-ttu-id="7ca55-102">ICLRTaskManager::CreateTask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7ca55-102">ICLRTaskManager::CreateTask Method</span></span>
<span data-ttu-id="7ca55-103">Açıkça ortak dil çalışma zamanı (CLR) yeni bir görev oluşturmasını ister.</span><span class="sxs-lookup"><span data-stu-id="7ca55-103">Requests explicitly that the common language runtime (CLR) create a new task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ca55-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7ca55-104">Syntax</span></span>  
  
```  
HRESULT CreateTask (  
    [out] ICLRTask **pTask  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7ca55-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7ca55-105">Parameters</span></span>  
 `pTask`  
 <span data-ttu-id="7ca55-106">[out] Yeni oluşturulan adresini gösteren bir işaretçi [Iclrtask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md), ya da görev oluşturulamadı yoksa null.</span><span class="sxs-lookup"><span data-stu-id="7ca55-106">[out] A pointer to the address of a newly created [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md), or null, if the task could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7ca55-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7ca55-107">Return Value</span></span>  
  
|<span data-ttu-id="7ca55-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7ca55-108">HRESULT</span></span>|<span data-ttu-id="7ca55-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7ca55-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7ca55-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="7ca55-110">S_OK</span></span>|<span data-ttu-id="7ca55-111">Yöntem başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="7ca55-111">The method returned successfully.</span></span>|  
|<span data-ttu-id="7ca55-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7ca55-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7ca55-113">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="7ca55-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7ca55-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7ca55-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7ca55-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="7ca55-115">The call timed out.</span></span>|  
|<span data-ttu-id="7ca55-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7ca55-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7ca55-117">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="7ca55-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7ca55-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7ca55-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7ca55-119">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="7ca55-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7ca55-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7ca55-120">E_FAIL</span></span>|<span data-ttu-id="7ca55-121">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="7ca55-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7ca55-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="7ca55-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7ca55-123">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="7ca55-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="7ca55-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="7ca55-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="7ca55-125">İstenen kaynak ayırmak yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="7ca55-125">Not enough memory is available to allocate the requested resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7ca55-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7ca55-126">Remarks</span></span>  
 <span data-ttu-id="7ca55-127">Kullanıcı kodu türlerinde kullanarak bir iş parçacığı oluşturduğunda CLR başlatma sırasında otomatik olarak yeni bir görev oluşturur <xref:System.Threading> ad alanı veya iş parçacığı havuzunun boyutunu yükseltilmiştir zaman.</span><span class="sxs-lookup"><span data-stu-id="7ca55-127">The CLR creates a new task automatically upon initialization, when user code creates a thread by using types in the <xref:System.Threading> namespace, or when the size of the thread pool is increased.</span></span> <span data-ttu-id="7ca55-128">Yönetilmeyen kod yönetilen işlevi çağrısı yaptığında görevleri de oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7ca55-128">It also creates tasks when unmanaged code makes a call to a managed function.</span></span>  
  
 <span data-ttu-id="7ca55-129">`CreateTask`ana bilgisayarın CLR yeni bir görev oluşturma açık bir istekte bulunun izin verir.</span><span class="sxs-lookup"><span data-stu-id="7ca55-129">`CreateTask` allows the host to make an explicit request that the CLR create a new task.</span></span> <span data-ttu-id="7ca55-130">Örneğin, ana bilgisayar veri yapılarını preinitialize için bu yöntemi çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7ca55-130">For example, the host can invoke this method to preinitialize data structures.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7ca55-131">Yeni görev askıya alınmış durumda döndürülür ve ana bilgisayar açıkça çağırır kadar askıda kalır [Ihosttask::Start](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md).</span><span class="sxs-lookup"><span data-stu-id="7ca55-131">The new task is returned in a suspended state and remains suspended until the host explicitly calls [IHostTask::Start](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ca55-132">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7ca55-132">Requirements</span></span>  
 <span data-ttu-id="7ca55-133">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ca55-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ca55-134">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7ca55-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7ca55-135">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="7ca55-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7ca55-136">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ca55-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ca55-137">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7ca55-137">See Also</span></span>  
 [<span data-ttu-id="7ca55-138">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7ca55-138">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="7ca55-139">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7ca55-139">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="7ca55-140">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7ca55-140">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="7ca55-141">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7ca55-141">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
