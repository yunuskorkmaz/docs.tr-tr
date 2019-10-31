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
ms.openlocfilehash: 9fd299ad25166bcbcf0202da13a5b4cbdd20d7d7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133796"
---
# <a name="ihostiocompletionmanagerinitializehostoverlapped-method"></a><span data-ttu-id="3eba2-102">IHostIoCompletionManager::InitializeHostOverlapped Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3eba2-102">IHostIoCompletionManager::InitializeHostOverlapped Method</span></span>
<span data-ttu-id="3eba2-103">Ana bilgisayara, zaman uyumsuz g/ç istekleri için kullanılan bir Win32 `OVERLAPPED` yapısına eklenecek özel verileri başlatma fırsatı sağlar.</span><span class="sxs-lookup"><span data-stu-id="3eba2-103">Provides the host with an opportunity to initialize any custom data to append to a Win32 `OVERLAPPED` structure that is used for asynchronous I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3eba2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3eba2-104">Syntax</span></span>  
  
```cpp  
HRESULT InitializeHostOverlapped (  
    [in] void* pvOverlapped  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3eba2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3eba2-105">Parameters</span></span>  
 `pvOverlapped`  
 <span data-ttu-id="3eba2-106">'ndaki G/ç isteğine dahil edilecek Win32 `OVERLAPPED` yapısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3eba2-106">[in] A pointer to the Win32 `OVERLAPPED` structure to be included with the I/O request.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3eba2-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3eba2-107">Return Value</span></span>  
  
|<span data-ttu-id="3eba2-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3eba2-108">HRESULT</span></span>|<span data-ttu-id="3eba2-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3eba2-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3eba2-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="3eba2-110">S_OK</span></span>|<span data-ttu-id="3eba2-111">`InitializeHostOverlapped` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="3eba2-111">`InitializeHostOverlapped` returned successfully.</span></span>|  
|<span data-ttu-id="3eba2-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3eba2-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3eba2-113">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="3eba2-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3eba2-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3eba2-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3eba2-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="3eba2-115">The call timed out.</span></span>|  
|<span data-ttu-id="3eba2-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3eba2-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3eba2-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="3eba2-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3eba2-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3eba2-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3eba2-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="3eba2-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3eba2-120">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="3eba2-120">E_FAIL</span></span>|<span data-ttu-id="3eba2-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="3eba2-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3eba2-122">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="3eba2-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3eba2-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="3eba2-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="3eba2-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="3eba2-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="3eba2-125">İstenen kaynağı ayırmak için yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="3eba2-125">Not enough memory was available to allocate the requested resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3eba2-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3eba2-126">Remarks</span></span>  
 <span data-ttu-id="3eba2-127">Windows platformu işlevleri, zaman uyumsuz g/ç isteklerinin durumunu depolamak için `OVERLAPPED` yapısını kullanır.</span><span class="sxs-lookup"><span data-stu-id="3eba2-127">The Windows Platform functions use the `OVERLAPPED` structure to store state for asynchronous I/O requests.</span></span> <span data-ttu-id="3eba2-128">CLR, konağa özel verileri ekleme fırsatını bir `OVERLAPPED` örneğine eklemek için `InitializeHostOverlapped` yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="3eba2-128">The CLR calls the `InitializeHostOverlapped` method to give the host the opportunity to append custom data to an `OVERLAPPED` instance.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="3eba2-129">Özel veri bloğunun başlangıcına ulaşmak için, ana bilgisayarların `OVERLAPPED` yapının boyutuna olan sapmayı ayarlaması gerekir (`sizeof(OVERLAPPED)`).</span><span class="sxs-lookup"><span data-stu-id="3eba2-129">To get to the beginning of their custom data block, hosts must set the offset to the size of the `OVERLAPPED` structure (`sizeof(OVERLAPPED)`).</span></span>  
  
 <span data-ttu-id="3eba2-130">E_OUTOFMEMORY dönüş değeri, konağın özel verilerini başlatamadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3eba2-130">A return value of E_OUTOFMEMORY indicates that the host has failed to initialize its custom data.</span></span> <span data-ttu-id="3eba2-131">Bu durumda, CLR bir hata bildirir ve çağrı başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="3eba2-131">In this case, the CLR reports an error and fails the call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3eba2-132">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3eba2-132">Requirements</span></span>  
 <span data-ttu-id="3eba2-133">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3eba2-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3eba2-134">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="3eba2-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3eba2-135">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="3eba2-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3eba2-136">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3eba2-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3eba2-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3eba2-137">See also</span></span>

- [<span data-ttu-id="3eba2-138">ICLRIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3eba2-138">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="3eba2-139">GetHostOverlappedSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3eba2-139">GetHostOverlappedSize Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-gethostoverlappedsize-method.md)
- [<span data-ttu-id="3eba2-140">IHostIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3eba2-140">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
