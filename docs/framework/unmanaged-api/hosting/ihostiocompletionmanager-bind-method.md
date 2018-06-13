---
title: IHostIoCompletionManager::Bind Yöntemi
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.Bind
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::Bind
helpviewer_keywords:
- IHostIoCompletionManager::Bind method [.NET Framework hosting]
- Bind method [.NET Framework hosting]
ms.assetid: acd74cb5-7e22-4a07-83c3-82288e1abd9f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 89a30cf4fa95df85e3650459e356a6a82b19bcd6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33439833"
---
# <a name="ihostiocompletionmanagerbind-method"></a><span data-ttu-id="392b5-102">IHostIoCompletionManager::Bind Yöntemi</span><span class="sxs-lookup"><span data-stu-id="392b5-102">IHostIoCompletionManager::Bind Method</span></span>
<span data-ttu-id="392b5-103">Belirtilen tanıtıcı önceki bir çağrı tarafından oluşturulan bir g/ç tamamlama bağlantı noktasına bağlar [CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md).</span><span class="sxs-lookup"><span data-stu-id="392b5-103">Binds the specified handle to an I/O completion port that has been created by an earlier call to [CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="392b5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="392b5-104">Syntax</span></span>  
  
```  
HRESULT Bind (  
    [in] HANDLE hPort,  
    [in] HANDLE hHandle  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="392b5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="392b5-105">Parameters</span></span>  
 `hPort`  
 <span data-ttu-id="392b5-106">[in] G/ç tamamlama bağlantı noktasına bağlanacak `hHandle`.</span><span class="sxs-lookup"><span data-stu-id="392b5-106">[in] The I/O completion port to which to bind `hHandle`.</span></span> <span data-ttu-id="392b5-107">Varsa değerini `hPort` null, `hHandle` varsayılan g/ç tamamlama bağlantı noktasına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="392b5-107">If the value of `hPort` is null, `hHandle` is bound to the default I/O completion port.</span></span>  
  
 `hHandle`  
 <span data-ttu-id="392b5-108">[in] Bağlamak için işletim sistemi tanıtıcı `hPort`.</span><span class="sxs-lookup"><span data-stu-id="392b5-108">[in] The operating system handle to bind to `hPort`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="392b5-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="392b5-109">Return Value</span></span>  
  
|<span data-ttu-id="392b5-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="392b5-110">HRESULT</span></span>|<span data-ttu-id="392b5-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="392b5-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="392b5-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="392b5-112">S_OK</span></span>|<span data-ttu-id="392b5-113">`Bind` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="392b5-113">`Bind` returned successfully.</span></span>|  
|<span data-ttu-id="392b5-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="392b5-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="392b5-115">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="392b5-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="392b5-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="392b5-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="392b5-117">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="392b5-117">The call timed out.</span></span>|  
|<span data-ttu-id="392b5-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="392b5-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="392b5-119">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="392b5-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="392b5-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="392b5-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="392b5-121">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="392b5-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="392b5-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="392b5-122">E_FAIL</span></span>|<span data-ttu-id="392b5-123">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="392b5-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="392b5-124">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="392b5-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="392b5-125">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="392b5-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="392b5-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="392b5-126">Remarks</span></span>  
 <span data-ttu-id="392b5-127">Bir g/ç tamamlama bağlantı noktasını yapılan bir çağrı kullanılarak oluşturulan `CreateIoCompletionPort`.</span><span class="sxs-lookup"><span data-stu-id="392b5-127">An I/O completion port is created by using a call to `CreateIoCompletionPort`.</span></span> <span data-ttu-id="392b5-128">CLR çağrıları `Bind` bir tanıtıcı Bu bağlantı noktasına bağlanamadı.</span><span class="sxs-lookup"><span data-stu-id="392b5-128">The CLR calls `Bind` to bind a handle to that port.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="392b5-129">Bir g/ç isteği tamamlandığında konak çağırmalısınız [Iclrıocompletionmanager::onComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="392b5-129">When an I/O request completes, the host must call the [ICLRIoCompletionManager::OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="392b5-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="392b5-130">Requirements</span></span>  
 <span data-ttu-id="392b5-131">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="392b5-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="392b5-132">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="392b5-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="392b5-133">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="392b5-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="392b5-134">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="392b5-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="392b5-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="392b5-135">See Also</span></span>  
 [<span data-ttu-id="392b5-136">ICLRIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="392b5-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
