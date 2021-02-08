---
description: ': IHostSyncManager:: Createsemafor yöntemi hakkında daha fazla bilgi edinin'
title: IHostSyncManager::CreateSemaphore Yöntemi
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateSemaphore
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateSemaphore
helpviewer_keywords:
- CreateSemaphore method [.NET Framework hosting]
- IHostSyncManager::CreateSemaphore method [.NET Framework hosting]
ms.assetid: 37679e94-5ff9-4173-8fa5-457febeb89bf
topic_type:
- apiref
ms.openlocfilehash: 5a03ef7532e2ac8357ec015b40cc54942f5420e5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784749"
---
# <a name="ihostsyncmanagercreatesemaphore-method"></a><span data-ttu-id="30a74-103">IHostSyncManager::CreateSemaphore Yöntemi</span><span class="sxs-lookup"><span data-stu-id="30a74-103">IHostSyncManager::CreateSemaphore Method</span></span>

<span data-ttu-id="30a74-104">Bekleme olayları için semafor olarak kullanılacak ortak dil çalışma zamanı (CLR) için bir [ıhostsemafor](ihostsemaphore-interface.md) nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="30a74-104">Creates an [IHostSemaphore](ihostsemaphore-interface.md) object for the common language runtime (CLR) to use as a semaphore for wait events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30a74-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="30a74-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateSemaphore (  
    [in]  DWORD dwInitial,  
    [in]  DWORD dwMax,  
    [out] IHostSemaphore **ppSemaphore  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="30a74-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="30a74-106">Parameters</span></span>  

 `dwInitial`  
 <span data-ttu-id="30a74-107">'ndaki İçin başlangıç sayısı `ppSemaphore` .</span><span class="sxs-lookup"><span data-stu-id="30a74-107">[in] The initial count for `ppSemaphore`.</span></span>  
  
 `dwMax`  
 <span data-ttu-id="30a74-108">'ndaki İçin maksimum sayı `ppSemaphore` .</span><span class="sxs-lookup"><span data-stu-id="30a74-108">[in] The maximum count for `ppSemaphore`.</span></span>  
  
 `ppSemaphore`  
 <span data-ttu-id="30a74-109">dışı Bir örneğin adresine yönelik bir işaretçi `IHostSemaphore` veya semafor oluşturuoluşturulamadığı takdirde null.</span><span class="sxs-lookup"><span data-stu-id="30a74-109">[out] A pointer to the address of an `IHostSemaphore` instance, or null if the semaphore could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="30a74-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="30a74-110">Return Value</span></span>  
  
|<span data-ttu-id="30a74-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="30a74-111">HRESULT</span></span>|<span data-ttu-id="30a74-112">Description</span><span class="sxs-lookup"><span data-stu-id="30a74-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="30a74-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="30a74-113">S_OK</span></span>|<span data-ttu-id="30a74-114">`CreateSemaphore` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="30a74-114">`CreateSemaphore` returned successfully.</span></span>|  
|<span data-ttu-id="30a74-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="30a74-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="30a74-116">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="30a74-116">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="30a74-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="30a74-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="30a74-118">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="30a74-118">The call timed out.</span></span>|  
|<span data-ttu-id="30a74-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="30a74-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="30a74-120">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="30a74-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="30a74-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="30a74-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="30a74-122">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="30a74-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="30a74-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="30a74-123">E_FAIL</span></span>|<span data-ttu-id="30a74-124">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="30a74-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="30a74-125">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="30a74-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="30a74-126">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="30a74-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="30a74-127">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="30a74-127">E_OUTOFMEMORY</span></span>|<span data-ttu-id="30a74-128">İstenen olay nesnesini oluşturmak için yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="30a74-128">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="30a74-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="30a74-129">Remarks</span></span>  

 <span data-ttu-id="30a74-130">`CreateSemaphore` aynı ada sahip Win32 işlevini yansıtır.</span><span class="sxs-lookup"><span data-stu-id="30a74-130">`CreateSemaphore` mirrors the Win32 function that has the same name.</span></span> <span data-ttu-id="30a74-131">`dwInitial`Ve `dwMax` parametreleri, semafor sayısı Için `lInitialCount` sırasıyla Win32 ve parametreler için aynı semantiğini kullanır `lMaximumCount` .</span><span class="sxs-lookup"><span data-stu-id="30a74-131">The `dwInitial` and `dwMax` parameters use the same semantics for the semaphore count as the Win32 `lInitialCount` and `lMaximumCount` parameters, respectively.</span></span> <span data-ttu-id="30a74-132">`dwInitial` sıfır ile `dwMax` (dahil) arasında olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="30a74-132">`dwInitial` must be between zero and `dwMax`, inclusive.</span></span> <span data-ttu-id="30a74-133">`dwMax` sıfırdan büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="30a74-133">`dwMax` must be greater than zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30a74-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="30a74-134">Requirements</span></span>  

 <span data-ttu-id="30a74-135">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30a74-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30a74-136">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="30a74-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="30a74-137">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="30a74-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="30a74-138">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30a74-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30a74-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="30a74-139">See also</span></span>

- [<span data-ttu-id="30a74-140">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="30a74-140">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="30a74-141">IHostSemaphore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="30a74-141">IHostSemaphore Interface</span></span>](ihostsemaphore-interface.md)
- [<span data-ttu-id="30a74-142">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="30a74-142">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
