---
description: ': IHostTaskManager:: GetCurrentTask Yöntemi hakkında daha fazla bilgi'
title: IHostTaskManager::GetCurrentTask Yöntemi
ms.date: 03/30/2017
api_name:
- IHostTaskManager.GetCurrentTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::GetCurrentTask
helpviewer_keywords:
- GetCurrentTask method, IHostTaskManager interface [.NET Framework hosting]
- IHostTaskManager::GetCurrentTask method [.NET Framework hosting]
ms.assetid: f17bca49-90bd-4dee-a5e1-b9a57ea46f85
topic_type:
- apiref
ms.openlocfilehash: 7e7e516fe4a706fce8b0302f318cfbb164a86eea
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753815"
---
# <a name="ihosttaskmanagergetcurrenttask-method"></a><span data-ttu-id="8ca56-103">IHostTaskManager::GetCurrentTask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8ca56-103">IHostTaskManager::GetCurrentTask Method</span></span>

<span data-ttu-id="8ca56-104">Bu çağrının yapıldığı işletim sistemi iş parçacığında yürütülmekte olan göreve yönelik bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="8ca56-104">Gets an interface pointer to the task that is currently executing on the operating system thread from which this call is made.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ca56-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8ca56-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentTask (  
    [out] IHostTask **pTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8ca56-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8ca56-106">Parameters</span></span>  

 `pTask`  
 <span data-ttu-id="8ca56-107">dışı Şu anda yürütülmekte olan görevi temsil eden bir [IHostTask](ihosttask-interface.md) örneğinin adresine yönelik bir işaretçi veya herhangi bir görev yürütülerek null.</span><span class="sxs-lookup"><span data-stu-id="8ca56-107">[out] A pointer to the address of an [IHostTask](ihosttask-interface.md) instance that represents the currently executing task, or null, if no task is currently executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8ca56-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8ca56-108">Return Value</span></span>  
  
|<span data-ttu-id="8ca56-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8ca56-109">HRESULT</span></span>|<span data-ttu-id="8ca56-110">Description</span><span class="sxs-lookup"><span data-stu-id="8ca56-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8ca56-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="8ca56-111">S_OK</span></span>|<span data-ttu-id="8ca56-112">`GetCurrentTask` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="8ca56-112">`GetCurrentTask` returned successfully.</span></span>|  
|<span data-ttu-id="8ca56-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8ca56-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8ca56-114">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="8ca56-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8ca56-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8ca56-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8ca56-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="8ca56-116">The call timed out.</span></span>|  
|<span data-ttu-id="8ca56-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8ca56-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8ca56-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="8ca56-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8ca56-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8ca56-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8ca56-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="8ca56-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8ca56-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8ca56-121">E_FAIL</span></span>|<span data-ttu-id="8ca56-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="8ca56-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8ca56-123">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="8ca56-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8ca56-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="8ca56-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="8ca56-125">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="8ca56-125">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="8ca56-126">`GetCurrentTask` , konak denetimi dışında bir işletim sistemi iş parçacığında çağırılır.</span><span class="sxs-lookup"><span data-stu-id="8ca56-126">`GetCurrentTask` was called on an operating system thread outside the control of the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8ca56-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8ca56-127">Remarks</span></span>  

 <span data-ttu-id="8ca56-128">Konak, `pTask` clr girişini başlatmadığından bir görevi engellemek için parametresini null olarak da ayarlayabilir.</span><span class="sxs-lookup"><span data-stu-id="8ca56-128">The host can also set the `pTask` parameter to null to prevent a task that it did not initiate from entering the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ca56-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8ca56-129">Requirements</span></span>  

 <span data-ttu-id="8ca56-130">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ca56-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ca56-131">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8ca56-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8ca56-132">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="8ca56-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8ca56-133">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ca56-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ca56-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8ca56-134">See also</span></span>

- [<span data-ttu-id="8ca56-135">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8ca56-135">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="8ca56-136">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8ca56-136">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="8ca56-137">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8ca56-137">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="8ca56-138">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8ca56-138">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
