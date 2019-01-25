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
ms.openlocfilehash: 008e76b57ed0925eaae29cf7d2b451fc9ddd08a1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54730106"
---
# <a name="iclrsyncmanagerdeleterwlockowneriterator-method"></a><span data-ttu-id="58def-102">ICLRSyncManager::DeleteRWLockOwnerIterator Yöntemi</span><span class="sxs-lookup"><span data-stu-id="58def-102">ICLRSyncManager::DeleteRWLockOwnerIterator Method</span></span>
<span data-ttu-id="58def-103">Ortak dil çalışma zamanı (CLR) için bir çağrı tarafından oluşturulan bir yineleyici yok etmek isteyen [Iclrsyncmanager::createrwlockownerıterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md).</span><span class="sxs-lookup"><span data-stu-id="58def-103">Requests that the common language runtime (CLR) destroy an iterator that was created by a call to [ICLRSyncManager::CreateRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58def-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="58def-104">Syntax</span></span>  
  
```  
HRESULT DeleteRWLockOwnerIterator (  
    [in] SIZE_T  Iterator  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="58def-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="58def-105">Parameters</span></span>  
 `Iterator`  
 <span data-ttu-id="58def-106">[in] Bir çağrı kullanılarak oluşturulmuş yineleyici `CreateRWLockOwnerIterator`.</span><span class="sxs-lookup"><span data-stu-id="58def-106">[in] The iterator that was created by using a call to `CreateRWLockOwnerIterator`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="58def-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="58def-107">Return Value</span></span>  
  
|<span data-ttu-id="58def-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="58def-108">HRESULT</span></span>|<span data-ttu-id="58def-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="58def-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="58def-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="58def-110">S_OK</span></span>|<span data-ttu-id="58def-111">`DeleteRWLockOwnerIterator` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="58def-111">`DeleteRWLockOwnerIterator` returned successfully.</span></span>|  
|<span data-ttu-id="58def-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="58def-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="58def-113">CLR'yi işlem içine yüklenmemiş veya içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda olduğundan.</span><span class="sxs-lookup"><span data-stu-id="58def-113">The CLR has not been loaded into a process, or is in a state in which it cannot run managed code or successfully process the call.</span></span>|  
|<span data-ttu-id="58def-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="58def-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="58def-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="58def-115">The call timed out.</span></span>|  
|<span data-ttu-id="58def-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="58def-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="58def-117">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="58def-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="58def-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="58def-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="58def-119">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="58def-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="58def-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="58def-120">E_FAIL</span></span>|<span data-ttu-id="58def-121">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="58def-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="58def-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="58def-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="58def-123">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="58def-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="58def-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="58def-124">Remarks</span></span>  
 <span data-ttu-id="58def-125">Konak bu yöntemini çağırabilir ve `CreateRWLockOwnerIterator` iş parçacığı uygulaması eşitlenmiş kalmasını sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="58def-125">The host can call this method and `CreateRWLockOwnerIterator` to ensure that its threading implementation remains synchronized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58def-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="58def-126">Requirements</span></span>  
 <span data-ttu-id="58def-127">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="58def-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58def-128">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="58def-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="58def-129">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="58def-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="58def-130">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58def-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58def-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="58def-131">See also</span></span>
- [<span data-ttu-id="58def-132">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="58def-132">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="58def-133">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="58def-133">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
