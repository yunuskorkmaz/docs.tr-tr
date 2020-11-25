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
ms.openlocfilehash: 5d57bc742ebcba00f9fbe569a4be27b82a5f8055
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726515"
---
# <a name="iclrtaskgetmemstats-method"></a><span data-ttu-id="1a43d-102">ICLRTask::GetMemStats Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1a43d-102">ICLRTask::GetMemStats Method</span></span>

<span data-ttu-id="1a43d-103">Geçerli [ICLRTask](iclrtask-interface.md) örneğinin temsil ettiği görevle ilgili istatistiksel bellek kullanım bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="1a43d-103">Gets statistical memory usage information related to the task that the current [ICLRTask](iclrtask-interface.md) instance represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a43d-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="1a43d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMemStats (  
    [out] COR_GC_THREAD_STATS *pMemUsage  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1a43d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1a43d-105">Parameters</span></span>  

 `pMemUsage`  
 <span data-ttu-id="1a43d-106">dışı Ayrılan bayt sayısı dahil olmak üzere, görevin bellek kullanımıyla ilgili ayrıntıları içeren [COR_GC_THREAD_STATS](cor-gc-thread-stats-structure.md) örneğine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1a43d-106">[out] A pointer to a [COR_GC_THREAD_STATS](cor-gc-thread-stats-structure.md) instance that contains details about the memory usage of the task, including the number of bytes allocated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1a43d-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1a43d-107">Return Value</span></span>  
  
|<span data-ttu-id="1a43d-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1a43d-108">HRESULT</span></span>|<span data-ttu-id="1a43d-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1a43d-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1a43d-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="1a43d-110">S_OK</span></span>|<span data-ttu-id="1a43d-111">`GetMemStats` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="1a43d-111">`GetMemStats` returned successfully.</span></span>|  
|<span data-ttu-id="1a43d-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1a43d-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1a43d-113">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="1a43d-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1a43d-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1a43d-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1a43d-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="1a43d-115">The call timed out.</span></span>|  
|<span data-ttu-id="1a43d-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1a43d-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1a43d-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="1a43d-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1a43d-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1a43d-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1a43d-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="1a43d-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1a43d-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1a43d-120">E_FAIL</span></span>|<span data-ttu-id="1a43d-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="1a43d-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1a43d-122">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="1a43d-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1a43d-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="1a43d-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1a43d-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1a43d-124">Requirements</span></span>  

 <span data-ttu-id="1a43d-125">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a43d-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a43d-126">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="1a43d-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1a43d-127">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="1a43d-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1a43d-128">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a43d-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a43d-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1a43d-129">See also</span></span>

- [<span data-ttu-id="1a43d-130">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1a43d-130">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="1a43d-131">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1a43d-131">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="1a43d-132">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1a43d-132">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="1a43d-133">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1a43d-133">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
