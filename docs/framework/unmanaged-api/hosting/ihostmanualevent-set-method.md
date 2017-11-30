---
title: "IHostManualEvent::Set Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostManualEvent.Set
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostManualEvent::Set
helpviewer_keywords:
- Set method, IHostManualEvent interface [.NET Framework hosting]
- IHostManualEvent::Set method [.NET Framework hosting]
ms.assetid: e930c174-f71d-4faa-bb59-f0fb3df4d77b
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7f093e1278e74553ed78445e0cb83127a219e622
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostmanualeventset-method"></a><span data-ttu-id="730a2-102">IHostManualEvent::Set Yöntemi</span><span class="sxs-lookup"><span data-stu-id="730a2-102">IHostManualEvent::Set Method</span></span>
<span data-ttu-id="730a2-103">Geçerli ayarlar [Ihostmanualevent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) iş durumuna örneği.</span><span class="sxs-lookup"><span data-stu-id="730a2-103">Sets the current [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance to a signaled state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="730a2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="730a2-104">Syntax</span></span>  
  
```  
HRESULT Set ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="730a2-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="730a2-105">Return Value</span></span>  
  
|<span data-ttu-id="730a2-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="730a2-106">HRESULT</span></span>|<span data-ttu-id="730a2-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="730a2-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="730a2-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="730a2-108">S_OK</span></span>|<span data-ttu-id="730a2-109">`Set`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="730a2-109">`Set` returned successfully.</span></span>|  
|<span data-ttu-id="730a2-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="730a2-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="730a2-111">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="730a2-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="730a2-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="730a2-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="730a2-113">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="730a2-113">The call timed out.</span></span>|  
|<span data-ttu-id="730a2-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="730a2-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="730a2-115">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="730a2-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="730a2-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="730a2-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="730a2-117">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="730a2-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="730a2-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="730a2-118">E_FAIL</span></span>|<span data-ttu-id="730a2-119">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="730a2-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="730a2-120">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="730a2-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="730a2-121">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="730a2-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="730a2-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="730a2-122">Requirements</span></span>  
 <span data-ttu-id="730a2-123">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="730a2-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="730a2-124">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="730a2-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="730a2-125">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="730a2-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="730a2-126">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="730a2-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="730a2-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="730a2-127">See Also</span></span>  
 [<span data-ttu-id="730a2-128">Iclrsyncmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="730a2-128">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="730a2-129">Ihostautoevent arabirimi</span><span class="sxs-lookup"><span data-stu-id="730a2-129">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="730a2-130">Ihostmanualevent arabirimi</span><span class="sxs-lookup"><span data-stu-id="730a2-130">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 [<span data-ttu-id="730a2-131">Ihostsemaphore arabirimi</span><span class="sxs-lookup"><span data-stu-id="730a2-131">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 [<span data-ttu-id="730a2-132">Ihostsyncmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="730a2-132">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
