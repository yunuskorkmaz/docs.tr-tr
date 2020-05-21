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
ms.openlocfilehash: c67f00acd61d6e0cdf3adfa0d3d0fda2a06a6f31
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762994"
---
# <a name="iclrtasklocksheld-method"></a><span data-ttu-id="8005b-102">ICLRTask::LocksHeld Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8005b-102">ICLRTask::LocksHeld Method</span></span>
<span data-ttu-id="8005b-103">Görevde şu anda tutulan kilitlerin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="8005b-103">Gets the number of locks currently held on the task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8005b-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="8005b-104">Syntax</span></span>  
  
```cpp  
HRESULT LocksHeld (  
    [out] SIZE_T *pLockCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8005b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8005b-105">Parameters</span></span>  
 `pLockCount`  
 <span data-ttu-id="8005b-106">dışı Yöntem çağrısı sırasında görevde tutulan kilitlerin sayısı.</span><span class="sxs-lookup"><span data-stu-id="8005b-106">[out] The number of locks held on the task at the time of the method call.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8005b-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8005b-107">Return Value</span></span>  
  
|<span data-ttu-id="8005b-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8005b-108">HRESULT</span></span>|<span data-ttu-id="8005b-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8005b-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8005b-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="8005b-110">S_OK</span></span>|<span data-ttu-id="8005b-111">`LocksHeld`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="8005b-111">`LocksHeld` returned successfully.</span></span>|  
|<span data-ttu-id="8005b-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8005b-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8005b-113">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="8005b-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8005b-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8005b-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8005b-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="8005b-115">The call timed out.</span></span>|  
|<span data-ttu-id="8005b-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8005b-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8005b-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="8005b-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8005b-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8005b-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8005b-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="8005b-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8005b-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8005b-120">E_FAIL</span></span>|<span data-ttu-id="8005b-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="8005b-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8005b-122">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="8005b-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8005b-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="8005b-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8005b-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8005b-124">Requirements</span></span>  
 <span data-ttu-id="8005b-125">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8005b-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8005b-126">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8005b-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8005b-127">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="8005b-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8005b-128">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8005b-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8005b-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8005b-129">See also</span></span>

- [<span data-ttu-id="8005b-130">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8005b-130">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="8005b-131">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8005b-131">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="8005b-132">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8005b-132">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="8005b-133">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8005b-133">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
