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
ms.openlocfilehash: 83b029c24321946f777966daa7a486f9e8e7b7a8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61641378"
---
# <a name="iclrruntimehostgetclrcontrol-method"></a><span data-ttu-id="30cf7-102">ICLRRuntimeHost::GetCLRControl Yöntemi</span><span class="sxs-lookup"><span data-stu-id="30cf7-102">ICLRRuntimeHost::GetCLRControl Method</span></span>
<span data-ttu-id="30cf7-103">Türü bir arabirim işaretçisi alır [Iclrcontrol arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) konakları ortak dil çalışma zamanı (CLR) yönlerini özelleştirmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="30cf7-103">Gets an interface pointer of type [ICLRControl Interface](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) that hosts can use to customize aspects of the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30cf7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="30cf7-104">Syntax</span></span>  
  
```  
HRESULT GetCLRControl(  
    [out] ICLRControl** pCLRControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="30cf7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="30cf7-105">Parameters</span></span>  
 `pCLRControl`  
 <span data-ttu-id="30cf7-106">[out] Bir arabirim işaretçisi türünde [Iclrcontrol arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) CLR ek yönlerini yapılandırmak için ana bilgisayarları etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="30cf7-106">[out] An interface pointer of type [ICLRControl Interface](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) that enables hosts to configure additional aspects of the CLR.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="30cf7-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="30cf7-107">Return Value</span></span>  
  
|<span data-ttu-id="30cf7-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="30cf7-108">HRESULT</span></span>|<span data-ttu-id="30cf7-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="30cf7-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="30cf7-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="30cf7-110">S_OK</span></span>|<span data-ttu-id="30cf7-111">`GetCLRControl` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="30cf7-111">`GetCLRControl` returned successfully.</span></span>|  
|<span data-ttu-id="30cf7-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="30cf7-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="30cf7-113">CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="30cf7-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="30cf7-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="30cf7-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="30cf7-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="30cf7-115">The call timed out.</span></span>|  
|<span data-ttu-id="30cf7-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="30cf7-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="30cf7-117">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="30cf7-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="30cf7-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="30cf7-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="30cf7-119">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="30cf7-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="30cf7-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="30cf7-120">E_FAIL</span></span>|<span data-ttu-id="30cf7-121">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="30cf7-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="30cf7-122">CLR, artık bir yöntem E_FAIL döndürürse, işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="30cf7-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="30cf7-123">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="30cf7-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="30cf7-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="30cf7-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="30cf7-125">CLR zaten başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="30cf7-125">The CLR has already started.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="30cf7-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="30cf7-126">Remarks</span></span>  
 <span data-ttu-id="30cf7-127">`ICLRControl` sağlar [GetCLRManager metodu](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) manager türlerinden biri için bir arabirim işaretçisini almak konağı sağlayan yöntemi.</span><span class="sxs-lookup"><span data-stu-id="30cf7-127">`ICLRControl` provides the [GetCLRManager Method](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method, which enables the host to get an interface pointer to one of the manager types.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30cf7-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="30cf7-128">Requirements</span></span>  
 <span data-ttu-id="30cf7-129">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30cf7-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30cf7-130">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="30cf7-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="30cf7-131">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="30cf7-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="30cf7-132">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30cf7-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30cf7-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="30cf7-133">See also</span></span>

- [<span data-ttu-id="30cf7-134">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="30cf7-134">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="30cf7-135">ICLRRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="30cf7-135">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
