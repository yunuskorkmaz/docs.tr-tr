---
title: ICLRSyncManager::DeleteRWLockOwnerIterator Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRSyncManager.DeleteRWLockOwnerIterator
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRSyncManager::DeleteRWLockOwnerIterator
helpviewer_keywords:
- ICLRSyncManager::DeleteRWLockOwnerIterator method [.NET Framework hosting]
- DeleteRWLockOwnerIterator method [.NET Framework hosting]
ms.assetid: fcfd340a-b7d6-44e4-8167-2c05b789d483
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5ee4a09902be093bdbfe0b367f4add35bdda571c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434073"
---
# <a name="iclrsyncmanagerdeleterwlockowneriterator-method"></a><span data-ttu-id="2609f-102">ICLRSyncManager::DeleteRWLockOwnerIterator Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2609f-102">ICLRSyncManager::DeleteRWLockOwnerIterator Method</span></span>
<span data-ttu-id="2609f-103">Ortak dil çalışma zamanı (CLR) için yapılan bir çağrı tarafından oluşturulmuş bir yineleyici destroy istekleri [Iclrsyncmanager::createrwlockownerıterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md).</span><span class="sxs-lookup"><span data-stu-id="2609f-103">Requests that the common language runtime (CLR) destroy an iterator that was created by a call to [ICLRSyncManager::CreateRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2609f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2609f-104">Syntax</span></span>  
  
```  
HRESULT DeleteRWLockOwnerIterator (  
    [in] SIZE_T  Iterator  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2609f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2609f-105">Parameters</span></span>  
 `Iterator`  
 <span data-ttu-id="2609f-106">[in] Bir çağrı kullanılarak oluşturulmuş yineleyici `CreateRWLockOwnerIterator`.</span><span class="sxs-lookup"><span data-stu-id="2609f-106">[in] The iterator that was created by using a call to `CreateRWLockOwnerIterator`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2609f-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2609f-107">Return Value</span></span>  
  
|<span data-ttu-id="2609f-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2609f-108">HRESULT</span></span>|<span data-ttu-id="2609f-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2609f-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2609f-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="2609f-110">S_OK</span></span>|<span data-ttu-id="2609f-111">`DeleteRWLockOwnerIterator` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="2609f-111">`DeleteRWLockOwnerIterator` returned successfully.</span></span>|  
|<span data-ttu-id="2609f-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2609f-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2609f-113">CLR süreç içine yüklendi değil veya içinde yönetilen kod çalıştıramaz veya başarıyla çağrıyı işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="2609f-113">The CLR has not been loaded into a process, or is in a state in which it cannot run managed code or successfully process the call.</span></span>|  
|<span data-ttu-id="2609f-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2609f-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2609f-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="2609f-115">The call timed out.</span></span>|  
|<span data-ttu-id="2609f-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2609f-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2609f-117">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="2609f-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2609f-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2609f-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2609f-119">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="2609f-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2609f-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2609f-120">E_FAIL</span></span>|<span data-ttu-id="2609f-121">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="2609f-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2609f-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="2609f-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2609f-123">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="2609f-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2609f-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2609f-124">Remarks</span></span>  
 <span data-ttu-id="2609f-125">Konak bu yöntemini çağırabilir ve `CreateRWLockOwnerIterator` iş parçacığı uygulaması eşitlenmiş kalmasını sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="2609f-125">The host can call this method and `CreateRWLockOwnerIterator` to ensure that its threading implementation remains synchronized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2609f-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2609f-126">Requirements</span></span>  
 <span data-ttu-id="2609f-127">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2609f-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2609f-128">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2609f-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2609f-129">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="2609f-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2609f-130">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2609f-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2609f-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2609f-131">See Also</span></span>  
 [<span data-ttu-id="2609f-132">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2609f-132">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="2609f-133">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2609f-133">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
