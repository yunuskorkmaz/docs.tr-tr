---
title: ICLRDebugManager::IsDebuggerAttached Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRDebugManager.IsDebuggerAttached
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::IsDebuggerAttached
helpviewer_keywords:
- IsDebuggerAttached method, ICLRDebugManager interface [.NET Framework hosting]
- ICLRDebugManager::IsDebuggerAttached method [.NET Framework hosting]
ms.assetid: 2f105fe0-f52d-49c5-bda5-583fb27e3aa6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1d6c071b3ac68cb38fc85aff65fff49a71ea4275
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59095393"
---
# <a name="iclrdebugmanagerisdebuggerattached-method"></a><span data-ttu-id="72500-102">ICLRDebugManager::IsDebuggerAttached Yöntemi</span><span class="sxs-lookup"><span data-stu-id="72500-102">ICLRDebugManager::IsDebuggerAttached Method</span></span>
<span data-ttu-id="72500-103">Bir hata ayıklayıcı işleme ekli olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="72500-103">Gets a value that indicates whether a debugger is attached to the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72500-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="72500-104">Syntax</span></span>  
  
```  
HRESULT IsDebuggerAttached (  
    [out] BOOL *pbAttached  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="72500-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="72500-105">Parameters</span></span>  
 `pbAttached`  
 <span data-ttu-id="72500-106">[out] `true` işlemine bağlı; Aksi takdirde bir hata ayıklayıcı, `false`.</span><span class="sxs-lookup"><span data-stu-id="72500-106">[out] `true` if a debugger is attached to the process; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="72500-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="72500-107">Return Value</span></span>  
  
|<span data-ttu-id="72500-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="72500-108">HRESULT</span></span>|<span data-ttu-id="72500-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="72500-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="72500-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="72500-110">S_OK</span></span>|<span data-ttu-id="72500-111">`IsDebuggerAttached` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="72500-111">`IsDebuggerAttached` returned successfully.</span></span>|  
|<span data-ttu-id="72500-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="72500-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="72500-113">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="72500-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="72500-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="72500-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="72500-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="72500-115">The call timed out.</span></span>|  
|<span data-ttu-id="72500-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="72500-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="72500-117">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="72500-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="72500-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="72500-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="72500-119">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="72500-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="72500-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="72500-120">E_FAIL</span></span>|<span data-ttu-id="72500-121">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="72500-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="72500-122">CLR, artık E_FAIL bir yöntemin dönüşünün ardından, işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="72500-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="72500-123">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="72500-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="72500-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="72500-124">Remarks</span></span>  
 <span data-ttu-id="72500-125">`IsDebuggerAttached` bir hata ayıklayıcı işleme ekli olup olmadığını belirlemek için CLR sorgulamak için ana sağlar.</span><span class="sxs-lookup"><span data-stu-id="72500-125">`IsDebuggerAttached` allows the host to query the CLR to determine whether a debugger is attached to the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72500-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="72500-126">Requirements</span></span>  
 <span data-ttu-id="72500-127">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72500-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72500-128">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="72500-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="72500-129">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="72500-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="72500-130">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72500-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72500-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="72500-131">See also</span></span>

- [<span data-ttu-id="72500-132">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="72500-132">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="72500-133">ICLRDebugManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="72500-133">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)
- [<span data-ttu-id="72500-134">IHostControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="72500-134">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
