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
ms.openlocfilehash: 02066d3923714e66bf287f1435b7854280c97cb7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73195824"
---
# <a name="ihostsyncmanagercreatesemaphore-method"></a><span data-ttu-id="61fd5-102">IHostSyncManager::CreateSemaphore Yöntemi</span><span class="sxs-lookup"><span data-stu-id="61fd5-102">IHostSyncManager::CreateSemaphore Method</span></span>
<span data-ttu-id="61fd5-103">Bekleme olayları için semafor olarak kullanılacak ortak dil çalışma zamanı (CLR) için bir [ıhostsemafor](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="61fd5-103">Creates an [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) object for the common language runtime (CLR) to use as a semaphore for wait events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61fd5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="61fd5-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateSemaphore (  
    [in]  DWORD dwInitial,  
    [in]  DWORD dwMax,  
    [out] IHostSemaphore **ppSemaphore  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="61fd5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="61fd5-105">Parameters</span></span>  
 `dwInitial`  
 <span data-ttu-id="61fd5-106">'ndaki `ppSemaphore`için başlangıç sayısı.</span><span class="sxs-lookup"><span data-stu-id="61fd5-106">[in] The initial count for `ppSemaphore`.</span></span>  
  
 `dwMax`  
 <span data-ttu-id="61fd5-107">'ndaki `ppSemaphore`için maksimum sayı.</span><span class="sxs-lookup"><span data-stu-id="61fd5-107">[in] The maximum count for `ppSemaphore`.</span></span>  
  
 `ppSemaphore`  
 <span data-ttu-id="61fd5-108">dışı `IHostSemaphore` örneğinin adresine yönelik bir işaretçi veya semafor oluşturuoluşturulamadığı takdirde null.</span><span class="sxs-lookup"><span data-stu-id="61fd5-108">[out] A pointer to the address of an `IHostSemaphore` instance, or null if the semaphore could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="61fd5-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="61fd5-109">Return Value</span></span>  
  
|<span data-ttu-id="61fd5-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="61fd5-110">HRESULT</span></span>|<span data-ttu-id="61fd5-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="61fd5-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="61fd5-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="61fd5-112">S_OK</span></span>|<span data-ttu-id="61fd5-113">`CreateSemaphore` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="61fd5-113">`CreateSemaphore` returned successfully.</span></span>|  
|<span data-ttu-id="61fd5-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="61fd5-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="61fd5-115">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="61fd5-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="61fd5-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="61fd5-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="61fd5-117">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="61fd5-117">The call timed out.</span></span>|  
|<span data-ttu-id="61fd5-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="61fd5-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="61fd5-119">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="61fd5-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="61fd5-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="61fd5-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="61fd5-121">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="61fd5-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="61fd5-122">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="61fd5-122">E_FAIL</span></span>|<span data-ttu-id="61fd5-123">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="61fd5-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="61fd5-124">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="61fd5-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="61fd5-125">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="61fd5-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="61fd5-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="61fd5-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="61fd5-127">İstenen olay nesnesini oluşturmak için yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="61fd5-127">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="61fd5-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="61fd5-128">Remarks</span></span>  
 <span data-ttu-id="61fd5-129">`CreateSemaphore`, aynı ada sahip Win32 işlevini yansıtır.</span><span class="sxs-lookup"><span data-stu-id="61fd5-129">`CreateSemaphore` mirrors the Win32 function that has the same name.</span></span> <span data-ttu-id="61fd5-130">`dwInitial` ve `dwMax` parametreleri, semafor sayısı için sırasıyla Win32 `lInitialCount` ve `lMaximumCount` parametreleri olarak aynı semantiğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="61fd5-130">The `dwInitial` and `dwMax` parameters use the same semantics for the semaphore count as the Win32 `lInitialCount` and `lMaximumCount` parameters, respectively.</span></span> <span data-ttu-id="61fd5-131">`dwInitial` sıfır ile `dwMax`(dahil) arasında olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="61fd5-131">`dwInitial` must be between zero and `dwMax`, inclusive.</span></span> <span data-ttu-id="61fd5-132">`dwMax` sıfırdan büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="61fd5-132">`dwMax` must be greater than zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61fd5-133">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="61fd5-133">Requirements</span></span>  
 <span data-ttu-id="61fd5-134">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61fd5-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61fd5-135">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="61fd5-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="61fd5-136">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="61fd5-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="61fd5-137">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61fd5-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61fd5-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="61fd5-138">See also</span></span>

- [<span data-ttu-id="61fd5-139">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="61fd5-139">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="61fd5-140">IHostSemaphore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="61fd5-140">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="61fd5-141">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="61fd5-141">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
