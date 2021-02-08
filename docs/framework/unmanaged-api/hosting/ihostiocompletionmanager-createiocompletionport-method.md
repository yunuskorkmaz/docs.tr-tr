---
description: 'Şu konuda daha fazla bilgi edinin: ıhostiocompletionmanager:: CreateIoCompletionPort Yöntemi'
title: IHostIoCompletionManager::CreateIoCompletionPort Yöntemi
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.CreateIoCompletionPort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::CreateIoCompletionPort
helpviewer_keywords:
- IHostIoCompletionManager::CreateIoCompletionPort method [.NET Framework hosting]
- CreateIoCompletionPort method [.NET Framework hosting]
ms.assetid: 907a2b43-68db-44a7-acac-89e792e7bb3c
topic_type:
- apiref
ms.openlocfilehash: da4cd595e84c341eb15837ff97f4ba23cac23210
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789443"
---
# <a name="ihostiocompletionmanagercreateiocompletionport-method"></a><span data-ttu-id="67c20-103">IHostIoCompletionManager::CreateIoCompletionPort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="67c20-103">IHostIoCompletionManager::CreateIoCompletionPort Method</span></span>

<span data-ttu-id="67c20-104">Konağın yeni bir g/ç tamamlama bağlantı noktası oluşturmasını ister.</span><span class="sxs-lookup"><span data-stu-id="67c20-104">Requests that the host create a new I/O completion port.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67c20-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="67c20-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateIoCompletionPort (  
    [out] HANDLE *phPort  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="67c20-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="67c20-106">Parameters</span></span>  

 `phPort`  
 <span data-ttu-id="67c20-107">dışı Yeni oluşturulan g/ç tamamlama bağlantı noktasına yönelik bir tanıtıcı işaretçisi veya bağlantı noktası oluşturuoluşturulamadığı 0 (sıfır).</span><span class="sxs-lookup"><span data-stu-id="67c20-107">[out] A pointer to a handle to the newly created I/O completion port, or 0 (zero), if the port could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="67c20-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="67c20-108">Return Value</span></span>  
  
|<span data-ttu-id="67c20-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="67c20-109">HRESULT</span></span>|<span data-ttu-id="67c20-110">Description</span><span class="sxs-lookup"><span data-stu-id="67c20-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="67c20-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="67c20-111">S_OK</span></span>|<span data-ttu-id="67c20-112">`CreateIoCompletionPort` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="67c20-112">`CreateIoCompletionPort` returned successfully.</span></span>|  
|<span data-ttu-id="67c20-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="67c20-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="67c20-114">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="67c20-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="67c20-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="67c20-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="67c20-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="67c20-116">The call timed out.</span></span>|  
|<span data-ttu-id="67c20-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="67c20-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="67c20-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="67c20-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="67c20-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="67c20-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="67c20-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="67c20-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="67c20-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="67c20-121">E_FAIL</span></span>|<span data-ttu-id="67c20-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="67c20-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="67c20-123">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="67c20-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="67c20-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="67c20-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="67c20-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="67c20-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="67c20-126">İstenen kaynağı ayırmak için yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="67c20-126">Not enough memory was available to allocate the requested resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="67c20-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="67c20-127">Remarks</span></span>  

 <span data-ttu-id="67c20-128">CLR, `CreateIoCompletionPort` konağın yeni bir g/ç tamamlama bağlantı noktası oluşturmasını istemek için yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="67c20-128">The CLR calls the `CreateIoCompletionPort` method to request that the host create a new I/O completion port.</span></span> <span data-ttu-id="67c20-129">[Ihostiocompletionmanager:: bind](ihostiocompletionmanager-bind-method.md) yöntemine yapılan bir çağrı aracılığıyla g/ç işlemlerini bu bağlantı noktasına bağlar.</span><span class="sxs-lookup"><span data-stu-id="67c20-129">It binds I/O operations to this port through a call to the [IHostIoCompletionManager::Bind](ihostiocompletionmanager-bind-method.md) method.</span></span> <span data-ttu-id="67c20-130">Ana bilgisayar, [ıclriocompletionmanager:: OnFinish](iclriocompletionmanager-oncomplete-method.md)ÇAĞıRARAK durumu clr 'ye geri bildirir.</span><span class="sxs-lookup"><span data-stu-id="67c20-130">The host reports status back to the CLR by calling [ICLRIoCompletionManager::OnComplete](iclriocompletionmanager-oncomplete-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67c20-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="67c20-131">Requirements</span></span>  

 <span data-ttu-id="67c20-132">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="67c20-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67c20-133">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="67c20-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="67c20-134">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="67c20-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="67c20-135">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67c20-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67c20-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="67c20-136">See also</span></span>

- [<span data-ttu-id="67c20-137">ICLRIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="67c20-137">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="67c20-138">IHostIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="67c20-138">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
