---
title: IHostTask::GetPriority Metodu
ms.date: 03/30/2017
api_name:
- IHostTask.GetPriority
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::GetPriority
helpviewer_keywords:
- GetPriority method [.NET Framework hosting]
- IHostTask::GetPriority method [.NET Framework hosting]
ms.assetid: 4b463cd6-77c1-4f9a-8518-346ad8fc4b70
topic_type:
- apiref
ms.openlocfilehash: 6c33fa6d2e6cb09f013c5334461e61235db549f7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121414"
---
# <a name="ihosttaskgetpriority-method"></a><span data-ttu-id="5bc05-102">IHostTask::GetPriority Metodu</span><span class="sxs-lookup"><span data-stu-id="5bc05-102">IHostTask::GetPriority Method</span></span>
<span data-ttu-id="5bc05-103">Geçerli [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) örneği tarafından temsil edilen görevin iş parçacığı öncelik düzeyini alır.</span><span class="sxs-lookup"><span data-stu-id="5bc05-103">Gets the thread priority level of the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5bc05-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5bc05-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPriority (  
    [out] int *pPriority  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5bc05-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5bc05-105">Parameters</span></span>  
 `pPriority`  
 <span data-ttu-id="5bc05-106">dışı Geçerli `IHostTask` örneği tarafından temsil edilen görevin iş parçacığı öncelik düzeyini gösteren bir tamsayı işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="5bc05-106">[out] A pointer to an integer that indicates the thread priority level of the task represented by the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5bc05-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5bc05-107">Return Value</span></span>  
  
|<span data-ttu-id="5bc05-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5bc05-108">HRESULT</span></span>|<span data-ttu-id="5bc05-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5bc05-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5bc05-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="5bc05-110">S_OK</span></span>|<span data-ttu-id="5bc05-111">`GetPriority` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="5bc05-111">`GetPriority` returned successfully.</span></span>|  
|<span data-ttu-id="5bc05-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5bc05-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5bc05-113">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="5bc05-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5bc05-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5bc05-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5bc05-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="5bc05-115">The call timed out.</span></span>|  
|<span data-ttu-id="5bc05-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5bc05-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5bc05-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="5bc05-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5bc05-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5bc05-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5bc05-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="5bc05-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5bc05-120">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="5bc05-120">E_FAIL</span></span>|<span data-ttu-id="5bc05-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="5bc05-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5bc05-122">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="5bc05-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5bc05-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="5bc05-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5bc05-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5bc05-124">Remarks</span></span>  
 <span data-ttu-id="5bc05-125">İş parçacığı öncelik düzeyi değerleri Win32 `SetThreadPriority` işlevi tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="5bc05-125">Thread priority level values are defined by the Win32 `SetThreadPriority` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5bc05-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5bc05-126">Requirements</span></span>  
 <span data-ttu-id="5bc05-127">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5bc05-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5bc05-128">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="5bc05-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5bc05-129">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="5bc05-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5bc05-130">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5bc05-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bc05-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5bc05-131">See also</span></span>

- [<span data-ttu-id="5bc05-132">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5bc05-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="5bc05-133">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5bc05-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="5bc05-134">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5bc05-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="5bc05-135">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5bc05-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
