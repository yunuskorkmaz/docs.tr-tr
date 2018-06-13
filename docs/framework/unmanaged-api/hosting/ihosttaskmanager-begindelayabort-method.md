---
title: IHostTaskManager::BeginDelayAbort Yöntemi
ms.date: 03/30/2017
api_name:
- IHostTaskManager.BeginDelayAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::BeginDelayAbort
helpviewer_keywords:
- BeginDelayAbort method [.NET Framework hosting]
- IHostTaskManager::BeginDelayAbort method [.NET Framework hosting]
ms.assetid: 75f42a8b-ed68-4718-a030-a179cfba7d72
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 65bb59efa9d38fa32baa38eb239103f5cfa8be86
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33441922"
---
# <a name="ihosttaskmanagerbegindelayabort-method"></a><span data-ttu-id="f6491-102">IHostTaskManager::BeginDelayAbort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f6491-102">IHostTaskManager::BeginDelayAbort Method</span></span>
<span data-ttu-id="f6491-103">Yönetilen kod konak bir süre içinde geçerli görev iptal gerekir girme bildirir.</span><span class="sxs-lookup"><span data-stu-id="f6491-103">Notifies the host that managed code is entering a period in which the current task must not be aborted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6491-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f6491-104">Syntax</span></span>  
  
```  
HRESULT BeginDelayAbort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="f6491-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f6491-105">Return Value</span></span>  
  
|<span data-ttu-id="f6491-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f6491-106">HRESULT</span></span>|<span data-ttu-id="f6491-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f6491-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f6491-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="f6491-108">S_OK</span></span>|<span data-ttu-id="f6491-109">`BeginDelayAbort` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="f6491-109">`BeginDelayAbort` returned successfully.</span></span>|  
|<span data-ttu-id="f6491-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f6491-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f6491-111">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="f6491-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f6491-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f6491-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f6491-113">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="f6491-113">The call timed out.</span></span>|  
|<span data-ttu-id="f6491-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f6491-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f6491-115">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="f6491-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f6491-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f6491-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f6491-117">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="f6491-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f6491-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f6491-118">E_FAIL</span></span>|<span data-ttu-id="f6491-119">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="f6491-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f6491-120">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="f6491-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f6491-121">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="f6491-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="f6491-122">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="f6491-122">E_UNEXPECTED</span></span>|<span data-ttu-id="f6491-123">`BeginDelayAbort` zaten, ancak karşılık gelen çağrıyı çağrıldı [EndDelayAbort](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enddelayabort-method.md) henüz alınmamıştır.</span><span class="sxs-lookup"><span data-stu-id="f6491-123">`BeginDelayAbort` has already been called, but the corresponding call to [EndDelayAbort](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enddelayabort-method.md) has not yet been received.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f6491-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f6491-124">Remarks</span></span>  
 <span data-ttu-id="f6491-125">Ana kadar geçerli görevi iptal değil `EndDelayAbort` olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="f6491-125">The host must not abort the current task until `EndDelayAbort` is called.</span></span> <span data-ttu-id="f6491-126">Başka bir şekilde çağırırsanız `BeginDelayAbort` müdahalede bulunan bir çağrı olmadan yapılan `EndDelayAbort`, konağı ndan E_UNEXPECTED döndürmelidir `BeginDelayAbort`ve herhangi bir eylem yapması.</span><span class="sxs-lookup"><span data-stu-id="f6491-126">If another call to `BeginDelayAbort` is made without an intervening call to `EndDelayAbort`, the host should return E_UNEXPECTED from `BeginDelayAbort`, and should take no action.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6491-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f6491-127">Requirements</span></span>  
 <span data-ttu-id="f6491-128">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6491-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6491-129">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f6491-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f6491-130">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="f6491-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f6491-131">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6491-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6491-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f6491-132">See Also</span></span>  
 [<span data-ttu-id="f6491-133">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f6491-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="f6491-134">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f6491-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="f6491-135">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f6491-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="f6491-136">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f6491-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
