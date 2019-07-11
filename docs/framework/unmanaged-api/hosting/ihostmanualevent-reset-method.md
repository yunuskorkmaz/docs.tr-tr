---
title: IHostManualEvent::Reset Yöntemi
ms.date: 03/30/2017
api_name:
- IHostManualEvent.Reset
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostManualEvent::Reset
helpviewer_keywords:
- Reset method, IHostManualEvent interface [.NET Framework hosting]
- IHostManualEvent::Reset method [.NET Framework hosting]
ms.assetid: 0d101168-b5e3-49ce-90c7-85cf2db83c4c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 37ba54665dbd8d10c7e7aac9a0692c8882fb5209
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67767294"
---
# <a name="ihostmanualeventreset-method"></a><span data-ttu-id="eee9e-102">IHostManualEvent::Reset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="eee9e-102">IHostManualEvent::Reset Method</span></span>
<span data-ttu-id="eee9e-103">Geçerli sıfırlar [Ihostmanualevent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) verilmemiş bir duruma örneği.</span><span class="sxs-lookup"><span data-stu-id="eee9e-103">Resets the current [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance to a non-signaled state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eee9e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="eee9e-104">Syntax</span></span>  
  
```cpp  
HRESULT Reset ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="eee9e-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="eee9e-105">Return Value</span></span>  
  
|<span data-ttu-id="eee9e-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="eee9e-106">HRESULT</span></span>|<span data-ttu-id="eee9e-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="eee9e-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="eee9e-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="eee9e-108">S_OK</span></span>|<span data-ttu-id="eee9e-109">`Reset` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="eee9e-109">`Reset` returned successfully.</span></span>|  
|<span data-ttu-id="eee9e-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="eee9e-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="eee9e-111">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="eee9e-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="eee9e-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="eee9e-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="eee9e-113">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="eee9e-113">The call timed out.</span></span>|  
|<span data-ttu-id="eee9e-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="eee9e-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="eee9e-115">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="eee9e-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="eee9e-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="eee9e-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="eee9e-117">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="eee9e-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="eee9e-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="eee9e-118">E_FAIL</span></span>|<span data-ttu-id="eee9e-119">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="eee9e-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="eee9e-120">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="eee9e-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="eee9e-121">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="eee9e-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="eee9e-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="eee9e-122">Requirements</span></span>  
 <span data-ttu-id="eee9e-123">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eee9e-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eee9e-124">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="eee9e-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="eee9e-125">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="eee9e-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="eee9e-126">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eee9e-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eee9e-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eee9e-127">See also</span></span>

- [<span data-ttu-id="eee9e-128">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="eee9e-128">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="eee9e-129">IHostAutoEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="eee9e-129">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="eee9e-130">IHostManualEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="eee9e-130">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="eee9e-131">IHostSemaphore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="eee9e-131">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="eee9e-132">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="eee9e-132">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
