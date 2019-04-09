---
title: IHostIoCompletionManager::CreateIoCompletionPort Yöntemi
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.CreateIoCompletionPort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::CreateIoCompletionPort
helpviewer_keywords:
- IHostIoCompletionManager::CreateIoCompletionPort method [.NET Framework hosting]
- CreateIoCompletionPort method [.NET Framework hosting]
ms.assetid: 907a2b43-68db-44a7-acac-89e792e7bb3c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8cf7978af4081b84a361e0a96a6c9da7180cb217
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59194051"
---
# <a name="ihostiocompletionmanagercreateiocompletionport-method"></a><span data-ttu-id="6f837-102">IHostIoCompletionManager::CreateIoCompletionPort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6f837-102">IHostIoCompletionManager::CreateIoCompletionPort Method</span></span>
<span data-ttu-id="6f837-103">Ana bilgisayar yeni bir g/ç tamamlama bağlantı oluşturma isteği.</span><span class="sxs-lookup"><span data-stu-id="6f837-103">Requests that the host create a new I/O completion port.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f837-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6f837-104">Syntax</span></span>  
  
```  
HRESULT CreateIoCompletionPort (  
    [out] HANDLE *phPort  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6f837-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6f837-105">Parameters</span></span>  
 `phPort`  
 <span data-ttu-id="6f837-106">[out] Yeni oluşturulan g/ç tamamlama bağlantı noktasını ya da 0 (sıfır), bağlantı noktası oluşturulamadı, işleyici için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6f837-106">[out] A pointer to a handle to the newly created I/O completion port, or 0 (zero), if the port could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6f837-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="6f837-107">Return Value</span></span>  
  
|<span data-ttu-id="6f837-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6f837-108">HRESULT</span></span>|<span data-ttu-id="6f837-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6f837-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6f837-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="6f837-110">S_OK</span></span>|`CreateIoCompletionPort` <span data-ttu-id="6f837-111">başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="6f837-111">returned successfully.</span></span>|  
|<span data-ttu-id="6f837-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6f837-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6f837-113">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="6f837-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6f837-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6f837-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6f837-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="6f837-115">The call timed out.</span></span>|  
|<span data-ttu-id="6f837-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6f837-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6f837-117">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="6f837-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6f837-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6f837-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6f837-119">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="6f837-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6f837-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6f837-120">E_FAIL</span></span>|<span data-ttu-id="6f837-121">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="6f837-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6f837-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="6f837-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6f837-123">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="6f837-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="6f837-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="6f837-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="6f837-125">İstenen kaynağı ayırmak yeterli bellek yoktu.</span><span class="sxs-lookup"><span data-stu-id="6f837-125">Not enough memory was available to allocate the requested resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6f837-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6f837-126">Remarks</span></span>  
 <span data-ttu-id="6f837-127">CLR çağrıları `CreateIoCompletionPort` yöntemi ana bilgisayar yeni bir g/ç tamamlama bağlantı oluşturmasını isteyin.</span><span class="sxs-lookup"><span data-stu-id="6f837-127">The CLR calls the `CreateIoCompletionPort` method to request that the host create a new I/O completion port.</span></span> <span data-ttu-id="6f837-128">Bu bağlantı noktasına yapılan bir çağrıyla g/ç işlemleri bağlar [Ihostıocompletionmanager::Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6f837-128">It binds I/O operations to this port through a call to the [IHostIoCompletionManager::Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) method.</span></span> <span data-ttu-id="6f837-129">Ana rapor durumu geri CLR çağırarak [Iclrıocompletionmanager::onComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md).</span><span class="sxs-lookup"><span data-stu-id="6f837-129">The host reports status back to the CLR by calling [ICLRIoCompletionManager::OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f837-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6f837-130">Requirements</span></span>  
 <span data-ttu-id="6f837-131">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6f837-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f837-132">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6f837-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6f837-133">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="6f837-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="6f837-134">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="6f837-134">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6f837-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6f837-135">See also</span></span>

- [<span data-ttu-id="6f837-136">ICLRIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6f837-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="6f837-137">IHostIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6f837-137">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
