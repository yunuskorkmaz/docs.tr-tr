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
ms.openlocfilehash: 023e112aa8273d99efce2e0f2116f95569ac0c3b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33438974"
---
# <a name="ihostiocompletionmanagerinitializehostoverlapped-method"></a><span data-ttu-id="7f1fb-102">IHostIoCompletionManager::InitializeHostOverlapped Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7f1fb-102">IHostIoCompletionManager::InitializeHostOverlapped Method</span></span>
<span data-ttu-id="7f1fb-103">Win32'ye eklemek için herhangi bir özel veri başlatmak için bir fırsat ile ana bilgisayarının sağladığı `OVERLAPPED` zaman uyumsuz g/ç istekleri için kullanılan yapısı.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-103">Provides the host with an opportunity to initialize any custom data to append to a Win32 `OVERLAPPED` structure that is used for asynchronous I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f1fb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7f1fb-104">Syntax</span></span>  
  
```  
HRESULT InitializeHostOverlapped (  
    [in] void* pvOverlapped  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7f1fb-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7f1fb-105">Parameters</span></span>  
 `pvOverlapped`  
 <span data-ttu-id="7f1fb-106">[in] Win32 için bir işaretçi `OVERLAPPED` g/ç isteği dahil edilecek yapısı.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-106">[in] A pointer to the Win32 `OVERLAPPED` structure to be included with the I/O request.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7f1fb-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7f1fb-107">Return Value</span></span>  
  
|<span data-ttu-id="7f1fb-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7f1fb-108">HRESULT</span></span>|<span data-ttu-id="7f1fb-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7f1fb-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7f1fb-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="7f1fb-110">S_OK</span></span>|<span data-ttu-id="7f1fb-111">`InitializeHostOverlapped` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-111">`InitializeHostOverlapped` returned successfully.</span></span>|  
|<span data-ttu-id="7f1fb-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7f1fb-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7f1fb-113">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7f1fb-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7f1fb-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7f1fb-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-115">The call timed out.</span></span>|  
|<span data-ttu-id="7f1fb-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7f1fb-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7f1fb-117">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7f1fb-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7f1fb-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7f1fb-119">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7f1fb-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7f1fb-120">E_FAIL</span></span>|<span data-ttu-id="7f1fb-121">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7f1fb-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7f1fb-123">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="7f1fb-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="7f1fb-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="7f1fb-125">İstenen kaynak ayırmak yeterli bellek yoktu.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-125">Not enough memory was available to allocate the requested resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7f1fb-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7f1fb-126">Remarks</span></span>  
 <span data-ttu-id="7f1fb-127">Windows platformu işlevleri kullanım `OVERLAPPED` zaman uyumsuz g/ç istekleri için durumu depolamak üzere yapısı.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-127">The Windows Platform functions use the `OVERLAPPED` structure to store state for asynchronous I/O requests.</span></span> <span data-ttu-id="7f1fb-128">CLR çağrıları `InitializeHostOverlapped` ana bilgisayar için özel veri Ekle fırsatı sunmak için yöntemi bir `OVERLAPPED` örneği.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-128">The CLR calls the `InitializeHostOverlapped` method to give the host the opportunity to append custom data to an `OVERLAPPED` instance.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7f1fb-129">Kendi özel veri bloğu başlangıcına almak için ana uzaklık boyutuna ayarlamalısınız `OVERLAPPED` yapısı (`sizeof(OVERLAPPED)`).</span><span class="sxs-lookup"><span data-stu-id="7f1fb-129">To get to the beginning of their custom data block, hosts must set the offset to the size of the `OVERLAPPED` structure (`sizeof(OVERLAPPED)`).</span></span>  
  
 <span data-ttu-id="7f1fb-130">E_OUTOFMEMORY dönüş değeri, konak, kendi özel veri başlatmak başarısız olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-130">A return value of E_OUTOFMEMORY indicates that the host has failed to initialize its custom data.</span></span> <span data-ttu-id="7f1fb-131">Bu durumda, CLR bir hata bildirir ve çağrı başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-131">In this case, the CLR reports an error and fails the call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f1fb-132">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7f1fb-132">Requirements</span></span>  
 <span data-ttu-id="7f1fb-133">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f1fb-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f1fb-134">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7f1fb-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7f1fb-135">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="7f1fb-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7f1fb-136">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f1fb-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f1fb-137">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7f1fb-137">See Also</span></span>  
 [<span data-ttu-id="7f1fb-138">ICLRIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7f1fb-138">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="7f1fb-139">GetHostOverlappedSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7f1fb-139">GetHostOverlappedSize Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-gethostoverlappedsize-method.md)  
 [<span data-ttu-id="7f1fb-140">IHostIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7f1fb-140">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
