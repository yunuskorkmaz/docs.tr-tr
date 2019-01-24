---
title: ICLRTask::GetMemStats Metodu
ms.date: 03/30/2017
api_name:
- ICLRTask.GetMemStats
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::GetMemStats
helpviewer_keywords:
- ICLRTask::GetMemStats method [.NET Framework hosting]
- GetMemStats method [.NET Framework hosting]
ms.assetid: c9e07657-1682-4c30-a336-f8658ff1a125
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6a6383761b878c7e916064f9a046641d00a1c6ba
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54734276"
---
# <a name="iclrtaskgetmemstats-method"></a><span data-ttu-id="6e621-102">ICLRTask::GetMemStats Metodu</span><span class="sxs-lookup"><span data-stu-id="6e621-102">ICLRTask::GetMemStats Method</span></span>
<span data-ttu-id="6e621-103">Görevle ilgili istatistiksel bellek kullanım bilgilerini alır, geçerli [Iclrtask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) örneğini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6e621-103">Gets statistical memory usage information related to the task that the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e621-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6e621-104">Syntax</span></span>  
  
```  
HRESULT GetMemStats (  
    [out] COR_GC_THREAD_STATS *pMemUsage  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6e621-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6e621-105">Parameters</span></span>  
 `pMemUsage`  
 <span data-ttu-id="6e621-106">[out] Bir işaretçi bir [COR_GC_THREAD_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-thread-stats-structure.md) görevin ayrılan bayt sayısı dahil olmak üzere, bellek kullanımı hakkında ayrıntılar içeren örneği.</span><span class="sxs-lookup"><span data-stu-id="6e621-106">[out] A pointer to a [COR_GC_THREAD_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-thread-stats-structure.md) instance that contains details about the memory usage of the task, including the number of bytes allocated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6e621-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="6e621-107">Return Value</span></span>  
  
|<span data-ttu-id="6e621-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6e621-108">HRESULT</span></span>|<span data-ttu-id="6e621-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6e621-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6e621-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="6e621-110">S_OK</span></span>|<span data-ttu-id="6e621-111">`GetMemStats` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="6e621-111">`GetMemStats` returned successfully.</span></span>|  
|<span data-ttu-id="6e621-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6e621-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6e621-113">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="6e621-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6e621-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6e621-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6e621-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="6e621-115">The call timed out.</span></span>|  
|<span data-ttu-id="6e621-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6e621-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6e621-117">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="6e621-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6e621-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6e621-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6e621-119">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="6e621-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6e621-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6e621-120">E_FAIL</span></span>|<span data-ttu-id="6e621-121">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="6e621-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6e621-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="6e621-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6e621-123">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="6e621-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6e621-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6e621-124">Requirements</span></span>  
 <span data-ttu-id="6e621-125">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6e621-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e621-126">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6e621-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6e621-127">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="6e621-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6e621-128">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e621-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e621-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6e621-129">See also</span></span>
- [<span data-ttu-id="6e621-130">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6e621-130">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="6e621-131">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6e621-131">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="6e621-132">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6e621-132">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="6e621-133">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6e621-133">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
