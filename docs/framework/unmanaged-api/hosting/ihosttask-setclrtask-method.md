---
description: ': IHostTask:: SetCLRTask yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 381b7827f043b6ef1d4a6698f5eb103233c9af55
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784684"
---
# <a name="ihosttasksetclrtask-method"></a><span data-ttu-id="2a557-103">IHostTask::SetCLRTask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2a557-103">IHostTask::SetCLRTask Method</span></span>

<span data-ttu-id="2a557-104">Bir `ICLRTask` örneği geçerli [IHostTask](ihosttask-interface.md) örneğiyle ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="2a557-104">Associates an `ICLRTask` instance with the current [IHostTask](ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a557-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2a557-105">Syntax</span></span>  
  
```cpp  
HRESULT SetCLRTask (  
    [in] ICLRTask *pCLRTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2a557-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2a557-106">Parameters</span></span>  

 `pCLRTask`  
 <span data-ttu-id="2a557-107">'ndaki `ICLRTask` Geçerli örnekle ilişkilendirilecek örneğe yönelik bir arabirim işaretçisi `IHostTask` .</span><span class="sxs-lookup"><span data-stu-id="2a557-107">[in] An interface pointer to the `ICLRTask` instance to be associated with the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2a557-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2a557-108">Return Value</span></span>  
  
|<span data-ttu-id="2a557-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2a557-109">HRESULT</span></span>|<span data-ttu-id="2a557-110">Description</span><span class="sxs-lookup"><span data-stu-id="2a557-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2a557-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="2a557-111">S_OK</span></span>|<span data-ttu-id="2a557-112">`SetCLRTask` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="2a557-112">`SetCLRTask` returned successfully.</span></span>|  
|<span data-ttu-id="2a557-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2a557-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2a557-114">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="2a557-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2a557-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2a557-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2a557-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="2a557-116">The call timed out.</span></span>|  
|<span data-ttu-id="2a557-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2a557-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2a557-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="2a557-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2a557-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2a557-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2a557-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="2a557-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2a557-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2a557-121">E_FAIL</span></span>|<span data-ttu-id="2a557-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="2a557-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2a557-123">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="2a557-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2a557-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="2a557-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2a557-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2a557-125">Remarks</span></span>  

 <span data-ttu-id="2a557-126">CLR, `SetCLRTask` bir `ICLRTask` örneği `IHostTask` [IHostTaskManager:: CreateTask](ihosttaskmanager-createtask-method.md)çağrısıyla oluşturulan geçerli örnekle ilişkilendirmek için çağırır.</span><span class="sxs-lookup"><span data-stu-id="2a557-126">The CLR calls `SetCLRTask` to associate an `ICLRTask` instance with the current `IHostTask` instance, which was created by a call to [IHostTaskManager::CreateTask](ihosttaskmanager-createtask-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a557-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2a557-127">Requirements</span></span>  

 <span data-ttu-id="2a557-128">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a557-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a557-129">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2a557-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2a557-130">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="2a557-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2a557-131">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a557-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a557-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2a557-132">See also</span></span>

- [<span data-ttu-id="2a557-133">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2a557-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="2a557-134">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2a557-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="2a557-135">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2a557-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="2a557-136">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2a557-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
