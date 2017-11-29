---
title: ICLRRuntimeHost::GetCLRControl Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeHost.GetCLRControl
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeHost::GetCLRControl
helpviewer_keywords:
- ICLRRuntimeHost::GetCLRControl method [.NET Framework hosting]
- GetCLRControl method [.NET Framework hosting]
ms.assetid: e47e3655-efd5-4572-a1dc-50c69bf2a468
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4072c21ea002523fe8086151a40c4e17b775ebbb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrruntimehostgetclrcontrol-method"></a><span data-ttu-id="88618-102">ICLRRuntimeHost::GetCLRControl Metodu</span><span class="sxs-lookup"><span data-stu-id="88618-102">ICLRRuntimeHost::GetCLRControl Method</span></span>
<span data-ttu-id="88618-103">Arabirim işaretçisi türü alır [Iclrcontrol arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) konakları ortak dil çalışma zamanı (CLR) yönlerini özelleştirmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="88618-103">Gets an interface pointer of type [ICLRControl Interface](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) that hosts can use to customize aspects of the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88618-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="88618-104">Syntax</span></span>  
  
```  
HRESULT GetCLRControl(  
    [out] ICLRControl** pCLRControl  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="88618-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="88618-105">Parameters</span></span>  
 `pCLRControl`  
 <span data-ttu-id="88618-106">[out] Arabirim işaretçisi türü [Iclrcontrol arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) CLR ek yönlerini yapılandırmak ana bilgisayarları sağlar.</span><span class="sxs-lookup"><span data-stu-id="88618-106">[out] An interface pointer of type [ICLRControl Interface](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) that enables hosts to configure additional aspects of the CLR.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="88618-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="88618-107">Return Value</span></span>  
  
|<span data-ttu-id="88618-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="88618-108">HRESULT</span></span>|<span data-ttu-id="88618-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="88618-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="88618-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="88618-110">S_OK</span></span>|<span data-ttu-id="88618-111">`GetCLRControl`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="88618-111">`GetCLRControl` returned successfully.</span></span>|  
|<span data-ttu-id="88618-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="88618-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="88618-113">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="88618-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="88618-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="88618-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="88618-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="88618-115">The call timed out.</span></span>|  
|<span data-ttu-id="88618-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="88618-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="88618-117">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="88618-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="88618-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="88618-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="88618-119">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="88618-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="88618-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="88618-120">E_FAIL</span></span>|<span data-ttu-id="88618-121">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="88618-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="88618-122">Bir yöntem E_FAIL döndürürse, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="88618-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="88618-123">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="88618-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="88618-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="88618-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="88618-125">CLR zaten başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="88618-125">The CLR has already started.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="88618-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="88618-126">Remarks</span></span>  
 <span data-ttu-id="88618-127">`ICLRControl`sağlar [GetCLRManager yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) Yöneticisi türden biri için bir arabirim işaretçisi almak için konağı etkinleştirir yöntemi.</span><span class="sxs-lookup"><span data-stu-id="88618-127">`ICLRControl` provides the [GetCLRManager Method](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method, which enables the host to get an interface pointer to one of the manager types.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88618-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="88618-128">Requirements</span></span>  
 <span data-ttu-id="88618-129">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="88618-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88618-130">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="88618-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="88618-131">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="88618-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="88618-132">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="88618-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88618-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="88618-133">See Also</span></span>  
 [<span data-ttu-id="88618-134">Iclrcontrol arabirimi</span><span class="sxs-lookup"><span data-stu-id="88618-134">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="88618-135">Iclrruntimehost arabirimi</span><span class="sxs-lookup"><span data-stu-id="88618-135">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
