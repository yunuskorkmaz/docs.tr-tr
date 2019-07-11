---
title: IHostThreadPoolManager::GetAvailableThreads Yöntemi
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager.GetAvailableThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager::GetAvailableThreads
helpviewer_keywords:
- GetAvailableThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
- IHostThreadPoolManager::GetAvailableThreads method [.NET Framework hosting]
ms.assetid: 61d26dfd-7f24-4e7d-a63e-b30a463f08e1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 21a727a5287f6eaad600fc37befc32790fc4cf26
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67749305"
---
# <a name="ihostthreadpoolmanagergetavailablethreads-method"></a><span data-ttu-id="51ce3-102">IHostThreadPoolManager::GetAvailableThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="51ce3-102">IHostThreadPoolManager::GetAvailableThreads Method</span></span>
<span data-ttu-id="51ce3-103">İş öğeleri şu anda işleme değil iş parçacığı havuzundaki iş parçacığı sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="51ce3-103">Gets the number of threads in the thread pool that are not currently processing work items.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51ce3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="51ce3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAvailableThreads (  
    [out] DWORD *pdwAvailableWorkerThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="51ce3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="51ce3-105">Parameters</span></span>  
 `pdwAvailableWorkerThreads`  
 <span data-ttu-id="51ce3-106">[out] İş öğeleri şu anda işleme değil iş parçacığı havuzundaki iş parçacığı sayısını işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="51ce3-106">[out] Pointer to the number of threads in the thread pool that are not currently processing work items.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="51ce3-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="51ce3-107">Return Value</span></span>  
  
|<span data-ttu-id="51ce3-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="51ce3-108">HRESULT</span></span>|<span data-ttu-id="51ce3-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="51ce3-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="51ce3-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="51ce3-110">S_OK</span></span>|<span data-ttu-id="51ce3-111">`GetAvailableThreads` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="51ce3-111">`GetAvailableThreads` returned successfully.</span></span>|  
|<span data-ttu-id="51ce3-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="51ce3-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="51ce3-113">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="51ce3-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="51ce3-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="51ce3-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="51ce3-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="51ce3-115">The call timed out.</span></span>|  
|<span data-ttu-id="51ce3-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="51ce3-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="51ce3-117">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="51ce3-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="51ce3-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="51ce3-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="51ce3-119">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="51ce3-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="51ce3-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="51ce3-120">E_FAIL</span></span>|<span data-ttu-id="51ce3-121">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="51ce3-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="51ce3-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="51ce3-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="51ce3-123">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="51ce3-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="51ce3-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="51ce3-124">E_NOTIMPL</span></span>|<span data-ttu-id="51ce3-125">Ana bilgisayar uygulaması sağlamaz `GetAvailableThreads`.</span><span class="sxs-lookup"><span data-stu-id="51ce3-125">The host does not provide an implementation of `GetAvailableThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="51ce3-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="51ce3-126">Remarks</span></span>  
 <span data-ttu-id="51ce3-127">Ana bilgisayar uygulaması sağlamıyorsa `GetAvailableThreads`, E_NOTIMPL bir HRESULT değerini döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="51ce3-127">If the host does not provide an implementation of `GetAvailableThreads`, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51ce3-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="51ce3-128">Requirements</span></span>  
 <span data-ttu-id="51ce3-129">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="51ce3-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51ce3-130">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="51ce3-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="51ce3-131">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="51ce3-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="51ce3-132">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51ce3-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51ce3-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="51ce3-133">See also</span></span>

- <xref:System.Threading.ThreadPool.GetAvailableThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="51ce3-134">IHostThreadPoolManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="51ce3-134">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
