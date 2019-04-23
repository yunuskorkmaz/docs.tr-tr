---
title: IHostTaskManager::EndDelayAbort Yöntemi
ms.date: 03/30/2017
api_name:
- IHostTaskManager.EndDelayAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::EndDelayAbort
helpviewer_keywords:
- EndDelayAbort method [.NET Framework hosting]
- IHostTaskManager::EndDelayAbort method [.NET Framework hosting]
ms.assetid: 6e02facb-2504-4356-9af5-0cee1f8436a7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 10d12e5cab41f016ddee78089dc1df1f5c942ecd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59194454"
---
# <a name="ihosttaskmanagerenddelayabort-method"></a><span data-ttu-id="1d21a-102">IHostTaskManager::EndDelayAbort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1d21a-102">IHostTaskManager::EndDelayAbort Method</span></span>
<span data-ttu-id="1d21a-103">Yönetilen kod ana bilgisayar çağrısında şu, geçerli görev gerekir değil iptal edilir, dönem çıkıyor bildirir [Ihosttaskmanager::begindelayabort](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-begindelayabort-method.md).</span><span class="sxs-lookup"><span data-stu-id="1d21a-103">Notifies the host that managed code is exiting the period in which the current task must not be aborted, following an earlier call to [IHostTaskManager::BeginDelayAbort](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-begindelayabort-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d21a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1d21a-104">Syntax</span></span>  
  
```  
HRESULT EndDelayAbort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="1d21a-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1d21a-105">Return Value</span></span>  
  
|<span data-ttu-id="1d21a-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1d21a-106">HRESULT</span></span>|<span data-ttu-id="1d21a-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1d21a-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1d21a-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="1d21a-108">S_OK</span></span>|<span data-ttu-id="1d21a-109">`EndDelayAbort` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="1d21a-109">`EndDelayAbort` returned successfully.</span></span>|  
|<span data-ttu-id="1d21a-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1d21a-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1d21a-111">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="1d21a-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1d21a-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1d21a-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1d21a-113">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="1d21a-113">The call timed out.</span></span>|  
|<span data-ttu-id="1d21a-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1d21a-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1d21a-115">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="1d21a-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1d21a-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1d21a-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1d21a-117">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="1d21a-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1d21a-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1d21a-118">E_FAIL</span></span>|<span data-ttu-id="1d21a-119">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="1d21a-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1d21a-120">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="1d21a-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1d21a-121">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="1d21a-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="1d21a-122">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="1d21a-122">E_UNEXPECTED</span></span>|<span data-ttu-id="1d21a-123">`EndDelayAbort` karşılık gelen bir çağrı olmadan çağrıldı `BeginDelayAbort`.</span><span class="sxs-lookup"><span data-stu-id="1d21a-123">`EndDelayAbort` was called without a corresponding call to `BeginDelayAbort`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1d21a-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1d21a-124">Remarks</span></span>  
 <span data-ttu-id="1d21a-125">CLR karşılık gelen bir çağrıda `BeginDelayAbort` çağırmadan önce geçerli görevdeki `EndDelayAbort`.</span><span class="sxs-lookup"><span data-stu-id="1d21a-125">The CLR makes a corresponding call to `BeginDelayAbort` on the current task before calling `EndDelayAbort`.</span></span> <span data-ttu-id="1d21a-126">Bu çağrı, mevcut olmadığında konağın uygulaması [Ihosttaskmanager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md) gelen E_UNEXPECTED döndürmelidir `EndDelayAbort`ve herhangi bir eylem yapması.</span><span class="sxs-lookup"><span data-stu-id="1d21a-126">In the absence of such a corresponding call, the host's implementation of [IHostTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md) should return E_UNEXPECTED from `EndDelayAbort`, and should take no action.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d21a-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1d21a-127">Requirements</span></span>  
 <span data-ttu-id="1d21a-128">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1d21a-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d21a-129">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1d21a-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1d21a-130">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="1d21a-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1d21a-131">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d21a-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d21a-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1d21a-132">See also</span></span>

- <xref:System.Threading>
- [<span data-ttu-id="1d21a-133">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1d21a-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="1d21a-134">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1d21a-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="1d21a-135">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1d21a-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="1d21a-136">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1d21a-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
