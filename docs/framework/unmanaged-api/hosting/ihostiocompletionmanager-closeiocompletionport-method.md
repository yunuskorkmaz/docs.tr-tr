---
title: IHostIoCompletionManager::CloseIoCompletionPort Yöntemi
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.CloseIoCompletionPort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::CloseIoCompletionPort
helpviewer_keywords:
- IHostIoCompletionManager::CloseIoCompletionPort method [.NET Framework hosting]
- CloseIoCompletionPort method [.NET Framework hosting]
ms.assetid: e86ad7be-3758-498a-a972-5522d69dfbb3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cceced01b34f10cf38b41cfcb2a17059650f9ad9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67736530"
---
# <a name="ihostiocompletionmanagercloseiocompletionport-method"></a><span data-ttu-id="8d497-102">IHostIoCompletionManager::CloseIoCompletionPort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8d497-102">IHostIoCompletionManager::CloseIoCompletionPort Method</span></span>
<span data-ttu-id="8d497-103">Konak, önceki bir çağrı yoluyla açık bir bağlantı noktası kapatmak ister [CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md).</span><span class="sxs-lookup"><span data-stu-id="8d497-103">Requests that the host close a port that was opened through an earlier call to [CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d497-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8d497-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseIoCompletionPort (  
    [in] HANDLE hPort  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8d497-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8d497-105">Parameters</span></span>  
 `hPort`  
 <span data-ttu-id="8d497-106">[in] Kapatmak için bağlantı noktası tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="8d497-106">[in] The handle of the port to close.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8d497-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8d497-107">Return Value</span></span>  
  
|<span data-ttu-id="8d497-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8d497-108">HRESULT</span></span>|<span data-ttu-id="8d497-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8d497-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8d497-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="8d497-110">S_OK</span></span>|<span data-ttu-id="8d497-111">`CloseIoCompletionPort` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="8d497-111">`CloseIoCompletionPort` returned successfully.</span></span>|  
|<span data-ttu-id="8d497-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8d497-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8d497-113">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="8d497-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8d497-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8d497-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8d497-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="8d497-115">The call timed out.</span></span>|  
|<span data-ttu-id="8d497-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8d497-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8d497-117">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="8d497-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8d497-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8d497-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8d497-119">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="8d497-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8d497-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8d497-120">E_FAIL</span></span>|<span data-ttu-id="8d497-121">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="8d497-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8d497-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="8d497-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8d497-123">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="8d497-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="8d497-124">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="8d497-124">E_INVALIDARG</span></span>|<span data-ttu-id="8d497-125">Geçersiz bağlantı noktası tanıtıcı geçirildi.</span><span class="sxs-lookup"><span data-stu-id="8d497-125">An invalid port handle was passed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8d497-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8d497-126">Remarks</span></span>  
 <span data-ttu-id="8d497-127">`hPort` önceki bir çağrı tarafından oluşturulan bir bağlantı noktası için bir tanıtıcı olmalıdır `CreateIoCompletionPort`.</span><span class="sxs-lookup"><span data-stu-id="8d497-127">`hPort` must be a handle to a port that was created by an earlier call to `CreateIoCompletionPort`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d497-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8d497-128">Requirements</span></span>  
 <span data-ttu-id="8d497-129">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8d497-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d497-130">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8d497-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8d497-131">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="8d497-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8d497-132">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d497-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d497-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8d497-133">See also</span></span>

- [<span data-ttu-id="8d497-134">ICLRIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8d497-134">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="8d497-135">IHostIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8d497-135">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
