---
description: ': ICLRTask:: GetMemStats metodu hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: ed81e9ced20a43528247d70012077ffd466f9ed1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784983"
---
# <a name="iclrtaskgetmemstats-method"></a><span data-ttu-id="13a20-103">ICLRTask::GetMemStats Yöntemi</span><span class="sxs-lookup"><span data-stu-id="13a20-103">ICLRTask::GetMemStats Method</span></span>

<span data-ttu-id="13a20-104">Geçerli [ICLRTask](iclrtask-interface.md) örneğinin temsil ettiği görevle ilgili istatistiksel bellek kullanım bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="13a20-104">Gets statistical memory usage information related to the task that the current [ICLRTask](iclrtask-interface.md) instance represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13a20-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="13a20-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMemStats (  
    [out] COR_GC_THREAD_STATS *pMemUsage  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="13a20-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="13a20-106">Parameters</span></span>  

 `pMemUsage`  
 <span data-ttu-id="13a20-107">dışı Ayrılan bayt sayısı dahil olmak üzere, görevin bellek kullanımıyla ilgili ayrıntıları içeren [COR_GC_THREAD_STATS](cor-gc-thread-stats-structure.md) örneğine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="13a20-107">[out] A pointer to a [COR_GC_THREAD_STATS](cor-gc-thread-stats-structure.md) instance that contains details about the memory usage of the task, including the number of bytes allocated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="13a20-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="13a20-108">Return Value</span></span>  
  
|<span data-ttu-id="13a20-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="13a20-109">HRESULT</span></span>|<span data-ttu-id="13a20-110">Description</span><span class="sxs-lookup"><span data-stu-id="13a20-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="13a20-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="13a20-111">S_OK</span></span>|<span data-ttu-id="13a20-112">`GetMemStats` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="13a20-112">`GetMemStats` returned successfully.</span></span>|  
|<span data-ttu-id="13a20-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="13a20-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="13a20-114">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="13a20-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="13a20-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="13a20-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="13a20-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="13a20-116">The call timed out.</span></span>|  
|<span data-ttu-id="13a20-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="13a20-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="13a20-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="13a20-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="13a20-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="13a20-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="13a20-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="13a20-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="13a20-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="13a20-121">E_FAIL</span></span>|<span data-ttu-id="13a20-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="13a20-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="13a20-123">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="13a20-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="13a20-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="13a20-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="13a20-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="13a20-125">Requirements</span></span>  

 <span data-ttu-id="13a20-126">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13a20-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13a20-127">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="13a20-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="13a20-128">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="13a20-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="13a20-129">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13a20-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13a20-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="13a20-130">See also</span></span>

- [<span data-ttu-id="13a20-131">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="13a20-131">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="13a20-132">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="13a20-132">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="13a20-133">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="13a20-133">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="13a20-134">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="13a20-134">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
