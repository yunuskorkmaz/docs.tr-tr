---
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
ms.openlocfilehash: 5e2e49b4c993e127a31b54d40f721e0714198780
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804771"
---
# <a name="ihostiocompletionmanagercloseiocompletionport-method"></a><span data-ttu-id="35751-102">IHostIoCompletionManager::CloseIoCompletionPort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="35751-102">IHostIoCompletionManager::CloseIoCompletionPort Method</span></span>
<span data-ttu-id="35751-103">Konağın bir [CreateIoCompletionPort](ihostiocompletionmanager-createiocompletionport-method.md)daha önceki çağrısıyla açılan bir bağlantı noktasını kapatmasını ister.</span><span class="sxs-lookup"><span data-stu-id="35751-103">Requests that the host close a port that was opened through an earlier call to [CreateIoCompletionPort](ihostiocompletionmanager-createiocompletionport-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35751-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="35751-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseIoCompletionPort (  
    [in] HANDLE hPort  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="35751-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="35751-105">Parameters</span></span>  
 `hPort`  
 <span data-ttu-id="35751-106">'ndaki Kapatılacak bağlantı noktasının tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="35751-106">[in] The handle of the port to close.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="35751-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="35751-107">Return Value</span></span>  
  
|<span data-ttu-id="35751-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="35751-108">HRESULT</span></span>|<span data-ttu-id="35751-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="35751-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="35751-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="35751-110">S_OK</span></span>|<span data-ttu-id="35751-111">`CloseIoCompletionPort`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="35751-111">`CloseIoCompletionPort` returned successfully.</span></span>|  
|<span data-ttu-id="35751-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="35751-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="35751-113">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="35751-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="35751-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="35751-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="35751-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="35751-115">The call timed out.</span></span>|  
|<span data-ttu-id="35751-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="35751-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="35751-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="35751-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="35751-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="35751-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="35751-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="35751-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="35751-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="35751-120">E_FAIL</span></span>|<span data-ttu-id="35751-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="35751-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="35751-122">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="35751-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="35751-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="35751-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="35751-124">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="35751-124">E_INVALIDARG</span></span>|<span data-ttu-id="35751-125">Geçersiz bir bağlantı noktası tanıtıcısı geçildi.</span><span class="sxs-lookup"><span data-stu-id="35751-125">An invalid port handle was passed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="35751-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="35751-126">Remarks</span></span>  
 <span data-ttu-id="35751-127">`hPort`daha önceki çağrısıyla oluşturulmuş bir bağlantı noktasının tanıtıcısı olmalıdır `CreateIoCompletionPort` .</span><span class="sxs-lookup"><span data-stu-id="35751-127">`hPort` must be a handle to a port that was created by an earlier call to `CreateIoCompletionPort`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35751-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="35751-128">Requirements</span></span>  
 <span data-ttu-id="35751-129">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="35751-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35751-130">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="35751-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="35751-131">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="35751-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="35751-132">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="35751-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35751-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="35751-133">See also</span></span>

- [<span data-ttu-id="35751-134">ICLRIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="35751-134">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="35751-135">IHostIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="35751-135">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
