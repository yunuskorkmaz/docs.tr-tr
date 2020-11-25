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
ms.openlocfilehash: 27d1ce06800075d2690bc508554b70f8d10168af
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95715023"
---
# <a name="iclrgcmanager2setgcstartuplimitsex-method"></a><span data-ttu-id="a1ff8-102">ICLRGCManager2::SetGCStartupLimitsEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a1ff8-102">ICLRGCManager2::SetGCStartupLimitsEx Method</span></span>

<span data-ttu-id="a1ff8-103">Çöp toplama kesiminin boyutunu ve çöp toplama sisteminin oluşturma 0 ' nın en büyük boyutunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="a1ff8-103">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1ff8-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="a1ff8-104">Syntax</span></span>  
  
```cpp  
HRESULT SetGCStartupLimitsEx (  
    [in] SIZE_T SegmentSize,
    [in] SIZE_T MaxGen0Size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a1ff8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a1ff8-105">Parameters</span></span>  

 `SegmentSize`  
 <span data-ttu-id="a1ff8-106">'ndaki Bir çöp toplama kesiminin belirtilen boyutu.</span><span class="sxs-lookup"><span data-stu-id="a1ff8-106">[in] The specified size of a garbage collection segment.</span></span>  
  
 <span data-ttu-id="a1ff8-107">En küçük kesim boyutu 4 MB 'tır.</span><span class="sxs-lookup"><span data-stu-id="a1ff8-107">The minimum segment size is 4 MB.</span></span> <span data-ttu-id="a1ff8-108">Segmentler, 1 MB veya daha büyük artışlarla artırılabilir.</span><span class="sxs-lookup"><span data-stu-id="a1ff8-108">Segments can be increased in increments of 1 MB or larger.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="a1ff8-109">'ndaki Oluşturma 0 için belirtilen en büyük boyut.</span><span class="sxs-lookup"><span data-stu-id="a1ff8-109">[in] The specified maximum size for generation 0.</span></span>  
  
 <span data-ttu-id="a1ff8-110">Minimum nesil 0 boyutu 64 KB 'tır.</span><span class="sxs-lookup"><span data-stu-id="a1ff8-110">The minimum generation 0 size is 64 KB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a1ff8-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a1ff8-111">Return Value</span></span>  
  
|<span data-ttu-id="a1ff8-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a1ff8-112">HRESULT</span></span>|<span data-ttu-id="a1ff8-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a1ff8-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a1ff8-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="a1ff8-114">S_OK</span></span>|<span data-ttu-id="a1ff8-115">`SetGCStartupLimitsEx` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="a1ff8-115">`SetGCStartupLimitsEx` returned successfully.</span></span>|  
|<span data-ttu-id="a1ff8-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a1ff8-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a1ff8-117">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="a1ff8-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a1ff8-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a1ff8-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a1ff8-119">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="a1ff8-119">The call timed out.</span></span>|  
|<span data-ttu-id="a1ff8-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a1ff8-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a1ff8-121">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="a1ff8-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a1ff8-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a1ff8-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a1ff8-123">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="a1ff8-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a1ff8-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a1ff8-124">E_FAIL</span></span>|<span data-ttu-id="a1ff8-125">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="a1ff8-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a1ff8-126">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="a1ff8-126">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a1ff8-127">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="a1ff8-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a1ff8-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a1ff8-128">Remarks</span></span>  

 <span data-ttu-id="a1ff8-129">`SetGCStartupLimitsEx`Ayarlayan değerler yalnızca konak başlatılmadan önce belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="a1ff8-129">The values that `SetGCStartupLimitsEx` sets can be specified only before the host is started.</span></span> <span data-ttu-id="a1ff8-130">Daha sonraki çağrıları `SetGCStartupLimitsEx` yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="a1ff8-130">Later calls to `SetGCStartupLimitsEx` are ignored.</span></span>  
  
 <span data-ttu-id="a1ff8-131">Diğerini etkilemeden parametre ayarlamak için değiştirmek istemediğiniz parametre için 0 (sıfır) değerini belirtin.</span><span class="sxs-lookup"><span data-stu-id="a1ff8-131">To set either parameter without affecting the other, specify 0 (zero) for the parameter you don't want to change.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1ff8-132">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a1ff8-132">Requirements</span></span>  

 <span data-ttu-id="a1ff8-133">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1ff8-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1ff8-134">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a1ff8-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a1ff8-135">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="a1ff8-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a1ff8-136">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1ff8-136">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1ff8-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a1ff8-137">See also</span></span>

- [<span data-ttu-id="a1ff8-138">Otomatik bellek yönetimi</span><span class="sxs-lookup"><span data-stu-id="a1ff8-138">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="a1ff8-139">Çöp toplama</span><span class="sxs-lookup"><span data-stu-id="a1ff8-139">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="a1ff8-140">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a1ff8-140">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="a1ff8-141">ICLRGCManager2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a1ff8-141">ICLRGCManager2 Interface</span></span>](iclrgcmanager2-interface.md)
