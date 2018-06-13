---
title: IHostSyncManager::SetCLRSyncManager Yöntemi
ms.date: 03/30/2017
api_name:
- IHostSyncManager.SetCLRSyncManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::SetCLRSyncManager
helpviewer_keywords:
- IHostSyncManager::SetCLRSyncManager method [.NET Framework hosting]
- SetCLRSyncManager method [.NET Framework hosting]
ms.assetid: 2b8bbe76-a45d-4989-bacb-11df42f8798c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aef7866d912951972ec9c66efccca671c3787da6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33443693"
---
# <a name="ihostsyncmanagersetclrsyncmanager-method"></a><span data-ttu-id="8282d-102">IHostSyncManager::SetCLRSyncManager Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8282d-102">IHostSyncManager::SetCLRSyncManager Method</span></span>
<span data-ttu-id="8282d-103">Ayarlar [Iclrsyncmanager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) geçerli ilişkilendirmek için örnek [Ihostsyncmanager](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md) örneği.</span><span class="sxs-lookup"><span data-stu-id="8282d-103">Sets the [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) instance to associate with the current [IHostSyncManager](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8282d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8282d-104">Syntax</span></span>  
  
```  
HRESULT SetCLRSyncManager (  
    [in] ICLRSyncManager *pManager  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8282d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8282d-105">Parameters</span></span>  
 `pManager`  
 <span data-ttu-id="8282d-106">[in] Bir işaretçi bir `ICLRSyncManager` ortak dil çalışma zamanı tarafından (CLR) sağlanan örneği.</span><span class="sxs-lookup"><span data-stu-id="8282d-106">[in] A pointer to an `ICLRSyncManager` instance supplied by the common language runtime (CLR).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8282d-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8282d-107">Return Value</span></span>  
  
|<span data-ttu-id="8282d-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8282d-108">HRESULT</span></span>|<span data-ttu-id="8282d-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8282d-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8282d-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="8282d-110">S_OK</span></span>|<span data-ttu-id="8282d-111">`SetCLRSyncManager` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="8282d-111">`SetCLRSyncManager` returned successfully.</span></span>|  
|<span data-ttu-id="8282d-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8282d-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8282d-113">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="8282d-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8282d-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8282d-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8282d-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="8282d-115">The call timed out.</span></span>|  
|<span data-ttu-id="8282d-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8282d-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8282d-117">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="8282d-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8282d-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8282d-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8282d-119">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="8282d-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8282d-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8282d-120">E_FAIL</span></span>|<span data-ttu-id="8282d-121">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="8282d-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8282d-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="8282d-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8282d-123">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="8282d-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8282d-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8282d-124">Remarks</span></span>  
 <span data-ttu-id="8282d-125">Barındırma arabirimleri CLR ile konak arasındaki iletişimi kolaylaştırmak için genellikle çiftler halinde gelir.</span><span class="sxs-lookup"><span data-stu-id="8282d-125">To facilitate communication between the host and the CLR, hosting interfaces generally come in pairs.</span></span> <span data-ttu-id="8282d-126">Çiftinin bir üye ana bilgisayar tarafından uygulanır ve diğer üye CLR tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="8282d-126">One member of the pair is implemented by the host, and the other member is implemented by the CLR.</span></span> <span data-ttu-id="8282d-127">Bir ana bilgisayar tarafı uygulaması olarak `IHostSyncManager` arabirimi karşılık gelen `ICLRSyncManager` CLR tarafından uygulanan arabirimi.</span><span class="sxs-lookup"><span data-stu-id="8282d-127">As a host-side implementation, the `IHostSyncManager` interface corresponds to the `ICLRSyncManager` interface implemented by the CLR.</span></span> <span data-ttu-id="8282d-128">CLR çağrıları `SetCLRSyncManager` sağlamak için bir `ICLRSyncManager` geçerli ilişkilendirmek ana bilgisayar için örnek `IHostSyncManager` örneği.</span><span class="sxs-lookup"><span data-stu-id="8282d-128">The CLR calls `SetCLRSyncManager` to supply an `ICLRSyncManager` instance for the host to associate with the current `IHostSyncManager` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8282d-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8282d-129">Requirements</span></span>  
 <span data-ttu-id="8282d-130">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8282d-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8282d-131">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8282d-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8282d-132">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="8282d-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8282d-133">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8282d-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8282d-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8282d-134">See Also</span></span>  
 [<span data-ttu-id="8282d-135">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8282d-135">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="8282d-136">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8282d-136">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
