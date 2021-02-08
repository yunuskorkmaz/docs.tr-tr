---
description: ': IHostSyncManager:: CreateCrstWithSpinCount yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 3c43f1a3d52eb7174844ecb4079cf54413f20853
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784827"
---
# <a name="ihostsyncmanagercreatecrstwithspincount-method"></a><span data-ttu-id="da7b1-103">IHostSyncManager::CreateCrstWithSpinCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="da7b1-103">IHostSyncManager::CreateCrstWithSpinCount Method</span></span>

<span data-ttu-id="da7b1-104">Eşitleme için döngü sayısı olan bir kritik bölüm nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="da7b1-104">Creates a critical section object with spin count for synchronization.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da7b1-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="da7b1-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateCrstWithSpinCount (  
    [in]  DWORD dwSpinCount,  
    [out] IHostCrst** ppCrst  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="da7b1-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="da7b1-106">Parameters</span></span>  

 `dwSpinCount`  
 <span data-ttu-id="da7b1-107">'ndaki Kritik bölüm nesnesinin döndürme sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="da7b1-107">[in] Specifies the spin count for the critical section object.</span></span>  
  
 `ppCrst`  
 <span data-ttu-id="da7b1-108">dışı [IHostCrst](ihostcrst-interface.md) örneğinin adresine yönelik bir işaretçi veya kritik bölüm oluşturulanmadıysa null.</span><span class="sxs-lookup"><span data-stu-id="da7b1-108">[out] A pointer to the address of an [IHostCrst](ihostcrst-interface.md) instance, or null if the critical section could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="da7b1-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="da7b1-109">Return Value</span></span>  
  
|<span data-ttu-id="da7b1-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="da7b1-110">HRESULT</span></span>|<span data-ttu-id="da7b1-111">Description</span><span class="sxs-lookup"><span data-stu-id="da7b1-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="da7b1-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="da7b1-112">S_OK</span></span>|<span data-ttu-id="da7b1-113">`CreateCrstWithSpinCount` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="da7b1-113">`CreateCrstWithSpinCount` returned successfully.</span></span>|  
|<span data-ttu-id="da7b1-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="da7b1-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="da7b1-115">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="da7b1-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="da7b1-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="da7b1-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="da7b1-117">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="da7b1-117">The call timed out.</span></span>|  
|<span data-ttu-id="da7b1-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="da7b1-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="da7b1-119">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="da7b1-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="da7b1-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="da7b1-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="da7b1-121">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="da7b1-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="da7b1-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="da7b1-122">E_FAIL</span></span>|<span data-ttu-id="da7b1-123">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="da7b1-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="da7b1-124">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="da7b1-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="da7b1-125">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="da7b1-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="da7b1-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="da7b1-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="da7b1-127">İstenen kritik bölümü oluşturmak için yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="da7b1-127">Not enough memory was available to create the requested critical section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="da7b1-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="da7b1-128">Remarks</span></span>  

 <span data-ttu-id="da7b1-129">Bir döndürme sayısı yalnızca çok işlemcili bir sistemde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="da7b1-129">A spin count is used only on a multi-processor system.</span></span> <span data-ttu-id="da7b1-130">Dönüş sayısı, bir çağıran iş parçacığının, kullanılamayan bir kritik bölümle ilişkili bir semafor üzerinde bekleme işlemi gerçekleştirmeden önce kaç kez dönmesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="da7b1-130">The spin count specifies the number of times a calling thread must spin before it performs a wait operation on a semaphore that is associated with an unavailable critical section.</span></span> <span data-ttu-id="da7b1-131">Kritik bölüm, döndürme işlemi sırasında ücretsiz hale gelirse, çağıran iş parçacığı bekleme işlemini önler.</span><span class="sxs-lookup"><span data-stu-id="da7b1-131">If the critical section becomes free during the spin operation, the calling thread avoids the wait operation.</span></span> <span data-ttu-id="da7b1-132">`CreateCrstWithSpinCount` Win32 işlevini yansıtır `InitializeCriticalSectionAndSpinCount` .</span><span class="sxs-lookup"><span data-stu-id="da7b1-132">`CreateCrstWithSpinCount` mirrors the Win32 `InitializeCriticalSectionAndSpinCount` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da7b1-133">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="da7b1-133">Requirements</span></span>  

 <span data-ttu-id="da7b1-134">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="da7b1-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da7b1-135">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="da7b1-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="da7b1-136">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="da7b1-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="da7b1-137">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da7b1-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da7b1-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="da7b1-138">See also</span></span>

- [<span data-ttu-id="da7b1-139">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="da7b1-139">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="da7b1-140">IHostSemaphore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="da7b1-140">IHostSemaphore Interface</span></span>](ihostsemaphore-interface.md)
- [<span data-ttu-id="da7b1-141">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="da7b1-141">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
