---
description: 'Şu konuda daha fazla bilgi edinin: ICLRTask:: LocksHeld Yöntemi'
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
ms.openlocfilehash: 5dff0b2a80594e03d61d50c6d9fa52bb12bb42f2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799557"
---
# <a name="iclrtasklocksheld-method"></a><span data-ttu-id="bbe36-103">ICLRTask::LocksHeld Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bbe36-103">ICLRTask::LocksHeld Method</span></span>

<span data-ttu-id="bbe36-104">Görevde şu anda tutulan kilitlerin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="bbe36-104">Gets the number of locks currently held on the task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bbe36-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bbe36-105">Syntax</span></span>  
  
```cpp  
HRESULT LocksHeld (  
    [out] SIZE_T *pLockCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bbe36-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bbe36-106">Parameters</span></span>  

 `pLockCount`  
 <span data-ttu-id="bbe36-107">dışı Yöntem çağrısı sırasında görevde tutulan kilitlerin sayısı.</span><span class="sxs-lookup"><span data-stu-id="bbe36-107">[out] The number of locks held on the task at the time of the method call.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bbe36-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="bbe36-108">Return Value</span></span>  
  
|<span data-ttu-id="bbe36-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bbe36-109">HRESULT</span></span>|<span data-ttu-id="bbe36-110">Description</span><span class="sxs-lookup"><span data-stu-id="bbe36-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bbe36-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="bbe36-111">S_OK</span></span>|<span data-ttu-id="bbe36-112">`LocksHeld` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="bbe36-112">`LocksHeld` returned successfully.</span></span>|  
|<span data-ttu-id="bbe36-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="bbe36-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="bbe36-114">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="bbe36-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="bbe36-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="bbe36-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="bbe36-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="bbe36-116">The call timed out.</span></span>|  
|<span data-ttu-id="bbe36-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="bbe36-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="bbe36-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="bbe36-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="bbe36-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="bbe36-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="bbe36-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="bbe36-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="bbe36-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bbe36-121">E_FAIL</span></span>|<span data-ttu-id="bbe36-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="bbe36-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="bbe36-123">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="bbe36-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="bbe36-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="bbe36-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bbe36-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bbe36-125">Requirements</span></span>  

 <span data-ttu-id="bbe36-126">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bbe36-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bbe36-127">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="bbe36-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bbe36-128">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="bbe36-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bbe36-129">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bbe36-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbe36-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bbe36-130">See also</span></span>

- [<span data-ttu-id="bbe36-131">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bbe36-131">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="bbe36-132">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bbe36-132">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="bbe36-133">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bbe36-133">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="bbe36-134">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bbe36-134">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
