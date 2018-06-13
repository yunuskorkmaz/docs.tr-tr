---
title: ICLRGCManager2::SetGCStartupLimitsEx Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRGCManager2.SetGCStartupLimitsEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager2::SetCLRGCStartupLimitsEx
helpviewer_keywords:
- ICLRGCManager2::SetGCStartupLimitsEx method [.NET Framework hosting]
- SetGCStartupLimitsEx method, ICLRGCManager2 interface [.NET Framework hosting]
ms.assetid: 6c3a08a9-5d65-48d4-8bbf-2a86ed7d356a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 65fbf0bf42f7312ad80b61bf452b62a4d0ff93c9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436130"
---
# <a name="iclrgcmanager2setgcstartuplimitsex-method"></a><span data-ttu-id="453c9-102">ICLRGCManager2::SetGCStartupLimitsEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="453c9-102">ICLRGCManager2::SetGCStartupLimitsEx Method</span></span>
<span data-ttu-id="453c9-103">Çöp toplama kesim boyutunu ve en büyük boyutu 0 atık toplama sistemin nesil ayarlar.</span><span class="sxs-lookup"><span data-stu-id="453c9-103">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="453c9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="453c9-104">Syntax</span></span>  
  
```  
HRESULT SetGCStartupLimitsEx (  
    [in] SIZE_T SegmentSize,   
    [in] SIZE_T MaxGen0Size  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="453c9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="453c9-105">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="453c9-106">[in] Çöp toplama kesim belirtilen boyutu.</span><span class="sxs-lookup"><span data-stu-id="453c9-106">[in] The specified size of a garbage collection segment.</span></span>  
  
 <span data-ttu-id="453c9-107">Minimum kesim boyutu 4 MB'tır.</span><span class="sxs-lookup"><span data-stu-id="453c9-107">The minimum segment size is 4 MB.</span></span> <span data-ttu-id="453c9-108">Kesimleri artan aralıklarla 1 MB veya daha büyük olabilir.</span><span class="sxs-lookup"><span data-stu-id="453c9-108">Segments can be increased in increments of 1 MB or larger.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="453c9-109">[in] 0 oluşturma için belirtilen en büyük boyutu.</span><span class="sxs-lookup"><span data-stu-id="453c9-109">[in] The specified maximum size for generation 0.</span></span>  
  
 <span data-ttu-id="453c9-110">Minimum kuşak 0 boyutu 64 KB'tır.</span><span class="sxs-lookup"><span data-stu-id="453c9-110">The minimum generation 0 size is 64 KB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="453c9-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="453c9-111">Return Value</span></span>  
  
|<span data-ttu-id="453c9-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="453c9-112">HRESULT</span></span>|<span data-ttu-id="453c9-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="453c9-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="453c9-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="453c9-114">S_OK</span></span>|<span data-ttu-id="453c9-115">`SetGCStartupLimitsEx` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="453c9-115">`SetGCStartupLimitsEx` returned successfully.</span></span>|  
|<span data-ttu-id="453c9-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="453c9-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="453c9-117">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="453c9-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="453c9-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="453c9-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="453c9-119">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="453c9-119">The call timed out.</span></span>|  
|<span data-ttu-id="453c9-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="453c9-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="453c9-121">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="453c9-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="453c9-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="453c9-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="453c9-123">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="453c9-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="453c9-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="453c9-124">E_FAIL</span></span>|<span data-ttu-id="453c9-125">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="453c9-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="453c9-126">CLR, artık bir yöntem E_FAIL döndükten sonra işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="453c9-126">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="453c9-127">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="453c9-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="453c9-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="453c9-128">Remarks</span></span>  
 <span data-ttu-id="453c9-129">Değerleri, `SetGCStartupLimitsEx` kümeleri yalnızca ana başlatılmadan önce belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="453c9-129">The values that `SetGCStartupLimitsEx` sets can be specified only before the host is started.</span></span> <span data-ttu-id="453c9-130">Daha sonra çağrılar `SetGCStartupLimitsEx` göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="453c9-130">Later calls to `SetGCStartupLimitsEx` are ignored.</span></span>  
  
 <span data-ttu-id="453c9-131">Her iki parametre diğer etkilemeden ayarlamak için değiştirmek istemiyorsanız parametresi için 0 (sıfır) belirtin.</span><span class="sxs-lookup"><span data-stu-id="453c9-131">To set either parameter without affecting the other, specify 0 (zero) for the parameter you don't want to change.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="453c9-132">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="453c9-132">Requirements</span></span>  
 <span data-ttu-id="453c9-133">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="453c9-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="453c9-134">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="453c9-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="453c9-135">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="453c9-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="453c9-136">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="453c9-136">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="453c9-137">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="453c9-137">See Also</span></span>  
 [<span data-ttu-id="453c9-138">Otomatik Bellek Yönetimi</span><span class="sxs-lookup"><span data-stu-id="453c9-138">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)  
 [<span data-ttu-id="453c9-139">Atık Toplama</span><span class="sxs-lookup"><span data-stu-id="453c9-139">Garbage Collection</span></span>](../../../../docs/standard/garbage-collection/index.md)  
 [<span data-ttu-id="453c9-140">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="453c9-140">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="453c9-141">ICLRGCManager2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="453c9-141">ICLRGCManager2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md)
