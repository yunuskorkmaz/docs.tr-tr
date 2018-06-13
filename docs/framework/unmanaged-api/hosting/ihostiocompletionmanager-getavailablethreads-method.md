---
title: IHostIoCompletionManager::GetAvailableThreads Metodu
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bb5de5b46a46d5caa74b83f16d943edc39d08b01
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33441844"
---
# <a name="ihostiocompletionmanagergetavailablethreads-method"></a><span data-ttu-id="deb84-102">IHostIoCompletionManager::GetAvailableThreads Metodu</span><span class="sxs-lookup"><span data-stu-id="deb84-102">IHostIoCompletionManager::GetAvailableThreads Method</span></span>
<span data-ttu-id="deb84-103">G/ç Tamamlama iş parçacıklarının, istekleri şu anda bakım değil, ana bilgisayar tarafından yönetilen iş parçacığı sayısı toplam sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="deb84-103">Gets the number of I/O completion threads, of the total number of threads managed by the host, that are not currently servicing requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="deb84-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="deb84-104">Syntax</span></span>  
  
```  
HRESULT GetAvailableThreads (  
    [out] DWORD *pdwAvailableIoCompletionThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="deb84-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="deb84-105">Parameters</span></span>  
 `pdwAvailableIoCompletionThreads`  
 <span data-ttu-id="deb84-106">[out] Hizmet istekleri için şu anda kullanılabilen ana bilgisayar tarafından yönetilen g/ç Tamamlama iş parçacığı sayısını gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="deb84-106">[out] A pointer to the number of I/O completion threads managed by the host that are currently available to service requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="deb84-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="deb84-107">Return Value</span></span>  
  
|<span data-ttu-id="deb84-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="deb84-108">HRESULT</span></span>|<span data-ttu-id="deb84-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="deb84-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="deb84-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="deb84-110">S_OK</span></span>|<span data-ttu-id="deb84-111">`GetAvailableThreads` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="deb84-111">`GetAvailableThreads` returned successfully.</span></span>|  
|<span data-ttu-id="deb84-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="deb84-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="deb84-113">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="deb84-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="deb84-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="deb84-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="deb84-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="deb84-115">The call timed out.</span></span>|  
|<span data-ttu-id="deb84-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="deb84-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="deb84-117">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="deb84-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="deb84-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="deb84-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="deb84-119">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="deb84-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="deb84-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="deb84-120">E_FAIL</span></span>|<span data-ttu-id="deb84-121">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="deb84-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="deb84-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="deb84-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="deb84-123">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="deb84-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="deb84-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="deb84-124">E_NOTIMPL</span></span>|<span data-ttu-id="deb84-125">Ana bilgisayar uygulaması sağlamaz `GetAvailableThreads`.</span><span class="sxs-lookup"><span data-stu-id="deb84-125">The host does not provide an implementation of `GetAvailableThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="deb84-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="deb84-126">Remarks</span></span>  
 <span data-ttu-id="deb84-127">Bir ana bilgisayar uygulaması, performans ve ölçeklenebilirlik gibi nedenlerle g/ç Tamamlama iş parçacığı havuzunun boyutunu özel denetime isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="deb84-127">A host might want exclusive control over the size of the I/O completion thread pool, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="deb84-128">Bu nedenle, ana bilgisayar uygulamak için gerekli olmayan `GetAvailableThreads`.</span><span class="sxs-lookup"><span data-stu-id="deb84-128">Therefore, the host is not required to implement `GetAvailableThreads`.</span></span> <span data-ttu-id="deb84-129">Bu durumda, konak E_NOTIMPL Bu yönteminden döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="deb84-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="deb84-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="deb84-130">Requirements</span></span>  
 <span data-ttu-id="deb84-131">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="deb84-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="deb84-132">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="deb84-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="deb84-133">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="deb84-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="deb84-134">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="deb84-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="deb84-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="deb84-135">See Also</span></span>  
 [<span data-ttu-id="deb84-136">ICLRIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="deb84-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="deb84-137">IHostIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="deb84-137">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
