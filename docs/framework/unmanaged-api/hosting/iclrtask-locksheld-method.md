---
title: ICLRTask::LocksHeld Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRTask.LocksHeld
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::LocksHeld
helpviewer_keywords:
- LocksHeld method [.NET Framework hosting]
- ICLRTask::LocksHeld method [.NET Framework hosting]
ms.assetid: e88a4dc3-02cc-4703-a474-292b71c40657
topic_type:
- apiref
ms.openlocfilehash: 755dfed4107a602390a4402a2dde83e08986b623
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731702"
---
# <a name="iclrtasklocksheld-method"></a><span data-ttu-id="1d214-102">ICLRTask::LocksHeld Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1d214-102">ICLRTask::LocksHeld Method</span></span>

<span data-ttu-id="1d214-103">Görevde şu anda tutulan kilitlerin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="1d214-103">Gets the number of locks currently held on the task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d214-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="1d214-104">Syntax</span></span>  
  
```cpp  
HRESULT LocksHeld (  
    [out] SIZE_T *pLockCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1d214-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1d214-105">Parameters</span></span>  

 `pLockCount`  
 <span data-ttu-id="1d214-106">dışı Yöntem çağrısı sırasında görevde tutulan kilitlerin sayısı.</span><span class="sxs-lookup"><span data-stu-id="1d214-106">[out] The number of locks held on the task at the time of the method call.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1d214-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1d214-107">Return Value</span></span>  
  
|<span data-ttu-id="1d214-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1d214-108">HRESULT</span></span>|<span data-ttu-id="1d214-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1d214-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1d214-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="1d214-110">S_OK</span></span>|<span data-ttu-id="1d214-111">`LocksHeld` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="1d214-111">`LocksHeld` returned successfully.</span></span>|  
|<span data-ttu-id="1d214-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1d214-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1d214-113">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="1d214-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1d214-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1d214-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1d214-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="1d214-115">The call timed out.</span></span>|  
|<span data-ttu-id="1d214-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1d214-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1d214-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="1d214-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1d214-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1d214-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1d214-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="1d214-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1d214-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1d214-120">E_FAIL</span></span>|<span data-ttu-id="1d214-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="1d214-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1d214-122">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="1d214-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1d214-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="1d214-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1d214-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1d214-124">Requirements</span></span>  

 <span data-ttu-id="1d214-125">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1d214-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d214-126">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="1d214-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1d214-127">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="1d214-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1d214-128">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d214-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d214-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1d214-129">See also</span></span>

- [<span data-ttu-id="1d214-130">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1d214-130">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="1d214-131">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1d214-131">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="1d214-132">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1d214-132">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="1d214-133">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1d214-133">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
