---
title: IHostThreadPoolManager::QueueUserWorkItem Yöntemi
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager.QueueUserWorkItem
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager::QueueUserWorkItem
helpviewer_keywords:
- IHostThreadPoolManager::QueueUserWorkItem method [.NET Framework hosting]
- QueueUserWorkItem method [.NET Framework hosting]
ms.assetid: 41602053-8670-4827-9d61-cbfcba509b9c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 03185f3f554c5454b23b0c72c42d68714488e6be
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57501714"
---
# <a name="ihostthreadpoolmanagerqueueuserworkitem-method"></a><span data-ttu-id="46f78-102">IHostThreadPoolManager::QueueUserWorkItem Yöntemi</span><span class="sxs-lookup"><span data-stu-id="46f78-102">IHostThreadPoolManager::QueueUserWorkItem Method</span></span>
<span data-ttu-id="46f78-103">Bir işlev yürütme için sıraya alır ve bu işlev tarafından kullanılan verileri içeren bir nesne belirtir.</span><span class="sxs-lookup"><span data-stu-id="46f78-103">Queues a function for execution, and specifies an object containing data to be used by that function.</span></span> <span data-ttu-id="46f78-104">Bir iş parçacığı kullanılabilir hale geldiğinde işlevi yürütür.</span><span class="sxs-lookup"><span data-stu-id="46f78-104">The function executes when a thread becomes available.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46f78-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="46f78-105">Syntax</span></span>  
  
```  
HRESULT QueueUserWorkItem (  
    [in] LPTHREAD_START_ROUTINE Function,  
    [in] PVOID Context,  
    [in] ULONG Flags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="46f78-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="46f78-106">Parameters</span></span>  
 `Function`  
 <span data-ttu-id="46f78-107">[in] Yürütülecek bir işlevi temsil eden bir işlev işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="46f78-107">[in] A function pointer that represents the function to execute.</span></span>  
  
 `Context`  
 <span data-ttu-id="46f78-108">[in] Tarafından kullanılan veri içeren bir nesne `Function`.</span><span class="sxs-lookup"><span data-stu-id="46f78-108">[in] An object that contains data to be used by `Function`.</span></span>  
  
 `Flags`  
 <span data-ttu-id="46f78-109">[in] Bayrakları değerlerden birini, Win32 için tanımlanan `QueueUserWorkItem` yürütme denetleyen yöntemi.</span><span class="sxs-lookup"><span data-stu-id="46f78-109">[in] One of the flags values, as defined for the Win32 `QueueUserWorkItem` method, that control execution.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="46f78-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="46f78-110">Return Value</span></span>  
  
|<span data-ttu-id="46f78-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="46f78-111">HRESULT</span></span>|<span data-ttu-id="46f78-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="46f78-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="46f78-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="46f78-113">S_OK</span></span>|<span data-ttu-id="46f78-114">`QueueUserWorkItem` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="46f78-114">`QueueUserWorkItem` returned successfully.</span></span>|  
|<span data-ttu-id="46f78-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="46f78-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="46f78-116">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="46f78-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="46f78-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="46f78-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="46f78-118">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="46f78-118">The call timed out.</span></span>|  
|<span data-ttu-id="46f78-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="46f78-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="46f78-120">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="46f78-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="46f78-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="46f78-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="46f78-122">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="46f78-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="46f78-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="46f78-123">E_FAIL</span></span>|<span data-ttu-id="46f78-124">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="46f78-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="46f78-125">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="46f78-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="46f78-126">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="46f78-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="46f78-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="46f78-127">Remarks</span></span>  
 <span data-ttu-id="46f78-128">`QueueUserWorkItem` iş parçacığı havuzundaki çalışan iş parçacığı için bir iş öğesini kuyruğa yerleştirir.</span><span class="sxs-lookup"><span data-stu-id="46f78-128">`QueueUserWorkItem` queues a work item to a worker thread in the thread pool.</span></span> <span data-ttu-id="46f78-129">İmza ve parametre türlerinden aynı ada sahip karşılık gelen Win32 işlevini gereksinimlerine aynıdır.</span><span class="sxs-lookup"><span data-stu-id="46f78-129">Its signature and parameter types are identical to those of the corresponding Win32 function, which has the same name.</span></span> <span data-ttu-id="46f78-130">Daha fazla bilgi için Windows Platform belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="46f78-130">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46f78-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="46f78-131">Requirements</span></span>  
 <span data-ttu-id="46f78-132">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="46f78-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46f78-133">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="46f78-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="46f78-134">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="46f78-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="46f78-135">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46f78-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46f78-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="46f78-136">See also</span></span>
- <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="46f78-137">IHostThreadPoolManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="46f78-137">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
