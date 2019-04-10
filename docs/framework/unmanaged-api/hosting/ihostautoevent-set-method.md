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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5af9f55bdcfe23f0b2a051b33cb1280f312820a7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59227021"
---
# <a name="ihostautoeventset-method"></a><span data-ttu-id="e9112-102">IHostAutoEvent::Set Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e9112-102">IHostAutoEvent::Set Method</span></span>
<span data-ttu-id="e9112-103">Geçerli ayarlar [Ihostautoevent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) sinyal verilmiş duruma örneği.</span><span class="sxs-lookup"><span data-stu-id="e9112-103">Sets the current [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance to a signaled state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9112-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e9112-104">Syntax</span></span>  
  
```  
HRESULT Set ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="e9112-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e9112-105">Return Value</span></span>  
  
|<span data-ttu-id="e9112-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e9112-106">HRESULT</span></span>|<span data-ttu-id="e9112-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e9112-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e9112-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="e9112-108">S_OK</span></span>|`Set` <span data-ttu-id="e9112-109">başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="e9112-109">returned successfully.</span></span>|  
|<span data-ttu-id="e9112-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e9112-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e9112-111">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="e9112-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e9112-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e9112-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e9112-113">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="e9112-113">The call timed out.</span></span>|  
|<span data-ttu-id="e9112-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e9112-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e9112-115">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="e9112-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e9112-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e9112-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e9112-117">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="e9112-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e9112-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e9112-118">E_FAIL</span></span>|<span data-ttu-id="e9112-119">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="e9112-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e9112-120">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="e9112-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e9112-121">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="e9112-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e9112-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e9112-122">Requirements</span></span>  
 <span data-ttu-id="e9112-123">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9112-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9112-124">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e9112-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e9112-125">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="e9112-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="e9112-126">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="e9112-126">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e9112-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e9112-127">See also</span></span>

- [<span data-ttu-id="e9112-128">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e9112-128">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="e9112-129">IHostAutoEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e9112-129">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="e9112-130">IHostManualEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e9112-130">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="e9112-131">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e9112-131">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
