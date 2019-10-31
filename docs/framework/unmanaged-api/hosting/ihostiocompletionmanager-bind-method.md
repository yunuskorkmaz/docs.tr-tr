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
ms.openlocfilehash: 84fc99f6a5feb7ec73ee16942ba2794fc082dc89
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133909"
---
# <a name="ihostiocompletionmanagerbind-method"></a><span data-ttu-id="8afb4-102">IHostIoCompletionManager::Bind Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8afb4-102">IHostIoCompletionManager::Bind Method</span></span>
<span data-ttu-id="8afb4-103">Belirtilen tanıtıcıyı, daha önceki bir [CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md)çağrısıyla oluşturulmuş bir g/ç tamamlama bağlantı noktasına bağlar.</span><span class="sxs-lookup"><span data-stu-id="8afb4-103">Binds the specified handle to an I/O completion port that has been created by an earlier call to [CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8afb4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8afb4-104">Syntax</span></span>  
  
```cpp  
HRESULT Bind (  
    [in] HANDLE hPort,  
    [in] HANDLE hHandle  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8afb4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8afb4-105">Parameters</span></span>  
 `hPort`  
 <span data-ttu-id="8afb4-106">'ndaki `hHandle`bağlanacağı g/ç tamamlama bağlantı noktası.</span><span class="sxs-lookup"><span data-stu-id="8afb4-106">[in] The I/O completion port to which to bind `hHandle`.</span></span> <span data-ttu-id="8afb4-107">`hPort` değeri null ise, `hHandle` varsayılan g/ç tamamlama bağlantı noktasına bağlanır.</span><span class="sxs-lookup"><span data-stu-id="8afb4-107">If the value of `hPort` is null, `hHandle` is bound to the default I/O completion port.</span></span>  
  
 `hHandle`  
 <span data-ttu-id="8afb4-108">'ndaki `hPort`bağlanacak işletim sistemi tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="8afb4-108">[in] The operating system handle to bind to `hPort`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8afb4-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8afb4-109">Return Value</span></span>  
  
|<span data-ttu-id="8afb4-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8afb4-110">HRESULT</span></span>|<span data-ttu-id="8afb4-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8afb4-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8afb4-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="8afb4-112">S_OK</span></span>|<span data-ttu-id="8afb4-113">`Bind` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="8afb4-113">`Bind` returned successfully.</span></span>|  
|<span data-ttu-id="8afb4-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8afb4-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8afb4-115">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="8afb4-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8afb4-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8afb4-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8afb4-117">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="8afb4-117">The call timed out.</span></span>|  
|<span data-ttu-id="8afb4-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8afb4-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8afb4-119">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="8afb4-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8afb4-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8afb4-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8afb4-121">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="8afb4-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8afb4-122">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="8afb4-122">E_FAIL</span></span>|<span data-ttu-id="8afb4-123">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="8afb4-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8afb4-124">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="8afb4-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8afb4-125">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="8afb4-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8afb4-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8afb4-126">Remarks</span></span>  
 <span data-ttu-id="8afb4-127">Bir g/ç tamamlama bağlantı noktası, `CreateIoCompletionPort`çağrısı kullanılarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="8afb4-127">An I/O completion port is created by using a call to `CreateIoCompletionPort`.</span></span> <span data-ttu-id="8afb4-128">CLR, bu bağlantı noktasına bir tanıtıcı bağlamak için `Bind` çağırır.</span><span class="sxs-lookup"><span data-stu-id="8afb4-128">The CLR calls `Bind` to bind a handle to that port.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8afb4-129">G/ç isteği tamamlandığında, ana bilgisayar [ıclriocompletionmanager:: Ontamamlanmıştır](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md) metodunu çağırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8afb4-129">When an I/O request completes, the host must call the [ICLRIoCompletionManager::OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8afb4-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8afb4-130">Requirements</span></span>  
 <span data-ttu-id="8afb4-131">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8afb4-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8afb4-132">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8afb4-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8afb4-133">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="8afb4-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8afb4-134">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8afb4-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8afb4-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8afb4-135">See also</span></span>

- [<span data-ttu-id="8afb4-136">ICLRIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8afb4-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
