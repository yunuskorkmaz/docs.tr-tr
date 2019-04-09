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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59194454"
---
# <a name="ihosttaskmanagerenddelayabort-method"></a><span data-ttu-id="e9ad7-102">IHostTaskManager::EndDelayAbort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e9ad7-102">IHostTaskManager::EndDelayAbort Method</span></span>
<span data-ttu-id="e9ad7-103">Yönetilen kod ana bilgisayar çağrısında şu, geçerli görev gerekir değil iptal edilir, dönem çıkıyor bildirir [Ihosttaskmanager::begindelayabort](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-begindelayabort-method.md).</span><span class="sxs-lookup"><span data-stu-id="e9ad7-103">Notifies the host that managed code is exiting the period in which the current task must not be aborted, following an earlier call to [IHostTaskManager::BeginDelayAbort](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-begindelayabort-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9ad7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e9ad7-104">Syntax</span></span>  
  
```  
HRESULT EndDelayAbort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="e9ad7-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e9ad7-105">Return Value</span></span>  
  
|<span data-ttu-id="e9ad7-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e9ad7-106">HRESULT</span></span>|<span data-ttu-id="e9ad7-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e9ad7-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e9ad7-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="e9ad7-108">S_OK</span></span>|`EndDelayAbort` <span data-ttu-id="e9ad7-109">başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="e9ad7-109">returned successfully.</span></span>|  
|<span data-ttu-id="e9ad7-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e9ad7-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e9ad7-111">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="e9ad7-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e9ad7-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e9ad7-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e9ad7-113">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="e9ad7-113">The call timed out.</span></span>|  
|<span data-ttu-id="e9ad7-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e9ad7-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e9ad7-115">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="e9ad7-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e9ad7-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e9ad7-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e9ad7-117">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="e9ad7-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e9ad7-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e9ad7-118">E_FAIL</span></span>|<span data-ttu-id="e9ad7-119">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="e9ad7-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e9ad7-120">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="e9ad7-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e9ad7-121">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="e9ad7-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e9ad7-122">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="e9ad7-122">E_UNEXPECTED</span></span>|`EndDelayAbort` <span data-ttu-id="e9ad7-123">karşılık gelen bir çağrı olmadan çağrıldı `BeginDelayAbort`.</span><span class="sxs-lookup"><span data-stu-id="e9ad7-123">was called without a corresponding call to `BeginDelayAbort`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e9ad7-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e9ad7-124">Remarks</span></span>  
 <span data-ttu-id="e9ad7-125">CLR karşılık gelen bir çağrıda `BeginDelayAbort` çağırmadan önce geçerli görevdeki `EndDelayAbort`.</span><span class="sxs-lookup"><span data-stu-id="e9ad7-125">The CLR makes a corresponding call to `BeginDelayAbort` on the current task before calling `EndDelayAbort`.</span></span> <span data-ttu-id="e9ad7-126">Bu çağrı, mevcut olmadığında konağın uygulaması [Ihosttaskmanager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md) gelen E_UNEXPECTED döndürmelidir `EndDelayAbort`ve herhangi bir eylem yapması.</span><span class="sxs-lookup"><span data-stu-id="e9ad7-126">In the absence of such a corresponding call, the host's implementation of [IHostTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md) should return E_UNEXPECTED from `EndDelayAbort`, and should take no action.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9ad7-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e9ad7-127">Requirements</span></span>  
 <span data-ttu-id="e9ad7-128">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9ad7-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9ad7-129">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e9ad7-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e9ad7-130">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="e9ad7-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="e9ad7-131">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="e9ad7-131">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e9ad7-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e9ad7-132">See also</span></span>

- <xref:System.Threading>
- [<span data-ttu-id="e9ad7-133">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e9ad7-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="e9ad7-134">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e9ad7-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="e9ad7-135">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e9ad7-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="e9ad7-136">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e9ad7-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
