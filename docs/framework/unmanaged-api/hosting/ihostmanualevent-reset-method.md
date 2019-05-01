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
ms.openlocfilehash: 9b3de70e6bdecba6370174ee825d2dec7c14270e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61935687"
---
# <a name="ihostmanualeventreset-method"></a><span data-ttu-id="0c28a-102">IHostManualEvent::Reset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0c28a-102">IHostManualEvent::Reset Method</span></span>
<span data-ttu-id="0c28a-103">Geçerli sıfırlar [Ihostmanualevent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) verilmemiş bir duruma örneği.</span><span class="sxs-lookup"><span data-stu-id="0c28a-103">Resets the current [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance to a non-signaled state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c28a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0c28a-104">Syntax</span></span>  
  
```  
HRESULT Reset ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="0c28a-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0c28a-105">Return Value</span></span>  
  
|<span data-ttu-id="0c28a-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0c28a-106">HRESULT</span></span>|<span data-ttu-id="0c28a-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0c28a-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0c28a-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="0c28a-108">S_OK</span></span>|<span data-ttu-id="0c28a-109">`Reset` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="0c28a-109">`Reset` returned successfully.</span></span>|  
|<span data-ttu-id="0c28a-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0c28a-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0c28a-111">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="0c28a-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0c28a-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0c28a-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0c28a-113">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="0c28a-113">The call timed out.</span></span>|  
|<span data-ttu-id="0c28a-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0c28a-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0c28a-115">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="0c28a-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0c28a-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0c28a-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0c28a-117">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="0c28a-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0c28a-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0c28a-118">E_FAIL</span></span>|<span data-ttu-id="0c28a-119">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="0c28a-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0c28a-120">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="0c28a-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0c28a-121">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="0c28a-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0c28a-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0c28a-122">Requirements</span></span>  
 <span data-ttu-id="0c28a-123">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c28a-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c28a-124">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0c28a-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0c28a-125">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="0c28a-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0c28a-126">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c28a-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c28a-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0c28a-127">See also</span></span>

- [<span data-ttu-id="0c28a-128">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0c28a-128">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="0c28a-129">IHostAutoEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0c28a-129">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="0c28a-130">IHostManualEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0c28a-130">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="0c28a-131">IHostSemaphore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0c28a-131">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="0c28a-132">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0c28a-132">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
