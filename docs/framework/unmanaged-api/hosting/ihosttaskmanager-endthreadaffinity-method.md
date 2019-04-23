---
title: IHostTaskManager::EndThreadAffinity Yöntemi
ms.date: 03/30/2017
api_name:
- IHostTaskManager.EndThreadAffinity
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::EndThreadAffinity
helpviewer_keywords:
- EndThreadAffinity method [.NET Framework hosting]
- IHostTaskManager::EndThreadAffinity method [.NET Framework hosting]
ms.assetid: 7738a904-0cd7-4fde-a3eb-2323a5533157
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3f94f365aa8c9221c64e9611deab3597e06ed862
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59157904"
---
# <a name="ihosttaskmanagerendthreadaffinity-method"></a><span data-ttu-id="b99b1-102">IHostTaskManager::EndThreadAffinity Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b99b1-102">IHostTaskManager::EndThreadAffinity Method</span></span>
<span data-ttu-id="b99b1-103">Yönetilen kod ana bilgisayar, dönem içinde geçerli görev gerekir taşınamaz başka bir işletim sistemi iş parçacığı için önceki bir çağrıyı izleyen çıkıyor bildirir [Ihosttaskmanager::beginthreadaffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-beginthreadaffinity-method.md).</span><span class="sxs-lookup"><span data-stu-id="b99b1-103">Notifies the host that managed code is exiting the period in which the current task must not be moved to another operating system thread, following an earlier call to [IHostTaskManager::BeginThreadAffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-beginthreadaffinity-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b99b1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b99b1-104">Syntax</span></span>  
  
```  
HRESULT EndThreadAffinity ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="b99b1-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b99b1-105">Return Value</span></span>  
  
|<span data-ttu-id="b99b1-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b99b1-106">HRESULT</span></span>|<span data-ttu-id="b99b1-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b99b1-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b99b1-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="b99b1-108">S_OK</span></span>|<span data-ttu-id="b99b1-109">`EndThreadAffinity` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="b99b1-109">`EndThreadAffinity` returned successfully.</span></span>|  
|<span data-ttu-id="b99b1-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b99b1-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b99b1-111">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="b99b1-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b99b1-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b99b1-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b99b1-113">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="b99b1-113">The call timed out.</span></span>|  
|<span data-ttu-id="b99b1-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b99b1-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b99b1-115">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="b99b1-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b99b1-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b99b1-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b99b1-117">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="b99b1-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b99b1-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b99b1-118">E_FAIL</span></span>|<span data-ttu-id="b99b1-119">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="b99b1-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b99b1-120">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="b99b1-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b99b1-121">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="b99b1-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="b99b1-122">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="b99b1-122">E_UNEXPECTED</span></span>|<span data-ttu-id="b99b1-123">`EndThreadAffinity` Önceki karşılık gelen bir arama olmadan çağrıldı `BeginThreadAffinity`.</span><span class="sxs-lookup"><span data-stu-id="b99b1-123">`EndThreadAffinity` was called without an earlier corresponding call to `BeginThreadAffinity`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b99b1-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b99b1-124">Remarks</span></span>  
 <span data-ttu-id="b99b1-125">CLR karşılık gelen bir çağrıda `BeginThreadAffinity` çağırmadan önce geçerli görevdeki `EndThreadAffinity`.</span><span class="sxs-lookup"><span data-stu-id="b99b1-125">The CLR makes a corresponding call to `BeginThreadAffinity` on the current task before calling `EndThreadAffinity`.</span></span> <span data-ttu-id="b99b1-126">Bu çağrı, mevcut olmadığında konağın uygulaması [Ihosttaskmanager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md) E_UNEXPECTED döndürür ve eylem yok.</span><span class="sxs-lookup"><span data-stu-id="b99b1-126">In the absence of such a corresponding call, the host's implementation of [IHostTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md) should return E_UNEXPECTED, and take no action.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b99b1-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b99b1-127">Requirements</span></span>  
 <span data-ttu-id="b99b1-128">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b99b1-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b99b1-129">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b99b1-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b99b1-130">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="b99b1-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b99b1-131">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b99b1-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b99b1-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b99b1-132">See also</span></span>

- <xref:System.Threading>
- [<span data-ttu-id="b99b1-133">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b99b1-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="b99b1-134">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b99b1-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="b99b1-135">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b99b1-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="b99b1-136">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b99b1-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
