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
ms.openlocfilehash: b6eac134a4ffb1813cdc6957632ce5fb9b1a5fff
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842276"
---
# <a name="ihosttasksetclrtask-method"></a><span data-ttu-id="40751-102">IHostTask::SetCLRTask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="40751-102">IHostTask::SetCLRTask Method</span></span>
<span data-ttu-id="40751-103">Bir `ICLRTask` örneği geçerli [IHostTask](ihosttask-interface.md) örneğiyle ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="40751-103">Associates an `ICLRTask` instance with the current [IHostTask](ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40751-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="40751-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCLRTask (  
    [in] ICLRTask *pCLRTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="40751-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="40751-105">Parameters</span></span>  
 `pCLRTask`  
 <span data-ttu-id="40751-106">'ndaki `ICLRTask`Geçerli örnekle ilişkilendirilecek örneğe yönelik bir arabirim işaretçisi `IHostTask` .</span><span class="sxs-lookup"><span data-stu-id="40751-106">[in] An interface pointer to the `ICLRTask` instance to be associated with the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="40751-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="40751-107">Return Value</span></span>  
  
|<span data-ttu-id="40751-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="40751-108">HRESULT</span></span>|<span data-ttu-id="40751-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="40751-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="40751-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="40751-110">S_OK</span></span>|<span data-ttu-id="40751-111">`SetCLRTask`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="40751-111">`SetCLRTask` returned successfully.</span></span>|  
|<span data-ttu-id="40751-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="40751-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="40751-113">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="40751-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="40751-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="40751-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="40751-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="40751-115">The call timed out.</span></span>|  
|<span data-ttu-id="40751-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="40751-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="40751-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="40751-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="40751-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="40751-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="40751-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="40751-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="40751-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="40751-120">E_FAIL</span></span>|<span data-ttu-id="40751-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="40751-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="40751-122">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="40751-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="40751-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="40751-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="40751-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="40751-124">Remarks</span></span>  
 <span data-ttu-id="40751-125">CLR, `SetCLRTask` bir `ICLRTask` örneği `IHostTask` [IHostTaskManager:: CreateTask](ihosttaskmanager-createtask-method.md)çağrısıyla oluşturulan geçerli örnekle ilişkilendirmek için çağırır.</span><span class="sxs-lookup"><span data-stu-id="40751-125">The CLR calls `SetCLRTask` to associate an `ICLRTask` instance with the current `IHostTask` instance, which was created by a call to [IHostTaskManager::CreateTask](ihosttaskmanager-createtask-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40751-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="40751-126">Requirements</span></span>  
 <span data-ttu-id="40751-127">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40751-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40751-128">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="40751-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="40751-129">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="40751-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="40751-130">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40751-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40751-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="40751-131">See also</span></span>

- [<span data-ttu-id="40751-132">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="40751-132">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="40751-133">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="40751-133">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="40751-134">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="40751-134">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="40751-135">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="40751-135">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
