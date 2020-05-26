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
ms.openlocfilehash: 3566907544c72da2735e155d9088fe09fea4a728
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803473"
---
# <a name="ihostsyncmanagercreatecrst-method"></a><span data-ttu-id="86cde-102">IHostSyncManager::CreateCrst Yöntemi</span><span class="sxs-lookup"><span data-stu-id="86cde-102">IHostSyncManager::CreateCrst Method</span></span>
<span data-ttu-id="86cde-103">Eşitleme için bir kritik bölüm nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="86cde-103">Creates a critical section object for synchronization.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86cde-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="86cde-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateCrst (  
    [out] IHostCrst** ppCrst  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="86cde-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="86cde-105">Parameters</span></span>  
 `ppCrst`  
 <span data-ttu-id="86cde-106">dışı Ana bilgisayar tarafından uygulanan bir [IHostCrst](ihostcrst-interface.md) örneğinin adresine yönelik bir işaretçi veya kritik bölüm oluşturulanmadıysa null.</span><span class="sxs-lookup"><span data-stu-id="86cde-106">[out] A pointer to the address of an [IHostCrst](ihostcrst-interface.md) instance implemented by the host, or null if the critical section could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="86cde-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="86cde-107">Return Value</span></span>  
  
|<span data-ttu-id="86cde-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="86cde-108">HRESULT</span></span>|<span data-ttu-id="86cde-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="86cde-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="86cde-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="86cde-110">S_OK</span></span>|<span data-ttu-id="86cde-111">`CreateCrst`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="86cde-111">`CreateCrst` returned successfully.</span></span>|  
|<span data-ttu-id="86cde-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="86cde-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="86cde-113">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="86cde-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="86cde-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="86cde-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="86cde-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="86cde-115">The call timed out.</span></span>|  
|<span data-ttu-id="86cde-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="86cde-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="86cde-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="86cde-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="86cde-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="86cde-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="86cde-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="86cde-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="86cde-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="86cde-120">E_FAIL</span></span>|<span data-ttu-id="86cde-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="86cde-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="86cde-122">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="86cde-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="86cde-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="86cde-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="86cde-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="86cde-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="86cde-125">İstenen kritik bölümü oluşturmak için yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="86cde-125">Not enough memory was available to create the requested critical section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="86cde-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="86cde-126">Remarks</span></span>  
 <span data-ttu-id="86cde-127">Kritik bölüm nesneleri, bir mutex nesnesi tarafından sağlananlara benzer bir eşitleme sağlar, ancak bu kritik bölümler yalnızca tek bir işlemin iş parçacıkları tarafından kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="86cde-127">Critical section objects provide synchronization similar to that provided by a mutex object, except that critical sections can be used only by the threads of a single process.</span></span> <span data-ttu-id="86cde-128">`CreateCrst`Win32 işlevini yansıtır `InitializeCriticalSection` .</span><span class="sxs-lookup"><span data-stu-id="86cde-128">`CreateCrst` mirrors the Win32 `InitializeCriticalSection` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86cde-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="86cde-129">Requirements</span></span>  
 <span data-ttu-id="86cde-130">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86cde-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86cde-131">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="86cde-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="86cde-132">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="86cde-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="86cde-133">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86cde-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86cde-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="86cde-134">See also</span></span>

- [<span data-ttu-id="86cde-135">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="86cde-135">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="86cde-136">IHostCrst Arabirimi</span><span class="sxs-lookup"><span data-stu-id="86cde-136">IHostCrst Interface</span></span>](ihostcrst-interface.md)
- [<span data-ttu-id="86cde-137">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="86cde-137">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
- [<span data-ttu-id="86cde-138">IHostSemaphore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="86cde-138">IHostSemaphore Interface</span></span>](ihostsemaphore-interface.md)
- [<span data-ttu-id="86cde-139">Karşılıklı dışlamalar</span><span class="sxs-lookup"><span data-stu-id="86cde-139">Mutexes</span></span>](../../../standard/threading/mutexes.md)
- [<span data-ttu-id="86cde-140">Semafor ve SemaphoreSlim</span><span class="sxs-lookup"><span data-stu-id="86cde-140">Semaphore and SemaphoreSlim</span></span>](../../../standard/threading/semaphore-and-semaphoreslim.md)
