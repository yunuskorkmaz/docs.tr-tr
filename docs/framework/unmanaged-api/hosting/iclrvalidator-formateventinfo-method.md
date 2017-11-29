---
title: "ICLRValidator::FormatEventInfo Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRValidator.FormatEventInfo
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRValidator::FormatEventInfo
helpviewer_keywords:
- FormatEventInfo method, ICLRValidator interface [.NET Framework hosting]
- ICLRValidator::FormatEventInfo method [.NET Framework hosting]
ms.assetid: 808e1f1d-52f4-47c4-83cc-dcf47d075219
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d03864ac8e4e0423e45ac084e01af98e3eab13a2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrvalidatorformateventinfo-method"></a><span data-ttu-id="9dfbe-102">ICLRValidator::FormatEventInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9dfbe-102">ICLRValidator::FormatEventInfo Method</span></span>
<span data-ttu-id="9dfbe-103">Belirtilen doğrulama hata hakkında ayrıntılı bir ileti alır.</span><span class="sxs-lookup"><span data-stu-id="9dfbe-103">Gets a detailed message about the specified validation error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9dfbe-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9dfbe-104">Syntax</span></span>  
  
```  
HRESULT FormatEventInfo (  
    [in] HRESULT            hVECode,  
    [in] VEContext          Context,  
    [in, out] LPWSTR        msg,  
    [in] unsigned long      ulMaxLength,  
    [in] SAFEARRAY(VARIANT) psa  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9dfbe-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9dfbe-105">Parameters</span></span>  
 `hVECode`  
 <span data-ttu-id="9dfbe-106">[in] Doğrulama hata işleyicisine geçirilen HRESULT değeri.</span><span class="sxs-lookup"><span data-stu-id="9dfbe-106">[in] The HRESULT value that was passed to the validation error handler.</span></span>  
  
 `Context`  
 <span data-ttu-id="9dfbe-107">[in] A `VEContext` doğrulama hataları hakkında bağlam bilgilerini içeren örneği.</span><span class="sxs-lookup"><span data-stu-id="9dfbe-107">[in] A `VEContext` instance that contains context information about the validation errors.</span></span>  
  
 `msg`  
 <span data-ttu-id="9dfbe-108">[içinde out] Kolay hata iletisi.</span><span class="sxs-lookup"><span data-stu-id="9dfbe-108">[in, out] The friendly error message.</span></span>  
  
 `ulMaxLength`  
 <span data-ttu-id="9dfbe-109">[in] Hata iletisinin en büyük uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="9dfbe-109">[in] The maximum length of the error message.</span></span>  
  
 `psa`  
 <span data-ttu-id="9dfbe-110">[in] Ek parametreler iletisinde kullanılacak güvenli bir dizi.</span><span class="sxs-lookup"><span data-stu-id="9dfbe-110">[in] A safe array of additional parameters to be used in the message.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9dfbe-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9dfbe-111">Return Value</span></span>  
  
|<span data-ttu-id="9dfbe-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9dfbe-112">HRESULT</span></span>|<span data-ttu-id="9dfbe-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9dfbe-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9dfbe-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="9dfbe-114">S_OK</span></span>|<span data-ttu-id="9dfbe-115">`FormatEventInfo`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="9dfbe-115">`FormatEventInfo` returned successfully.</span></span>|  
|<span data-ttu-id="9dfbe-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9dfbe-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9dfbe-117">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="9dfbe-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9dfbe-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9dfbe-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9dfbe-119">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="9dfbe-119">The call timed out.</span></span>|  
|<span data-ttu-id="9dfbe-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9dfbe-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9dfbe-121">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="9dfbe-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9dfbe-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9dfbe-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9dfbe-123">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="9dfbe-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9dfbe-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9dfbe-124">E_FAIL</span></span>|<span data-ttu-id="9dfbe-125">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="9dfbe-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9dfbe-126">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="9dfbe-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9dfbe-127">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="9dfbe-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9dfbe-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9dfbe-128">Requirements</span></span>  
 <span data-ttu-id="9dfbe-129">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9dfbe-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9dfbe-130">**Başlık:** IValidator.idl, IValidator.h</span><span class="sxs-lookup"><span data-stu-id="9dfbe-130">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="9dfbe-131">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="9dfbe-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9dfbe-132">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9dfbe-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9dfbe-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9dfbe-133">See Also</span></span>  
 [<span data-ttu-id="9dfbe-134">Iclrerrorreportingmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="9dfbe-134">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)  
 [<span data-ttu-id="9dfbe-135">Iclrvalidator arabirimi</span><span class="sxs-lookup"><span data-stu-id="9dfbe-135">ICLRValidator Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)
