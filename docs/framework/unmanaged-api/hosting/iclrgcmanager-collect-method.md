---
title: "ICLRGCManager::Collect Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRGCManager.Collect
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRGCManager::Collect
helpviewer_keywords:
- ICLRGCManager::Collect method [.NET Framework hosting]
- Collect method, ICLRGCManager interface [.NET Framework hosting]
ms.assetid: 0c6cbbea-c27c-4695-bda3-17c1910d8ddb
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 96f99855654a3a86873ca4623d8617f74030938b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrgcmanagercollect-method"></a><span data-ttu-id="4a906-102">ICLRGCManager::Collect Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4a906-102">ICLRGCManager::Collect Method</span></span>
<span data-ttu-id="4a906-103">Çöp toplama belirtilen oluşturma için zorlar.</span><span class="sxs-lookup"><span data-stu-id="4a906-103">Forces a garbage collection for the specified generation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a906-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4a906-104">Syntax</span></span>  
  
```  
HRESULT Collect (  
    [in] LONG Generation  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4a906-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4a906-105">Parameters</span></span>  
 `Generation`  
 <span data-ttu-id="4a906-106">[in] Toplanacak oluşturma.</span><span class="sxs-lookup"><span data-stu-id="4a906-106">[in] The generation to collect.</span></span> <span data-ttu-id="4a906-107">-1 değeri, tüm nesli koleksiyonu zorlar.</span><span class="sxs-lookup"><span data-stu-id="4a906-107">A value of -1 forces a collection of all generations.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4a906-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="4a906-108">Return Value</span></span>  
  
|<span data-ttu-id="4a906-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4a906-109">HRESULT</span></span>|<span data-ttu-id="4a906-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4a906-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4a906-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="4a906-111">S_OK</span></span>|<span data-ttu-id="4a906-112">`Collect`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="4a906-112">`Collect` returned successfully.</span></span>|  
|<span data-ttu-id="4a906-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4a906-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4a906-114">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="4a906-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4a906-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4a906-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4a906-116">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="4a906-116">The call timed out.</span></span>|  
|<span data-ttu-id="4a906-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4a906-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4a906-118">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="4a906-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4a906-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4a906-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4a906-120">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="4a906-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4a906-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4a906-121">E_FAIL</span></span>|<span data-ttu-id="4a906-122">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="4a906-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4a906-123">CLR, artık bir yöntem E_FAIL döndükten sonra işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="4a906-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4a906-124">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="4a906-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4a906-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4a906-125">Remarks</span></span>  
 <span data-ttu-id="4a906-126">`Collect` Yöntemi geçerli durumuna bakılmaksızın bir koleksiyon gerçekleştirmek için CLR'nin atık toplayıcı zorlar.</span><span class="sxs-lookup"><span data-stu-id="4a906-126">The `Collect` method forces the CLR's garbage collector to perform a collection regardless of its current state.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a906-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4a906-127">Requirements</span></span>  
 <span data-ttu-id="4a906-128">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a906-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a906-129">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4a906-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4a906-130">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="4a906-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4a906-131">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a906-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a906-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4a906-132">See Also</span></span>  
 [<span data-ttu-id="4a906-133">Otomatik bellek yönetimi</span><span class="sxs-lookup"><span data-stu-id="4a906-133">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)  
 [<span data-ttu-id="4a906-134">Çöp toplama</span><span class="sxs-lookup"><span data-stu-id="4a906-134">Garbage Collection</span></span>](../../../../docs/standard/garbage-collection/index.md)  
 [<span data-ttu-id="4a906-135">Iclrcontrol arabirimi</span><span class="sxs-lookup"><span data-stu-id="4a906-135">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="4a906-136">Iclrgcmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="4a906-136">ICLRGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)  
 [<span data-ttu-id="4a906-137">CLR barındırma arabirimleri</span><span class="sxs-lookup"><span data-stu-id="4a906-137">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 [<span data-ttu-id="4a906-138">Barındırma arabirimleri</span><span class="sxs-lookup"><span data-stu-id="4a906-138">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="4a906-139">Barındırma</span><span class="sxs-lookup"><span data-stu-id="4a906-139">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
