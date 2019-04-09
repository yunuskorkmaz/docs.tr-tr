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
ms.openlocfilehash: b4f16db1d35f8a0de1c755566e27b07bf9067dfe
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59129200"
---
# <a name="ihostthreadpoolmanagergetavailablethreads-method"></a><span data-ttu-id="0b985-102">IHostThreadPoolManager::GetAvailableThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0b985-102">IHostThreadPoolManager::GetAvailableThreads Method</span></span>
<span data-ttu-id="0b985-103">İş öğeleri şu anda işleme değil iş parçacığı havuzundaki iş parçacığı sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="0b985-103">Gets the number of threads in the thread pool that are not currently processing work items.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b985-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0b985-104">Syntax</span></span>  
  
```  
HRESULT GetAvailableThreads (  
    [out] DWORD *pdwAvailableWorkerThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0b985-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0b985-105">Parameters</span></span>  
 `pdwAvailableWorkerThreads`  
 <span data-ttu-id="0b985-106">[out] İş öğeleri şu anda işleme değil iş parçacığı havuzundaki iş parçacığı sayısını işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="0b985-106">[out] Pointer to the number of threads in the thread pool that are not currently processing work items.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0b985-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0b985-107">Return Value</span></span>  
  
|<span data-ttu-id="0b985-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0b985-108">HRESULT</span></span>|<span data-ttu-id="0b985-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0b985-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0b985-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="0b985-110">S_OK</span></span>|`GetAvailableThreads` <span data-ttu-id="0b985-111">başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="0b985-111">returned successfully.</span></span>|  
|<span data-ttu-id="0b985-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0b985-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0b985-113">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="0b985-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0b985-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0b985-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0b985-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="0b985-115">The call timed out.</span></span>|  
|<span data-ttu-id="0b985-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0b985-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0b985-117">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="0b985-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0b985-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0b985-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0b985-119">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="0b985-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0b985-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0b985-120">E_FAIL</span></span>|<span data-ttu-id="0b985-121">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="0b985-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0b985-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="0b985-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0b985-123">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="0b985-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="0b985-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="0b985-124">E_NOTIMPL</span></span>|<span data-ttu-id="0b985-125">Ana bilgisayar uygulaması sağlamaz `GetAvailableThreads`.</span><span class="sxs-lookup"><span data-stu-id="0b985-125">The host does not provide an implementation of `GetAvailableThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0b985-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0b985-126">Remarks</span></span>  
 <span data-ttu-id="0b985-127">Ana bilgisayar uygulaması sağlamıyorsa `GetAvailableThreads`, E_NOTIMPL bir HRESULT değerini döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="0b985-127">If the host does not provide an implementation of `GetAvailableThreads`, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b985-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0b985-128">Requirements</span></span>  
 <span data-ttu-id="0b985-129">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b985-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b985-130">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0b985-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0b985-131">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="0b985-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="0b985-132">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="0b985-132">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0b985-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0b985-133">See also</span></span>

- <xref:System.Threading.ThreadPool.GetAvailableThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="0b985-134">IHostThreadPoolManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0b985-134">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
