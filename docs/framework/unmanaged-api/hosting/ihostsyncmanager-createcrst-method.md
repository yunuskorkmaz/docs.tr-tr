---
title: IHostSyncManager::CreateCrst Yöntemi
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateCrst
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateCrst
helpviewer_keywords:
- CreateCrst method [.NET Framework hosting]
- IHostSyncManager::CreateCrst method [.NET Framework hosting]
ms.assetid: ac278cc8-2540-4a6c-b5c6-b90c3970b4f4
topic_type:
- apiref
ms.openlocfilehash: 27861a9258916f4c188d981c44833e5be4c507f2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95682891"
---
# <a name="ihostsyncmanagercreatecrst-method"></a><span data-ttu-id="fdc26-102">IHostSyncManager::CreateCrst Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fdc26-102">IHostSyncManager::CreateCrst Method</span></span>

<span data-ttu-id="fdc26-103">Eşitleme için bir kritik bölüm nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fdc26-103">Creates a critical section object for synchronization.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fdc26-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="fdc26-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateCrst (  
    [out] IHostCrst** ppCrst  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fdc26-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fdc26-105">Parameters</span></span>  

 `ppCrst`  
 <span data-ttu-id="fdc26-106">dışı Ana bilgisayar tarafından uygulanan bir [IHostCrst](ihostcrst-interface.md) örneğinin adresine yönelik bir işaretçi veya kritik bölüm oluşturulanmadıysa null.</span><span class="sxs-lookup"><span data-stu-id="fdc26-106">[out] A pointer to the address of an [IHostCrst](ihostcrst-interface.md) instance implemented by the host, or null if the critical section could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fdc26-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="fdc26-107">Return Value</span></span>  
  
|<span data-ttu-id="fdc26-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fdc26-108">HRESULT</span></span>|<span data-ttu-id="fdc26-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fdc26-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fdc26-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="fdc26-110">S_OK</span></span>|<span data-ttu-id="fdc26-111">`CreateCrst` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="fdc26-111">`CreateCrst` returned successfully.</span></span>|  
|<span data-ttu-id="fdc26-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fdc26-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fdc26-113">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="fdc26-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fdc26-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fdc26-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="fdc26-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="fdc26-115">The call timed out.</span></span>|  
|<span data-ttu-id="fdc26-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="fdc26-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="fdc26-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="fdc26-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="fdc26-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="fdc26-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="fdc26-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="fdc26-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="fdc26-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fdc26-120">E_FAIL</span></span>|<span data-ttu-id="fdc26-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="fdc26-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fdc26-122">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="fdc26-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="fdc26-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="fdc26-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="fdc26-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="fdc26-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="fdc26-125">İstenen kritik bölümü oluşturmak için yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="fdc26-125">Not enough memory was available to create the requested critical section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fdc26-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fdc26-126">Remarks</span></span>  

 <span data-ttu-id="fdc26-127">Kritik bölüm nesneleri, bir mutex nesnesi tarafından sağlananlara benzer bir eşitleme sağlar, ancak bu kritik bölümler yalnızca tek bir işlemin iş parçacıkları tarafından kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fdc26-127">Critical section objects provide synchronization similar to that provided by a mutex object, except that critical sections can be used only by the threads of a single process.</span></span> <span data-ttu-id="fdc26-128">`CreateCrst` Win32 işlevini yansıtır `InitializeCriticalSection` .</span><span class="sxs-lookup"><span data-stu-id="fdc26-128">`CreateCrst` mirrors the Win32 `InitializeCriticalSection` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fdc26-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fdc26-129">Requirements</span></span>  

 <span data-ttu-id="fdc26-130">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fdc26-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fdc26-131">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="fdc26-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fdc26-132">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="fdc26-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fdc26-133">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fdc26-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdc26-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fdc26-134">See also</span></span>

- [<span data-ttu-id="fdc26-135">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fdc26-135">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="fdc26-136">IHostCrst Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fdc26-136">IHostCrst Interface</span></span>](ihostcrst-interface.md)
- [<span data-ttu-id="fdc26-137">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fdc26-137">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
- [<span data-ttu-id="fdc26-138">IHostSemaphore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fdc26-138">IHostSemaphore Interface</span></span>](ihostsemaphore-interface.md)
- [<span data-ttu-id="fdc26-139">Zaman Uyumu Sağlayıcılar</span><span class="sxs-lookup"><span data-stu-id="fdc26-139">Mutexes</span></span>](../../../standard/threading/mutexes.md)
- [<span data-ttu-id="fdc26-140">Semafor ve SemaphoreSlim</span><span class="sxs-lookup"><span data-stu-id="fdc26-140">Semaphore and SemaphoreSlim</span></span>](../../../standard/threading/semaphore-and-semaphoreslim.md)
