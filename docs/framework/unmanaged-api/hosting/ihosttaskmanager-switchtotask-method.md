---
title: IHostTaskManager::SwitchToTask Yöntemi
ms.date: 03/30/2017
api_name:
- IHostTaskManager.SwitchToTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::SwitchToTask
helpviewer_keywords:
- IHostTaskManager::SwitchToTask method [.NET Framework hosting]
- SwitchToTask method [.NET Framework hosting]
ms.assetid: 35d0c27e-4b14-49ce-810d-7ab2120177e8
topic_type:
- apiref
ms.openlocfilehash: a55b43f3629cebb0ba1d3a7ac1802126874418d8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122123"
---
# <a name="ihosttaskmanagerswitchtotask-method"></a><span data-ttu-id="d9058-102">IHostTaskManager::SwitchToTask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d9058-102">IHostTaskManager::SwitchToTask Method</span></span>
<span data-ttu-id="d9058-103">Ana bilgisayara geçerli görevi geçiş yapmak zorunda olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="d9058-103">Notifies the host that it should switch out the current task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9058-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d9058-104">Syntax</span></span>  
  
```cpp  
HRESULT SwitchToTask (  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d9058-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d9058-105">Parameters</span></span>  
 `option`  
 <span data-ttu-id="d9058-106">'ndaki [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) sabit listesi değerlerinden biri, istenen işlem engelliyorsa konağın yapması gereken eylemi belirtir.</span><span class="sxs-lookup"><span data-stu-id="d9058-106">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) enumeration values, indicating the action the host should take if the requested operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d9058-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d9058-107">Return Value</span></span>  
  
|<span data-ttu-id="d9058-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d9058-108">HRESULT</span></span>|<span data-ttu-id="d9058-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d9058-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d9058-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="d9058-110">S_OK</span></span>|<span data-ttu-id="d9058-111">`SwitchToTask` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="d9058-111">`SwitchToTask` returned successfully.</span></span>|  
|<span data-ttu-id="d9058-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d9058-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d9058-113">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="d9058-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d9058-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d9058-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d9058-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="d9058-115">The call timed out.</span></span>|  
|<span data-ttu-id="d9058-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d9058-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d9058-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="d9058-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d9058-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d9058-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d9058-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="d9058-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d9058-120">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="d9058-120">E_FAIL</span></span>|<span data-ttu-id="d9058-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="d9058-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d9058-122">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="d9058-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d9058-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="d9058-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d9058-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d9058-124">Remarks</span></span>  
 <span data-ttu-id="d9058-125">Konak, istenen veya gereken şekilde başka bir görevde geçiş yapabilir.</span><span class="sxs-lookup"><span data-stu-id="d9058-125">The host can switch in another task as desired or needed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d9058-126">`SwitchToTask` konağın hangi görevi geçmesi gerektiğini belirtmez; yalnızca geçiş yapmak zorunda olduğu görevi belirtir.</span><span class="sxs-lookup"><span data-stu-id="d9058-126">`SwitchToTask` does not specify which task the host should switch to; it specifies only the task that it should switch from.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9058-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d9058-127">Requirements</span></span>  
 <span data-ttu-id="d9058-128">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9058-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9058-129">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d9058-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d9058-130">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="d9058-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d9058-131">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9058-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9058-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d9058-132">See also</span></span>

- [<span data-ttu-id="d9058-133">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d9058-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="d9058-134">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d9058-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="d9058-135">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d9058-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="d9058-136">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d9058-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
