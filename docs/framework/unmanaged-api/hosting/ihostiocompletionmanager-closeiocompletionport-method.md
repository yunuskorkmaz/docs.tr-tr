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
ms.openlocfilehash: 32a7c8b1c1c61eddb18ade1e77af5ea973fbaadc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61760135"
---
# <a name="ihostiocompletionmanagercloseiocompletionport-method"></a><span data-ttu-id="13262-102">IHostIoCompletionManager::CloseIoCompletionPort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="13262-102">IHostIoCompletionManager::CloseIoCompletionPort Method</span></span>
<span data-ttu-id="13262-103">Konak, önceki bir çağrı yoluyla açık bir bağlantı noktası kapatmak ister [CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md).</span><span class="sxs-lookup"><span data-stu-id="13262-103">Requests that the host close a port that was opened through an earlier call to [CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13262-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="13262-104">Syntax</span></span>  
  
```  
HRESULT CloseIoCompletionPort (  
    [in] HANDLE hPort  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="13262-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="13262-105">Parameters</span></span>  
 `hPort`  
 <span data-ttu-id="13262-106">[in] Kapatmak için bağlantı noktası tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="13262-106">[in] The handle of the port to close.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="13262-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="13262-107">Return Value</span></span>  
  
|<span data-ttu-id="13262-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="13262-108">HRESULT</span></span>|<span data-ttu-id="13262-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="13262-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="13262-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="13262-110">S_OK</span></span>|<span data-ttu-id="13262-111">`CloseIoCompletionPort` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="13262-111">`CloseIoCompletionPort` returned successfully.</span></span>|  
|<span data-ttu-id="13262-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="13262-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="13262-113">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="13262-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="13262-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="13262-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="13262-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="13262-115">The call timed out.</span></span>|  
|<span data-ttu-id="13262-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="13262-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="13262-117">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="13262-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="13262-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="13262-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="13262-119">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="13262-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="13262-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="13262-120">E_FAIL</span></span>|<span data-ttu-id="13262-121">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="13262-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="13262-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="13262-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="13262-123">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="13262-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="13262-124">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="13262-124">E_INVALIDARG</span></span>|<span data-ttu-id="13262-125">Geçersiz bağlantı noktası tanıtıcı geçirildi.</span><span class="sxs-lookup"><span data-stu-id="13262-125">An invalid port handle was passed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="13262-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="13262-126">Remarks</span></span>  
 <span data-ttu-id="13262-127">`hPort` önceki bir çağrı tarafından oluşturulan bir bağlantı noktası için bir tanıtıcı olmalıdır `CreateIoCompletionPort`.</span><span class="sxs-lookup"><span data-stu-id="13262-127">`hPort` must be a handle to a port that was created by an earlier call to `CreateIoCompletionPort`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13262-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="13262-128">Requirements</span></span>  
 <span data-ttu-id="13262-129">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13262-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13262-130">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="13262-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="13262-131">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="13262-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="13262-132">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13262-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13262-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="13262-133">See also</span></span>

- [<span data-ttu-id="13262-134">ICLRIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="13262-134">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="13262-135">IHostIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="13262-135">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
