---
title: "IHostIoCompletionManager::CloseIoCompletionPort Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostIoCompletionManager.CloseIoCompletionPort
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostIoCompletionManager::CloseIoCompletionPort
helpviewer_keywords:
- IHostIoCompletionManager::CloseIoCompletionPort method [.NET Framework hosting]
- CloseIoCompletionPort method [.NET Framework hosting]
ms.assetid: e86ad7be-3758-498a-a972-5522d69dfbb3
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 066d51c821cf86522ffaca4c15db360ce96ed773
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostiocompletionmanagercloseiocompletionport-method"></a><span data-ttu-id="c6ffa-102">IHostIoCompletionManager::CloseIoCompletionPort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c6ffa-102">IHostIoCompletionManager::CloseIoCompletionPort Method</span></span>
<span data-ttu-id="c6ffa-103">Ana bilgisayar daha önceki bir çağrı aracılığıyla açılmış bir bağlantı noktasını kapatmak istekleri [CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md).</span><span class="sxs-lookup"><span data-stu-id="c6ffa-103">Requests that the host close a port that was opened through an earlier call to [CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6ffa-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c6ffa-104">Syntax</span></span>  
  
```  
HRESULT CloseIoCompletionPort (  
    [in] HANDLE hPort  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c6ffa-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c6ffa-105">Parameters</span></span>  
 `hPort`  
 <span data-ttu-id="c6ffa-106">[in] Kapatmak için bağlantı noktası işleci.</span><span class="sxs-lookup"><span data-stu-id="c6ffa-106">[in] The handle of the port to close.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c6ffa-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c6ffa-107">Return Value</span></span>  
  
|<span data-ttu-id="c6ffa-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c6ffa-108">HRESULT</span></span>|<span data-ttu-id="c6ffa-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c6ffa-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c6ffa-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="c6ffa-110">S_OK</span></span>|<span data-ttu-id="c6ffa-111">`CloseIoCompletionPort`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="c6ffa-111">`CloseIoCompletionPort` returned successfully.</span></span>|  
|<span data-ttu-id="c6ffa-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c6ffa-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c6ffa-113">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="c6ffa-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c6ffa-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c6ffa-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c6ffa-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="c6ffa-115">The call timed out.</span></span>|  
|<span data-ttu-id="c6ffa-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c6ffa-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c6ffa-117">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="c6ffa-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c6ffa-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c6ffa-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c6ffa-119">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="c6ffa-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c6ffa-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c6ffa-120">E_FAIL</span></span>|<span data-ttu-id="c6ffa-121">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="c6ffa-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c6ffa-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="c6ffa-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c6ffa-123">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="c6ffa-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="c6ffa-124">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="c6ffa-124">E_INVALIDARG</span></span>|<span data-ttu-id="c6ffa-125">Geçersiz bağlantı noktası tanıtıcı geçirildi.</span><span class="sxs-lookup"><span data-stu-id="c6ffa-125">An invalid port handle was passed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c6ffa-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c6ffa-126">Remarks</span></span>  
 <span data-ttu-id="c6ffa-127">`hPort`önceki bir çağrı tarafından oluşturulan bir bağlantı noktası için bir tanıtıcı olmalıdır `CreateIoCompletionPort`.</span><span class="sxs-lookup"><span data-stu-id="c6ffa-127">`hPort` must be a handle to a port that was created by an earlier call to `CreateIoCompletionPort`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6ffa-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c6ffa-128">Requirements</span></span>  
 <span data-ttu-id="c6ffa-129">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c6ffa-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6ffa-130">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c6ffa-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c6ffa-131">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="c6ffa-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c6ffa-132">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6ffa-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6ffa-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c6ffa-133">See Also</span></span>  
 [<span data-ttu-id="c6ffa-134">Iclrıocompletionmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="c6ffa-134">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="c6ffa-135">Ihostıocompletionmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="c6ffa-135">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
