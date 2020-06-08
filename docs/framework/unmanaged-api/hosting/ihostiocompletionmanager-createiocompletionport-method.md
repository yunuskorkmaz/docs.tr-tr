---
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
ms.openlocfilehash: 240712296254e02f4d268a00e1c15ef34f4519f1
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501562"
---
# <a name="ihostiocompletionmanagercreateiocompletionport-method"></a><span data-ttu-id="79175-102">IHostIoCompletionManager::CreateIoCompletionPort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="79175-102">IHostIoCompletionManager::CreateIoCompletionPort Method</span></span>
<span data-ttu-id="79175-103">Konağın yeni bir g/ç tamamlama bağlantı noktası oluşturmasını ister.</span><span class="sxs-lookup"><span data-stu-id="79175-103">Requests that the host create a new I/O completion port.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79175-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="79175-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateIoCompletionPort (  
    [out] HANDLE *phPort  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="79175-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="79175-105">Parameters</span></span>  
 `phPort`  
 <span data-ttu-id="79175-106">dışı Yeni oluşturulan g/ç tamamlama bağlantı noktasına yönelik bir tanıtıcı işaretçisi veya bağlantı noktası oluşturuoluşturulamadığı 0 (sıfır).</span><span class="sxs-lookup"><span data-stu-id="79175-106">[out] A pointer to a handle to the newly created I/O completion port, or 0 (zero), if the port could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="79175-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="79175-107">Return Value</span></span>  
  
|<span data-ttu-id="79175-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="79175-108">HRESULT</span></span>|<span data-ttu-id="79175-109">Description</span><span class="sxs-lookup"><span data-stu-id="79175-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="79175-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="79175-110">S_OK</span></span>|<span data-ttu-id="79175-111">`CreateIoCompletionPort`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="79175-111">`CreateIoCompletionPort` returned successfully.</span></span>|  
|<span data-ttu-id="79175-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="79175-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="79175-113">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="79175-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="79175-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="79175-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="79175-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="79175-115">The call timed out.</span></span>|  
|<span data-ttu-id="79175-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="79175-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="79175-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="79175-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="79175-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="79175-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="79175-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="79175-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="79175-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="79175-120">E_FAIL</span></span>|<span data-ttu-id="79175-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="79175-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="79175-122">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="79175-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="79175-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="79175-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="79175-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="79175-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="79175-125">İstenen kaynağı ayırmak için yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="79175-125">Not enough memory was available to allocate the requested resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="79175-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="79175-126">Remarks</span></span>  
 <span data-ttu-id="79175-127">CLR, `CreateIoCompletionPort` konağın yeni bir g/ç tamamlama bağlantı noktası oluşturmasını istemek için yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="79175-127">The CLR calls the `CreateIoCompletionPort` method to request that the host create a new I/O completion port.</span></span> <span data-ttu-id="79175-128">[Ihostiocompletionmanager:: bind](ihostiocompletionmanager-bind-method.md) yöntemine yapılan bir çağrı aracılığıyla g/ç işlemlerini bu bağlantı noktasına bağlar.</span><span class="sxs-lookup"><span data-stu-id="79175-128">It binds I/O operations to this port through a call to the [IHostIoCompletionManager::Bind](ihostiocompletionmanager-bind-method.md) method.</span></span> <span data-ttu-id="79175-129">Ana bilgisayar, [ıclriocompletionmanager:: OnFinish](iclriocompletionmanager-oncomplete-method.md)ÇAĞıRARAK durumu clr 'ye geri bildirir.</span><span class="sxs-lookup"><span data-stu-id="79175-129">The host reports status back to the CLR by calling [ICLRIoCompletionManager::OnComplete](iclriocompletionmanager-oncomplete-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79175-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="79175-130">Requirements</span></span>  
 <span data-ttu-id="79175-131">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="79175-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79175-132">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="79175-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="79175-133">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="79175-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="79175-134">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79175-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79175-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="79175-135">See also</span></span>

- [<span data-ttu-id="79175-136">ICLRIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="79175-136">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="79175-137">IHostIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="79175-137">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
