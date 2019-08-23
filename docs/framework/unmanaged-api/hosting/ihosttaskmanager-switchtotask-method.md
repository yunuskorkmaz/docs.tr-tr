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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4af3d73a4c45654d1d40ef2fbf44a0e2b3e1bf32
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913708"
---
# <a name="ihosttaskmanagerswitchtotask-method"></a><span data-ttu-id="95c09-102">IHostTaskManager::SwitchToTask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="95c09-102">IHostTaskManager::SwitchToTask Method</span></span>
<span data-ttu-id="95c09-103">Ana bilgisayara geçerli görevi geçiş yapmak zorunda olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="95c09-103">Notifies the host that it should switch out the current task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95c09-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="95c09-104">Syntax</span></span>  
  
```cpp  
HRESULT SwitchToTask (  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="95c09-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="95c09-105">Parameters</span></span>  
 `option`  
 <span data-ttu-id="95c09-106">'ndaki [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) sabit listesi değerlerinden biri, istenen işlem engelliyorsa konağın yapması gereken eylemi belirtir.</span><span class="sxs-lookup"><span data-stu-id="95c09-106">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) enumeration values, indicating the action the host should take if the requested operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="95c09-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="95c09-107">Return Value</span></span>  
  
|<span data-ttu-id="95c09-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="95c09-108">HRESULT</span></span>|<span data-ttu-id="95c09-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="95c09-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="95c09-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="95c09-110">S_OK</span></span>|<span data-ttu-id="95c09-111">`SwitchToTask`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="95c09-111">`SwitchToTask` returned successfully.</span></span>|  
|<span data-ttu-id="95c09-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="95c09-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="95c09-113">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="95c09-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="95c09-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="95c09-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="95c09-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="95c09-115">The call timed out.</span></span>|  
|<span data-ttu-id="95c09-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="95c09-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="95c09-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="95c09-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="95c09-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="95c09-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="95c09-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="95c09-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="95c09-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="95c09-120">E_FAIL</span></span>|<span data-ttu-id="95c09-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="95c09-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="95c09-122">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="95c09-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="95c09-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="95c09-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="95c09-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="95c09-124">Remarks</span></span>  
 <span data-ttu-id="95c09-125">Konak, istenen veya gereken şekilde başka bir görevde geçiş yapabilir.</span><span class="sxs-lookup"><span data-stu-id="95c09-125">The host can switch in another task as desired or needed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="95c09-126">`SwitchToTask`Konağın hangi görevi geçmesi gerektiğini belirtmez; yalnızca geçiş yapmak zorunda olduğu görevi belirtir.</span><span class="sxs-lookup"><span data-stu-id="95c09-126">`SwitchToTask` does not specify which task the host should switch to; it specifies only the task that it should switch from.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95c09-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="95c09-127">Requirements</span></span>  
 <span data-ttu-id="95c09-128">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95c09-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95c09-129">**Üst bilgi** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="95c09-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="95c09-130">**Kitaplığı** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="95c09-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="95c09-131">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95c09-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95c09-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="95c09-132">See also</span></span>

- [<span data-ttu-id="95c09-133">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="95c09-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="95c09-134">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="95c09-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="95c09-135">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="95c09-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="95c09-136">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="95c09-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
