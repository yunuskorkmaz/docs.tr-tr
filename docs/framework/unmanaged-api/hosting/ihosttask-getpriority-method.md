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
ms.openlocfilehash: d30dcbe4e7c289c23c5af00e4bdadedc186809b4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95714776"
---
# <a name="ihosttaskgetpriority-method"></a><span data-ttu-id="e48c7-102">IHostTask::GetPriority Metodu</span><span class="sxs-lookup"><span data-stu-id="e48c7-102">IHostTask::GetPriority Method</span></span>

<span data-ttu-id="e48c7-103">Geçerli [IHostTask](ihosttask-interface.md) örneği tarafından temsil edilen görevin iş parçacığı öncelik düzeyini alır.</span><span class="sxs-lookup"><span data-stu-id="e48c7-103">Gets the thread priority level of the task represented by the current [IHostTask](ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e48c7-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="e48c7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPriority (  
    [out] int *pPriority  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e48c7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e48c7-105">Parameters</span></span>  

 `pPriority`  
 <span data-ttu-id="e48c7-106">dışı Geçerli örnek tarafından temsil edilen görevin iş parçacığı öncelik düzeyini gösteren bir tamsayı işaretçisi `IHostTask` .</span><span class="sxs-lookup"><span data-stu-id="e48c7-106">[out] A pointer to an integer that indicates the thread priority level of the task represented by the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e48c7-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e48c7-107">Return Value</span></span>  
  
|<span data-ttu-id="e48c7-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e48c7-108">HRESULT</span></span>|<span data-ttu-id="e48c7-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e48c7-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e48c7-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="e48c7-110">S_OK</span></span>|<span data-ttu-id="e48c7-111">`GetPriority` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="e48c7-111">`GetPriority` returned successfully.</span></span>|  
|<span data-ttu-id="e48c7-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e48c7-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e48c7-113">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="e48c7-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e48c7-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e48c7-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e48c7-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="e48c7-115">The call timed out.</span></span>|  
|<span data-ttu-id="e48c7-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e48c7-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e48c7-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="e48c7-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e48c7-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e48c7-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e48c7-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="e48c7-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e48c7-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e48c7-120">E_FAIL</span></span>|<span data-ttu-id="e48c7-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="e48c7-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e48c7-122">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="e48c7-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e48c7-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="e48c7-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e48c7-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e48c7-124">Remarks</span></span>  

 <span data-ttu-id="e48c7-125">İş parçacığı öncelik düzeyi değerleri Win32 işlevi tarafından tanımlanır `SetThreadPriority` .</span><span class="sxs-lookup"><span data-stu-id="e48c7-125">Thread priority level values are defined by the Win32 `SetThreadPriority` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e48c7-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e48c7-126">Requirements</span></span>  

 <span data-ttu-id="e48c7-127">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e48c7-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e48c7-128">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e48c7-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e48c7-129">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="e48c7-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e48c7-130">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e48c7-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e48c7-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e48c7-131">See also</span></span>

- [<span data-ttu-id="e48c7-132">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e48c7-132">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="e48c7-133">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e48c7-133">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="e48c7-134">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e48c7-134">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="e48c7-135">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e48c7-135">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
