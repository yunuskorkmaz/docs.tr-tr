---
title: IHostTask::SetCLRTask Yöntemi
ms.date: 03/30/2017
api_name:
- IHostTask.SetCLRTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::SetCLRTask
helpviewer_keywords:
- SetCLRTask method [.NET Framework hosting]
- IHostTask::SetCLRTask method [.NET Framework hosting]
ms.assetid: e9d39c80-41a1-49e7-bb5e-ea3433bfb5d7
topic_type:
- apiref
ms.openlocfilehash: bbb563a304e3ff7cdba3dfe7e394da9cf138ff10
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121364"
---
# <a name="ihosttasksetclrtask-method"></a><span data-ttu-id="56272-102">IHostTask::SetCLRTask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="56272-102">IHostTask::SetCLRTask Method</span></span>
<span data-ttu-id="56272-103">Bir `ICLRTask` örneğini geçerli [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) örneğiyle ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="56272-103">Associates an `ICLRTask` instance with the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56272-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="56272-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCLRTask (  
    [in] ICLRTask *pCLRTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="56272-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="56272-105">Parameters</span></span>  
 `pCLRTask`  
 <span data-ttu-id="56272-106">'ndaki Geçerli `IHostTask` örneğiyle ilişkilendirilecek `ICLRTask` örneğine yönelik bir arabirim işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="56272-106">[in] An interface pointer to the `ICLRTask` instance to be associated with the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="56272-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="56272-107">Return Value</span></span>  
  
|<span data-ttu-id="56272-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="56272-108">HRESULT</span></span>|<span data-ttu-id="56272-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="56272-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="56272-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="56272-110">S_OK</span></span>|<span data-ttu-id="56272-111">`SetCLRTask` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="56272-111">`SetCLRTask` returned successfully.</span></span>|  
|<span data-ttu-id="56272-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="56272-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="56272-113">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="56272-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="56272-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="56272-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="56272-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="56272-115">The call timed out.</span></span>|  
|<span data-ttu-id="56272-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="56272-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="56272-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="56272-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="56272-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="56272-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="56272-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="56272-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="56272-120">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="56272-120">E_FAIL</span></span>|<span data-ttu-id="56272-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="56272-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="56272-122">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="56272-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="56272-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="56272-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="56272-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="56272-124">Remarks</span></span>  
 <span data-ttu-id="56272-125">CLR, bir `ICLRTask` örneğini [IHostTaskManager:: CreateTask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-createtask-method.md)çağrısıyla oluşturulan geçerli `IHostTask` örneğiyle ilişkilendirmek için `SetCLRTask` çağırır.</span><span class="sxs-lookup"><span data-stu-id="56272-125">The CLR calls `SetCLRTask` to associate an `ICLRTask` instance with the current `IHostTask` instance, which was created by a call to [IHostTaskManager::CreateTask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-createtask-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56272-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="56272-126">Requirements</span></span>  
 <span data-ttu-id="56272-127">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="56272-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56272-128">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="56272-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="56272-129">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="56272-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="56272-130">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56272-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56272-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="56272-131">See also</span></span>

- [<span data-ttu-id="56272-132">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="56272-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="56272-133">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="56272-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="56272-134">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="56272-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="56272-135">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="56272-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
