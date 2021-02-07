---
description: 'Daha fazla bilgi edinin: ICLRGCManager2:: SetGCStartupLimitsEx yöntemi'
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
ms.openlocfilehash: 2a4801d2f6255f5f84e0a4bae7a1886689ee8dc5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689246"
---
# <a name="iclrgcmanager2setgcstartuplimitsex-method"></a><span data-ttu-id="58dcd-103">ICLRGCManager2::SetGCStartupLimitsEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="58dcd-103">ICLRGCManager2::SetGCStartupLimitsEx Method</span></span>

<span data-ttu-id="58dcd-104">Çöp toplama kesiminin boyutunu ve çöp toplama sisteminin oluşturma 0 ' nın en büyük boyutunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="58dcd-104">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58dcd-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="58dcd-105">Syntax</span></span>  
  
```cpp  
HRESULT SetGCStartupLimitsEx (  
    [in] SIZE_T SegmentSize,
    [in] SIZE_T MaxGen0Size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="58dcd-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="58dcd-106">Parameters</span></span>  

 `SegmentSize`  
 <span data-ttu-id="58dcd-107">'ndaki Bir çöp toplama kesiminin belirtilen boyutu.</span><span class="sxs-lookup"><span data-stu-id="58dcd-107">[in] The specified size of a garbage collection segment.</span></span>  
  
 <span data-ttu-id="58dcd-108">En küçük kesim boyutu 4 MB 'tır.</span><span class="sxs-lookup"><span data-stu-id="58dcd-108">The minimum segment size is 4 MB.</span></span> <span data-ttu-id="58dcd-109">Segmentler, 1 MB veya daha büyük artışlarla artırılabilir.</span><span class="sxs-lookup"><span data-stu-id="58dcd-109">Segments can be increased in increments of 1 MB or larger.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="58dcd-110">'ndaki Oluşturma 0 için belirtilen en büyük boyut.</span><span class="sxs-lookup"><span data-stu-id="58dcd-110">[in] The specified maximum size for generation 0.</span></span>  
  
 <span data-ttu-id="58dcd-111">Minimum nesil 0 boyutu 64 KB 'tır.</span><span class="sxs-lookup"><span data-stu-id="58dcd-111">The minimum generation 0 size is 64 KB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="58dcd-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="58dcd-112">Return Value</span></span>  
  
|<span data-ttu-id="58dcd-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="58dcd-113">HRESULT</span></span>|<span data-ttu-id="58dcd-114">Description</span><span class="sxs-lookup"><span data-stu-id="58dcd-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="58dcd-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="58dcd-115">S_OK</span></span>|<span data-ttu-id="58dcd-116">`SetGCStartupLimitsEx` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="58dcd-116">`SetGCStartupLimitsEx` returned successfully.</span></span>|  
|<span data-ttu-id="58dcd-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="58dcd-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="58dcd-118">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="58dcd-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="58dcd-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="58dcd-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="58dcd-120">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="58dcd-120">The call timed out.</span></span>|  
|<span data-ttu-id="58dcd-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="58dcd-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="58dcd-122">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="58dcd-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="58dcd-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="58dcd-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="58dcd-124">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="58dcd-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="58dcd-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="58dcd-125">E_FAIL</span></span>|<span data-ttu-id="58dcd-126">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="58dcd-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="58dcd-127">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="58dcd-127">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="58dcd-128">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="58dcd-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="58dcd-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="58dcd-129">Remarks</span></span>  

 <span data-ttu-id="58dcd-130">`SetGCStartupLimitsEx`Ayarlayan değerler yalnızca konak başlatılmadan önce belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="58dcd-130">The values that `SetGCStartupLimitsEx` sets can be specified only before the host is started.</span></span> <span data-ttu-id="58dcd-131">Daha sonraki çağrıları `SetGCStartupLimitsEx` yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="58dcd-131">Later calls to `SetGCStartupLimitsEx` are ignored.</span></span>  
  
 <span data-ttu-id="58dcd-132">Diğerini etkilemeden parametre ayarlamak için değiştirmek istemediğiniz parametre için 0 (sıfır) değerini belirtin.</span><span class="sxs-lookup"><span data-stu-id="58dcd-132">To set either parameter without affecting the other, specify 0 (zero) for the parameter you don't want to change.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58dcd-133">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="58dcd-133">Requirements</span></span>  

 <span data-ttu-id="58dcd-134">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="58dcd-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58dcd-135">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="58dcd-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="58dcd-136">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="58dcd-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="58dcd-137">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58dcd-137">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58dcd-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="58dcd-138">See also</span></span>

- [<span data-ttu-id="58dcd-139">Otomatik bellek yönetimi</span><span class="sxs-lookup"><span data-stu-id="58dcd-139">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="58dcd-140">Çöp toplama</span><span class="sxs-lookup"><span data-stu-id="58dcd-140">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="58dcd-141">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="58dcd-141">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="58dcd-142">ICLRGCManager2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="58dcd-142">ICLRGCManager2 Interface</span></span>](iclrgcmanager2-interface.md)
