---
description: ': Ihostiocompletionmanager:: Bind yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 2105bf06c23f70588d0c1bc0cd849b8e810d121e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784866"
---
# <a name="ihostiocompletionmanagerbind-method"></a><span data-ttu-id="23bac-103">IHostIoCompletionManager::Bind Yöntemi</span><span class="sxs-lookup"><span data-stu-id="23bac-103">IHostIoCompletionManager::Bind Method</span></span>

<span data-ttu-id="23bac-104">Belirtilen tanıtıcıyı, daha önceki bir [CreateIoCompletionPort](ihostiocompletionmanager-createiocompletionport-method.md)çağrısıyla oluşturulmuş bir g/ç tamamlama bağlantı noktasına bağlar.</span><span class="sxs-lookup"><span data-stu-id="23bac-104">Binds the specified handle to an I/O completion port that has been created by an earlier call to [CreateIoCompletionPort](ihostiocompletionmanager-createiocompletionport-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23bac-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="23bac-105">Syntax</span></span>  
  
```cpp  
HRESULT Bind (  
    [in] HANDLE hPort,  
    [in] HANDLE hHandle  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="23bac-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="23bac-106">Parameters</span></span>  

 `hPort`  
 <span data-ttu-id="23bac-107">'ndaki Bağlanacak g/ç tamamlama bağlantı noktası `hHandle` .</span><span class="sxs-lookup"><span data-stu-id="23bac-107">[in] The I/O completion port to which to bind `hHandle`.</span></span> <span data-ttu-id="23bac-108">Değeri `hPort` null ise `hHandle` varsayılan g/ç tamamlama bağlantı noktasına bağlanır.</span><span class="sxs-lookup"><span data-stu-id="23bac-108">If the value of `hPort` is null, `hHandle` is bound to the default I/O completion port.</span></span>  
  
 `hHandle`  
 <span data-ttu-id="23bac-109">'ndaki Bağlanacak işletim sistemi tanıtıcısı `hPort` .</span><span class="sxs-lookup"><span data-stu-id="23bac-109">[in] The operating system handle to bind to `hPort`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="23bac-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="23bac-110">Return Value</span></span>  
  
|<span data-ttu-id="23bac-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="23bac-111">HRESULT</span></span>|<span data-ttu-id="23bac-112">Description</span><span class="sxs-lookup"><span data-stu-id="23bac-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="23bac-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="23bac-113">S_OK</span></span>|<span data-ttu-id="23bac-114">`Bind` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="23bac-114">`Bind` returned successfully.</span></span>|  
|<span data-ttu-id="23bac-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="23bac-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="23bac-116">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="23bac-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="23bac-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="23bac-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="23bac-118">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="23bac-118">The call timed out.</span></span>|  
|<span data-ttu-id="23bac-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="23bac-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="23bac-120">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="23bac-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="23bac-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="23bac-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="23bac-122">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="23bac-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="23bac-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="23bac-123">E_FAIL</span></span>|<span data-ttu-id="23bac-124">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="23bac-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="23bac-125">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="23bac-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="23bac-126">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="23bac-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="23bac-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="23bac-127">Remarks</span></span>  

 <span data-ttu-id="23bac-128">Bir g/ç tamamlama bağlantı noktası, için çağrısı kullanılarak oluşturulur `CreateIoCompletionPort` .</span><span class="sxs-lookup"><span data-stu-id="23bac-128">An I/O completion port is created by using a call to `CreateIoCompletionPort`.</span></span> <span data-ttu-id="23bac-129">CLR, `Bind` Bu bağlantı noktasına bir tanıtıcı bağlamak için çağırır.</span><span class="sxs-lookup"><span data-stu-id="23bac-129">The CLR calls `Bind` to bind a handle to that port.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="23bac-130">G/ç isteği tamamlandığında, ana bilgisayar [ıclriocompletionmanager:: Ontamamlanmıştır](iclriocompletionmanager-oncomplete-method.md) metodunu çağırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="23bac-130">When an I/O request completes, the host must call the [ICLRIoCompletionManager::OnComplete](iclriocompletionmanager-oncomplete-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23bac-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="23bac-131">Requirements</span></span>  

 <span data-ttu-id="23bac-132">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="23bac-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23bac-133">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="23bac-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="23bac-134">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="23bac-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="23bac-135">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23bac-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23bac-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="23bac-136">See also</span></span>

- [<span data-ttu-id="23bac-137">ICLRIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="23bac-137">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
