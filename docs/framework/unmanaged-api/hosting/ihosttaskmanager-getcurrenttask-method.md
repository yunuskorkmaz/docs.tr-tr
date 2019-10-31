---
title: IHostTaskManager::GetCurrentTask Yöntemi
ms.date: 03/30/2017
api_name:
- IHostTaskManager.GetCurrentTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::GetCurrentTask
helpviewer_keywords:
- GetCurrentTask method, IHostTaskManager interface [.NET Framework hosting]
- IHostTaskManager::GetCurrentTask method [.NET Framework hosting]
ms.assetid: f17bca49-90bd-4dee-a5e1-b9a57ea46f85
topic_type:
- apiref
ms.openlocfilehash: d1d6ddfe7834a1c6f22b9195042d32363d6ea6cc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133049"
---
# <a name="ihosttaskmanagergetcurrenttask-method"></a><span data-ttu-id="09ed3-102">IHostTaskManager::GetCurrentTask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="09ed3-102">IHostTaskManager::GetCurrentTask Method</span></span>
<span data-ttu-id="09ed3-103">Bu çağrının yapıldığı işletim sistemi iş parçacığında yürütülmekte olan göreve yönelik bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="09ed3-103">Gets an interface pointer to the task that is currently executing on the operating system thread from which this call is made.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09ed3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="09ed3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentTask (  
    [out] IHostTask **pTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="09ed3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="09ed3-105">Parameters</span></span>  
 `pTask`  
 <span data-ttu-id="09ed3-106">dışı Şu anda yürütülmekte olan görevi temsil eden bir [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) örneğinin adresine yönelik bir işaretçi veya herhangi bir görev yürütülerek null.</span><span class="sxs-lookup"><span data-stu-id="09ed3-106">[out] A pointer to the address of an [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance that represents the currently executing task, or null, if no task is currently executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="09ed3-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="09ed3-107">Return Value</span></span>  
  
|<span data-ttu-id="09ed3-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="09ed3-108">HRESULT</span></span>|<span data-ttu-id="09ed3-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="09ed3-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="09ed3-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="09ed3-110">S_OK</span></span>|<span data-ttu-id="09ed3-111">`GetCurrentTask` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="09ed3-111">`GetCurrentTask` returned successfully.</span></span>|  
|<span data-ttu-id="09ed3-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="09ed3-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="09ed3-113">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="09ed3-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="09ed3-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="09ed3-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="09ed3-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="09ed3-115">The call timed out.</span></span>|  
|<span data-ttu-id="09ed3-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="09ed3-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="09ed3-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="09ed3-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="09ed3-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="09ed3-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="09ed3-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="09ed3-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="09ed3-120">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="09ed3-120">E_FAIL</span></span>|<span data-ttu-id="09ed3-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="09ed3-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="09ed3-122">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="09ed3-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="09ed3-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="09ed3-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="09ed3-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="09ed3-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="09ed3-125">`GetCurrentTask`, konak denetimi dışındaki bir işletim sistemi iş parçacığında çağrıldı.</span><span class="sxs-lookup"><span data-stu-id="09ed3-125">`GetCurrentTask` was called on an operating system thread outside the control of the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="09ed3-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="09ed3-126">Remarks</span></span>  
 <span data-ttu-id="09ed3-127">Konak, CLR girişini başlatmadığından bir görevi engellemek için `pTask` parametresini null olarak ayarlayabilir.</span><span class="sxs-lookup"><span data-stu-id="09ed3-127">The host can also set the `pTask` parameter to null to prevent a task that it did not initiate from entering the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09ed3-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="09ed3-128">Requirements</span></span>  
 <span data-ttu-id="09ed3-129">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="09ed3-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09ed3-130">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="09ed3-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="09ed3-131">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="09ed3-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="09ed3-132">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09ed3-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09ed3-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="09ed3-133">See also</span></span>

- [<span data-ttu-id="09ed3-134">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="09ed3-134">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="09ed3-135">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="09ed3-135">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="09ed3-136">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="09ed3-136">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="09ed3-137">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="09ed3-137">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
