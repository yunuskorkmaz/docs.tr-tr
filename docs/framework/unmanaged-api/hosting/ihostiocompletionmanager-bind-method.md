---
title: "IHostIoCompletionManager::Bind Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a34de8c04e248d2973e9b27c10da9313db5077ff
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostiocompletionmanagerbind-method"></a><span data-ttu-id="b5e20-102">IHostIoCompletionManager::Bind Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b5e20-102">IHostIoCompletionManager::Bind Method</span></span>
<span data-ttu-id="b5e20-103">Belirtilen tanıtıcı önceki bir çağrı tarafından oluşturulan bir g/ç tamamlama bağlantı noktasına bağlar [CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md).</span><span class="sxs-lookup"><span data-stu-id="b5e20-103">Binds the specified handle to an I/O completion port that has been created by an earlier call to [CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5e20-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b5e20-104">Syntax</span></span>  
  
```  
HRESULT Bind (  
    [in] HANDLE hPort,  
    [in] HANDLE hHandle  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b5e20-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b5e20-105">Parameters</span></span>  
 `hPort`  
 <span data-ttu-id="b5e20-106">[in] G/ç tamamlama bağlantı noktasına bağlanacak `hHandle`.</span><span class="sxs-lookup"><span data-stu-id="b5e20-106">[in] The I/O completion port to which to bind `hHandle`.</span></span> <span data-ttu-id="b5e20-107">Varsa değerini `hPort` null, `hHandle` varsayılan g/ç tamamlama bağlantı noktasına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="b5e20-107">If the value of `hPort` is null, `hHandle` is bound to the default I/O completion port.</span></span>  
  
 `hHandle`  
 <span data-ttu-id="b5e20-108">[in] Bağlamak için işletim sistemi tanıtıcı `hPort`.</span><span class="sxs-lookup"><span data-stu-id="b5e20-108">[in] The operating system handle to bind to `hPort`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b5e20-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b5e20-109">Return Value</span></span>  
  
|<span data-ttu-id="b5e20-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b5e20-110">HRESULT</span></span>|<span data-ttu-id="b5e20-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b5e20-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b5e20-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="b5e20-112">S_OK</span></span>|<span data-ttu-id="b5e20-113">`Bind`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="b5e20-113">`Bind` returned successfully.</span></span>|  
|<span data-ttu-id="b5e20-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b5e20-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b5e20-115">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="b5e20-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b5e20-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b5e20-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b5e20-117">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="b5e20-117">The call timed out.</span></span>|  
|<span data-ttu-id="b5e20-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b5e20-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b5e20-119">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="b5e20-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b5e20-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b5e20-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b5e20-121">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="b5e20-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b5e20-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b5e20-122">E_FAIL</span></span>|<span data-ttu-id="b5e20-123">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="b5e20-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b5e20-124">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="b5e20-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b5e20-125">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="b5e20-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b5e20-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b5e20-126">Remarks</span></span>  
 <span data-ttu-id="b5e20-127">Bir g/ç tamamlama bağlantı noktasını yapılan bir çağrı kullanılarak oluşturulan `CreateIoCompletionPort`.</span><span class="sxs-lookup"><span data-stu-id="b5e20-127">An I/O completion port is created by using a call to `CreateIoCompletionPort`.</span></span> <span data-ttu-id="b5e20-128">CLR çağrıları `Bind` bir tanıtıcı Bu bağlantı noktasına bağlanamadı.</span><span class="sxs-lookup"><span data-stu-id="b5e20-128">The CLR calls `Bind` to bind a handle to that port.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b5e20-129">Bir g/ç isteği tamamlandığında konak çağırmalısınız [Iclrıocompletionmanager::onComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b5e20-129">When an I/O request completes, the host must call the [ICLRIoCompletionManager::OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5e20-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b5e20-130">Requirements</span></span>  
 <span data-ttu-id="b5e20-131">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b5e20-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5e20-132">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b5e20-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b5e20-133">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="b5e20-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b5e20-134">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5e20-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5e20-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b5e20-135">See Also</span></span>  
 [<span data-ttu-id="b5e20-136">ICLRIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b5e20-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
