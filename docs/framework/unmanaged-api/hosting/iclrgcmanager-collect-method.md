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
ms.openlocfilehash: 90ce4e888ddb3a10dd0dfd7e68463311db86742f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95677771"
---
# <a name="iclrgcmanagercollect-method"></a><span data-ttu-id="fa26f-102">ICLRGCManager::Collect Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fa26f-102">ICLRGCManager::Collect Method</span></span>

<span data-ttu-id="fa26f-103">Belirtilen oluşturma için bir çöp toplamayı zorlar.</span><span class="sxs-lookup"><span data-stu-id="fa26f-103">Forces a garbage collection for the specified generation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa26f-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="fa26f-104">Syntax</span></span>  
  
```cpp  
HRESULT Collect (  
    [in] LONG Generation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fa26f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fa26f-105">Parameters</span></span>  

 `Generation`  
 <span data-ttu-id="fa26f-106">'ndaki Toplanacak oluşturma.</span><span class="sxs-lookup"><span data-stu-id="fa26f-106">[in] The generation to collect.</span></span> <span data-ttu-id="fa26f-107">-1 değeri, tüm nesiller koleksiyonunu zorlar.</span><span class="sxs-lookup"><span data-stu-id="fa26f-107">A value of -1 forces a collection of all generations.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fa26f-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="fa26f-108">Return Value</span></span>  
  
|<span data-ttu-id="fa26f-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fa26f-109">HRESULT</span></span>|<span data-ttu-id="fa26f-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fa26f-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fa26f-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="fa26f-111">S_OK</span></span>|<span data-ttu-id="fa26f-112">`Collect` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="fa26f-112">`Collect` returned successfully.</span></span>|  
|<span data-ttu-id="fa26f-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fa26f-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fa26f-114">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="fa26f-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fa26f-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fa26f-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="fa26f-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="fa26f-116">The call timed out.</span></span>|  
|<span data-ttu-id="fa26f-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="fa26f-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="fa26f-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="fa26f-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="fa26f-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="fa26f-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="fa26f-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="fa26f-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="fa26f-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fa26f-121">E_FAIL</span></span>|<span data-ttu-id="fa26f-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="fa26f-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fa26f-123">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="fa26f-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="fa26f-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="fa26f-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fa26f-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fa26f-125">Remarks</span></span>  

 <span data-ttu-id="fa26f-126">`Collect`Yöntemi, clr 'nin çöp toplayıcısının geçerli durumundan bağımsız olarak bir koleksiyon gerçekleştirmesini zorlar.</span><span class="sxs-lookup"><span data-stu-id="fa26f-126">The `Collect` method forces the CLR's garbage collector to perform a collection regardless of its current state.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa26f-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fa26f-127">Requirements</span></span>  

 <span data-ttu-id="fa26f-128">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fa26f-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa26f-129">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="fa26f-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fa26f-130">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="fa26f-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fa26f-131">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa26f-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa26f-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fa26f-132">See also</span></span>

- [<span data-ttu-id="fa26f-133">Otomatik bellek yönetimi</span><span class="sxs-lookup"><span data-stu-id="fa26f-133">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="fa26f-134">Çöp toplama</span><span class="sxs-lookup"><span data-stu-id="fa26f-134">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="fa26f-135">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fa26f-135">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="fa26f-136">ICLRGCManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fa26f-136">ICLRGCManager Interface</span></span>](iclrgcmanager-interface.md)
- [<span data-ttu-id="fa26f-137">CLR Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="fa26f-137">CLR Hosting Interfaces</span></span>](clr-hosting-interfaces.md)
- [<span data-ttu-id="fa26f-138">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="fa26f-138">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="fa26f-139">Hosting</span><span class="sxs-lookup"><span data-stu-id="fa26f-139">Hosting</span></span>](index.md)
