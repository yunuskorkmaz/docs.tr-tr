---
description: 'Şu konuda daha fazla bilgi edinin: ıhostiocompletionmanager:: GetAvailableThreads yöntemi'
title: IHostIoCompletionManager::GetAvailableThreads Yöntemi
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.GetAvailableThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::GetAvailableThreads
helpviewer_keywords:
- GetAvailableThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
- IHostIoCompletionManager::GetAvailableThreads method [.NET Framework hosting]
ms.assetid: bab363d1-b859-47a4-9884-5661c611cce7
topic_type:
- apiref
ms.openlocfilehash: d50f79716f72b902102a2a97a0bce5dfe645334f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708565"
---
# <a name="ihostiocompletionmanagergetavailablethreads-method"></a><span data-ttu-id="48f26-103">IHostIoCompletionManager::GetAvailableThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="48f26-103">IHostIoCompletionManager::GetAvailableThreads Method</span></span>

<span data-ttu-id="48f26-104">Ana bilgisayar tarafından yönetilen ve şu anda istekleri olmayan iş parçacıklarının toplam sayısı olan g/ç Tamamlama iş parçacığı sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="48f26-104">Gets the number of I/O completion threads, of the total number of threads managed by the host, that are not currently servicing requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48f26-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="48f26-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAvailableThreads (  
    [out] DWORD *pdwAvailableIoCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="48f26-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="48f26-106">Parameters</span></span>  

 `pdwAvailableIoCompletionThreads`  
 <span data-ttu-id="48f26-107">dışı Şu anda hizmet istekleri için kullanılabilir olan ana bilgisayar tarafından yönetilen g/ç Tamamlama iş parçacığı sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="48f26-107">[out] A pointer to the number of I/O completion threads managed by the host that are currently available to service requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="48f26-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="48f26-108">Return Value</span></span>  
  
|<span data-ttu-id="48f26-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="48f26-109">HRESULT</span></span>|<span data-ttu-id="48f26-110">Description</span><span class="sxs-lookup"><span data-stu-id="48f26-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="48f26-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="48f26-111">S_OK</span></span>|<span data-ttu-id="48f26-112">`GetAvailableThreads` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="48f26-112">`GetAvailableThreads` returned successfully.</span></span>|  
|<span data-ttu-id="48f26-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="48f26-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="48f26-114">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="48f26-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="48f26-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="48f26-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="48f26-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="48f26-116">The call timed out.</span></span>|  
|<span data-ttu-id="48f26-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="48f26-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="48f26-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="48f26-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="48f26-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="48f26-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="48f26-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="48f26-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="48f26-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="48f26-121">E_FAIL</span></span>|<span data-ttu-id="48f26-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="48f26-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="48f26-123">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="48f26-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="48f26-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="48f26-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="48f26-125">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="48f26-125">E_NOTIMPL</span></span>|<span data-ttu-id="48f26-126">Konak, uygulamasının bir uygulamasını sağlamaz `GetAvailableThreads` .</span><span class="sxs-lookup"><span data-stu-id="48f26-126">The host does not provide an implementation of `GetAvailableThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="48f26-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="48f26-127">Remarks</span></span>  

 <span data-ttu-id="48f26-128">Bir ana bilgisayar, uygulama, performans veya ölçeklenebilirlik gibi nedenlerle g/ç Tamamlama iş parçacığı havuzunun boyutu üzerinde özel denetim istiyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="48f26-128">A host might want exclusive control over the size of the I/O completion thread pool, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="48f26-129">Bu nedenle, konağın uygulanması gerekli değildir `GetAvailableThreads` .</span><span class="sxs-lookup"><span data-stu-id="48f26-129">Therefore, the host is not required to implement `GetAvailableThreads`.</span></span> <span data-ttu-id="48f26-130">Bu durumda, ana bilgisayar bu yöntemden E_NOTIMPL döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="48f26-130">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48f26-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="48f26-131">Requirements</span></span>  

 <span data-ttu-id="48f26-132">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="48f26-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48f26-133">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="48f26-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="48f26-134">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="48f26-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="48f26-135">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48f26-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48f26-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="48f26-136">See also</span></span>

- [<span data-ttu-id="48f26-137">ICLRIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="48f26-137">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="48f26-138">IHostIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="48f26-138">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
