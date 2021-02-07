---
description: 'Şu konuda daha fazla bilgi edinin: IHostAutoEvent:: set yöntemi'
title: IHostAutoEvent::Set Yöntemi
ms.date: 03/30/2017
api_name:
- IHostAutoEvent.Set
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAutoEvent::Set
helpviewer_keywords:
- Set method, IHostAutoEvent interface [.NET Framework hosting]
- IHostAutoEvent::Set method [.NET Framework hosting]
ms.assetid: 46becf3e-bc0e-4338-85c0-9ab0df76a1d0
topic_type:
- apiref
ms.openlocfilehash: e4ba63b5250a383431e410cd6e552f8344fedf5d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708945"
---
# <a name="ihostautoeventset-method"></a><span data-ttu-id="ca76e-103">IHostAutoEvent::Set Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ca76e-103">IHostAutoEvent::Set Method</span></span>

<span data-ttu-id="ca76e-104">Geçerli [IHostAutoEvent](ihostautoevent-interface.md) örneğini sinyal alındı durumuna ayarlar.</span><span class="sxs-lookup"><span data-stu-id="ca76e-104">Sets the current [IHostAutoEvent](ihostautoevent-interface.md) instance to a signaled state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca76e-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="ca76e-105">Syntax</span></span>  
  
```cpp  
HRESULT Set ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="ca76e-106">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ca76e-106">Return Value</span></span>  
  
|<span data-ttu-id="ca76e-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ca76e-107">HRESULT</span></span>|<span data-ttu-id="ca76e-108">Description</span><span class="sxs-lookup"><span data-stu-id="ca76e-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ca76e-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="ca76e-109">S_OK</span></span>|<span data-ttu-id="ca76e-110">`Set` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="ca76e-110">`Set` returned successfully.</span></span>|  
|<span data-ttu-id="ca76e-111">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ca76e-111">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ca76e-112">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="ca76e-112">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ca76e-113">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ca76e-113">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ca76e-114">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="ca76e-114">The call timed out.</span></span>|  
|<span data-ttu-id="ca76e-115">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ca76e-115">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ca76e-116">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="ca76e-116">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ca76e-117">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ca76e-117">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ca76e-118">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="ca76e-118">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ca76e-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ca76e-119">E_FAIL</span></span>|<span data-ttu-id="ca76e-120">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="ca76e-120">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ca76e-121">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="ca76e-121">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ca76e-122">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="ca76e-122">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ca76e-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ca76e-123">Requirements</span></span>  

 <span data-ttu-id="ca76e-124">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca76e-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca76e-125">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ca76e-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ca76e-126">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="ca76e-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ca76e-127">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca76e-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca76e-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ca76e-128">See also</span></span>

- [<span data-ttu-id="ca76e-129">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ca76e-129">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="ca76e-130">IHostAutoEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ca76e-130">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="ca76e-131">IHostManualEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ca76e-131">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="ca76e-132">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ca76e-132">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
