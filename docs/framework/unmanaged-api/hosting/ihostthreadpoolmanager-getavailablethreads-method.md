---
description: ': IHostThreadPoolManager:: GetAvailableThreads yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 95ecaa5757442bb384d303c1f8dafa342bd62f5e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789341"
---
# <a name="ihostthreadpoolmanagergetavailablethreads-method"></a><span data-ttu-id="4cf37-103">IHostThreadPoolManager::GetAvailableThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4cf37-103">IHostThreadPoolManager::GetAvailableThreads Method</span></span>

<span data-ttu-id="4cf37-104">İş öğelerini işlemeyen iş parçacığı havuzundaki iş parçacığı sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="4cf37-104">Gets the number of threads in the thread pool that are not currently processing work items.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4cf37-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4cf37-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAvailableThreads (  
    [out] DWORD *pdwAvailableWorkerThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4cf37-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4cf37-106">Parameters</span></span>  

 `pdwAvailableWorkerThreads`  
 <span data-ttu-id="4cf37-107">dışı İş öğelerinin Şu anda işlemeyen iş parçacığı havuzundaki iş parçacığı sayısına yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4cf37-107">[out] Pointer to the number of threads in the thread pool that are not currently processing work items.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4cf37-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="4cf37-108">Return Value</span></span>  
  
|<span data-ttu-id="4cf37-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4cf37-109">HRESULT</span></span>|<span data-ttu-id="4cf37-110">Description</span><span class="sxs-lookup"><span data-stu-id="4cf37-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4cf37-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="4cf37-111">S_OK</span></span>|<span data-ttu-id="4cf37-112">`GetAvailableThreads` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="4cf37-112">`GetAvailableThreads` returned successfully.</span></span>|  
|<span data-ttu-id="4cf37-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4cf37-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4cf37-114">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="4cf37-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4cf37-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4cf37-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4cf37-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="4cf37-116">The call timed out.</span></span>|  
|<span data-ttu-id="4cf37-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4cf37-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4cf37-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="4cf37-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4cf37-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4cf37-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4cf37-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="4cf37-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4cf37-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4cf37-121">E_FAIL</span></span>|<span data-ttu-id="4cf37-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="4cf37-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4cf37-123">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="4cf37-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4cf37-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="4cf37-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="4cf37-125">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="4cf37-125">E_NOTIMPL</span></span>|<span data-ttu-id="4cf37-126">Konak, uygulamasının bir uygulamasını sağlamaz `GetAvailableThreads` .</span><span class="sxs-lookup"><span data-stu-id="4cf37-126">The host does not provide an implementation of `GetAvailableThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4cf37-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4cf37-127">Remarks</span></span>  

 <span data-ttu-id="4cf37-128">Konak uygulamasının bir uygulamasını sağlamıyorsa `GetAvailableThreads` , E_NOTIMPL BIR HRESULT değeri döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="4cf37-128">If the host does not provide an implementation of `GetAvailableThreads`, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4cf37-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4cf37-129">Requirements</span></span>  

 <span data-ttu-id="4cf37-130">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4cf37-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4cf37-131">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="4cf37-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4cf37-132">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="4cf37-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4cf37-133">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4cf37-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cf37-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4cf37-134">See also</span></span>

- <xref:System.Threading.ThreadPool.GetAvailableThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="4cf37-135">IHostThreadPoolManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4cf37-135">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)
