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
ms.openlocfilehash: b2dcc342c218b3d6999d777e2658424c92f7e07a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33438795"
---
# <a name="ihostmanualeventreset-method"></a><span data-ttu-id="74093-102">IHostManualEvent::Reset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="74093-102">IHostManualEvent::Reset Method</span></span>
<span data-ttu-id="74093-103">Geçerli sıfırlar [Ihostmanualevent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) işaret olmayan bir duruma örneği.</span><span class="sxs-lookup"><span data-stu-id="74093-103">Resets the current [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance to a non-signaled state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74093-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="74093-104">Syntax</span></span>  
  
```  
HRESULT Reset ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="74093-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="74093-105">Return Value</span></span>  
  
|<span data-ttu-id="74093-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="74093-106">HRESULT</span></span>|<span data-ttu-id="74093-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="74093-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="74093-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="74093-108">S_OK</span></span>|<span data-ttu-id="74093-109">`Reset` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="74093-109">`Reset` returned successfully.</span></span>|  
|<span data-ttu-id="74093-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="74093-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="74093-111">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="74093-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="74093-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="74093-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="74093-113">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="74093-113">The call timed out.</span></span>|  
|<span data-ttu-id="74093-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="74093-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="74093-115">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="74093-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="74093-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="74093-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="74093-117">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="74093-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="74093-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="74093-118">E_FAIL</span></span>|<span data-ttu-id="74093-119">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="74093-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="74093-120">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="74093-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="74093-121">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="74093-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="74093-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="74093-122">Requirements</span></span>  
 <span data-ttu-id="74093-123">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74093-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74093-124">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="74093-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="74093-125">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="74093-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="74093-126">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74093-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74093-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="74093-127">See Also</span></span>  
 [<span data-ttu-id="74093-128">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="74093-128">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="74093-129">IHostAutoEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="74093-129">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="74093-130">IHostManualEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="74093-130">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 [<span data-ttu-id="74093-131">IHostSemaphore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="74093-131">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 [<span data-ttu-id="74093-132">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="74093-132">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
