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
ms.openlocfilehash: 75517ae55ebae07242f19c19c5473780ce4b0809
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762922"
---
# <a name="iclrtaskswitchout-method"></a><span data-ttu-id="ae318-102">ICLRTask::SwitchOut Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ae318-102">ICLRTask::SwitchOut Method</span></span>
<span data-ttu-id="ae318-103">Geçerli [ICLRTask](iclrtask-interface.md) örneği tarafından temsil edilen görevin artık bir çalıştırılabilir durumunda olmadığını ortak dil çalışma zamanına (CLR) bildirir.</span><span class="sxs-lookup"><span data-stu-id="ae318-103">Notifies the common language runtime (CLR) that the task represented by the current [ICLRTask](iclrtask-interface.md) instance is no longer in an operable state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae318-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="ae318-104">Syntax</span></span>  
  
```cpp  
HRESULT SwitchOut ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="ae318-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ae318-105">Return Value</span></span>  
  
|<span data-ttu-id="ae318-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ae318-106">HRESULT</span></span>|<span data-ttu-id="ae318-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ae318-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ae318-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="ae318-108">S_OK</span></span>|<span data-ttu-id="ae318-109">`SwitchOut`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="ae318-109">`SwitchOut` returned successfully.</span></span>|  
|<span data-ttu-id="ae318-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ae318-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ae318-111">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="ae318-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ae318-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ae318-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ae318-113">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="ae318-113">The call timed out.</span></span>|  
|<span data-ttu-id="ae318-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ae318-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ae318-115">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="ae318-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ae318-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ae318-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ae318-117">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="ae318-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ae318-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ae318-118">E_FAIL</span></span>|<span data-ttu-id="ae318-119">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="ae318-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ae318-120">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="ae318-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ae318-121">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="ae318-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ae318-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ae318-122">Remarks</span></span>  
 <span data-ttu-id="ae318-123">Bir ana bilgisayar `SwitchOut` , clr 'yi, geçerli örneği temsil eden görevi yürütmeyi geçici olarak durdurduğunu bilgilendirmek için çağırır `ICLRTask` ve görevi yeniden zamanlayacaktır.</span><span class="sxs-lookup"><span data-stu-id="ae318-123">A host calls `SwitchOut` to inform the CLR that it has temporarily stopped executing the task that the current `ICLRTask` instance represents, and will reschedule the task.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae318-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ae318-124">Requirements</span></span>  
 <span data-ttu-id="ae318-125">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae318-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae318-126">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ae318-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ae318-127">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="ae318-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ae318-128">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae318-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae318-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ae318-129">See also</span></span>

- [<span data-ttu-id="ae318-130">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ae318-130">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="ae318-131">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ae318-131">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="ae318-132">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ae318-132">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="ae318-133">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ae318-133">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
