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
ms.openlocfilehash: 6f9eb28ea1a60991d047494336035aaf239b9edd
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57478602"
---
# <a name="ihostthreadpoolmanagergetavailablethreads-method"></a><span data-ttu-id="cb9fd-102">IHostThreadPoolManager::GetAvailableThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cb9fd-102">IHostThreadPoolManager::GetAvailableThreads Method</span></span>
<span data-ttu-id="cb9fd-103">İş öğeleri şu anda işleme değil iş parçacığı havuzundaki iş parçacığı sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="cb9fd-103">Gets the number of threads in the thread pool that are not currently processing work items.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb9fd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cb9fd-104">Syntax</span></span>  
  
```  
HRESULT GetAvailableThreads (  
    [out] DWORD *pdwAvailableWorkerThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cb9fd-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cb9fd-105">Parameters</span></span>  
 `pdwAvailableWorkerThreads`  
 <span data-ttu-id="cb9fd-106">[out] İş öğeleri şu anda işleme değil iş parçacığı havuzundaki iş parçacığı sayısını işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="cb9fd-106">[out] Pointer to the number of threads in the thread pool that are not currently processing work items.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cb9fd-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="cb9fd-107">Return Value</span></span>  
  
|<span data-ttu-id="cb9fd-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cb9fd-108">HRESULT</span></span>|<span data-ttu-id="cb9fd-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cb9fd-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cb9fd-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="cb9fd-110">S_OK</span></span>|<span data-ttu-id="cb9fd-111">`GetAvailableThreads` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="cb9fd-111">`GetAvailableThreads` returned successfully.</span></span>|  
|<span data-ttu-id="cb9fd-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="cb9fd-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="cb9fd-113">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="cb9fd-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="cb9fd-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="cb9fd-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="cb9fd-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="cb9fd-115">The call timed out.</span></span>|  
|<span data-ttu-id="cb9fd-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="cb9fd-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="cb9fd-117">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="cb9fd-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="cb9fd-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="cb9fd-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="cb9fd-119">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="cb9fd-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="cb9fd-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="cb9fd-120">E_FAIL</span></span>|<span data-ttu-id="cb9fd-121">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="cb9fd-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="cb9fd-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="cb9fd-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="cb9fd-123">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="cb9fd-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="cb9fd-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="cb9fd-124">E_NOTIMPL</span></span>|<span data-ttu-id="cb9fd-125">Ana bilgisayar uygulaması sağlamaz `GetAvailableThreads`.</span><span class="sxs-lookup"><span data-stu-id="cb9fd-125">The host does not provide an implementation of `GetAvailableThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cb9fd-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cb9fd-126">Remarks</span></span>  
 <span data-ttu-id="cb9fd-127">Ana bilgisayar uygulaması sağlamıyorsa `GetAvailableThreads`, E_NOTIMPL bir HRESULT değerini döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="cb9fd-127">If the host does not provide an implementation of `GetAvailableThreads`, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb9fd-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cb9fd-128">Requirements</span></span>  
 <span data-ttu-id="cb9fd-129">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb9fd-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb9fd-130">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="cb9fd-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cb9fd-131">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="cb9fd-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cb9fd-132">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb9fd-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb9fd-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cb9fd-133">See also</span></span>
- <xref:System.Threading.ThreadPool.GetAvailableThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="cb9fd-134">IHostThreadPoolManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cb9fd-134">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
