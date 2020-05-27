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
ms.openlocfilehash: 8d18e6c1dca7f52b17c19f4638410a08866905f7
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804806"
---
# <a name="ihostiocompletionmanagerbind-method"></a><span data-ttu-id="da7e6-102">IHostIoCompletionManager::Bind Yöntemi</span><span class="sxs-lookup"><span data-stu-id="da7e6-102">IHostIoCompletionManager::Bind Method</span></span>
<span data-ttu-id="da7e6-103">Belirtilen tanıtıcıyı, daha önceki bir [CreateIoCompletionPort](ihostiocompletionmanager-createiocompletionport-method.md)çağrısıyla oluşturulmuş bir g/ç tamamlama bağlantı noktasına bağlar.</span><span class="sxs-lookup"><span data-stu-id="da7e6-103">Binds the specified handle to an I/O completion port that has been created by an earlier call to [CreateIoCompletionPort](ihostiocompletionmanager-createiocompletionport-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da7e6-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="da7e6-104">Syntax</span></span>  
  
```cpp  
HRESULT Bind (  
    [in] HANDLE hPort,  
    [in] HANDLE hHandle  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="da7e6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="da7e6-105">Parameters</span></span>  
 `hPort`  
 <span data-ttu-id="da7e6-106">'ndaki Bağlanacak g/ç tamamlama bağlantı noktası `hHandle` .</span><span class="sxs-lookup"><span data-stu-id="da7e6-106">[in] The I/O completion port to which to bind `hHandle`.</span></span> <span data-ttu-id="da7e6-107">Değeri `hPort` null ise `hHandle` varsayılan g/ç tamamlama bağlantı noktasına bağlanır.</span><span class="sxs-lookup"><span data-stu-id="da7e6-107">If the value of `hPort` is null, `hHandle` is bound to the default I/O completion port.</span></span>  
  
 `hHandle`  
 <span data-ttu-id="da7e6-108">'ndaki Bağlanacak işletim sistemi tanıtıcısı `hPort` .</span><span class="sxs-lookup"><span data-stu-id="da7e6-108">[in] The operating system handle to bind to `hPort`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="da7e6-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="da7e6-109">Return Value</span></span>  
  
|<span data-ttu-id="da7e6-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="da7e6-110">HRESULT</span></span>|<span data-ttu-id="da7e6-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="da7e6-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="da7e6-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="da7e6-112">S_OK</span></span>|<span data-ttu-id="da7e6-113">`Bind`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="da7e6-113">`Bind` returned successfully.</span></span>|  
|<span data-ttu-id="da7e6-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="da7e6-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="da7e6-115">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="da7e6-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="da7e6-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="da7e6-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="da7e6-117">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="da7e6-117">The call timed out.</span></span>|  
|<span data-ttu-id="da7e6-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="da7e6-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="da7e6-119">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="da7e6-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="da7e6-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="da7e6-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="da7e6-121">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="da7e6-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="da7e6-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="da7e6-122">E_FAIL</span></span>|<span data-ttu-id="da7e6-123">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="da7e6-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="da7e6-124">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="da7e6-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="da7e6-125">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="da7e6-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="da7e6-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="da7e6-126">Remarks</span></span>  
 <span data-ttu-id="da7e6-127">Bir g/ç tamamlama bağlantı noktası, için çağrısı kullanılarak oluşturulur `CreateIoCompletionPort` .</span><span class="sxs-lookup"><span data-stu-id="da7e6-127">An I/O completion port is created by using a call to `CreateIoCompletionPort`.</span></span> <span data-ttu-id="da7e6-128">CLR, `Bind` Bu bağlantı noktasına bir tanıtıcı bağlamak için çağırır.</span><span class="sxs-lookup"><span data-stu-id="da7e6-128">The CLR calls `Bind` to bind a handle to that port.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="da7e6-129">G/ç isteği tamamlandığında, ana bilgisayar [ıclriocompletionmanager:: Ontamamlanmıştır](iclriocompletionmanager-oncomplete-method.md) metodunu çağırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="da7e6-129">When an I/O request completes, the host must call the [ICLRIoCompletionManager::OnComplete](iclriocompletionmanager-oncomplete-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da7e6-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="da7e6-130">Requirements</span></span>  
 <span data-ttu-id="da7e6-131">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="da7e6-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da7e6-132">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="da7e6-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="da7e6-133">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="da7e6-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="da7e6-134">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da7e6-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da7e6-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="da7e6-135">See also</span></span>

- [<span data-ttu-id="da7e6-136">ICLRIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="da7e6-136">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
