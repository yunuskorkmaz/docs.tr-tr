---
description: 'Şu konuda daha fazla bilgi edinin: IHostTask:: GetPriority Yöntemi'
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
ms.openlocfilehash: fb64164a54806a362888e93f031713ccc0ac3578
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784697"
---
# <a name="ihosttaskgetpriority-method"></a><span data-ttu-id="e428e-103">IHostTask::GetPriority Metodu</span><span class="sxs-lookup"><span data-stu-id="e428e-103">IHostTask::GetPriority Method</span></span>

<span data-ttu-id="e428e-104">Geçerli [IHostTask](ihosttask-interface.md) örneği tarafından temsil edilen görevin iş parçacığı öncelik düzeyini alır.</span><span class="sxs-lookup"><span data-stu-id="e428e-104">Gets the thread priority level of the task represented by the current [IHostTask](ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e428e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e428e-105">Syntax</span></span>  
  
```cpp  
HRESULT GetPriority (  
    [out] int *pPriority  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e428e-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e428e-106">Parameters</span></span>  

 `pPriority`  
 <span data-ttu-id="e428e-107">dışı Geçerli örnek tarafından temsil edilen görevin iş parçacığı öncelik düzeyini gösteren bir tamsayı işaretçisi `IHostTask` .</span><span class="sxs-lookup"><span data-stu-id="e428e-107">[out] A pointer to an integer that indicates the thread priority level of the task represented by the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e428e-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e428e-108">Return Value</span></span>  
  
|<span data-ttu-id="e428e-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e428e-109">HRESULT</span></span>|<span data-ttu-id="e428e-110">Description</span><span class="sxs-lookup"><span data-stu-id="e428e-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e428e-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="e428e-111">S_OK</span></span>|<span data-ttu-id="e428e-112">`GetPriority` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="e428e-112">`GetPriority` returned successfully.</span></span>|  
|<span data-ttu-id="e428e-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e428e-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e428e-114">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="e428e-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e428e-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e428e-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e428e-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="e428e-116">The call timed out.</span></span>|  
|<span data-ttu-id="e428e-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e428e-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e428e-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="e428e-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e428e-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e428e-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e428e-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="e428e-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e428e-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e428e-121">E_FAIL</span></span>|<span data-ttu-id="e428e-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="e428e-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e428e-123">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="e428e-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e428e-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="e428e-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e428e-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e428e-125">Remarks</span></span>  

 <span data-ttu-id="e428e-126">İş parçacığı öncelik düzeyi değerleri Win32 işlevi tarafından tanımlanır `SetThreadPriority` .</span><span class="sxs-lookup"><span data-stu-id="e428e-126">Thread priority level values are defined by the Win32 `SetThreadPriority` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e428e-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e428e-127">Requirements</span></span>  

 <span data-ttu-id="e428e-128">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e428e-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e428e-129">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e428e-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e428e-130">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="e428e-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e428e-131">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e428e-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e428e-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e428e-132">See also</span></span>

- [<span data-ttu-id="e428e-133">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e428e-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="e428e-134">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e428e-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="e428e-135">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e428e-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="e428e-136">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e428e-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
