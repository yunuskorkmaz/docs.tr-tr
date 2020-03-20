---
title: ICLRTask::RudeAbort Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRTask.RudeAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::RudeAbort
helpviewer_keywords:
- RudeAbort method, ICLRTask interface [.NET Framework hosting]
- ICLRTask::RudeAbort method [.NET Framework hosting]
ms.assetid: b5785468-fcd7-4cc3-8a5d-8796337b53fc
topic_type:
- apiref
ms.openlocfilehash: aacf9de36dc39b63ed36b672e31f40704413d608
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176337"
---
# <a name="iclrtaskrudeabort-method"></a><span data-ttu-id="c64b0-102">ICLRTask::RudeAbort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c64b0-102">ICLRTask::RudeAbort Method</span></span>
<span data-ttu-id="c64b0-103">Geçerli [ICLRTask Interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) örneği tarafından temsil edilen görevi derhal ve koşulsuz olarak iptal etmesi için ortak dil çalışma süresine (CLR) talimat verir.</span><span class="sxs-lookup"><span data-stu-id="c64b0-103">Instructs the common language runtime (CLR) to abort the task represented by the current [ICLRTask Interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance immediately and unconditionally.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c64b0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c64b0-104">Syntax</span></span>  
  
```cpp  
HRESULT RudeAbort ();
```  
  
## <a name="return-value"></a><span data-ttu-id="c64b0-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c64b0-105">Return Value</span></span>  
  
|<span data-ttu-id="c64b0-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c64b0-106">HRESULT</span></span>|<span data-ttu-id="c64b0-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c64b0-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c64b0-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="c64b0-108">S_OK</span></span>|<span data-ttu-id="c64b0-109">`RudeAbort`başarıyla döndürülür.</span><span class="sxs-lookup"><span data-stu-id="c64b0-109">`RudeAbort` returned successfully.</span></span>|  
|<span data-ttu-id="c64b0-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c64b0-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c64b0-111">CLR bir işleme yüklenmedi veya CLR yönetilen kodu çalıştıramadığı veya aramayı başarıyla işleyemediği bir durumdadır.</span><span class="sxs-lookup"><span data-stu-id="c64b0-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c64b0-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c64b0-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c64b0-113">Arama zaman doldu.</span><span class="sxs-lookup"><span data-stu-id="c64b0-113">The call timed out.</span></span>|  
|<span data-ttu-id="c64b0-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c64b0-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c64b0-115">Arayan kilidin sahibi değildir.</span><span class="sxs-lookup"><span data-stu-id="c64b0-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c64b0-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c64b0-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c64b0-117">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="c64b0-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c64b0-118">E_faıl</span><span class="sxs-lookup"><span data-stu-id="c64b0-118">E_FAIL</span></span>|<span data-ttu-id="c64b0-119">Bilinmeyen bir felaket hatası meydana geldi.</span><span class="sxs-lookup"><span data-stu-id="c64b0-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c64b0-120">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c64b0-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c64b0-121">Barındırma yöntemleri sonraki aramalar HOST_E_CLRNOTAVAILABLE döndürün.</span><span class="sxs-lookup"><span data-stu-id="c64b0-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c64b0-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c64b0-122">Remarks</span></span>  
 <span data-ttu-id="c64b0-123">Bir ev `RudeAbort` sahibi, bir görevi hemen iptal etmek için çağrıda bulunur.</span><span class="sxs-lookup"><span data-stu-id="c64b0-123">A host calls `RudeAbort` to abort a task immediately.</span></span> <span data-ttu-id="c64b0-124">Sonlandırıcılar ve özel durum işleme rutinlerinin yürütülmesi garanti edilmez.</span><span class="sxs-lookup"><span data-stu-id="c64b0-124">Finalizers and exception handling routines are not guaranteed to be executed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c64b0-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c64b0-125">Requirements</span></span>  
 <span data-ttu-id="c64b0-126">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c64b0-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c64b0-127">**Üstbilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c64b0-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c64b0-128">**Kütüphane:** MSCorEE.dll bir kaynak olarak dahil</span><span class="sxs-lookup"><span data-stu-id="c64b0-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c64b0-129">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c64b0-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c64b0-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c64b0-130">See also</span></span>

- [<span data-ttu-id="c64b0-131">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c64b0-131">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="c64b0-132">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c64b0-132">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="c64b0-133">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c64b0-133">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="c64b0-134">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c64b0-134">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
