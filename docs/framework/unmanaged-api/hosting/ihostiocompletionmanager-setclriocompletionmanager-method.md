---
title: IHostIoCompletionManager::SetCLRIoCompletionManager Yöntemi
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.SetCLRIoCompletionManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::SetCLRIoCompletionManager
helpviewer_keywords:
- IHostIoCompletionManager::SetCLRIoCompletionManager method [.NET Framework hosting]
- SetCLRIoCompletionManager method [.NET Framework hosting]
ms.assetid: 4254bb01-3a14-4f34-a3be-60ff1f5072b5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d7e07450b108eb3c5ea083a2ec2f51981941153f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54669022"
---
# <a name="ihostiocompletionmanagersetclriocompletionmanager-method"></a><span data-ttu-id="838f6-102">IHostIoCompletionManager::SetCLRIoCompletionManager Yöntemi</span><span class="sxs-lookup"><span data-stu-id="838f6-102">IHostIoCompletionManager::SetCLRIoCompletionManager Method</span></span>
<span data-ttu-id="838f6-103">Bir arabirim işaretçisi ile ana bilgisayarının sağladığı [Iclrıocompletionmanager](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md) ortak dil çalışma zamanı tarafından (CLR) uygulanan örnek.</span><span class="sxs-lookup"><span data-stu-id="838f6-103">Provides the host with an interface pointer to the [ICLRIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md) instance implemented by the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="838f6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="838f6-104">Syntax</span></span>  
  
```  
HRESULT SetCLRIoCompletionManager (  
    [in] ICLRIoCompletionManager *pManager  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="838f6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="838f6-105">Parameters</span></span>  
 `pManager`  
 <span data-ttu-id="838f6-106">[in] Bir arabirim işaretçisi için bir `ICLRIoCompletionManager` CLR tarafından sağlanan örneği.</span><span class="sxs-lookup"><span data-stu-id="838f6-106">[in] An interface pointer to an `ICLRIoCompletionManager` instance provided by the CLR.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="838f6-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="838f6-107">Return Value</span></span>  
  
|<span data-ttu-id="838f6-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="838f6-108">HRESULT</span></span>|<span data-ttu-id="838f6-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="838f6-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="838f6-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="838f6-110">S_OK</span></span>|<span data-ttu-id="838f6-111">`SetCLRIoCompletionManager` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="838f6-111">`SetCLRIoCompletionManager` returned successfully.</span></span>|  
|<span data-ttu-id="838f6-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="838f6-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="838f6-113">CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="838f6-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="838f6-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="838f6-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="838f6-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="838f6-115">The call timed out.</span></span>|  
|<span data-ttu-id="838f6-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="838f6-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="838f6-117">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="838f6-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="838f6-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="838f6-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="838f6-119">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="838f6-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="838f6-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="838f6-120">E_FAIL</span></span>|<span data-ttu-id="838f6-121">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="838f6-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="838f6-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="838f6-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="838f6-123">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="838f6-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="838f6-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="838f6-124">Remarks</span></span>  
 <span data-ttu-id="838f6-125">CLR çağırdı sonra `SetCLRIoCompletionManager`, konak çağırmalıdır [Iclrıocompletionmanager::onComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md) bir g/ç isteği tamamlandığında, CLR bildirir.</span><span class="sxs-lookup"><span data-stu-id="838f6-125">After the CLR has called `SetCLRIoCompletionManager`, the host must call [ICLRIoCompletionManager::OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md) to notify the CLR when an I/O request has been completed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="838f6-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="838f6-126">Requirements</span></span>  
 <span data-ttu-id="838f6-127">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="838f6-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="838f6-128">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="838f6-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="838f6-129">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="838f6-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="838f6-130">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="838f6-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="838f6-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="838f6-131">See also</span></span>
- [<span data-ttu-id="838f6-132">ICLRIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="838f6-132">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="838f6-133">IHostIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="838f6-133">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
