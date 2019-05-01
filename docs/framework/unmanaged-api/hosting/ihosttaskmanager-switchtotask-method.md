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
ms.openlocfilehash: a50c9f7fc5921d3e5c21dd3566de81ac2249f3dd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61796610"
---
# <a name="ihosttaskmanagerswitchtotask-method"></a><span data-ttu-id="cfbe3-102">IHostTaskManager::SwitchToTask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cfbe3-102">IHostTaskManager::SwitchToTask Method</span></span>
<span data-ttu-id="cfbe3-103">Konak, geçerli görevi geçmelisiniz bildirir.</span><span class="sxs-lookup"><span data-stu-id="cfbe3-103">Notifies the host that it should switch out the current task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cfbe3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cfbe3-104">Syntax</span></span>  
  
```  
HRESULT SwitchToTask (  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cfbe3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cfbe3-105">Parameters</span></span>  
 `option`  
 <span data-ttu-id="cfbe3-106">[in] Aşağıdakilerden birini [waıt_optıon](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) konak sürebilir, eylemini belirten numaralandırma değerlerinin istenen işlem engeller.</span><span class="sxs-lookup"><span data-stu-id="cfbe3-106">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) enumeration values, indicating the action the host should take if the requested operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cfbe3-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="cfbe3-107">Return Value</span></span>  
  
|<span data-ttu-id="cfbe3-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cfbe3-108">HRESULT</span></span>|<span data-ttu-id="cfbe3-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cfbe3-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cfbe3-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="cfbe3-110">S_OK</span></span>|<span data-ttu-id="cfbe3-111">`SwitchToTask` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="cfbe3-111">`SwitchToTask` returned successfully.</span></span>|  
|<span data-ttu-id="cfbe3-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="cfbe3-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="cfbe3-113">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="cfbe3-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="cfbe3-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="cfbe3-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="cfbe3-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="cfbe3-115">The call timed out.</span></span>|  
|<span data-ttu-id="cfbe3-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="cfbe3-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="cfbe3-117">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="cfbe3-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="cfbe3-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="cfbe3-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="cfbe3-119">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="cfbe3-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="cfbe3-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="cfbe3-120">E_FAIL</span></span>|<span data-ttu-id="cfbe3-121">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="cfbe3-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="cfbe3-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="cfbe3-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="cfbe3-123">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="cfbe3-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cfbe3-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cfbe3-124">Remarks</span></span>  
 <span data-ttu-id="cfbe3-125">Konak, istenen veya gerekli olarak başka bir görev içinde geçiş yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cfbe3-125">The host can switch in another task as desired or needed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cfbe3-126">`SwitchToTask` ana bilgisayar geçiş yapmamalıdır hangi görev belirtmez; Bu, yalnızca, geçiş görev belirtir.</span><span class="sxs-lookup"><span data-stu-id="cfbe3-126">`SwitchToTask` does not specify which task the host should switch to; it specifies only the task that it should switch from.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cfbe3-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cfbe3-127">Requirements</span></span>  
 <span data-ttu-id="cfbe3-128">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cfbe3-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cfbe3-129">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="cfbe3-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cfbe3-130">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="cfbe3-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cfbe3-131">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cfbe3-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfbe3-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cfbe3-132">See also</span></span>

- [<span data-ttu-id="cfbe3-133">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cfbe3-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="cfbe3-134">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cfbe3-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="cfbe3-135">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cfbe3-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="cfbe3-136">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cfbe3-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
