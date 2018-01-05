---
title: IHostTask::GetPriority Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTask.GetPriority
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTask::GetPriority
helpviewer_keywords:
- GetPriority method [.NET Framework hosting]
- IHostTask::GetPriority method [.NET Framework hosting]
ms.assetid: 4b463cd6-77c1-4f9a-8518-346ad8fc4b70
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 468a2e29ed3c031889fdc5df3d4defa6506d8fcf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ihosttaskgetpriority-method"></a><span data-ttu-id="81c35-102">IHostTask::GetPriority Metodu</span><span class="sxs-lookup"><span data-stu-id="81c35-102">IHostTask::GetPriority Method</span></span>
<span data-ttu-id="81c35-103">Geçerli tarafından temsil edilen görev iş parçacığı öncelik düzeyini alır [Ihosttask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) örneği.</span><span class="sxs-lookup"><span data-stu-id="81c35-103">Gets the thread priority level of the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81c35-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="81c35-104">Syntax</span></span>  
  
```  
HRESULT GetPriority (  
    [out] int *pPriority  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="81c35-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="81c35-105">Parameters</span></span>  
 `pPriority`  
 <span data-ttu-id="81c35-106">[out] Geçerli tarafından temsil edilen görev iş parçacığı öncelik düzeyini gösteren bir tamsayı gösteren bir işaretçi `IHostTask` örneği.</span><span class="sxs-lookup"><span data-stu-id="81c35-106">[out] A pointer to an integer that indicates the thread priority level of the task represented by the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="81c35-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="81c35-107">Return Value</span></span>  
  
|<span data-ttu-id="81c35-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="81c35-108">HRESULT</span></span>|<span data-ttu-id="81c35-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="81c35-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="81c35-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="81c35-110">S_OK</span></span>|<span data-ttu-id="81c35-111">`GetPriority`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="81c35-111">`GetPriority` returned successfully.</span></span>|  
|<span data-ttu-id="81c35-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="81c35-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="81c35-113">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="81c35-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="81c35-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="81c35-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="81c35-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="81c35-115">The call timed out.</span></span>|  
|<span data-ttu-id="81c35-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="81c35-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="81c35-117">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="81c35-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="81c35-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="81c35-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="81c35-119">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="81c35-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="81c35-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="81c35-120">E_FAIL</span></span>|<span data-ttu-id="81c35-121">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="81c35-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="81c35-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="81c35-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="81c35-123">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="81c35-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="81c35-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="81c35-124">Remarks</span></span>  
 <span data-ttu-id="81c35-125">İş parçacığı öncelik düzeyi değerleri Win32 tarafından tanımlanan `SetThreadPriority` işlevi.</span><span class="sxs-lookup"><span data-stu-id="81c35-125">Thread priority level values are defined by the Win32 `SetThreadPriority` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81c35-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="81c35-126">Requirements</span></span>  
 <span data-ttu-id="81c35-127">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81c35-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81c35-128">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="81c35-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="81c35-129">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="81c35-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="81c35-130">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81c35-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81c35-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="81c35-131">See Also</span></span>  
 [<span data-ttu-id="81c35-132">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="81c35-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="81c35-133">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="81c35-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="81c35-134">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="81c35-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="81c35-135">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="81c35-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
