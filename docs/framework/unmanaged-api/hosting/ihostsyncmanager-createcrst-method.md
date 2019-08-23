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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 622b6c523adfb7bae2fc38826152ef69709568cc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931072"
---
# <a name="ihostsyncmanagercreatecrst-method"></a><span data-ttu-id="8b90f-102">IHostSyncManager::CreateCrst Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8b90f-102">IHostSyncManager::CreateCrst Method</span></span>
<span data-ttu-id="8b90f-103">Eşitleme için bir kritik bölüm nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8b90f-103">Creates a critical section object for synchronization.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b90f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8b90f-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateCrst (  
    [out] IHostCrst** ppCrst  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8b90f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8b90f-105">Parameters</span></span>  
 `ppCrst`  
 <span data-ttu-id="8b90f-106">dışı Ana bilgisayar tarafından uygulanan bir [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) örneğinin adresine yönelik bir işaretçi veya kritik bölüm oluşturulanmadıysa null.</span><span class="sxs-lookup"><span data-stu-id="8b90f-106">[out] A pointer to the address of an [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance implemented by the host, or null if the critical section could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8b90f-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8b90f-107">Return Value</span></span>  
  
|<span data-ttu-id="8b90f-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8b90f-108">HRESULT</span></span>|<span data-ttu-id="8b90f-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8b90f-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8b90f-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="8b90f-110">S_OK</span></span>|<span data-ttu-id="8b90f-111">`CreateCrst`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="8b90f-111">`CreateCrst` returned successfully.</span></span>|  
|<span data-ttu-id="8b90f-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8b90f-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8b90f-113">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="8b90f-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8b90f-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8b90f-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8b90f-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="8b90f-115">The call timed out.</span></span>|  
|<span data-ttu-id="8b90f-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8b90f-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8b90f-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="8b90f-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8b90f-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8b90f-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8b90f-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="8b90f-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8b90f-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8b90f-120">E_FAIL</span></span>|<span data-ttu-id="8b90f-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="8b90f-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8b90f-122">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="8b90f-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8b90f-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="8b90f-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="8b90f-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="8b90f-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="8b90f-125">İstenen kritik bölümü oluşturmak için yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="8b90f-125">Not enough memory was available to create the requested critical section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8b90f-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8b90f-126">Remarks</span></span>  
 <span data-ttu-id="8b90f-127">Kritik bölüm nesneleri, bir mutex nesnesi tarafından sağlananlara benzer bir eşitleme sağlar, ancak bu kritik bölümler yalnızca tek bir işlemin iş parçacıkları tarafından kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8b90f-127">Critical section objects provide synchronization similar to that provided by a mutex object, except that critical sections can be used only by the threads of a single process.</span></span> <span data-ttu-id="8b90f-128">`CreateCrst`Win32 `InitializeCriticalSection` işlevini yansıtır.</span><span class="sxs-lookup"><span data-stu-id="8b90f-128">`CreateCrst` mirrors the Win32 `InitializeCriticalSection` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b90f-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8b90f-129">Requirements</span></span>  
 <span data-ttu-id="8b90f-130">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b90f-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b90f-131">**Üst bilgi** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8b90f-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8b90f-132">**Kitaplığı** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="8b90f-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8b90f-133">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b90f-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b90f-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8b90f-134">See also</span></span>

- [<span data-ttu-id="8b90f-135">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8b90f-135">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="8b90f-136">IHostCrst Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8b90f-136">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)
- [<span data-ttu-id="8b90f-137">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8b90f-137">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- [<span data-ttu-id="8b90f-138">IHostSemaphore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8b90f-138">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="8b90f-139">Karşılıklı dışlamalar</span><span class="sxs-lookup"><span data-stu-id="8b90f-139">Mutexes</span></span>](../../../standard/threading/mutexes.md)
- [<span data-ttu-id="8b90f-140">Semaphore ve SemaphoreSlim</span><span class="sxs-lookup"><span data-stu-id="8b90f-140">Semaphore and SemaphoreSlim</span></span>](../../../standard/threading/semaphore-and-semaphoreslim.md)
