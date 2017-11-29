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
ms.openlocfilehash: 3df37a9572c47ce4b4a5080f6aed3f307adba360
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrsyncmanagerdeleterwlockowneriterator-method"></a><span data-ttu-id="daafd-102">ICLRSyncManager::DeleteRWLockOwnerIterator Yöntemi</span><span class="sxs-lookup"><span data-stu-id="daafd-102">ICLRSyncManager::DeleteRWLockOwnerIterator Method</span></span>
<span data-ttu-id="daafd-103">Ortak dil çalışma zamanı (CLR) için yapılan bir çağrı tarafından oluşturulmuş bir yineleyici destroy istekleri [Iclrsyncmanager::createrwlockownerıterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md).</span><span class="sxs-lookup"><span data-stu-id="daafd-103">Requests that the common language runtime (CLR) destroy an iterator that was created by a call to [ICLRSyncManager::CreateRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="daafd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="daafd-104">Syntax</span></span>  
  
```  
HRESULT DeleteRWLockOwnerIterator (  
    [in] SIZE_T  Iterator  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="daafd-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="daafd-105">Parameters</span></span>  
 `Iterator`  
 <span data-ttu-id="daafd-106">[in] Bir çağrı kullanılarak oluşturulmuş yineleyici `CreateRWLockOwnerIterator`.</span><span class="sxs-lookup"><span data-stu-id="daafd-106">[in] The iterator that was created by using a call to `CreateRWLockOwnerIterator`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="daafd-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="daafd-107">Return Value</span></span>  
  
|<span data-ttu-id="daafd-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="daafd-108">HRESULT</span></span>|<span data-ttu-id="daafd-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="daafd-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="daafd-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="daafd-110">S_OK</span></span>|<span data-ttu-id="daafd-111">`DeleteRWLockOwnerIterator`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="daafd-111">`DeleteRWLockOwnerIterator` returned successfully.</span></span>|  
|<span data-ttu-id="daafd-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="daafd-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="daafd-113">CLR süreç içine yüklendi değil veya içinde yönetilen kod çalıştıramaz veya başarıyla çağrıyı işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="daafd-113">The CLR has not been loaded into a process, or is in a state in which it cannot run managed code or successfully process the call.</span></span>|  
|<span data-ttu-id="daafd-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="daafd-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="daafd-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="daafd-115">The call timed out.</span></span>|  
|<span data-ttu-id="daafd-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="daafd-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="daafd-117">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="daafd-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="daafd-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="daafd-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="daafd-119">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="daafd-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="daafd-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="daafd-120">E_FAIL</span></span>|<span data-ttu-id="daafd-121">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="daafd-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="daafd-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="daafd-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="daafd-123">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="daafd-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="daafd-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="daafd-124">Remarks</span></span>  
 <span data-ttu-id="daafd-125">Konak bu yöntemini çağırabilir ve `CreateRWLockOwnerIterator` iş parçacığı uygulaması eşitlenmiş kalmasını sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="daafd-125">The host can call this method and `CreateRWLockOwnerIterator` to ensure that its threading implementation remains synchronized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="daafd-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="daafd-126">Requirements</span></span>  
 <span data-ttu-id="daafd-127">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="daafd-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="daafd-128">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="daafd-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="daafd-129">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="daafd-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="daafd-130">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="daafd-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="daafd-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="daafd-131">See Also</span></span>  
 [<span data-ttu-id="daafd-132">Iclrsyncmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="daafd-132">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="daafd-133">Ihostsyncmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="daafd-133">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
