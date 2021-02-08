---
description: ': IHostSyncManager:: CreateCrst yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 7d1880f1553d159f62efe65afe8368a60b5bf9cc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784814"
---
# <a name="ihostsyncmanagercreatecrst-method"></a><span data-ttu-id="5ab83-103">IHostSyncManager::CreateCrst Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5ab83-103">IHostSyncManager::CreateCrst Method</span></span>

<span data-ttu-id="5ab83-104">Eşitleme için bir kritik bölüm nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5ab83-104">Creates a critical section object for synchronization.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ab83-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5ab83-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateCrst (  
    [out] IHostCrst** ppCrst  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5ab83-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5ab83-106">Parameters</span></span>  

 `ppCrst`  
 <span data-ttu-id="5ab83-107">dışı Ana bilgisayar tarafından uygulanan bir [IHostCrst](ihostcrst-interface.md) örneğinin adresine yönelik bir işaretçi veya kritik bölüm oluşturulanmadıysa null.</span><span class="sxs-lookup"><span data-stu-id="5ab83-107">[out] A pointer to the address of an [IHostCrst](ihostcrst-interface.md) instance implemented by the host, or null if the critical section could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5ab83-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5ab83-108">Return Value</span></span>  
  
|<span data-ttu-id="5ab83-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5ab83-109">HRESULT</span></span>|<span data-ttu-id="5ab83-110">Description</span><span class="sxs-lookup"><span data-stu-id="5ab83-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5ab83-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="5ab83-111">S_OK</span></span>|<span data-ttu-id="5ab83-112">`CreateCrst` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="5ab83-112">`CreateCrst` returned successfully.</span></span>|  
|<span data-ttu-id="5ab83-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5ab83-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5ab83-114">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="5ab83-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5ab83-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5ab83-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5ab83-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="5ab83-116">The call timed out.</span></span>|  
|<span data-ttu-id="5ab83-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5ab83-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5ab83-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="5ab83-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5ab83-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5ab83-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5ab83-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="5ab83-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5ab83-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5ab83-121">E_FAIL</span></span>|<span data-ttu-id="5ab83-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="5ab83-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5ab83-123">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="5ab83-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5ab83-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="5ab83-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="5ab83-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="5ab83-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="5ab83-126">İstenen kritik bölümü oluşturmak için yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="5ab83-126">Not enough memory was available to create the requested critical section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5ab83-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5ab83-127">Remarks</span></span>  

 <span data-ttu-id="5ab83-128">Kritik bölüm nesneleri, bir mutex nesnesi tarafından sağlananlara benzer bir eşitleme sağlar, ancak bu kritik bölümler yalnızca tek bir işlemin iş parçacıkları tarafından kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5ab83-128">Critical section objects provide synchronization similar to that provided by a mutex object, except that critical sections can be used only by the threads of a single process.</span></span> <span data-ttu-id="5ab83-129">`CreateCrst` Win32 işlevini yansıtır `InitializeCriticalSection` .</span><span class="sxs-lookup"><span data-stu-id="5ab83-129">`CreateCrst` mirrors the Win32 `InitializeCriticalSection` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ab83-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5ab83-130">Requirements</span></span>  

 <span data-ttu-id="5ab83-131">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ab83-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ab83-132">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="5ab83-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5ab83-133">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="5ab83-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5ab83-134">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ab83-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ab83-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5ab83-135">See also</span></span>

- [<span data-ttu-id="5ab83-136">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5ab83-136">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="5ab83-137">IHostCrst Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5ab83-137">IHostCrst Interface</span></span>](ihostcrst-interface.md)
- [<span data-ttu-id="5ab83-138">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5ab83-138">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
- [<span data-ttu-id="5ab83-139">IHostSemaphore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5ab83-139">IHostSemaphore Interface</span></span>](ihostsemaphore-interface.md)
- [<span data-ttu-id="5ab83-140">Zaman Uyumu Sağlayıcılar</span><span class="sxs-lookup"><span data-stu-id="5ab83-140">Mutexes</span></span>](../../../standard/threading/mutexes.md)
- [<span data-ttu-id="5ab83-141">Semafor ve SemaphoreSlim</span><span class="sxs-lookup"><span data-stu-id="5ab83-141">Semaphore and SemaphoreSlim</span></span>](../../../standard/threading/semaphore-and-semaphoreslim.md)
