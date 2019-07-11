---
title: IHostIoCompletionManager::InitializeHostOverlapped Yöntemi
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.InitializeHostOverlapped
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::InitializeHostOverlapped
helpviewer_keywords:
- IHostIoCompletionManager::InitializeHostOverlapped method [.NET Framework hosting]
- InitializeHostOverlapped method [.NET Framework hosting]
ms.assetid: c35199bf-bc47-4901-b467-4e8a37644bbb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9d27799e427efd3659dc2864e7d1e8e2061c5c19
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780768"
---
# <a name="ihostiocompletionmanagerinitializehostoverlapped-method"></a><span data-ttu-id="25936-102">IHostIoCompletionManager::InitializeHostOverlapped Yöntemi</span><span class="sxs-lookup"><span data-stu-id="25936-102">IHostIoCompletionManager::InitializeHostOverlapped Method</span></span>
<span data-ttu-id="25936-103">Konak için bir Win32 eklemek için herhangi bir özel veri başlatmak üzere bir fırsat sağlar `OVERLAPPED` zaman uyumsuz g/ç istekleri için kullanılan yapısı.</span><span class="sxs-lookup"><span data-stu-id="25936-103">Provides the host with an opportunity to initialize any custom data to append to a Win32 `OVERLAPPED` structure that is used for asynchronous I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25936-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="25936-104">Syntax</span></span>  
  
```cpp  
HRESULT InitializeHostOverlapped (  
    [in] void* pvOverlapped  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="25936-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="25936-105">Parameters</span></span>  
 `pvOverlapped`  
 <span data-ttu-id="25936-106">[in] Win32 işaretçisi `OVERLAPPED` yapısı ile g/ç isteği dahil edilecek.</span><span class="sxs-lookup"><span data-stu-id="25936-106">[in] A pointer to the Win32 `OVERLAPPED` structure to be included with the I/O request.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="25936-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="25936-107">Return Value</span></span>  
  
|<span data-ttu-id="25936-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="25936-108">HRESULT</span></span>|<span data-ttu-id="25936-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="25936-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="25936-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="25936-110">S_OK</span></span>|<span data-ttu-id="25936-111">`InitializeHostOverlapped` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="25936-111">`InitializeHostOverlapped` returned successfully.</span></span>|  
|<span data-ttu-id="25936-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="25936-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="25936-113">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="25936-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="25936-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="25936-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="25936-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="25936-115">The call timed out.</span></span>|  
|<span data-ttu-id="25936-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="25936-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="25936-117">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="25936-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="25936-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="25936-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="25936-119">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="25936-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="25936-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="25936-120">E_FAIL</span></span>|<span data-ttu-id="25936-121">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="25936-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="25936-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="25936-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="25936-123">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="25936-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="25936-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="25936-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="25936-125">İstenen kaynağı ayırmak yeterli bellek yoktu.</span><span class="sxs-lookup"><span data-stu-id="25936-125">Not enough memory was available to allocate the requested resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="25936-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="25936-126">Remarks</span></span>  
 <span data-ttu-id="25936-127">Windows Platform işlevleri kullanmak `OVERLAPPED` zaman uyumsuz g/ç isteği için durumu depolamak üzere yapısı.</span><span class="sxs-lookup"><span data-stu-id="25936-127">The Windows Platform functions use the `OVERLAPPED` structure to store state for asynchronous I/O requests.</span></span> <span data-ttu-id="25936-128">CLR çağrıları `InitializeHostOverlapped` konak özel verilere eklemek içinse fırsatı sunmak için yöntemi bir `OVERLAPPED` örneği.</span><span class="sxs-lookup"><span data-stu-id="25936-128">The CLR calls the `InitializeHostOverlapped` method to give the host the opportunity to append custom data to an `OVERLAPPED` instance.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="25936-129">Kendi özel veri bloğunun başlangıcına almak için konaklar boyutuna uzaklık ayarlamanız gerekir `OVERLAPPED` yapısı (`sizeof(OVERLAPPED)`).</span><span class="sxs-lookup"><span data-stu-id="25936-129">To get to the beginning of their custom data block, hosts must set the offset to the size of the `OVERLAPPED` structure (`sizeof(OVERLAPPED)`).</span></span>  
  
 <span data-ttu-id="25936-130">E_OUTOFMEMORY dönüş değeri, konak özel verilerini başlatmak başarısız olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="25936-130">A return value of E_OUTOFMEMORY indicates that the host has failed to initialize its custom data.</span></span> <span data-ttu-id="25936-131">Bu durumda, CLR hata raporları ve çağrı başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="25936-131">In this case, the CLR reports an error and fails the call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25936-132">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="25936-132">Requirements</span></span>  
 <span data-ttu-id="25936-133">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25936-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25936-134">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="25936-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="25936-135">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="25936-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="25936-136">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25936-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25936-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="25936-137">See also</span></span>

- [<span data-ttu-id="25936-138">ICLRIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="25936-138">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="25936-139">GetHostOverlappedSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="25936-139">GetHostOverlappedSize Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-gethostoverlappedsize-method.md)
- [<span data-ttu-id="25936-140">IHostIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="25936-140">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
