---
title: IHostSyncManager::CreateCrstWithSpinCount Yöntemi
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateCrstWithSpinCount
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateCrstWithSpinCount
helpviewer_keywords:
- CreateCrstWithSpinCount method [.NET Framework hosting]
- IHostSyncManager::CreateCrstWithSpinCount method [.NET Framework hosting]
ms.assetid: 7280fa8c-3639-4abf-91cb-bc343da742d1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 50f292ab39bcf77d49d8a363b43b9233f350974c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33446774"
---
# <a name="ihostsyncmanagercreatecrstwithspincount-method"></a><span data-ttu-id="8f5ff-102">IHostSyncManager::CreateCrstWithSpinCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8f5ff-102">IHostSyncManager::CreateCrstWithSpinCount Method</span></span>
<span data-ttu-id="8f5ff-103">Eşitleme için döndürme sayısı ile bir kritik bölüm nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8f5ff-103">Creates a critical section object with spin count for synchronization.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f5ff-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8f5ff-104">Syntax</span></span>  
  
```  
HRESULT CreateCrstWithSpinCount (  
    [in]  DWORD dwSpinCount,  
    [out] IHostCrst** ppCrst  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8f5ff-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8f5ff-105">Parameters</span></span>  
 `dwSpinCount`  
 <span data-ttu-id="8f5ff-106">[in] Kritik bölüm nesne döndürme sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="8f5ff-106">[in] Specifies the spin count for the critical section object.</span></span>  
  
 `ppCrst`  
 <span data-ttu-id="8f5ff-107">[out] Adresine bir işaretçi bir [Ihostcrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) örneği veya kritik bölüm oluşturulamadı yoksa null.</span><span class="sxs-lookup"><span data-stu-id="8f5ff-107">[out] A pointer to the address of an [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance, or null if the critical section could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8f5ff-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8f5ff-108">Return Value</span></span>  
  
|<span data-ttu-id="8f5ff-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8f5ff-109">HRESULT</span></span>|<span data-ttu-id="8f5ff-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8f5ff-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8f5ff-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="8f5ff-111">S_OK</span></span>|<span data-ttu-id="8f5ff-112">`CreateCrstWithSpinCount` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="8f5ff-112">`CreateCrstWithSpinCount` returned successfully.</span></span>|  
|<span data-ttu-id="8f5ff-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8f5ff-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8f5ff-114">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="8f5ff-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8f5ff-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8f5ff-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8f5ff-116">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="8f5ff-116">The call timed out.</span></span>|  
|<span data-ttu-id="8f5ff-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8f5ff-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8f5ff-118">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="8f5ff-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8f5ff-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8f5ff-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8f5ff-120">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="8f5ff-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8f5ff-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8f5ff-121">E_FAIL</span></span>|<span data-ttu-id="8f5ff-122">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="8f5ff-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8f5ff-123">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="8f5ff-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8f5ff-124">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="8f5ff-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="8f5ff-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="8f5ff-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="8f5ff-126">İstenen kritik bölüm oluşturmak yeterli bellek yoktu.</span><span class="sxs-lookup"><span data-stu-id="8f5ff-126">Not enough memory was available to create the requested critical section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8f5ff-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8f5ff-127">Remarks</span></span>  
 <span data-ttu-id="8f5ff-128">Döngü sayısı yalnızca birden çok işlemcili bir sistemi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8f5ff-128">A spin count is used only on a multi-processor system.</span></span> <span data-ttu-id="8f5ff-129">Döngü sayısı kullanılamayan bir kritik bölümle ilişkilendirilmiş bir semafor üzerinde bir bekleme işlemi gerçekleştirmeden önce çağıran iş parçacığı Döndür gerekir sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="8f5ff-129">The spin count specifies the number of times a calling thread must spin before it performs a wait operation on a semaphore that is associated with an unavailable critical section.</span></span> <span data-ttu-id="8f5ff-130">Değer değiştirme işlemi sırasında kritik bölüm boş duruma gelirse, çağıran iş parçacığı bekleme işlem önler.</span><span class="sxs-lookup"><span data-stu-id="8f5ff-130">If the critical section becomes free during the spin operation, the calling thread avoids the wait operation.</span></span> <span data-ttu-id="8f5ff-131">`CreateCrstWithSpinCount` Win32 yansıtan `InitializeCriticalSectionAndSpinCount` işlevi.</span><span class="sxs-lookup"><span data-stu-id="8f5ff-131">`CreateCrstWithSpinCount` mirrors the Win32 `InitializeCriticalSectionAndSpinCount` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f5ff-132">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8f5ff-132">Requirements</span></span>  
 <span data-ttu-id="8f5ff-133">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f5ff-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f5ff-134">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8f5ff-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8f5ff-135">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="8f5ff-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8f5ff-136">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f5ff-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f5ff-137">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8f5ff-137">See Also</span></span>  
 [<span data-ttu-id="8f5ff-138">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8f5ff-138">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="8f5ff-139">IHostSemaphore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8f5ff-139">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 [<span data-ttu-id="8f5ff-140">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8f5ff-140">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
