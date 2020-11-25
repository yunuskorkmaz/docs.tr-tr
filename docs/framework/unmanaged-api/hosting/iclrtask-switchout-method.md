---
title: ICLRTask::SwitchOut Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRTask.SwitchOut
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::SwitchOut
helpviewer_keywords:
- ICLRTask::SwitchOut method [.NET Framework hosting]
- SwitchOut method [.NET Framework hosting]
ms.assetid: b6fb168c-b24b-4ecf-a390-2b5ba3317ae6
topic_type:
- apiref
ms.openlocfilehash: 1b27983b3f10eba225442dcd2f5df02062e53ed4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720282"
---
# <a name="iclrtaskswitchout-method"></a><span data-ttu-id="065bd-102">ICLRTask::SwitchOut Yöntemi</span><span class="sxs-lookup"><span data-stu-id="065bd-102">ICLRTask::SwitchOut Method</span></span>

<span data-ttu-id="065bd-103">Geçerli [ICLRTask](iclrtask-interface.md) örneği tarafından temsil edilen görevin artık bir çalıştırılabilir durumunda olmadığını ortak dil çalışma zamanına (CLR) bildirir.</span><span class="sxs-lookup"><span data-stu-id="065bd-103">Notifies the common language runtime (CLR) that the task represented by the current [ICLRTask](iclrtask-interface.md) instance is no longer in an operable state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="065bd-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="065bd-104">Syntax</span></span>  
  
```cpp  
HRESULT SwitchOut ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="065bd-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="065bd-105">Return Value</span></span>  
  
|<span data-ttu-id="065bd-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="065bd-106">HRESULT</span></span>|<span data-ttu-id="065bd-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="065bd-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="065bd-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="065bd-108">S_OK</span></span>|<span data-ttu-id="065bd-109">`SwitchOut` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="065bd-109">`SwitchOut` returned successfully.</span></span>|  
|<span data-ttu-id="065bd-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="065bd-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="065bd-111">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="065bd-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="065bd-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="065bd-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="065bd-113">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="065bd-113">The call timed out.</span></span>|  
|<span data-ttu-id="065bd-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="065bd-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="065bd-115">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="065bd-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="065bd-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="065bd-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="065bd-117">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="065bd-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="065bd-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="065bd-118">E_FAIL</span></span>|<span data-ttu-id="065bd-119">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="065bd-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="065bd-120">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="065bd-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="065bd-121">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="065bd-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="065bd-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="065bd-122">Remarks</span></span>  

 <span data-ttu-id="065bd-123">Bir ana bilgisayar `SwitchOut` , clr 'yi, geçerli örneği temsil eden görevi yürütmeyi geçici olarak durdurduğunu bilgilendirmek için çağırır `ICLRTask` ve görevi yeniden zamanlayacaktır.</span><span class="sxs-lookup"><span data-stu-id="065bd-123">A host calls `SwitchOut` to inform the CLR that it has temporarily stopped executing the task that the current `ICLRTask` instance represents, and will reschedule the task.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="065bd-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="065bd-124">Requirements</span></span>  

 <span data-ttu-id="065bd-125">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="065bd-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="065bd-126">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="065bd-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="065bd-127">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="065bd-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="065bd-128">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="065bd-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="065bd-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="065bd-129">See also</span></span>

- [<span data-ttu-id="065bd-130">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="065bd-130">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="065bd-131">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="065bd-131">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="065bd-132">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="065bd-132">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="065bd-133">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="065bd-133">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
