---
title: IHostTaskManager::GetCurrentTask Metodu
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bd92b03d87672875661bb5e5241c6fa46f099ce6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54732472"
---
# <a name="ihosttaskmanagergetcurrenttask-method"></a><span data-ttu-id="0c162-102">IHostTaskManager::GetCurrentTask Metodu</span><span class="sxs-lookup"><span data-stu-id="0c162-102">IHostTaskManager::GetCurrentTask Method</span></span>
<span data-ttu-id="0c162-103">Bu Çağrının yapıldığı işletim sistemi iş parçacığı üzerinde şu anda yürütülmekte olan görev için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="0c162-103">Gets an interface pointer to the task that is currently executing on the operating system thread from which this call is made.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c162-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0c162-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentTask (  
    [out] IHostTask **pTask  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0c162-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0c162-105">Parameters</span></span>  
 `pTask`  
 <span data-ttu-id="0c162-106">[out] Adresine bir işaretçi bir [Ihosttask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) hiçbir görev şu anda yürütülüyorsa o anda yürütülen görev veya null temsil eden örnek.</span><span class="sxs-lookup"><span data-stu-id="0c162-106">[out] A pointer to the address of an [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance that represents the currently executing task, or null, if no task is currently executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0c162-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0c162-107">Return Value</span></span>  
  
|<span data-ttu-id="0c162-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0c162-108">HRESULT</span></span>|<span data-ttu-id="0c162-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0c162-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0c162-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="0c162-110">S_OK</span></span>|<span data-ttu-id="0c162-111">`GetCurrentTask` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="0c162-111">`GetCurrentTask` returned successfully.</span></span>|  
|<span data-ttu-id="0c162-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0c162-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0c162-113">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="0c162-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0c162-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0c162-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0c162-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="0c162-115">The call timed out.</span></span>|  
|<span data-ttu-id="0c162-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0c162-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0c162-117">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="0c162-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0c162-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0c162-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0c162-119">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="0c162-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0c162-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0c162-120">E_FAIL</span></span>|<span data-ttu-id="0c162-121">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="0c162-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0c162-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="0c162-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0c162-123">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="0c162-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="0c162-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="0c162-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="0c162-125">`GetCurrentTask` konağın denetimin dışında kalan bir işletim sistemi iş parçacığı üzerinde çağrılmış.</span><span class="sxs-lookup"><span data-stu-id="0c162-125">`GetCurrentTask` was called on an operating system thread outside the control of the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0c162-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0c162-126">Remarks</span></span>  
 <span data-ttu-id="0c162-127">Konak de ayarlayabilirsiniz `pTask` parametresi null değil başlatmak bir görev CLR girmesini önlemek için.</span><span class="sxs-lookup"><span data-stu-id="0c162-127">The host can also set the `pTask` parameter to null to prevent a task that it did not initiate from entering the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c162-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0c162-128">Requirements</span></span>  
 <span data-ttu-id="0c162-129">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c162-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c162-130">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0c162-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0c162-131">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="0c162-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0c162-132">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c162-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c162-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0c162-133">See also</span></span>
- [<span data-ttu-id="0c162-134">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0c162-134">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="0c162-135">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0c162-135">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="0c162-136">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0c162-136">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="0c162-137">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0c162-137">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
