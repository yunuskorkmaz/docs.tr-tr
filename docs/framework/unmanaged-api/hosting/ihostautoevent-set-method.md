---
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
ms.openlocfilehash: 792b735522580eb7460da703899a00781e525419
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124444"
---
# <a name="ihostautoeventset-method"></a><span data-ttu-id="4d75b-102">IHostAutoEvent::Set Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4d75b-102">IHostAutoEvent::Set Method</span></span>
<span data-ttu-id="4d75b-103">Geçerli [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) örneğini sinyal alındı durumuna ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4d75b-103">Sets the current [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance to a signaled state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d75b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4d75b-104">Syntax</span></span>  
  
```cpp  
HRESULT Set ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="4d75b-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="4d75b-105">Return Value</span></span>  
  
|<span data-ttu-id="4d75b-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4d75b-106">HRESULT</span></span>|<span data-ttu-id="4d75b-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4d75b-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4d75b-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="4d75b-108">S_OK</span></span>|<span data-ttu-id="4d75b-109">`Set` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="4d75b-109">`Set` returned successfully.</span></span>|  
|<span data-ttu-id="4d75b-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4d75b-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4d75b-111">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="4d75b-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4d75b-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4d75b-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4d75b-113">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="4d75b-113">The call timed out.</span></span>|  
|<span data-ttu-id="4d75b-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4d75b-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4d75b-115">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="4d75b-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4d75b-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4d75b-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4d75b-117">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="4d75b-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4d75b-118">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="4d75b-118">E_FAIL</span></span>|<span data-ttu-id="4d75b-119">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="4d75b-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4d75b-120">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="4d75b-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4d75b-121">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="4d75b-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4d75b-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4d75b-122">Requirements</span></span>  
 <span data-ttu-id="4d75b-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4d75b-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d75b-124">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="4d75b-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4d75b-125">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="4d75b-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4d75b-126">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d75b-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d75b-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4d75b-127">See also</span></span>

- [<span data-ttu-id="4d75b-128">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4d75b-128">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="4d75b-129">IHostAutoEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4d75b-129">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="4d75b-130">IHostManualEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4d75b-130">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="4d75b-131">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4d75b-131">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
