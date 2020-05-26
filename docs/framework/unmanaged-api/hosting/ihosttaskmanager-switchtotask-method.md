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
ms.openlocfilehash: 7d1511924fc70c42252881a46f8aebb437a3f4f7
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83841951"
---
# <a name="ihosttaskmanagerswitchtotask-method"></a><span data-ttu-id="43d75-102">IHostTaskManager::SwitchToTask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="43d75-102">IHostTaskManager::SwitchToTask Method</span></span>
<span data-ttu-id="43d75-103">Ana bilgisayara geçerli görevi geçiş yapmak zorunda olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="43d75-103">Notifies the host that it should switch out the current task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43d75-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="43d75-104">Syntax</span></span>  
  
```cpp  
HRESULT SwitchToTask (  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="43d75-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="43d75-105">Parameters</span></span>  
 `option`  
 <span data-ttu-id="43d75-106">'ndaki İstenen işlem engelliyorsa konağın yapması gereken eylemi belirten [WAIT_OPTION](wait-option-enumeration.md) sabit listesi değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="43d75-106">[in] One of the [WAIT_OPTION](wait-option-enumeration.md) enumeration values, indicating the action the host should take if the requested operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="43d75-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="43d75-107">Return Value</span></span>  
  
|<span data-ttu-id="43d75-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="43d75-108">HRESULT</span></span>|<span data-ttu-id="43d75-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="43d75-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="43d75-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="43d75-110">S_OK</span></span>|<span data-ttu-id="43d75-111">`SwitchToTask`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="43d75-111">`SwitchToTask` returned successfully.</span></span>|  
|<span data-ttu-id="43d75-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="43d75-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="43d75-113">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="43d75-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="43d75-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="43d75-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="43d75-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="43d75-115">The call timed out.</span></span>|  
|<span data-ttu-id="43d75-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="43d75-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="43d75-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="43d75-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="43d75-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="43d75-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="43d75-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="43d75-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="43d75-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="43d75-120">E_FAIL</span></span>|<span data-ttu-id="43d75-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="43d75-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="43d75-122">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="43d75-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="43d75-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="43d75-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="43d75-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="43d75-124">Remarks</span></span>  
 <span data-ttu-id="43d75-125">Konak, istenen veya gereken şekilde başka bir görevde geçiş yapabilir.</span><span class="sxs-lookup"><span data-stu-id="43d75-125">The host can switch in another task as desired or needed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="43d75-126">`SwitchToTask`Konağın hangi görevi geçmesi gerektiğini belirtmez; yalnızca geçiş yapmak zorunda olduğu görevi belirtir.</span><span class="sxs-lookup"><span data-stu-id="43d75-126">`SwitchToTask` does not specify which task the host should switch to; it specifies only the task that it should switch from.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43d75-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="43d75-127">Requirements</span></span>  
 <span data-ttu-id="43d75-128">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="43d75-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43d75-129">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="43d75-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="43d75-130">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="43d75-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="43d75-131">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43d75-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43d75-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="43d75-132">See also</span></span>

- [<span data-ttu-id="43d75-133">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="43d75-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="43d75-134">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="43d75-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="43d75-135">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="43d75-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="43d75-136">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="43d75-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
