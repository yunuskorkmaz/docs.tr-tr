---
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
ms.openlocfilehash: 874951d6b5efed0dc08e6d0e166962767e295c3e
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842055"
---
# <a name="ihosttaskmanagergetcurrenttask-method"></a><span data-ttu-id="72138-102">IHostTaskManager::GetCurrentTask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="72138-102">IHostTaskManager::GetCurrentTask Method</span></span>
<span data-ttu-id="72138-103">Bu çağrının yapıldığı işletim sistemi iş parçacığında yürütülmekte olan göreve yönelik bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="72138-103">Gets an interface pointer to the task that is currently executing on the operating system thread from which this call is made.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72138-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="72138-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentTask (  
    [out] IHostTask **pTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="72138-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="72138-105">Parameters</span></span>  
 `pTask`  
 <span data-ttu-id="72138-106">dışı Şu anda yürütülmekte olan görevi temsil eden bir [IHostTask](ihosttask-interface.md) örneğinin adresine yönelik bir işaretçi veya herhangi bir görev yürütülerek null.</span><span class="sxs-lookup"><span data-stu-id="72138-106">[out] A pointer to the address of an [IHostTask](ihosttask-interface.md) instance that represents the currently executing task, or null, if no task is currently executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="72138-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="72138-107">Return Value</span></span>  
  
|<span data-ttu-id="72138-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="72138-108">HRESULT</span></span>|<span data-ttu-id="72138-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="72138-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="72138-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="72138-110">S_OK</span></span>|<span data-ttu-id="72138-111">`GetCurrentTask`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="72138-111">`GetCurrentTask` returned successfully.</span></span>|  
|<span data-ttu-id="72138-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="72138-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="72138-113">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="72138-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="72138-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="72138-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="72138-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="72138-115">The call timed out.</span></span>|  
|<span data-ttu-id="72138-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="72138-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="72138-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="72138-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="72138-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="72138-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="72138-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="72138-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="72138-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="72138-120">E_FAIL</span></span>|<span data-ttu-id="72138-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="72138-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="72138-122">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="72138-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="72138-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="72138-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="72138-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="72138-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="72138-125">`GetCurrentTask`, konak denetimi dışında bir işletim sistemi iş parçacığında çağırılır.</span><span class="sxs-lookup"><span data-stu-id="72138-125">`GetCurrentTask` was called on an operating system thread outside the control of the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="72138-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="72138-126">Remarks</span></span>  
 <span data-ttu-id="72138-127">Konak, `pTask` clr girişini başlatmadığından bir görevi engellemek için parametresini null olarak da ayarlayabilir.</span><span class="sxs-lookup"><span data-stu-id="72138-127">The host can also set the `pTask` parameter to null to prevent a task that it did not initiate from entering the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72138-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="72138-128">Requirements</span></span>  
 <span data-ttu-id="72138-129">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72138-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72138-130">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="72138-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="72138-131">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="72138-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="72138-132">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72138-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72138-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="72138-133">See also</span></span>

- [<span data-ttu-id="72138-134">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="72138-134">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="72138-135">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="72138-135">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="72138-136">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="72138-136">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="72138-137">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="72138-137">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
