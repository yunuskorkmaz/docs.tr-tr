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
ms.openlocfilehash: 9885149a71147db6eef13958b8ef825caa1d6ec6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176389"
---
# <a name="iclrgcmanager2setgcstartuplimitsex-method"></a><span data-ttu-id="8cc7c-102">ICLRGCManager2::SetGCStartupLimitsEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8cc7c-102">ICLRGCManager2::SetGCStartupLimitsEx Method</span></span>
<span data-ttu-id="8cc7c-103">Çöp toplama kesiminin boyutunu ve çöp toplama sisteminin oluşturma 0'ının maksimum boyutunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="8cc7c-103">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8cc7c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8cc7c-104">Syntax</span></span>  
  
```cpp  
HRESULT SetGCStartupLimitsEx (  
    [in] SIZE_T SegmentSize,
    [in] SIZE_T MaxGen0Size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8cc7c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8cc7c-105">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="8cc7c-106">[içinde] Çöp toplama kesiminin belirtilen boyutu.</span><span class="sxs-lookup"><span data-stu-id="8cc7c-106">[in] The specified size of a garbage collection segment.</span></span>  
  
 <span data-ttu-id="8cc7c-107">Minimum segment boyutu 4 MB'dır.</span><span class="sxs-lookup"><span data-stu-id="8cc7c-107">The minimum segment size is 4 MB.</span></span> <span data-ttu-id="8cc7c-108">Segmentler 1 MB veya daha büyük artışlarla artırılabilir.</span><span class="sxs-lookup"><span data-stu-id="8cc7c-108">Segments can be increased in increments of 1 MB or larger.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="8cc7c-109">[içinde] Nesil 0 için belirtilen maksimum boyut.</span><span class="sxs-lookup"><span data-stu-id="8cc7c-109">[in] The specified maximum size for generation 0.</span></span>  
  
 <span data-ttu-id="8cc7c-110">Minimum nesil 0 boyutu 64 KB'dir.</span><span class="sxs-lookup"><span data-stu-id="8cc7c-110">The minimum generation 0 size is 64 KB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8cc7c-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8cc7c-111">Return Value</span></span>  
  
|<span data-ttu-id="8cc7c-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8cc7c-112">HRESULT</span></span>|<span data-ttu-id="8cc7c-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8cc7c-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8cc7c-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="8cc7c-114">S_OK</span></span>|<span data-ttu-id="8cc7c-115">`SetGCStartupLimitsEx`başarıyla döndürülür.</span><span class="sxs-lookup"><span data-stu-id="8cc7c-115">`SetGCStartupLimitsEx` returned successfully.</span></span>|  
|<span data-ttu-id="8cc7c-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8cc7c-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8cc7c-117">Ortak dil çalışma süresi (CLR) bir işleme yüklenmedi veya CLR yönetilen kodu çalıştıramadığı veya aramayı başarıyla işleyemediği bir durumdadır.</span><span class="sxs-lookup"><span data-stu-id="8cc7c-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8cc7c-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8cc7c-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8cc7c-119">Arama zaman doldu.</span><span class="sxs-lookup"><span data-stu-id="8cc7c-119">The call timed out.</span></span>|  
|<span data-ttu-id="8cc7c-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8cc7c-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8cc7c-121">Arayan kilidin sahibi değildir.</span><span class="sxs-lookup"><span data-stu-id="8cc7c-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8cc7c-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8cc7c-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8cc7c-123">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="8cc7c-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8cc7c-124">E_faıl</span><span class="sxs-lookup"><span data-stu-id="8cc7c-124">E_FAIL</span></span>|<span data-ttu-id="8cc7c-125">Bilinmeyen bir felaket hatası meydana geldi.</span><span class="sxs-lookup"><span data-stu-id="8cc7c-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8cc7c-126">Bir yöntem E_FAIL döndükten sonra, CLR artık işlem içinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8cc7c-126">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8cc7c-127">Barındırma yöntemleri sonraki aramalar HOST_E_CLRNOTAVAILABLE döndürün.</span><span class="sxs-lookup"><span data-stu-id="8cc7c-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8cc7c-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8cc7c-128">Remarks</span></span>  
 <span data-ttu-id="8cc7c-129">Kümeler `SetGCStartupLimitsEx` değerleri yalnızca ana bilgisayar başlatılmadan önce belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="8cc7c-129">The values that `SetGCStartupLimitsEx` sets can be specified only before the host is started.</span></span> <span data-ttu-id="8cc7c-130">Daha sonra `SetGCStartupLimitsEx` yapılan aramalar yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="8cc7c-130">Later calls to `SetGCStartupLimitsEx` are ignored.</span></span>  
  
 <span data-ttu-id="8cc7c-131">Diğerini etkilemeden parametre yi ayarlamak için, değiştirmek istemediğiniz parametre için 0 (sıfır) belirtin.</span><span class="sxs-lookup"><span data-stu-id="8cc7c-131">To set either parameter without affecting the other, specify 0 (zero) for the parameter you don't want to change.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8cc7c-132">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8cc7c-132">Requirements</span></span>  
 <span data-ttu-id="8cc7c-133">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8cc7c-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8cc7c-134">**Üstbilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8cc7c-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8cc7c-135">**Kütüphane:** MSCorEE.dll bir kaynak olarak dahil</span><span class="sxs-lookup"><span data-stu-id="8cc7c-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8cc7c-136">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8cc7c-136">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cc7c-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8cc7c-137">See also</span></span>

- [<span data-ttu-id="8cc7c-138">Otomatik Bellek Yönetimi</span><span class="sxs-lookup"><span data-stu-id="8cc7c-138">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="8cc7c-139">Çöp Toplama</span><span class="sxs-lookup"><span data-stu-id="8cc7c-139">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="8cc7c-140">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8cc7c-140">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="8cc7c-141">ICLRGCManager2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8cc7c-141">ICLRGCManager2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md)
