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
ms.openlocfilehash: 9b448892a58dd120fd0f30f2b61be59e579b629a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54651415"
---
# <a name="iclrgcmanagercollect-method"></a><span data-ttu-id="ecf86-102">ICLRGCManager::Collect Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ecf86-102">ICLRGCManager::Collect Method</span></span>
<span data-ttu-id="ecf86-103">Bir çöp toplama işlemi için belirtilen oluşturmanın zorlar.</span><span class="sxs-lookup"><span data-stu-id="ecf86-103">Forces a garbage collection for the specified generation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecf86-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ecf86-104">Syntax</span></span>  
  
```  
HRESULT Collect (  
    [in] LONG Generation  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ecf86-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ecf86-105">Parameters</span></span>  
 `Generation`  
 <span data-ttu-id="ecf86-106">[in] Toplanacak oluşturma.</span><span class="sxs-lookup"><span data-stu-id="ecf86-106">[in] The generation to collect.</span></span> <span data-ttu-id="ecf86-107">-1 değeri, tüm nesillerdeki koleksiyonunu zorlar.</span><span class="sxs-lookup"><span data-stu-id="ecf86-107">A value of -1 forces a collection of all generations.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ecf86-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ecf86-108">Return Value</span></span>  
  
|<span data-ttu-id="ecf86-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ecf86-109">HRESULT</span></span>|<span data-ttu-id="ecf86-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ecf86-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ecf86-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="ecf86-111">S_OK</span></span>|<span data-ttu-id="ecf86-112">`Collect` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="ecf86-112">`Collect` returned successfully.</span></span>|  
|<span data-ttu-id="ecf86-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ecf86-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ecf86-114">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="ecf86-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ecf86-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ecf86-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ecf86-116">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="ecf86-116">The call timed out.</span></span>|  
|<span data-ttu-id="ecf86-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ecf86-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ecf86-118">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="ecf86-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ecf86-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ecf86-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ecf86-120">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="ecf86-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ecf86-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ecf86-121">E_FAIL</span></span>|<span data-ttu-id="ecf86-122">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="ecf86-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ecf86-123">CLR, artık E_FAIL bir yöntemin dönüşünün ardından, işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="ecf86-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ecf86-124">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="ecf86-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ecf86-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ecf86-125">Remarks</span></span>  
 <span data-ttu-id="ecf86-126">`Collect` Yöntem CLR'nin çöp toplayıcı, bir koleksiyon geçerli durumunda ne olursa olsun gerçekleştirmek için zorlar.</span><span class="sxs-lookup"><span data-stu-id="ecf86-126">The `Collect` method forces the CLR's garbage collector to perform a collection regardless of its current state.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ecf86-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ecf86-127">Requirements</span></span>  
 <span data-ttu-id="ecf86-128">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ecf86-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ecf86-129">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ecf86-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ecf86-130">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="ecf86-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ecf86-131">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ecf86-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecf86-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ecf86-132">See also</span></span>
- [<span data-ttu-id="ecf86-133">Otomatik Bellek Yönetimi</span><span class="sxs-lookup"><span data-stu-id="ecf86-133">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)
- [<span data-ttu-id="ecf86-134">Atık Toplama</span><span class="sxs-lookup"><span data-stu-id="ecf86-134">Garbage Collection</span></span>](../../../../docs/standard/garbage-collection/index.md)
- [<span data-ttu-id="ecf86-135">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ecf86-135">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="ecf86-136">ICLRGCManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ecf86-136">ICLRGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)
- [<span data-ttu-id="ecf86-137">CLR Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ecf86-137">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)
- [<span data-ttu-id="ecf86-138">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ecf86-138">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="ecf86-139">Barındırma</span><span class="sxs-lookup"><span data-stu-id="ecf86-139">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
