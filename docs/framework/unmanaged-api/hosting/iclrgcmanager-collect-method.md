---
title: ICLRGCManager::Collect Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRGCManager.Collect
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager::Collect
helpviewer_keywords:
- ICLRGCManager::Collect method [.NET Framework hosting]
- Collect method, ICLRGCManager interface [.NET Framework hosting]
ms.assetid: 0c6cbbea-c27c-4695-bda3-17c1910d8ddb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1746527a2667676dfeab89e72874204460bcd33c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59126679"
---
# <a name="iclrgcmanagercollect-method"></a><span data-ttu-id="2b2a1-102">ICLRGCManager::Collect Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2b2a1-102">ICLRGCManager::Collect Method</span></span>
<span data-ttu-id="2b2a1-103">Bir çöp toplama işlemi için belirtilen oluşturmanın zorlar.</span><span class="sxs-lookup"><span data-stu-id="2b2a1-103">Forces a garbage collection for the specified generation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b2a1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2b2a1-104">Syntax</span></span>  
  
```  
HRESULT Collect (  
    [in] LONG Generation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2b2a1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2b2a1-105">Parameters</span></span>  
 `Generation`  
 <span data-ttu-id="2b2a1-106">[in] Toplanacak oluşturma.</span><span class="sxs-lookup"><span data-stu-id="2b2a1-106">[in] The generation to collect.</span></span> <span data-ttu-id="2b2a1-107">-1 değeri, tüm nesillerdeki koleksiyonunu zorlar.</span><span class="sxs-lookup"><span data-stu-id="2b2a1-107">A value of -1 forces a collection of all generations.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2b2a1-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2b2a1-108">Return Value</span></span>  
  
|<span data-ttu-id="2b2a1-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2b2a1-109">HRESULT</span></span>|<span data-ttu-id="2b2a1-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2b2a1-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2b2a1-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="2b2a1-111">S_OK</span></span>|<span data-ttu-id="2b2a1-112">`Collect` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="2b2a1-112">`Collect` returned successfully.</span></span>|  
|<span data-ttu-id="2b2a1-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2b2a1-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2b2a1-114">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="2b2a1-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2b2a1-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2b2a1-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2b2a1-116">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="2b2a1-116">The call timed out.</span></span>|  
|<span data-ttu-id="2b2a1-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2b2a1-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2b2a1-118">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="2b2a1-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2b2a1-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2b2a1-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2b2a1-120">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="2b2a1-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2b2a1-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2b2a1-121">E_FAIL</span></span>|<span data-ttu-id="2b2a1-122">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="2b2a1-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2b2a1-123">CLR, artık E_FAIL bir yöntemin dönüşünün ardından, işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="2b2a1-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2b2a1-124">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="2b2a1-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2b2a1-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2b2a1-125">Remarks</span></span>  
 <span data-ttu-id="2b2a1-126">`Collect` Yöntem CLR'nin çöp toplayıcı, bir koleksiyon geçerli durumunda ne olursa olsun gerçekleştirmek için zorlar.</span><span class="sxs-lookup"><span data-stu-id="2b2a1-126">The `Collect` method forces the CLR's garbage collector to perform a collection regardless of its current state.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b2a1-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2b2a1-127">Requirements</span></span>  
 <span data-ttu-id="2b2a1-128">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2b2a1-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b2a1-129">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2b2a1-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2b2a1-130">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="2b2a1-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2b2a1-131">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b2a1-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b2a1-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2b2a1-132">See also</span></span>

- [<span data-ttu-id="2b2a1-133">Otomatik Bellek Yönetimi</span><span class="sxs-lookup"><span data-stu-id="2b2a1-133">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)
- [<span data-ttu-id="2b2a1-134">Atık Toplama</span><span class="sxs-lookup"><span data-stu-id="2b2a1-134">Garbage Collection</span></span>](../../../../docs/standard/garbage-collection/index.md)
- [<span data-ttu-id="2b2a1-135">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2b2a1-135">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="2b2a1-136">ICLRGCManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2b2a1-136">ICLRGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)
- [<span data-ttu-id="2b2a1-137">CLR Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="2b2a1-137">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)
- [<span data-ttu-id="2b2a1-138">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="2b2a1-138">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="2b2a1-139">Barındırma</span><span class="sxs-lookup"><span data-stu-id="2b2a1-139">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
