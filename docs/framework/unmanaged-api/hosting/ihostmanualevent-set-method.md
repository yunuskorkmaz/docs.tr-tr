---
title: IHostManualEvent::Set Yöntemi
ms.date: 03/30/2017
api_name:
- IHostManualEvent.Set
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostManualEvent::Set
helpviewer_keywords:
- Set method, IHostManualEvent interface [.NET Framework hosting]
- IHostManualEvent::Set method [.NET Framework hosting]
ms.assetid: e930c174-f71d-4faa-bb59-f0fb3df4d77b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3756ed3bc7863411849b9d733da816e567a86628
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67767308"
---
# <a name="ihostmanualeventset-method"></a><span data-ttu-id="d5fba-102">IHostManualEvent::Set Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d5fba-102">IHostManualEvent::Set Method</span></span>
<span data-ttu-id="d5fba-103">Geçerli ayarlar [Ihostmanualevent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) sinyal verilmiş duruma örneği.</span><span class="sxs-lookup"><span data-stu-id="d5fba-103">Sets the current [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance to a signaled state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5fba-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d5fba-104">Syntax</span></span>  
  
```cpp  
HRESULT Set ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="d5fba-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d5fba-105">Return Value</span></span>  
  
|<span data-ttu-id="d5fba-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d5fba-106">HRESULT</span></span>|<span data-ttu-id="d5fba-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d5fba-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d5fba-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="d5fba-108">S_OK</span></span>|<span data-ttu-id="d5fba-109">`Set` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="d5fba-109">`Set` returned successfully.</span></span>|  
|<span data-ttu-id="d5fba-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d5fba-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d5fba-111">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="d5fba-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d5fba-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d5fba-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d5fba-113">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="d5fba-113">The call timed out.</span></span>|  
|<span data-ttu-id="d5fba-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d5fba-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d5fba-115">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="d5fba-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d5fba-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d5fba-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d5fba-117">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="d5fba-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d5fba-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d5fba-118">E_FAIL</span></span>|<span data-ttu-id="d5fba-119">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="d5fba-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d5fba-120">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="d5fba-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d5fba-121">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="d5fba-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d5fba-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d5fba-122">Requirements</span></span>  
 <span data-ttu-id="d5fba-123">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5fba-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5fba-124">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d5fba-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d5fba-125">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="d5fba-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d5fba-126">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5fba-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5fba-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d5fba-127">See also</span></span>

- [<span data-ttu-id="d5fba-128">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d5fba-128">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="d5fba-129">IHostAutoEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d5fba-129">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="d5fba-130">IHostManualEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d5fba-130">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="d5fba-131">IHostSemaphore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d5fba-131">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="d5fba-132">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d5fba-132">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
