---
title: IHostCrst::Leave Yöntemi
ms.date: 03/30/2017
api_name:
- IHostCrst.Leave
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostCrst::Leave
helpviewer_keywords:
- IHostCrst::Leave method [.NET Framework hosting]
- Leave method [.NET Framework hosting]
ms.assetid: dfc51d9e-b36d-4dba-9ea1-4f63fa0601ae
topic_type:
- apiref
ms.openlocfilehash: 08af77c3a158b97cd698dbaeebdc7cdf1b9acfc3
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804887"
---
# <a name="ihostcrstleave-method"></a><span data-ttu-id="7f44d-102">IHostCrst::Leave Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7f44d-102">IHostCrst::Leave Method</span></span>
<span data-ttu-id="7f44d-103">Geçerli [IHostCrst](ihostcrst-interface.md)örneği tarafından temsil edilen kritik bölümü bırakır.</span><span class="sxs-lookup"><span data-stu-id="7f44d-103">Leaves the critical section that is represented by the current instance of [IHostCrst](ihostcrst-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f44d-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="7f44d-104">Syntax</span></span>  
  
```cpp  
HRESULT Leave ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="7f44d-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7f44d-105">Return Value</span></span>  
  
|<span data-ttu-id="7f44d-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7f44d-106">HRESULT</span></span>|<span data-ttu-id="7f44d-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7f44d-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7f44d-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="7f44d-108">S_OK</span></span>|<span data-ttu-id="7f44d-109">`Leave`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="7f44d-109">`Leave` returned successfully.</span></span>|  
|<span data-ttu-id="7f44d-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7f44d-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7f44d-111">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="7f44d-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7f44d-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7f44d-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7f44d-113">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="7f44d-113">The call timed out.</span></span>|  
|<span data-ttu-id="7f44d-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7f44d-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7f44d-115">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="7f44d-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7f44d-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7f44d-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7f44d-117">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="7f44d-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7f44d-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7f44d-118">E_FAIL</span></span>|<span data-ttu-id="7f44d-119">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="7f44d-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7f44d-120">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="7f44d-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7f44d-121">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="7f44d-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7f44d-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7f44d-122">Remarks</span></span>  
 <span data-ttu-id="7f44d-123">`Leave`CLR 'nin ilgili Win32 işlevini kullanmak yerine, konağın iş parçacığı uygulamasıyla doğrudan iletişim kurmasına izin verir `LeaveCriticalSection` .</span><span class="sxs-lookup"><span data-stu-id="7f44d-123">`Leave` allows the CLR to communicate directly with the host's threading implementation, rather than using the corresponding Win32 `LeaveCriticalSection` function.</span></span> <span data-ttu-id="7f44d-124">Geçerli örnek tarafından temsil edilen kritik bölümün sahipliğini alan bir iş parçacığı, `IHostCrst` `Leave` Bu kritik bölüme her girdiğinde her seferinde bir kez çağrı yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7f44d-124">A thread that takes ownership of the critical section represented by the current `IHostCrst` instance must call `Leave` once for each time it enters that critical section.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f44d-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7f44d-125">Requirements</span></span>  
 <span data-ttu-id="7f44d-126">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f44d-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f44d-127">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="7f44d-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7f44d-128">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="7f44d-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7f44d-129">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f44d-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f44d-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7f44d-130">See also</span></span>

- [<span data-ttu-id="7f44d-131">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7f44d-131">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="7f44d-132">IHostCrst Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7f44d-132">IHostCrst Interface</span></span>](ihostcrst-interface.md)
- [<span data-ttu-id="7f44d-133">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7f44d-133">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
