---
description: 'Şu konuda daha fazla bilgi edinin: IHostCrst:: Leave yöntemi'
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
ms.openlocfilehash: b00e62c7b2683ab6024a7c9b8de4645ceb59fb02
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708846"
---
# <a name="ihostcrstleave-method"></a><span data-ttu-id="425e4-103">IHostCrst::Leave Yöntemi</span><span class="sxs-lookup"><span data-stu-id="425e4-103">IHostCrst::Leave Method</span></span>

<span data-ttu-id="425e4-104">Geçerli [IHostCrst](ihostcrst-interface.md)örneği tarafından temsil edilen kritik bölümü bırakır.</span><span class="sxs-lookup"><span data-stu-id="425e4-104">Leaves the critical section that is represented by the current instance of [IHostCrst](ihostcrst-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="425e4-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="425e4-105">Syntax</span></span>  
  
```cpp  
HRESULT Leave ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="425e4-106">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="425e4-106">Return Value</span></span>  
  
|<span data-ttu-id="425e4-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="425e4-107">HRESULT</span></span>|<span data-ttu-id="425e4-108">Description</span><span class="sxs-lookup"><span data-stu-id="425e4-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="425e4-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="425e4-109">S_OK</span></span>|<span data-ttu-id="425e4-110">`Leave` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="425e4-110">`Leave` returned successfully.</span></span>|  
|<span data-ttu-id="425e4-111">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="425e4-111">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="425e4-112">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="425e4-112">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="425e4-113">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="425e4-113">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="425e4-114">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="425e4-114">The call timed out.</span></span>|  
|<span data-ttu-id="425e4-115">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="425e4-115">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="425e4-116">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="425e4-116">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="425e4-117">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="425e4-117">HOST_E_ABANDONED</span></span>|<span data-ttu-id="425e4-118">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="425e4-118">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="425e4-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="425e4-119">E_FAIL</span></span>|<span data-ttu-id="425e4-120">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="425e4-120">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="425e4-121">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="425e4-121">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="425e4-122">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="425e4-122">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="425e4-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="425e4-123">Remarks</span></span>  

 <span data-ttu-id="425e4-124">`Leave` CLR 'nin ilgili Win32 işlevini kullanmak yerine, konağın iş parçacığı uygulamasıyla doğrudan iletişim kurmasına izin verir `LeaveCriticalSection` .</span><span class="sxs-lookup"><span data-stu-id="425e4-124">`Leave` allows the CLR to communicate directly with the host's threading implementation, rather than using the corresponding Win32 `LeaveCriticalSection` function.</span></span> <span data-ttu-id="425e4-125">Geçerli örnek tarafından temsil edilen kritik bölümün sahipliğini alan bir iş parçacığı, `IHostCrst` `Leave` Bu kritik bölüme her girdiğinde her seferinde bir kez çağrı yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="425e4-125">A thread that takes ownership of the critical section represented by the current `IHostCrst` instance must call `Leave` once for each time it enters that critical section.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="425e4-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="425e4-126">Requirements</span></span>  

 <span data-ttu-id="425e4-127">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="425e4-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="425e4-128">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="425e4-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="425e4-129">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="425e4-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="425e4-130">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="425e4-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="425e4-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="425e4-131">See also</span></span>

- [<span data-ttu-id="425e4-132">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="425e4-132">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="425e4-133">IHostCrst Arabirimi</span><span class="sxs-lookup"><span data-stu-id="425e4-133">IHostCrst Interface</span></span>](ihostcrst-interface.md)
- [<span data-ttu-id="425e4-134">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="425e4-134">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
