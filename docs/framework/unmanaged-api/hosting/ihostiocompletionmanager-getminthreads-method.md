---
title: IHostIoCompletionManager::GetMinThreads Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IHostIoCompletionManager.GetMinThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::GetMinThreads
helpviewer_keywords:
- GetMinThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
- IHostIoCompletionManager::GetMinThreads method [.NET Framework hosting]
ms.assetid: d7a7f733-677d-481c-b3d5-444fcc502b8e
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f90a3f416520cc3f635f19d7ae34d5f9f304e9c6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostiocompletionmanagergetminthreads-method"></a><span data-ttu-id="c7817-102">IHostIoCompletionManager::GetMinThreads Metodu</span><span class="sxs-lookup"><span data-stu-id="c7817-102">IHostIoCompletionManager::GetMinThreads Method</span></span>
<span data-ttu-id="c7817-103">En düşük g/ç istekleri işlemek için ana bilgisayarının sağladığı iş parçacığı sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="c7817-103">Gets the minimum number of threads that the host provides for processing I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7817-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c7817-104">Syntax</span></span>  
  
```  
HRESULT GetMinThreads (  
    [out] DWORD *pdwMinIOCompletionThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c7817-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c7817-105">Parameters</span></span>  
 `pdwMinIOCompletionThreads`  
 <span data-ttu-id="c7817-106">[out] En az işlem g/ç istekleri ana bilgisayarının sağladığı iş parçacığı sayısını gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c7817-106">[out] A pointer to the minimum number of threads that the host provides to process I/O requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c7817-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c7817-107">Return Value</span></span>  
  
|<span data-ttu-id="c7817-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c7817-108">HRESULT</span></span>|<span data-ttu-id="c7817-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c7817-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c7817-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="c7817-110">S_OK</span></span>|<span data-ttu-id="c7817-111">`GetMinThreads`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="c7817-111">`GetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="c7817-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c7817-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c7817-113">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="c7817-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c7817-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c7817-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c7817-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="c7817-115">The call timed out.</span></span>|  
|<span data-ttu-id="c7817-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c7817-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c7817-117">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="c7817-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c7817-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c7817-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c7817-119">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="c7817-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c7817-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c7817-120">E_FAIL</span></span>|<span data-ttu-id="c7817-121">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="c7817-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c7817-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="c7817-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c7817-123">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="c7817-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="c7817-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="c7817-124">E_NOTIMPL</span></span>|<span data-ttu-id="c7817-125">Ana bilgisayar uygulaması sağlamaz `GetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="c7817-125">The host does not provide an implementation of `GetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c7817-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c7817-126">Remarks</span></span>  
 <span data-ttu-id="c7817-127">Bir ana bilgisayar uygulaması, performans ve ölçeklenebilirlik gibi nedenlerle hizmet g/ç istekleri için ayrılan iş parçacığı sayısını özel denetime isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c7817-127">A host might want exclusive control over the number of threads allotted to service I/O requests, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="c7817-128">Bu nedenle, ana bilgisayar uygulamak için gerekli olmayan `GetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="c7817-128">For this reason, the host is not required to implement `GetMinThreads`.</span></span> <span data-ttu-id="c7817-129">Bu durumda, konak E_NOTIMPL Bu yönteminden döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="c7817-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7817-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c7817-130">Requirements</span></span>  
 <span data-ttu-id="c7817-131">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7817-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7817-132">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c7817-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c7817-133">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="c7817-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c7817-134">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7817-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7817-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c7817-135">See Also</span></span>  
 [<span data-ttu-id="c7817-136">ICLRIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c7817-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="c7817-137">IHostIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c7817-137">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
