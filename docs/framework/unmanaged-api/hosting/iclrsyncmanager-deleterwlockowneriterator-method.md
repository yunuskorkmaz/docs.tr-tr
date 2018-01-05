---
title: "ICLRSyncManager::DeleteRWLockOwnerIterator Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRSyncManager.DeleteRWLockOwnerIterator
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRSyncManager::DeleteRWLockOwnerIterator
helpviewer_keywords:
- ICLRSyncManager::DeleteRWLockOwnerIterator method [.NET Framework hosting]
- DeleteRWLockOwnerIterator method [.NET Framework hosting]
ms.assetid: fcfd340a-b7d6-44e4-8167-2c05b789d483
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dce6699dc625c5c867befe1bc2e307cfaea7719a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrsyncmanagerdeleterwlockowneriterator-method"></a><span data-ttu-id="d95f6-102">ICLRSyncManager::DeleteRWLockOwnerIterator Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d95f6-102">ICLRSyncManager::DeleteRWLockOwnerIterator Method</span></span>
<span data-ttu-id="d95f6-103">Ortak dil çalışma zamanı (CLR) için yapılan bir çağrı tarafından oluşturulmuş bir yineleyici destroy istekleri [Iclrsyncmanager::createrwlockownerıterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md).</span><span class="sxs-lookup"><span data-stu-id="d95f6-103">Requests that the common language runtime (CLR) destroy an iterator that was created by a call to [ICLRSyncManager::CreateRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d95f6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d95f6-104">Syntax</span></span>  
  
```  
HRESULT DeleteRWLockOwnerIterator (  
    [in] SIZE_T  Iterator  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d95f6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d95f6-105">Parameters</span></span>  
 `Iterator`  
 <span data-ttu-id="d95f6-106">[in] Bir çağrı kullanılarak oluşturulmuş yineleyici `CreateRWLockOwnerIterator`.</span><span class="sxs-lookup"><span data-stu-id="d95f6-106">[in] The iterator that was created by using a call to `CreateRWLockOwnerIterator`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d95f6-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d95f6-107">Return Value</span></span>  
  
|<span data-ttu-id="d95f6-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d95f6-108">HRESULT</span></span>|<span data-ttu-id="d95f6-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d95f6-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d95f6-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="d95f6-110">S_OK</span></span>|<span data-ttu-id="d95f6-111">`DeleteRWLockOwnerIterator`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="d95f6-111">`DeleteRWLockOwnerIterator` returned successfully.</span></span>|  
|<span data-ttu-id="d95f6-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d95f6-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d95f6-113">CLR süreç içine yüklendi değil veya içinde yönetilen kod çalıştıramaz veya başarıyla çağrıyı işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="d95f6-113">The CLR has not been loaded into a process, or is in a state in which it cannot run managed code or successfully process the call.</span></span>|  
|<span data-ttu-id="d95f6-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d95f6-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d95f6-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="d95f6-115">The call timed out.</span></span>|  
|<span data-ttu-id="d95f6-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d95f6-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d95f6-117">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="d95f6-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d95f6-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d95f6-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d95f6-119">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="d95f6-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d95f6-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d95f6-120">E_FAIL</span></span>|<span data-ttu-id="d95f6-121">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="d95f6-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d95f6-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="d95f6-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d95f6-123">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="d95f6-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d95f6-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d95f6-124">Remarks</span></span>  
 <span data-ttu-id="d95f6-125">Konak bu yöntemini çağırabilir ve `CreateRWLockOwnerIterator` iş parçacığı uygulaması eşitlenmiş kalmasını sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="d95f6-125">The host can call this method and `CreateRWLockOwnerIterator` to ensure that its threading implementation remains synchronized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d95f6-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d95f6-126">Requirements</span></span>  
 <span data-ttu-id="d95f6-127">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d95f6-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d95f6-128">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d95f6-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d95f6-129">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="d95f6-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d95f6-130">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d95f6-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d95f6-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d95f6-131">See Also</span></span>  
 [<span data-ttu-id="d95f6-132">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d95f6-132">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="d95f6-133">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d95f6-133">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
