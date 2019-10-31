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
ms.openlocfilehash: cf79c0d0f6def46d7f4d55f17afbd1f1dff00ad9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133066"
---
# <a name="ihosttaskmanagerenddelayabort-method"></a><span data-ttu-id="8b7f6-102">IHostTaskManager::EndDelayAbort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8b7f6-102">IHostTaskManager::EndDelayAbort Method</span></span>
<span data-ttu-id="8b7f6-103">Şu anda [IHostTaskManager:: BeginDelayAbort](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-begindelayabort-method.md)' e daha önceki bir çağrıdan sonra, yönetilen kodun, geçerli görevin durdurulmadıkları dönemden çıkış olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="8b7f6-103">Notifies the host that managed code is exiting the period in which the current task must not be aborted, following an earlier call to [IHostTaskManager::BeginDelayAbort](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-begindelayabort-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b7f6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8b7f6-104">Syntax</span></span>  
  
```cpp  
HRESULT EndDelayAbort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="8b7f6-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8b7f6-105">Return Value</span></span>  
  
|<span data-ttu-id="8b7f6-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8b7f6-106">HRESULT</span></span>|<span data-ttu-id="8b7f6-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8b7f6-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8b7f6-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="8b7f6-108">S_OK</span></span>|<span data-ttu-id="8b7f6-109">`EndDelayAbort` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="8b7f6-109">`EndDelayAbort` returned successfully.</span></span>|  
|<span data-ttu-id="8b7f6-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8b7f6-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8b7f6-111">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="8b7f6-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8b7f6-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8b7f6-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8b7f6-113">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="8b7f6-113">The call timed out.</span></span>|  
|<span data-ttu-id="8b7f6-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8b7f6-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8b7f6-115">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="8b7f6-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8b7f6-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8b7f6-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8b7f6-117">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="8b7f6-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8b7f6-118">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="8b7f6-118">E_FAIL</span></span>|<span data-ttu-id="8b7f6-119">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="8b7f6-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8b7f6-120">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="8b7f6-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8b7f6-121">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="8b7f6-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="8b7f6-122">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="8b7f6-122">E_UNEXPECTED</span></span>|<span data-ttu-id="8b7f6-123">`EndDelayAbort`, `BeginDelayAbort`için karşılık gelen bir çağrı olmadan çağrıldı.</span><span class="sxs-lookup"><span data-stu-id="8b7f6-123">`EndDelayAbort` was called without a corresponding call to `BeginDelayAbort`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8b7f6-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8b7f6-124">Remarks</span></span>  
 <span data-ttu-id="8b7f6-125">CLR, `EndDelayAbort`çağrılmadan önce geçerli görevde `BeginDelayAbort` için karşılık gelen bir çağrı yapar.</span><span class="sxs-lookup"><span data-stu-id="8b7f6-125">The CLR makes a corresponding call to `BeginDelayAbort` on the current task before calling `EndDelayAbort`.</span></span> <span data-ttu-id="8b7f6-126">Buna karşılık gelen bir çağrının yokluğunda, konağın [IHostTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md) uygulaması, `EndDelayAbort`'den E_UNEXPECTED döndürmelidir ve hiçbir işlem yapması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="8b7f6-126">In the absence of such a corresponding call, the host's implementation of [IHostTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md) should return E_UNEXPECTED from `EndDelayAbort`, and should take no action.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b7f6-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8b7f6-127">Requirements</span></span>  
 <span data-ttu-id="8b7f6-128">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b7f6-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b7f6-129">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8b7f6-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8b7f6-130">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="8b7f6-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8b7f6-131">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b7f6-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b7f6-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8b7f6-132">See also</span></span>

- <xref:System.Threading>
- [<span data-ttu-id="8b7f6-133">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8b7f6-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="8b7f6-134">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8b7f6-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="8b7f6-135">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8b7f6-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="8b7f6-136">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8b7f6-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
