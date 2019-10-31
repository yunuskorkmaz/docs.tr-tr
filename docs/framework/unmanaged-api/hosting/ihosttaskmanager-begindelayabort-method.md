---
title: IHostTaskManager::BeginDelayAbort Yöntemi
ms.date: 03/30/2017
api_name:
- IHostTaskManager.BeginDelayAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::BeginDelayAbort
helpviewer_keywords:
- BeginDelayAbort method [.NET Framework hosting]
- IHostTaskManager::BeginDelayAbort method [.NET Framework hosting]
ms.assetid: 75f42a8b-ed68-4718-a030-a179cfba7d72
topic_type:
- apiref
ms.openlocfilehash: b765d5449cebbdec5f106a8e4743fee2f0ee5521
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133135"
---
# <a name="ihosttaskmanagerbegindelayabort-method"></a><span data-ttu-id="666b9-102">IHostTaskManager::BeginDelayAbort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="666b9-102">IHostTaskManager::BeginDelayAbort Method</span></span>
<span data-ttu-id="666b9-103">Ana bilgisayara, yönetilen kodun geçerli görevin durdurulmayan bir dönem girdiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="666b9-103">Notifies the host that managed code is entering a period in which the current task must not be aborted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="666b9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="666b9-104">Syntax</span></span>  
  
```cpp  
HRESULT BeginDelayAbort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="666b9-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="666b9-105">Return Value</span></span>  
  
|<span data-ttu-id="666b9-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="666b9-106">HRESULT</span></span>|<span data-ttu-id="666b9-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="666b9-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="666b9-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="666b9-108">S_OK</span></span>|<span data-ttu-id="666b9-109">`BeginDelayAbort` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="666b9-109">`BeginDelayAbort` returned successfully.</span></span>|  
|<span data-ttu-id="666b9-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="666b9-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="666b9-111">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="666b9-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="666b9-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="666b9-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="666b9-113">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="666b9-113">The call timed out.</span></span>|  
|<span data-ttu-id="666b9-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="666b9-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="666b9-115">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="666b9-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="666b9-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="666b9-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="666b9-117">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="666b9-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="666b9-118">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="666b9-118">E_FAIL</span></span>|<span data-ttu-id="666b9-119">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="666b9-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="666b9-120">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="666b9-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="666b9-121">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="666b9-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="666b9-122">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="666b9-122">E_UNEXPECTED</span></span>|<span data-ttu-id="666b9-123">`BeginDelayAbort` zaten çağrıldı, ancak buna karşılık gelen [EndDelayAbort](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enddelayabort-method.md) çağrısı henüz alınmadı.</span><span class="sxs-lookup"><span data-stu-id="666b9-123">`BeginDelayAbort` has already been called, but the corresponding call to [EndDelayAbort](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enddelayabort-method.md) has not yet been received.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="666b9-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="666b9-124">Remarks</span></span>  
 <span data-ttu-id="666b9-125">`EndDelayAbort` çağrılana kadar konağın geçerli görevi iptal etmelidir.</span><span class="sxs-lookup"><span data-stu-id="666b9-125">The host must not abort the current task until `EndDelayAbort` is called.</span></span> <span data-ttu-id="666b9-126">`BeginDelayAbort` başka bir çağrısı, `EndDelayAbort`için bir araya getirilen çağrı olmadan yapılırsa, ana bilgisayar `BeginDelayAbort`'tan E_UNEXPECTED döndürmelidir ve hiçbir işlem yapmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="666b9-126">If another call to `BeginDelayAbort` is made without an intervening call to `EndDelayAbort`, the host should return E_UNEXPECTED from `BeginDelayAbort`, and should take no action.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="666b9-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="666b9-127">Requirements</span></span>  
 <span data-ttu-id="666b9-128">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="666b9-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="666b9-129">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="666b9-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="666b9-130">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="666b9-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="666b9-131">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="666b9-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="666b9-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="666b9-132">See also</span></span>

- [<span data-ttu-id="666b9-133">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="666b9-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="666b9-134">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="666b9-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="666b9-135">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="666b9-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
