---
title: IHostTaskManager::SetCLRTaskManager Yöntemi
ms.date: 03/30/2017
api_name:
- IHostTaskManager.SetCLRTaskManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::SetCLRTaskManager
helpviewer_keywords:
- IHostTaskManager::SetCLRTaskManager method [.NET Framework hosting]
- SetCLRTaskManager method [.NET Framework hosting]
ms.assetid: ec90ee83-bd4b-408b-9274-62a923ab86a1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4a93efc0701248f8e4ef930261b31b3ce948647a
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57484933"
---
# <a name="ihosttaskmanagersetclrtaskmanager-method"></a><span data-ttu-id="caffd-102">IHostTaskManager::SetCLRTaskManager Yöntemi</span><span class="sxs-lookup"><span data-stu-id="caffd-102">IHostTaskManager::SetCLRTaskManager Method</span></span>
<span data-ttu-id="caffd-103">Bir arabirim işaretçisi ile ana bilgisayarının sağladığı bir [Iclrtaskmanager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md) ortak dil çalışma zamanı tarafından (CLR) uygulanan örnek.</span><span class="sxs-lookup"><span data-stu-id="caffd-103">Provides the host with an interface pointer to an [ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md) instance implemented by the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="caffd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="caffd-104">Syntax</span></span>  
  
```  
HRESULT SetCLRTaskManager (  
    [in] ICLRTaskManager *pManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="caffd-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="caffd-105">Parameters</span></span>  
 `pManager`  
 <span data-ttu-id="caffd-106">[in] Bir işaretçi bir `ICLRTaskManager` ortak dil çalışma zamanı tarafından uygulanan örnek.</span><span class="sxs-lookup"><span data-stu-id="caffd-106">[in] A pointer to an `ICLRTaskManager` instance implemented by the common language runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="caffd-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="caffd-107">Return Value</span></span>  
  
|<span data-ttu-id="caffd-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="caffd-108">HRESULT</span></span>|<span data-ttu-id="caffd-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="caffd-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="caffd-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="caffd-110">S_OK</span></span>|<span data-ttu-id="caffd-111">`SetCLRTaskManager` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="caffd-111">`SetCLRTaskManager` returned successfully.</span></span>|  
|<span data-ttu-id="caffd-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="caffd-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="caffd-113">CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="caffd-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="caffd-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="caffd-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="caffd-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="caffd-115">The call timed out.</span></span>|  
|<span data-ttu-id="caffd-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="caffd-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="caffd-117">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="caffd-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="caffd-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="caffd-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="caffd-119">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="caffd-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="caffd-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="caffd-120">E_FAIL</span></span>|<span data-ttu-id="caffd-121">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="caffd-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="caffd-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="caffd-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="caffd-123">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="caffd-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="caffd-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="caffd-124">Remarks</span></span>  
 <span data-ttu-id="caffd-125">Çalışma zamanı çağrıları `SetCLRTaskManager` konak bir arabirim işaretçisine sağlamak için bir `ICLRTaskManager` örneği.</span><span class="sxs-lookup"><span data-stu-id="caffd-125">The runtime calls `SetCLRTaskManager` to provide the host with an interface pointer to an `ICLRTaskManager` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="caffd-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="caffd-126">Requirements</span></span>  
 <span data-ttu-id="caffd-127">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="caffd-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="caffd-128">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="caffd-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="caffd-129">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="caffd-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="caffd-130">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="caffd-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="caffd-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="caffd-131">See also</span></span>
- [<span data-ttu-id="caffd-132">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="caffd-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="caffd-133">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="caffd-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="caffd-134">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="caffd-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="caffd-135">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="caffd-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
