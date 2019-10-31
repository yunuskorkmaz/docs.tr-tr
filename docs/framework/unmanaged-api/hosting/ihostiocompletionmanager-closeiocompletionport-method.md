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
ms.openlocfilehash: 254254af705f93793b030882e0ac79d0372ca55f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133890"
---
# <a name="ihostiocompletionmanagercloseiocompletionport-method"></a><span data-ttu-id="3ec0a-102">IHostIoCompletionManager::CloseIoCompletionPort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3ec0a-102">IHostIoCompletionManager::CloseIoCompletionPort Method</span></span>
<span data-ttu-id="3ec0a-103">Konağın bir [CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md)daha önceki çağrısıyla açılan bir bağlantı noktasını kapatmasını ister.</span><span class="sxs-lookup"><span data-stu-id="3ec0a-103">Requests that the host close a port that was opened through an earlier call to [CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ec0a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3ec0a-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseIoCompletionPort (  
    [in] HANDLE hPort  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3ec0a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3ec0a-105">Parameters</span></span>  
 `hPort`  
 <span data-ttu-id="3ec0a-106">'ndaki Kapatılacak bağlantı noktasının tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="3ec0a-106">[in] The handle of the port to close.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3ec0a-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3ec0a-107">Return Value</span></span>  
  
|<span data-ttu-id="3ec0a-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3ec0a-108">HRESULT</span></span>|<span data-ttu-id="3ec0a-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3ec0a-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3ec0a-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="3ec0a-110">S_OK</span></span>|<span data-ttu-id="3ec0a-111">`CloseIoCompletionPort` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="3ec0a-111">`CloseIoCompletionPort` returned successfully.</span></span>|  
|<span data-ttu-id="3ec0a-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3ec0a-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3ec0a-113">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="3ec0a-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3ec0a-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3ec0a-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3ec0a-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="3ec0a-115">The call timed out.</span></span>|  
|<span data-ttu-id="3ec0a-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3ec0a-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3ec0a-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="3ec0a-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3ec0a-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3ec0a-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3ec0a-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="3ec0a-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3ec0a-120">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="3ec0a-120">E_FAIL</span></span>|<span data-ttu-id="3ec0a-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="3ec0a-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3ec0a-122">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="3ec0a-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3ec0a-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="3ec0a-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="3ec0a-124">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="3ec0a-124">E_INVALIDARG</span></span>|<span data-ttu-id="3ec0a-125">Geçersiz bir bağlantı noktası tanıtıcısı geçildi.</span><span class="sxs-lookup"><span data-stu-id="3ec0a-125">An invalid port handle was passed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3ec0a-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3ec0a-126">Remarks</span></span>  
 <span data-ttu-id="3ec0a-127">`hPort`, `CreateIoCompletionPort`daha önceki bir çağrı tarafından oluşturulan bir bağlantı noktasının tanıtıcısı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3ec0a-127">`hPort` must be a handle to a port that was created by an earlier call to `CreateIoCompletionPort`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ec0a-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3ec0a-128">Requirements</span></span>  
 <span data-ttu-id="3ec0a-129">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3ec0a-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ec0a-130">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="3ec0a-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3ec0a-131">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="3ec0a-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3ec0a-132">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3ec0a-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ec0a-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3ec0a-133">See also</span></span>

- [<span data-ttu-id="3ec0a-134">ICLRIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3ec0a-134">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="3ec0a-135">IHostIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3ec0a-135">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
