---
description: ': ICLRGCManager:: Collect yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 7c2649f7ce3472c504c1e48a203cf89d4b8508e3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746067"
---
# <a name="iclrgcmanagercollect-method"></a><span data-ttu-id="dc5b3-103">ICLRGCManager::Collect Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dc5b3-103">ICLRGCManager::Collect Method</span></span>

<span data-ttu-id="dc5b3-104">Belirtilen oluşturma için bir çöp toplamayı zorlar.</span><span class="sxs-lookup"><span data-stu-id="dc5b3-104">Forces a garbage collection for the specified generation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc5b3-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dc5b3-105">Syntax</span></span>  
  
```cpp  
HRESULT Collect (  
    [in] LONG Generation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dc5b3-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="dc5b3-106">Parameters</span></span>  

 `Generation`  
 <span data-ttu-id="dc5b3-107">'ndaki Toplanacak oluşturma.</span><span class="sxs-lookup"><span data-stu-id="dc5b3-107">[in] The generation to collect.</span></span> <span data-ttu-id="dc5b3-108">-1 değeri, tüm nesiller koleksiyonunu zorlar.</span><span class="sxs-lookup"><span data-stu-id="dc5b3-108">A value of -1 forces a collection of all generations.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dc5b3-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="dc5b3-109">Return Value</span></span>  
  
|<span data-ttu-id="dc5b3-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="dc5b3-110">HRESULT</span></span>|<span data-ttu-id="dc5b3-111">Description</span><span class="sxs-lookup"><span data-stu-id="dc5b3-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dc5b3-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="dc5b3-112">S_OK</span></span>|<span data-ttu-id="dc5b3-113">`Collect` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="dc5b3-113">`Collect` returned successfully.</span></span>|  
|<span data-ttu-id="dc5b3-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="dc5b3-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="dc5b3-115">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="dc5b3-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="dc5b3-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="dc5b3-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="dc5b3-117">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="dc5b3-117">The call timed out.</span></span>|  
|<span data-ttu-id="dc5b3-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="dc5b3-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="dc5b3-119">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="dc5b3-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="dc5b3-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="dc5b3-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="dc5b3-121">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="dc5b3-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="dc5b3-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="dc5b3-122">E_FAIL</span></span>|<span data-ttu-id="dc5b3-123">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="dc5b3-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="dc5b3-124">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="dc5b3-124">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="dc5b3-125">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="dc5b3-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dc5b3-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dc5b3-126">Remarks</span></span>  

 <span data-ttu-id="dc5b3-127">`Collect`Yöntemi, clr 'nin çöp toplayıcısının geçerli durumundan bağımsız olarak bir koleksiyon gerçekleştirmesini zorlar.</span><span class="sxs-lookup"><span data-stu-id="dc5b3-127">The `Collect` method forces the CLR's garbage collector to perform a collection regardless of its current state.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc5b3-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dc5b3-128">Requirements</span></span>  

 <span data-ttu-id="dc5b3-129">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dc5b3-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc5b3-130">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="dc5b3-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dc5b3-131">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="dc5b3-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dc5b3-132">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc5b3-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc5b3-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dc5b3-133">See also</span></span>

- [<span data-ttu-id="dc5b3-134">Otomatik bellek yönetimi</span><span class="sxs-lookup"><span data-stu-id="dc5b3-134">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="dc5b3-135">Çöp toplama</span><span class="sxs-lookup"><span data-stu-id="dc5b3-135">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="dc5b3-136">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dc5b3-136">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="dc5b3-137">ICLRGCManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dc5b3-137">ICLRGCManager Interface</span></span>](iclrgcmanager-interface.md)
- [<span data-ttu-id="dc5b3-138">CLR Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="dc5b3-138">CLR Hosting Interfaces</span></span>](clr-hosting-interfaces.md)
- [<span data-ttu-id="dc5b3-139">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="dc5b3-139">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="dc5b3-140">Hosting</span><span class="sxs-lookup"><span data-stu-id="dc5b3-140">Hosting</span></span>](index.md)
