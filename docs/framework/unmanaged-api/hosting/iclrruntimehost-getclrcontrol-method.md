---
title: ICLRRuntimeHost::GetCLRControl Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.GetCLRControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::GetCLRControl
helpviewer_keywords:
- ICLRRuntimeHost::GetCLRControl method [.NET Framework hosting]
- GetCLRControl method [.NET Framework hosting]
ms.assetid: e47e3655-efd5-4572-a1dc-50c69bf2a468
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 06c3b060aaeb73b2d834c053cf47f0384ca4a38f
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57488477"
---
# <a name="iclrruntimehostgetclrcontrol-method"></a><span data-ttu-id="bc814-102">ICLRRuntimeHost::GetCLRControl Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bc814-102">ICLRRuntimeHost::GetCLRControl Method</span></span>
<span data-ttu-id="bc814-103">Türü bir arabirim işaretçisi alır [Iclrcontrol arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) konakları ortak dil çalışma zamanı (CLR) yönlerini özelleştirmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bc814-103">Gets an interface pointer of type [ICLRControl Interface](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) that hosts can use to customize aspects of the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc814-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bc814-104">Syntax</span></span>  
  
```  
HRESULT GetCLRControl(  
    [out] ICLRControl** pCLRControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bc814-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bc814-105">Parameters</span></span>  
 `pCLRControl`  
 <span data-ttu-id="bc814-106">[out] Bir arabirim işaretçisi türünde [Iclrcontrol arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) CLR ek yönlerini yapılandırmak için ana bilgisayarları etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="bc814-106">[out] An interface pointer of type [ICLRControl Interface](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) that enables hosts to configure additional aspects of the CLR.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bc814-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="bc814-107">Return Value</span></span>  
  
|<span data-ttu-id="bc814-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bc814-108">HRESULT</span></span>|<span data-ttu-id="bc814-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bc814-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bc814-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="bc814-110">S_OK</span></span>|<span data-ttu-id="bc814-111">`GetCLRControl` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="bc814-111">`GetCLRControl` returned successfully.</span></span>|  
|<span data-ttu-id="bc814-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="bc814-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="bc814-113">CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="bc814-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="bc814-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="bc814-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="bc814-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="bc814-115">The call timed out.</span></span>|  
|<span data-ttu-id="bc814-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="bc814-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="bc814-117">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="bc814-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="bc814-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="bc814-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="bc814-119">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="bc814-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="bc814-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bc814-120">E_FAIL</span></span>|<span data-ttu-id="bc814-121">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="bc814-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="bc814-122">CLR, artık bir yöntem E_FAIL döndürürse, işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="bc814-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="bc814-123">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="bc814-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="bc814-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="bc814-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="bc814-125">CLR zaten başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="bc814-125">The CLR has already started.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bc814-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bc814-126">Remarks</span></span>  
 <span data-ttu-id="bc814-127">`ICLRControl` sağlar [GetCLRManager metodu](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) manager türlerinden biri için bir arabirim işaretçisini almak konağı sağlayan yöntemi.</span><span class="sxs-lookup"><span data-stu-id="bc814-127">`ICLRControl` provides the [GetCLRManager Method](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method, which enables the host to get an interface pointer to one of the manager types.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc814-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bc814-128">Requirements</span></span>  
 <span data-ttu-id="bc814-129">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bc814-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc814-130">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="bc814-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bc814-131">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="bc814-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bc814-132">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc814-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc814-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bc814-133">See also</span></span>
- [<span data-ttu-id="bc814-134">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bc814-134">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="bc814-135">ICLRRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bc814-135">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
