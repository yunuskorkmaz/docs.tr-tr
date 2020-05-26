---
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
ms.openlocfilehash: 680280e959d523356b95a5a4d9390c80720c0330
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803136"
---
# <a name="ihostsyncmanagercreatesemaphore-method"></a><span data-ttu-id="30001-102">IHostSyncManager::CreateSemaphore Yöntemi</span><span class="sxs-lookup"><span data-stu-id="30001-102">IHostSyncManager::CreateSemaphore Method</span></span>
<span data-ttu-id="30001-103">Bekleme olayları için semafor olarak kullanılacak ortak dil çalışma zamanı (CLR) için bir [ıhostsemafor](ihostsemaphore-interface.md) nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="30001-103">Creates an [IHostSemaphore](ihostsemaphore-interface.md) object for the common language runtime (CLR) to use as a semaphore for wait events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30001-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="30001-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateSemaphore (  
    [in]  DWORD dwInitial,  
    [in]  DWORD dwMax,  
    [out] IHostSemaphore **ppSemaphore  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="30001-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="30001-105">Parameters</span></span>  
 `dwInitial`  
 <span data-ttu-id="30001-106">'ndaki İçin başlangıç sayısı `ppSemaphore` .</span><span class="sxs-lookup"><span data-stu-id="30001-106">[in] The initial count for `ppSemaphore`.</span></span>  
  
 `dwMax`  
 <span data-ttu-id="30001-107">'ndaki İçin maksimum sayı `ppSemaphore` .</span><span class="sxs-lookup"><span data-stu-id="30001-107">[in] The maximum count for `ppSemaphore`.</span></span>  
  
 `ppSemaphore`  
 <span data-ttu-id="30001-108">dışı Bir örneğin adresine yönelik bir işaretçi `IHostSemaphore` veya semafor oluşturuoluşturulamadığı takdirde null.</span><span class="sxs-lookup"><span data-stu-id="30001-108">[out] A pointer to the address of an `IHostSemaphore` instance, or null if the semaphore could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="30001-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="30001-109">Return Value</span></span>  
  
|<span data-ttu-id="30001-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="30001-110">HRESULT</span></span>|<span data-ttu-id="30001-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="30001-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="30001-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="30001-112">S_OK</span></span>|<span data-ttu-id="30001-113">`CreateSemaphore`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="30001-113">`CreateSemaphore` returned successfully.</span></span>|  
|<span data-ttu-id="30001-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="30001-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="30001-115">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="30001-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="30001-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="30001-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="30001-117">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="30001-117">The call timed out.</span></span>|  
|<span data-ttu-id="30001-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="30001-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="30001-119">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="30001-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="30001-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="30001-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="30001-121">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="30001-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="30001-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="30001-122">E_FAIL</span></span>|<span data-ttu-id="30001-123">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="30001-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="30001-124">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="30001-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="30001-125">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="30001-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="30001-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="30001-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="30001-127">İstenen olay nesnesini oluşturmak için yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="30001-127">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="30001-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="30001-128">Remarks</span></span>  
 <span data-ttu-id="30001-129">`CreateSemaphore`aynı ada sahip Win32 işlevini yansıtır.</span><span class="sxs-lookup"><span data-stu-id="30001-129">`CreateSemaphore` mirrors the Win32 function that has the same name.</span></span> <span data-ttu-id="30001-130">`dwInitial`Ve `dwMax` parametreleri, semafor sayısı Için `lInitialCount` sırasıyla Win32 ve parametreler için aynı semantiğini kullanır `lMaximumCount` .</span><span class="sxs-lookup"><span data-stu-id="30001-130">The `dwInitial` and `dwMax` parameters use the same semantics for the semaphore count as the Win32 `lInitialCount` and `lMaximumCount` parameters, respectively.</span></span> <span data-ttu-id="30001-131">`dwInitial`sıfır ile `dwMax` (dahil) arasında olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="30001-131">`dwInitial` must be between zero and `dwMax`, inclusive.</span></span> <span data-ttu-id="30001-132">`dwMax`sıfırdan büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="30001-132">`dwMax` must be greater than zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30001-133">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="30001-133">Requirements</span></span>  
 <span data-ttu-id="30001-134">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30001-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30001-135">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="30001-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="30001-136">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="30001-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="30001-137">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30001-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30001-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="30001-138">See also</span></span>

- [<span data-ttu-id="30001-139">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="30001-139">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="30001-140">IHostSemaphore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="30001-140">IHostSemaphore Interface</span></span>](ihostsemaphore-interface.md)
- [<span data-ttu-id="30001-141">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="30001-141">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
