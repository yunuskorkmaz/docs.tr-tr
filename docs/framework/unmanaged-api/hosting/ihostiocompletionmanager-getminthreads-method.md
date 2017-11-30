---
title: IHostIoCompletionManager::GetMinThreads Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostIoCompletionManager.GetMinThreads
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostIoCompletionManager::GetMinThreads
helpviewer_keywords:
- GetMinThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
- IHostIoCompletionManager::GetMinThreads method [.NET Framework hosting]
ms.assetid: d7a7f733-677d-481c-b3d5-444fcc502b8e
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6fb9369b67cd79c6e83dc13e2a1090ae611a5e5a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostiocompletionmanagergetminthreads-method"></a><span data-ttu-id="5ab6a-102">IHostIoCompletionManager::GetMinThreads Metodu</span><span class="sxs-lookup"><span data-stu-id="5ab6a-102">IHostIoCompletionManager::GetMinThreads Method</span></span>
<span data-ttu-id="5ab6a-103">En düşük g/ç istekleri işlemek için ana bilgisayarının sağladığı iş parçacığı sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="5ab6a-103">Gets the minimum number of threads that the host provides for processing I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ab6a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5ab6a-104">Syntax</span></span>  
  
```  
HRESULT GetMinThreads (  
    [out] DWORD *pdwMinIOCompletionThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5ab6a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5ab6a-105">Parameters</span></span>  
 `pdwMinIOCompletionThreads`  
 <span data-ttu-id="5ab6a-106">[out] En az işlem g/ç istekleri ana bilgisayarının sağladığı iş parçacığı sayısını gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5ab6a-106">[out] A pointer to the minimum number of threads that the host provides to process I/O requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5ab6a-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5ab6a-107">Return Value</span></span>  
  
|<span data-ttu-id="5ab6a-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5ab6a-108">HRESULT</span></span>|<span data-ttu-id="5ab6a-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5ab6a-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5ab6a-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="5ab6a-110">S_OK</span></span>|<span data-ttu-id="5ab6a-111">`GetMinThreads`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="5ab6a-111">`GetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="5ab6a-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5ab6a-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5ab6a-113">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="5ab6a-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5ab6a-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5ab6a-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5ab6a-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="5ab6a-115">The call timed out.</span></span>|  
|<span data-ttu-id="5ab6a-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5ab6a-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5ab6a-117">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="5ab6a-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5ab6a-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5ab6a-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5ab6a-119">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="5ab6a-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5ab6a-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5ab6a-120">E_FAIL</span></span>|<span data-ttu-id="5ab6a-121">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="5ab6a-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5ab6a-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="5ab6a-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5ab6a-123">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="5ab6a-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="5ab6a-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="5ab6a-124">E_NOTIMPL</span></span>|<span data-ttu-id="5ab6a-125">Ana bilgisayar uygulaması sağlamaz `GetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="5ab6a-125">The host does not provide an implementation of `GetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5ab6a-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5ab6a-126">Remarks</span></span>  
 <span data-ttu-id="5ab6a-127">Bir ana bilgisayar uygulaması, performans ve ölçeklenebilirlik gibi nedenlerle hizmet g/ç istekleri için ayrılan iş parçacığı sayısını özel denetime isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5ab6a-127">A host might want exclusive control over the number of threads allotted to service I/O requests, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="5ab6a-128">Bu nedenle, ana bilgisayar uygulamak için gerekli olmayan `GetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="5ab6a-128">For this reason, the host is not required to implement `GetMinThreads`.</span></span> <span data-ttu-id="5ab6a-129">Bu durumda, konak E_NOTIMPL Bu yönteminden döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="5ab6a-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ab6a-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5ab6a-130">Requirements</span></span>  
 <span data-ttu-id="5ab6a-131">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ab6a-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ab6a-132">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5ab6a-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5ab6a-133">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="5ab6a-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5ab6a-134">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ab6a-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ab6a-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5ab6a-135">See Also</span></span>  
 [<span data-ttu-id="5ab6a-136">Iclrıocompletionmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="5ab6a-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="5ab6a-137">Ihostıocompletionmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="5ab6a-137">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
