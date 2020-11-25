---
title: IHostTask::SetCLRTask Yöntemi
ms.date: 03/30/2017
api_name:
- IHostTask.SetCLRTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::SetCLRTask
helpviewer_keywords:
- SetCLRTask method [.NET Framework hosting]
- IHostTask::SetCLRTask method [.NET Framework hosting]
ms.assetid: e9d39c80-41a1-49e7-bb5e-ea3433bfb5d7
topic_type:
- apiref
ms.openlocfilehash: e6b9a4015a6139d6c8d7101fa7811c7ad9134e4c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720470"
---
# <a name="ihosttasksetclrtask-method"></a><span data-ttu-id="a1d8a-102">IHostTask::SetCLRTask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a1d8a-102">IHostTask::SetCLRTask Method</span></span>

<span data-ttu-id="a1d8a-103">Bir `ICLRTask` örneği geçerli [IHostTask](ihosttask-interface.md) örneğiyle ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="a1d8a-103">Associates an `ICLRTask` instance with the current [IHostTask](ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1d8a-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="a1d8a-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCLRTask (  
    [in] ICLRTask *pCLRTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a1d8a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a1d8a-105">Parameters</span></span>  

 `pCLRTask`  
 <span data-ttu-id="a1d8a-106">'ndaki `ICLRTask` Geçerli örnekle ilişkilendirilecek örneğe yönelik bir arabirim işaretçisi `IHostTask` .</span><span class="sxs-lookup"><span data-stu-id="a1d8a-106">[in] An interface pointer to the `ICLRTask` instance to be associated with the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a1d8a-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a1d8a-107">Return Value</span></span>  
  
|<span data-ttu-id="a1d8a-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a1d8a-108">HRESULT</span></span>|<span data-ttu-id="a1d8a-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a1d8a-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a1d8a-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="a1d8a-110">S_OK</span></span>|<span data-ttu-id="a1d8a-111">`SetCLRTask` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="a1d8a-111">`SetCLRTask` returned successfully.</span></span>|  
|<span data-ttu-id="a1d8a-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a1d8a-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a1d8a-113">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="a1d8a-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a1d8a-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a1d8a-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a1d8a-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="a1d8a-115">The call timed out.</span></span>|  
|<span data-ttu-id="a1d8a-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a1d8a-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a1d8a-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="a1d8a-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a1d8a-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a1d8a-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a1d8a-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="a1d8a-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a1d8a-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a1d8a-120">E_FAIL</span></span>|<span data-ttu-id="a1d8a-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="a1d8a-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a1d8a-122">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="a1d8a-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a1d8a-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="a1d8a-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a1d8a-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a1d8a-124">Remarks</span></span>  

 <span data-ttu-id="a1d8a-125">CLR, `SetCLRTask` bir `ICLRTask` örneği `IHostTask` [IHostTaskManager:: CreateTask](ihosttaskmanager-createtask-method.md)çağrısıyla oluşturulan geçerli örnekle ilişkilendirmek için çağırır.</span><span class="sxs-lookup"><span data-stu-id="a1d8a-125">The CLR calls `SetCLRTask` to associate an `ICLRTask` instance with the current `IHostTask` instance, which was created by a call to [IHostTaskManager::CreateTask](ihosttaskmanager-createtask-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1d8a-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a1d8a-126">Requirements</span></span>  

 <span data-ttu-id="a1d8a-127">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1d8a-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1d8a-128">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a1d8a-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a1d8a-129">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="a1d8a-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a1d8a-130">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1d8a-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1d8a-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a1d8a-131">See also</span></span>

- [<span data-ttu-id="a1d8a-132">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a1d8a-132">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="a1d8a-133">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a1d8a-133">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="a1d8a-134">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a1d8a-134">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="a1d8a-135">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a1d8a-135">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
