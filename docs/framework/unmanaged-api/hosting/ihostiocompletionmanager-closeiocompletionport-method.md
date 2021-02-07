---
description: 'Şu konuda daha fazla bilgi edinin: ıhostiocompletionmanager:: CloseIoCompletionPort Yöntemi'
title: IHostIoCompletionManager::CloseIoCompletionPort Yöntemi
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.CloseIoCompletionPort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::CloseIoCompletionPort
helpviewer_keywords:
- IHostIoCompletionManager::CloseIoCompletionPort method [.NET Framework hosting]
- CloseIoCompletionPort method [.NET Framework hosting]
ms.assetid: e86ad7be-3758-498a-a972-5522d69dfbb3
topic_type:
- apiref
ms.openlocfilehash: 987b9f4e0fa22fa977fa1b14c77c8c0381e3e399
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99728515"
---
# <a name="ihostiocompletionmanagercloseiocompletionport-method"></a><span data-ttu-id="c947d-103">IHostIoCompletionManager::CloseIoCompletionPort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c947d-103">IHostIoCompletionManager::CloseIoCompletionPort Method</span></span>

<span data-ttu-id="c947d-104">Konağın bir [CreateIoCompletionPort](ihostiocompletionmanager-createiocompletionport-method.md)daha önceki çağrısıyla açılan bir bağlantı noktasını kapatmasını ister.</span><span class="sxs-lookup"><span data-stu-id="c947d-104">Requests that the host close a port that was opened through an earlier call to [CreateIoCompletionPort](ihostiocompletionmanager-createiocompletionport-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c947d-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c947d-105">Syntax</span></span>  
  
```cpp  
HRESULT CloseIoCompletionPort (  
    [in] HANDLE hPort  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c947d-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c947d-106">Parameters</span></span>  

 `hPort`  
 <span data-ttu-id="c947d-107">'ndaki Kapatılacak bağlantı noktasının tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="c947d-107">[in] The handle of the port to close.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c947d-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c947d-108">Return Value</span></span>  
  
|<span data-ttu-id="c947d-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c947d-109">HRESULT</span></span>|<span data-ttu-id="c947d-110">Description</span><span class="sxs-lookup"><span data-stu-id="c947d-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c947d-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="c947d-111">S_OK</span></span>|<span data-ttu-id="c947d-112">`CloseIoCompletionPort` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="c947d-112">`CloseIoCompletionPort` returned successfully.</span></span>|  
|<span data-ttu-id="c947d-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c947d-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c947d-114">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="c947d-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c947d-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c947d-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c947d-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="c947d-116">The call timed out.</span></span>|  
|<span data-ttu-id="c947d-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c947d-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c947d-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="c947d-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c947d-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c947d-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c947d-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="c947d-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c947d-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c947d-121">E_FAIL</span></span>|<span data-ttu-id="c947d-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="c947d-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c947d-123">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="c947d-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c947d-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="c947d-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="c947d-125">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="c947d-125">E_INVALIDARG</span></span>|<span data-ttu-id="c947d-126">Geçersiz bir bağlantı noktası tanıtıcısı geçildi.</span><span class="sxs-lookup"><span data-stu-id="c947d-126">An invalid port handle was passed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c947d-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c947d-127">Remarks</span></span>  

 <span data-ttu-id="c947d-128">`hPort` daha önceki çağrısıyla oluşturulmuş bir bağlantı noktasının tanıtıcısı olmalıdır `CreateIoCompletionPort` .</span><span class="sxs-lookup"><span data-stu-id="c947d-128">`hPort` must be a handle to a port that was created by an earlier call to `CreateIoCompletionPort`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c947d-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c947d-129">Requirements</span></span>  

 <span data-ttu-id="c947d-130">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c947d-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c947d-131">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c947d-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c947d-132">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="c947d-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c947d-133">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c947d-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c947d-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c947d-134">See also</span></span>

- [<span data-ttu-id="c947d-135">ICLRIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c947d-135">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="c947d-136">IHostIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c947d-136">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
