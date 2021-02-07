---
description: 'Şu konuda daha fazla bilgi edinin: ıhostiocompletionmanager:: GetMaxThreads yöntemi'
title: IHostIoCompletionManager::GetMaxThreads Metodu
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.GetMaxThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::GetMaxThreads
helpviewer_keywords:
- IHostIoCompletionManager::GetMaxThreads method [.NET Framework hosting]
- GetMaxThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
ms.assetid: e7a6cadc-2433-4472-a701-58891abcde45
topic_type:
- apiref
ms.openlocfilehash: 10c36c058f5161330842fa9d71813c4520d4655c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708542"
---
# <a name="ihostiocompletionmanagergetmaxthreads-method"></a><span data-ttu-id="d0d8c-103">IHostIoCompletionManager::GetMaxThreads Metodu</span><span class="sxs-lookup"><span data-stu-id="d0d8c-103">IHostIoCompletionManager::GetMaxThreads Method</span></span>

<span data-ttu-id="d0d8c-104">Ana bilgisayarın g/ç isteklerine hizmet vermek için lot olarak barındırabileceği en fazla iş parçacığı sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="d0d8c-104">Gets the maximum number of threads that the host can allot to service I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0d8c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d0d8c-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMaxThreads (  
    [out] DWORD *pdwMaxIoCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d0d8c-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d0d8c-106">Parameters</span></span>  

 `pdwMaxIoCompletionThreads`  
 <span data-ttu-id="d0d8c-107">dışı İş parçacığı havuzunda ana bilgisayarın g/ç isteklerine hizmet verecek en fazla iş parçacığı sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d0d8c-107">[out] A pointer to the maximum number of threads in the thread pool that the host can allot to service I/O requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d0d8c-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d0d8c-108">Return Value</span></span>  
  
|<span data-ttu-id="d0d8c-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d0d8c-109">HRESULT</span></span>|<span data-ttu-id="d0d8c-110">Description</span><span class="sxs-lookup"><span data-stu-id="d0d8c-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d0d8c-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="d0d8c-111">S_OK</span></span>|<span data-ttu-id="d0d8c-112">`GetMaxThreads` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="d0d8c-112">`GetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="d0d8c-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d0d8c-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d0d8c-114">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="d0d8c-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d0d8c-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d0d8c-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d0d8c-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="d0d8c-116">The call timed out.</span></span>|  
|<span data-ttu-id="d0d8c-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d0d8c-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d0d8c-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="d0d8c-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d0d8c-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d0d8c-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d0d8c-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="d0d8c-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d0d8c-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d0d8c-121">E_FAIL</span></span>|<span data-ttu-id="d0d8c-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="d0d8c-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d0d8c-123">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="d0d8c-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d0d8c-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="d0d8c-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="d0d8c-125">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="d0d8c-125">E_NOTIMPL</span></span>|<span data-ttu-id="d0d8c-126">Konak, uygulamasının bir uygulamasını sağlamaz `GetMaxThreads` .</span><span class="sxs-lookup"><span data-stu-id="d0d8c-126">The host does not provide an implementation of `GetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d0d8c-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d0d8c-127">Remarks</span></span>  

 <span data-ttu-id="d0d8c-128">Bir ana bilgisayar, uygulama, performans veya ölçeklenebilirlik gibi nedenlerle g/ç isteklerini işlemek için ayrılan iş parçacığı sayısı üzerinde özel denetim istiyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="d0d8c-128">A host might want exclusive control over the number of threads that can be allotted to process I/O requests, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="d0d8c-129">Bu nedenle, konağın uygulanması gerekmez `GetMaxThreads` .</span><span class="sxs-lookup"><span data-stu-id="d0d8c-129">For this reason, the host is not required to implement `GetMaxThreads`.</span></span> <span data-ttu-id="d0d8c-130">Bu durumda, ana bilgisayar bu yöntemden E_NOTIMPL döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="d0d8c-130">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0d8c-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d0d8c-131">Requirements</span></span>  

 <span data-ttu-id="d0d8c-132">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d0d8c-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0d8c-133">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d0d8c-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d0d8c-134">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="d0d8c-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d0d8c-135">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0d8c-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0d8c-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d0d8c-136">See also</span></span>

- [<span data-ttu-id="d0d8c-137">ICLRIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d0d8c-137">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="d0d8c-138">IHostIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d0d8c-138">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
