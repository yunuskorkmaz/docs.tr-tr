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
ms.openlocfilehash: 2951b408efa39e1ac2afbd7d8ebcb5ea139a8a71
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54582457"
---
# <a name="ihostiocompletionmanagerinitializehostoverlapped-method"></a><span data-ttu-id="dffb3-102">IHostIoCompletionManager::InitializeHostOverlapped Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dffb3-102">IHostIoCompletionManager::InitializeHostOverlapped Method</span></span>
<span data-ttu-id="dffb3-103">Konak için bir Win32 eklemek için herhangi bir özel veri başlatmak üzere bir fırsat sağlar `OVERLAPPED` zaman uyumsuz g/ç istekleri için kullanılan yapısı.</span><span class="sxs-lookup"><span data-stu-id="dffb3-103">Provides the host with an opportunity to initialize any custom data to append to a Win32 `OVERLAPPED` structure that is used for asynchronous I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dffb3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dffb3-104">Syntax</span></span>  
  
```  
HRESULT InitializeHostOverlapped (  
    [in] void* pvOverlapped  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dffb3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="dffb3-105">Parameters</span></span>  
 `pvOverlapped`  
 <span data-ttu-id="dffb3-106">[in] Win32 işaretçisi `OVERLAPPED` yapısı ile g/ç isteği dahil edilecek.</span><span class="sxs-lookup"><span data-stu-id="dffb3-106">[in] A pointer to the Win32 `OVERLAPPED` structure to be included with the I/O request.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dffb3-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="dffb3-107">Return Value</span></span>  
  
|<span data-ttu-id="dffb3-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="dffb3-108">HRESULT</span></span>|<span data-ttu-id="dffb3-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dffb3-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dffb3-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="dffb3-110">S_OK</span></span>|<span data-ttu-id="dffb3-111">`InitializeHostOverlapped` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="dffb3-111">`InitializeHostOverlapped` returned successfully.</span></span>|  
|<span data-ttu-id="dffb3-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="dffb3-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="dffb3-113">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="dffb3-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="dffb3-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="dffb3-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="dffb3-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="dffb3-115">The call timed out.</span></span>|  
|<span data-ttu-id="dffb3-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="dffb3-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="dffb3-117">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="dffb3-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="dffb3-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="dffb3-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="dffb3-119">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="dffb3-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="dffb3-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="dffb3-120">E_FAIL</span></span>|<span data-ttu-id="dffb3-121">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="dffb3-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="dffb3-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="dffb3-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="dffb3-123">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="dffb3-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="dffb3-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="dffb3-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="dffb3-125">İstenen kaynağı ayırmak yeterli bellek yoktu.</span><span class="sxs-lookup"><span data-stu-id="dffb3-125">Not enough memory was available to allocate the requested resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dffb3-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dffb3-126">Remarks</span></span>  
 <span data-ttu-id="dffb3-127">Windows Platform işlevleri kullanmak `OVERLAPPED` zaman uyumsuz g/ç isteği için durumu depolamak üzere yapısı.</span><span class="sxs-lookup"><span data-stu-id="dffb3-127">The Windows Platform functions use the `OVERLAPPED` structure to store state for asynchronous I/O requests.</span></span> <span data-ttu-id="dffb3-128">CLR çağrıları `InitializeHostOverlapped` konak özel verilere eklemek içinse fırsatı sunmak için yöntemi bir `OVERLAPPED` örneği.</span><span class="sxs-lookup"><span data-stu-id="dffb3-128">The CLR calls the `InitializeHostOverlapped` method to give the host the opportunity to append custom data to an `OVERLAPPED` instance.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="dffb3-129">Kendi özel veri bloğunun başlangıcına almak için konaklar boyutuna uzaklık ayarlamanız gerekir `OVERLAPPED` yapısı (`sizeof(OVERLAPPED)`).</span><span class="sxs-lookup"><span data-stu-id="dffb3-129">To get to the beginning of their custom data block, hosts must set the offset to the size of the `OVERLAPPED` structure (`sizeof(OVERLAPPED)`).</span></span>  
  
 <span data-ttu-id="dffb3-130">E_OUTOFMEMORY dönüş değeri, konak özel verilerini başlatmak başarısız olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="dffb3-130">A return value of E_OUTOFMEMORY indicates that the host has failed to initialize its custom data.</span></span> <span data-ttu-id="dffb3-131">Bu durumda, CLR hata raporları ve çağrı başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="dffb3-131">In this case, the CLR reports an error and fails the call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dffb3-132">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dffb3-132">Requirements</span></span>  
 <span data-ttu-id="dffb3-133">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dffb3-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dffb3-134">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="dffb3-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dffb3-135">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="dffb3-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dffb3-136">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dffb3-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dffb3-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dffb3-137">See also</span></span>
- [<span data-ttu-id="dffb3-138">ICLRIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dffb3-138">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="dffb3-139">GetHostOverlappedSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dffb3-139">GetHostOverlappedSize Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-gethostoverlappedsize-method.md)
- [<span data-ttu-id="dffb3-140">IHostIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dffb3-140">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
