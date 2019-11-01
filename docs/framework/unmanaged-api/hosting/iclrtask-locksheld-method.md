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
ms.openlocfilehash: 3a3c42e2877957e3bbf5031e6ba650e4c9e0364e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73195941"
---
# <a name="iclrtasklocksheld-method"></a><span data-ttu-id="c6d07-102">ICLRTask::LocksHeld Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c6d07-102">ICLRTask::LocksHeld Method</span></span>
<span data-ttu-id="c6d07-103">Görevde şu anda tutulan kilitlerin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="c6d07-103">Gets the number of locks currently held on the task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6d07-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c6d07-104">Syntax</span></span>  
  
```cpp  
HRESULT LocksHeld (  
    [out] SIZE_T *pLockCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c6d07-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c6d07-105">Parameters</span></span>  
 `pLockCount`  
 <span data-ttu-id="c6d07-106">dışı Yöntem çağrısı sırasında görevde tutulan kilitlerin sayısı.</span><span class="sxs-lookup"><span data-stu-id="c6d07-106">[out] The number of locks held on the task at the time of the method call.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c6d07-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c6d07-107">Return Value</span></span>  
  
|<span data-ttu-id="c6d07-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c6d07-108">HRESULT</span></span>|<span data-ttu-id="c6d07-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c6d07-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c6d07-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="c6d07-110">S_OK</span></span>|<span data-ttu-id="c6d07-111">`LocksHeld` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="c6d07-111">`LocksHeld` returned successfully.</span></span>|  
|<span data-ttu-id="c6d07-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c6d07-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c6d07-113">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="c6d07-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c6d07-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c6d07-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c6d07-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="c6d07-115">The call timed out.</span></span>|  
|<span data-ttu-id="c6d07-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c6d07-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c6d07-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="c6d07-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c6d07-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c6d07-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c6d07-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="c6d07-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c6d07-120">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="c6d07-120">E_FAIL</span></span>|<span data-ttu-id="c6d07-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="c6d07-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c6d07-122">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="c6d07-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c6d07-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="c6d07-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c6d07-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c6d07-124">Requirements</span></span>  
 <span data-ttu-id="c6d07-125">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c6d07-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6d07-126">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c6d07-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c6d07-127">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="c6d07-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c6d07-128">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6d07-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6d07-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c6d07-129">See also</span></span>

- [<span data-ttu-id="c6d07-130">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c6d07-130">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="c6d07-131">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c6d07-131">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="c6d07-132">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c6d07-132">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="c6d07-133">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c6d07-133">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
