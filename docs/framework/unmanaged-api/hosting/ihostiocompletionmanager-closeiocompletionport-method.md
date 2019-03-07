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
ms.openlocfilehash: d6c9a6bf69b8f1728f9dfa6c19bc04670d96a6d8
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57494355"
---
# <a name="ihostiocompletionmanagercloseiocompletionport-method"></a><span data-ttu-id="f1234-102">IHostIoCompletionManager::CloseIoCompletionPort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f1234-102">IHostIoCompletionManager::CloseIoCompletionPort Method</span></span>
<span data-ttu-id="f1234-103">Konak, önceki bir çağrı yoluyla açık bir bağlantı noktası kapatmak ister [CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md).</span><span class="sxs-lookup"><span data-stu-id="f1234-103">Requests that the host close a port that was opened through an earlier call to [CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1234-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f1234-104">Syntax</span></span>  
  
```  
HRESULT CloseIoCompletionPort (  
    [in] HANDLE hPort  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f1234-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f1234-105">Parameters</span></span>  
 `hPort`  
 <span data-ttu-id="f1234-106">[in] Kapatmak için bağlantı noktası tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="f1234-106">[in] The handle of the port to close.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f1234-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f1234-107">Return Value</span></span>  
  
|<span data-ttu-id="f1234-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f1234-108">HRESULT</span></span>|<span data-ttu-id="f1234-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f1234-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f1234-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="f1234-110">S_OK</span></span>|<span data-ttu-id="f1234-111">`CloseIoCompletionPort` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="f1234-111">`CloseIoCompletionPort` returned successfully.</span></span>|  
|<span data-ttu-id="f1234-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f1234-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f1234-113">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="f1234-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f1234-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f1234-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f1234-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="f1234-115">The call timed out.</span></span>|  
|<span data-ttu-id="f1234-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f1234-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f1234-117">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="f1234-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f1234-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f1234-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f1234-119">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="f1234-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f1234-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f1234-120">E_FAIL</span></span>|<span data-ttu-id="f1234-121">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="f1234-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f1234-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="f1234-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f1234-123">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="f1234-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="f1234-124">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="f1234-124">E_INVALIDARG</span></span>|<span data-ttu-id="f1234-125">Geçersiz bağlantı noktası tanıtıcı geçirildi.</span><span class="sxs-lookup"><span data-stu-id="f1234-125">An invalid port handle was passed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f1234-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f1234-126">Remarks</span></span>  
 <span data-ttu-id="f1234-127">`hPort` önceki bir çağrı tarafından oluşturulan bir bağlantı noktası için bir tanıtıcı olmalıdır `CreateIoCompletionPort`.</span><span class="sxs-lookup"><span data-stu-id="f1234-127">`hPort` must be a handle to a port that was created by an earlier call to `CreateIoCompletionPort`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1234-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f1234-128">Requirements</span></span>  
 <span data-ttu-id="f1234-129">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1234-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1234-130">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f1234-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f1234-131">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="f1234-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f1234-132">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1234-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1234-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f1234-133">See also</span></span>
- [<span data-ttu-id="f1234-134">ICLRIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f1234-134">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="f1234-135">IHostIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f1234-135">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
