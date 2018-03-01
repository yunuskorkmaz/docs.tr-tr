---
title: ICLRTask::GetMemStats Metodu
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7ad5fb2b76ef282258b9a5293b890a19420c1906
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrtaskgetmemstats-method"></a><span data-ttu-id="ea855-102">ICLRTask::GetMemStats Metodu</span><span class="sxs-lookup"><span data-stu-id="ea855-102">ICLRTask::GetMemStats Method</span></span>
<span data-ttu-id="ea855-103">Görevle ilgili istatistiksel bellek kullanım bilgilerini alır, geçerli [Iclrtask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) örneğini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ea855-103">Gets statistical memory usage information related to the task that the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea855-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ea855-104">Syntax</span></span>  
  
```  
HRESULT GetMemStats (  
    [out] COR_GC_THREAD_STATS *pMemUsage  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ea855-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ea855-105">Parameters</span></span>  
 `pMemUsage`  
 <span data-ttu-id="ea855-106">[out] Bir işaretçi bir [COR_GC_THREAD_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-thread-stats-structure.md) ayrılan bayt sayısı dahil olmak üzere görev, bellek kullanımı hakkında ayrıntılar içeren örneği.</span><span class="sxs-lookup"><span data-stu-id="ea855-106">[out] A pointer to a [COR_GC_THREAD_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-thread-stats-structure.md) instance that contains details about the memory usage of the task, including the number of bytes allocated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ea855-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ea855-107">Return Value</span></span>  
  
|<span data-ttu-id="ea855-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ea855-108">HRESULT</span></span>|<span data-ttu-id="ea855-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ea855-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ea855-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="ea855-110">S_OK</span></span>|<span data-ttu-id="ea855-111">`GetMemStats`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="ea855-111">`GetMemStats` returned successfully.</span></span>|  
|<span data-ttu-id="ea855-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ea855-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ea855-113">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="ea855-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ea855-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ea855-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ea855-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="ea855-115">The call timed out.</span></span>|  
|<span data-ttu-id="ea855-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ea855-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ea855-117">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="ea855-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ea855-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ea855-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ea855-119">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="ea855-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ea855-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ea855-120">E_FAIL</span></span>|<span data-ttu-id="ea855-121">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="ea855-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ea855-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="ea855-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ea855-123">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="ea855-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ea855-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ea855-124">Requirements</span></span>  
 <span data-ttu-id="ea855-125">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ea855-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea855-126">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ea855-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ea855-127">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="ea855-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ea855-128">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea855-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea855-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ea855-129">See Also</span></span>  
 [<span data-ttu-id="ea855-130">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ea855-130">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="ea855-131">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ea855-131">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="ea855-132">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ea855-132">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="ea855-133">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ea855-133">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
