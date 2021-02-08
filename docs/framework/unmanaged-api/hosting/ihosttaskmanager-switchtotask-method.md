---
description: ': IHostTaskManager:: SwitchToTask Yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 6333dcdf7e1bbe6bde575f53f4743a1300c770f3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789365"
---
# <a name="ihosttaskmanagerswitchtotask-method"></a><span data-ttu-id="b4b5b-103">IHostTaskManager::SwitchToTask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b4b5b-103">IHostTaskManager::SwitchToTask Method</span></span>

<span data-ttu-id="b4b5b-104">Ana bilgisayara geçerli görevi geçiş yapmak zorunda olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="b4b5b-104">Notifies the host that it should switch out the current task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4b5b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b4b5b-105">Syntax</span></span>  
  
```cpp  
HRESULT SwitchToTask (  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b4b5b-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b4b5b-106">Parameters</span></span>  

 `option`  
 <span data-ttu-id="b4b5b-107">'ndaki İstenen işlem engelliyorsa konağın yapması gereken eylemi belirten [WAIT_OPTION](wait-option-enumeration.md) sabit listesi değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="b4b5b-107">[in] One of the [WAIT_OPTION](wait-option-enumeration.md) enumeration values, indicating the action the host should take if the requested operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b4b5b-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b4b5b-108">Return Value</span></span>  
  
|<span data-ttu-id="b4b5b-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b4b5b-109">HRESULT</span></span>|<span data-ttu-id="b4b5b-110">Description</span><span class="sxs-lookup"><span data-stu-id="b4b5b-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b4b5b-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="b4b5b-111">S_OK</span></span>|<span data-ttu-id="b4b5b-112">`SwitchToTask` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="b4b5b-112">`SwitchToTask` returned successfully.</span></span>|  
|<span data-ttu-id="b4b5b-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b4b5b-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b4b5b-114">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="b4b5b-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b4b5b-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b4b5b-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b4b5b-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="b4b5b-116">The call timed out.</span></span>|  
|<span data-ttu-id="b4b5b-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b4b5b-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b4b5b-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="b4b5b-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b4b5b-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b4b5b-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b4b5b-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="b4b5b-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b4b5b-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b4b5b-121">E_FAIL</span></span>|<span data-ttu-id="b4b5b-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="b4b5b-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b4b5b-123">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="b4b5b-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b4b5b-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="b4b5b-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b4b5b-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b4b5b-125">Remarks</span></span>  

 <span data-ttu-id="b4b5b-126">Konak, istenen veya gereken şekilde başka bir görevde geçiş yapabilir.</span><span class="sxs-lookup"><span data-stu-id="b4b5b-126">The host can switch in another task as desired or needed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b4b5b-127">`SwitchToTask` Konağın hangi görevi geçmesi gerektiğini belirtmez; yalnızca geçiş yapmak zorunda olduğu görevi belirtir.</span><span class="sxs-lookup"><span data-stu-id="b4b5b-127">`SwitchToTask` does not specify which task the host should switch to; it specifies only the task that it should switch from.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4b5b-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b4b5b-128">Requirements</span></span>  

 <span data-ttu-id="b4b5b-129">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b4b5b-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4b5b-130">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b4b5b-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b4b5b-131">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="b4b5b-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b4b5b-132">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4b5b-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4b5b-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b4b5b-133">See also</span></span>

- [<span data-ttu-id="b4b5b-134">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b4b5b-134">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="b4b5b-135">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b4b5b-135">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="b4b5b-136">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b4b5b-136">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="b4b5b-137">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b4b5b-137">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
