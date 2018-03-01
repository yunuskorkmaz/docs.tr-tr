---
title: "IHostManualEvent::Reset Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d1bbd10437662fc8b7fbb52d65d196d7a519538b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostmanualeventreset-method"></a><span data-ttu-id="906ba-102">IHostManualEvent::Reset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="906ba-102">IHostManualEvent::Reset Method</span></span>
<span data-ttu-id="906ba-103">Geçerli sıfırlar [Ihostmanualevent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) işaret olmayan bir duruma örneği.</span><span class="sxs-lookup"><span data-stu-id="906ba-103">Resets the current [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance to a non-signaled state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="906ba-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="906ba-104">Syntax</span></span>  
  
```  
HRESULT Reset ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="906ba-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="906ba-105">Return Value</span></span>  
  
|<span data-ttu-id="906ba-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="906ba-106">HRESULT</span></span>|<span data-ttu-id="906ba-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="906ba-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="906ba-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="906ba-108">S_OK</span></span>|<span data-ttu-id="906ba-109">`Reset`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="906ba-109">`Reset` returned successfully.</span></span>|  
|<span data-ttu-id="906ba-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="906ba-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="906ba-111">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="906ba-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="906ba-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="906ba-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="906ba-113">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="906ba-113">The call timed out.</span></span>|  
|<span data-ttu-id="906ba-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="906ba-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="906ba-115">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="906ba-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="906ba-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="906ba-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="906ba-117">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="906ba-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="906ba-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="906ba-118">E_FAIL</span></span>|<span data-ttu-id="906ba-119">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="906ba-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="906ba-120">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="906ba-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="906ba-121">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="906ba-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="906ba-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="906ba-122">Requirements</span></span>  
 <span data-ttu-id="906ba-123">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="906ba-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="906ba-124">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="906ba-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="906ba-125">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="906ba-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="906ba-126">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="906ba-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="906ba-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="906ba-127">See Also</span></span>  
 [<span data-ttu-id="906ba-128">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="906ba-128">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="906ba-129">IHostAutoEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="906ba-129">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="906ba-130">IHostManualEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="906ba-130">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 [<span data-ttu-id="906ba-131">IHostSemaphore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="906ba-131">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 [<span data-ttu-id="906ba-132">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="906ba-132">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
