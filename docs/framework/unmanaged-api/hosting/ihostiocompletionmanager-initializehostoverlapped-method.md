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
ms.openlocfilehash: ac7014962b99ac167e8192c13b2bae5ca92470f0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69948520"
---
# <a name="ihostiocompletionmanagerinitializehostoverlapped-method"></a><span data-ttu-id="ab47d-102">IHostIoCompletionManager::InitializeHostOverlapped Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ab47d-102">IHostIoCompletionManager::InitializeHostOverlapped Method</span></span>
<span data-ttu-id="ab47d-103">Ana bilgisayara, zaman uyumsuz g/ç istekleri için kullanılan bir Win32 `OVERLAPPED` yapısına eklenecek özel verileri başlatma fırsatı sağlar.</span><span class="sxs-lookup"><span data-stu-id="ab47d-103">Provides the host with an opportunity to initialize any custom data to append to a Win32 `OVERLAPPED` structure that is used for asynchronous I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab47d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ab47d-104">Syntax</span></span>  
  
```cpp  
HRESULT InitializeHostOverlapped (  
    [in] void* pvOverlapped  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ab47d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ab47d-105">Parameters</span></span>  
 `pvOverlapped`  
 <span data-ttu-id="ab47d-106">'ndaki G/ç isteğine dahil `OVERLAPPED` edilecek Win32 yapısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ab47d-106">[in] A pointer to the Win32 `OVERLAPPED` structure to be included with the I/O request.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ab47d-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ab47d-107">Return Value</span></span>  
  
|<span data-ttu-id="ab47d-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ab47d-108">HRESULT</span></span>|<span data-ttu-id="ab47d-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ab47d-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ab47d-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="ab47d-110">S_OK</span></span>|<span data-ttu-id="ab47d-111">`InitializeHostOverlapped`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="ab47d-111">`InitializeHostOverlapped` returned successfully.</span></span>|  
|<span data-ttu-id="ab47d-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ab47d-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ab47d-113">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="ab47d-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ab47d-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ab47d-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ab47d-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="ab47d-115">The call timed out.</span></span>|  
|<span data-ttu-id="ab47d-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ab47d-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ab47d-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="ab47d-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ab47d-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ab47d-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ab47d-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="ab47d-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ab47d-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ab47d-120">E_FAIL</span></span>|<span data-ttu-id="ab47d-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="ab47d-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ab47d-122">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="ab47d-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ab47d-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="ab47d-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="ab47d-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="ab47d-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="ab47d-125">İstenen kaynağı ayırmak için yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="ab47d-125">Not enough memory was available to allocate the requested resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ab47d-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ab47d-126">Remarks</span></span>  
 <span data-ttu-id="ab47d-127">Windows platformu işlevleri, zaman uyumsuz `OVERLAPPED` g/ç isteklerinin durumunu depolamak için yapıyı kullanır.</span><span class="sxs-lookup"><span data-stu-id="ab47d-127">The Windows Platform functions use the `OVERLAPPED` structure to store state for asynchronous I/O requests.</span></span> <span data-ttu-id="ab47d-128">CLR, konağa özel `InitializeHostOverlapped` verileri ekleme fırsatına bir `OVERLAPPED` örneğe çağrı yapmak için yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="ab47d-128">The CLR calls the `InitializeHostOverlapped` method to give the host the opportunity to append custom data to an `OVERLAPPED` instance.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="ab47d-129">Özel veri bloğunun başlangıcına ulaşmak için, Konaklar `OVERLAPPED` yapının (`sizeof(OVERLAPPED)`) boyutuna kadar olan sapmayı ayarlamış olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ab47d-129">To get to the beginning of their custom data block, hosts must set the offset to the size of the `OVERLAPPED` structure (`sizeof(OVERLAPPED)`).</span></span>  
  
 <span data-ttu-id="ab47d-130">E_OUTOFMEMORY dönüş değeri, konağın özel verilerini başlatamadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ab47d-130">A return value of E_OUTOFMEMORY indicates that the host has failed to initialize its custom data.</span></span> <span data-ttu-id="ab47d-131">Bu durumda, CLR bir hata bildirir ve çağrı başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="ab47d-131">In this case, the CLR reports an error and fails the call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab47d-132">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ab47d-132">Requirements</span></span>  
 <span data-ttu-id="ab47d-133">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab47d-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab47d-134">**Üst bilgi** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ab47d-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ab47d-135">**Kitaplığı** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="ab47d-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ab47d-136">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab47d-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab47d-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ab47d-137">See also</span></span>

- [<span data-ttu-id="ab47d-138">ICLRIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ab47d-138">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="ab47d-139">GetHostOverlappedSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ab47d-139">GetHostOverlappedSize Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-gethostoverlappedsize-method.md)
- [<span data-ttu-id="ab47d-140">IHostIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ab47d-140">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
