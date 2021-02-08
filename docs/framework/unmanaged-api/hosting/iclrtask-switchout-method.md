---
description: ': ICLRTask:: geçiş yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 6c491c4d9005fb850c5adecd025730f1ea71f513
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784944"
---
# <a name="iclrtaskswitchout-method"></a><span data-ttu-id="14270-103">ICLRTask::SwitchOut Yöntemi</span><span class="sxs-lookup"><span data-stu-id="14270-103">ICLRTask::SwitchOut Method</span></span>

<span data-ttu-id="14270-104">Geçerli [ICLRTask](iclrtask-interface.md) örneği tarafından temsil edilen görevin artık bir çalıştırılabilir durumunda olmadığını ortak dil çalışma zamanına (CLR) bildirir.</span><span class="sxs-lookup"><span data-stu-id="14270-104">Notifies the common language runtime (CLR) that the task represented by the current [ICLRTask](iclrtask-interface.md) instance is no longer in an operable state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14270-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="14270-105">Syntax</span></span>  
  
```cpp  
HRESULT SwitchOut ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="14270-106">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="14270-106">Return Value</span></span>  
  
|<span data-ttu-id="14270-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="14270-107">HRESULT</span></span>|<span data-ttu-id="14270-108">Description</span><span class="sxs-lookup"><span data-stu-id="14270-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="14270-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="14270-109">S_OK</span></span>|<span data-ttu-id="14270-110">`SwitchOut` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="14270-110">`SwitchOut` returned successfully.</span></span>|  
|<span data-ttu-id="14270-111">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="14270-111">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="14270-112">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="14270-112">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="14270-113">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="14270-113">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="14270-114">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="14270-114">The call timed out.</span></span>|  
|<span data-ttu-id="14270-115">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="14270-115">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="14270-116">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="14270-116">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="14270-117">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="14270-117">HOST_E_ABANDONED</span></span>|<span data-ttu-id="14270-118">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="14270-118">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="14270-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="14270-119">E_FAIL</span></span>|<span data-ttu-id="14270-120">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="14270-120">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="14270-121">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="14270-121">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="14270-122">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="14270-122">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="14270-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="14270-123">Remarks</span></span>  

 <span data-ttu-id="14270-124">Bir ana bilgisayar `SwitchOut` , clr 'yi, geçerli örneği temsil eden görevi yürütmeyi geçici olarak durdurduğunu bilgilendirmek için çağırır `ICLRTask` ve görevi yeniden zamanlayacaktır.</span><span class="sxs-lookup"><span data-stu-id="14270-124">A host calls `SwitchOut` to inform the CLR that it has temporarily stopped executing the task that the current `ICLRTask` instance represents, and will reschedule the task.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="14270-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="14270-125">Requirements</span></span>  

 <span data-ttu-id="14270-126">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="14270-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14270-127">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="14270-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="14270-128">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="14270-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="14270-129">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14270-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14270-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="14270-130">See also</span></span>

- [<span data-ttu-id="14270-131">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="14270-131">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="14270-132">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="14270-132">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="14270-133">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="14270-133">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="14270-134">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="14270-134">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
