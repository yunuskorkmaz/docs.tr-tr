---
title: ICLRTask::GetMemStats Yöntemi
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
ms.openlocfilehash: 0bf8b6f393806e590be8f97dbfe2d01d5746c339
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139694"
---
# <a name="iclrtaskgetmemstats-method"></a><span data-ttu-id="89f61-102">ICLRTask::GetMemStats Yöntemi</span><span class="sxs-lookup"><span data-stu-id="89f61-102">ICLRTask::GetMemStats Method</span></span>
<span data-ttu-id="89f61-103">Geçerli [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) örneğinin temsil ettiği görevle ilgili istatistiksel bellek kullanım bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="89f61-103">Gets statistical memory usage information related to the task that the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89f61-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="89f61-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMemStats (  
    [out] COR_GC_THREAD_STATS *pMemUsage  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="89f61-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="89f61-105">Parameters</span></span>  
 `pMemUsage`  
 <span data-ttu-id="89f61-106">dışı Ayrılan bayt sayısı dahil olmak üzere, görevin bellek kullanımıyla ilgili ayrıntıları içeren bir [COR_GC_THREAD_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-thread-stats-structure.md) örneği işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="89f61-106">[out] A pointer to a [COR_GC_THREAD_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-thread-stats-structure.md) instance that contains details about the memory usage of the task, including the number of bytes allocated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="89f61-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="89f61-107">Return Value</span></span>  
  
|<span data-ttu-id="89f61-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="89f61-108">HRESULT</span></span>|<span data-ttu-id="89f61-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="89f61-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="89f61-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="89f61-110">S_OK</span></span>|<span data-ttu-id="89f61-111">`GetMemStats` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="89f61-111">`GetMemStats` returned successfully.</span></span>|  
|<span data-ttu-id="89f61-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="89f61-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="89f61-113">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="89f61-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="89f61-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="89f61-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="89f61-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="89f61-115">The call timed out.</span></span>|  
|<span data-ttu-id="89f61-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="89f61-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="89f61-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="89f61-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="89f61-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="89f61-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="89f61-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="89f61-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="89f61-120">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="89f61-120">E_FAIL</span></span>|<span data-ttu-id="89f61-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="89f61-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="89f61-122">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="89f61-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="89f61-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="89f61-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="89f61-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="89f61-124">Requirements</span></span>  
 <span data-ttu-id="89f61-125">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89f61-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89f61-126">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="89f61-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="89f61-127">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="89f61-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="89f61-128">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89f61-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89f61-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="89f61-129">See also</span></span>

- [<span data-ttu-id="89f61-130">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="89f61-130">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="89f61-131">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="89f61-131">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="89f61-132">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="89f61-132">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="89f61-133">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="89f61-133">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
