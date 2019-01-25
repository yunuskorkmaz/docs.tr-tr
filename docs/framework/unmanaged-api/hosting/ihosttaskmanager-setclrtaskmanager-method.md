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
ms.openlocfilehash: 0d18ccc18afa3bb3b7079139886c308882b2efc8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54616660"
---
# <a name="ihosttaskmanagersetclrtaskmanager-method"></a><span data-ttu-id="32a30-102">IHostTaskManager::SetCLRTaskManager Yöntemi</span><span class="sxs-lookup"><span data-stu-id="32a30-102">IHostTaskManager::SetCLRTaskManager Method</span></span>
<span data-ttu-id="32a30-103">Bir arabirim işaretçisi ile ana bilgisayarının sağladığı bir [Iclrtaskmanager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md) ortak dil çalışma zamanı tarafından (CLR) uygulanan örnek.</span><span class="sxs-lookup"><span data-stu-id="32a30-103">Provides the host with an interface pointer to an [ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md) instance implemented by the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32a30-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="32a30-104">Syntax</span></span>  
  
```  
HRESULT SetCLRTaskManager (  
    [in] ICLRTaskManager *pManager  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="32a30-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="32a30-105">Parameters</span></span>  
 `pManager`  
 <span data-ttu-id="32a30-106">[in] Bir işaretçi bir `ICLRTaskManager` ortak dil çalışma zamanı tarafından uygulanan örnek.</span><span class="sxs-lookup"><span data-stu-id="32a30-106">[in] A pointer to an `ICLRTaskManager` instance implemented by the common language runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="32a30-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="32a30-107">Return Value</span></span>  
  
|<span data-ttu-id="32a30-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="32a30-108">HRESULT</span></span>|<span data-ttu-id="32a30-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="32a30-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="32a30-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="32a30-110">S_OK</span></span>|<span data-ttu-id="32a30-111">`SetCLRTaskManager` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="32a30-111">`SetCLRTaskManager` returned successfully.</span></span>|  
|<span data-ttu-id="32a30-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="32a30-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="32a30-113">CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="32a30-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="32a30-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="32a30-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="32a30-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="32a30-115">The call timed out.</span></span>|  
|<span data-ttu-id="32a30-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="32a30-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="32a30-117">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="32a30-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="32a30-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="32a30-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="32a30-119">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="32a30-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="32a30-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="32a30-120">E_FAIL</span></span>|<span data-ttu-id="32a30-121">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="32a30-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="32a30-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="32a30-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="32a30-123">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="32a30-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="32a30-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="32a30-124">Remarks</span></span>  
 <span data-ttu-id="32a30-125">Çalışma zamanı çağrıları `SetCLRTaskManager` konak bir arabirim işaretçisine sağlamak için bir `ICLRTaskManager` örneği.</span><span class="sxs-lookup"><span data-stu-id="32a30-125">The runtime calls `SetCLRTaskManager` to provide the host with an interface pointer to an `ICLRTaskManager` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32a30-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="32a30-126">Requirements</span></span>  
 <span data-ttu-id="32a30-127">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32a30-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32a30-128">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="32a30-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="32a30-129">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="32a30-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="32a30-130">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32a30-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32a30-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="32a30-131">See also</span></span>
- [<span data-ttu-id="32a30-132">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="32a30-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="32a30-133">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="32a30-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="32a30-134">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="32a30-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="32a30-135">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="32a30-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
