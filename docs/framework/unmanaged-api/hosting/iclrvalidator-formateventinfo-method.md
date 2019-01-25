---
title: ICLRValidator::FormatEventInfo Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRValidator.FormatEventInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRValidator::FormatEventInfo
helpviewer_keywords:
- FormatEventInfo method, ICLRValidator interface [.NET Framework hosting]
- ICLRValidator::FormatEventInfo method [.NET Framework hosting]
ms.assetid: 808e1f1d-52f4-47c4-83cc-dcf47d075219
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 31b99ce4435c1282380291e3c3c15723381e8ab4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54741853"
---
# <a name="iclrvalidatorformateventinfo-method"></a><span data-ttu-id="50c93-102">ICLRValidator::FormatEventInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="50c93-102">ICLRValidator::FormatEventInfo Method</span></span>
<span data-ttu-id="50c93-103">Belirtilen doğrulama hatası hakkında ayrıntılı bir ileti alır.</span><span class="sxs-lookup"><span data-stu-id="50c93-103">Gets a detailed message about the specified validation error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50c93-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="50c93-104">Syntax</span></span>  
  
```  
HRESULT FormatEventInfo (  
    [in] HRESULT            hVECode,  
    [in] VEContext          Context,  
    [in, out] LPWSTR        msg,  
    [in] unsigned long      ulMaxLength,  
    [in] SAFEARRAY(VARIANT) psa  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="50c93-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="50c93-105">Parameters</span></span>  
 `hVECode`  
 <span data-ttu-id="50c93-106">[in] Doğrulama hata işleyicisine geçirilen HRESULT değerini.</span><span class="sxs-lookup"><span data-stu-id="50c93-106">[in] The HRESULT value that was passed to the validation error handler.</span></span>  
  
 `Context`  
 <span data-ttu-id="50c93-107">[in] A `VEContext` doğrulama hataları hakkında bağlam bilgisi içeren örneği.</span><span class="sxs-lookup"><span data-stu-id="50c93-107">[in] A `VEContext` instance that contains context information about the validation errors.</span></span>  
  
 `msg`  
 <span data-ttu-id="50c93-108">[out içinde] Kolay hata iletisi.</span><span class="sxs-lookup"><span data-stu-id="50c93-108">[in, out] The friendly error message.</span></span>  
  
 `ulMaxLength`  
 <span data-ttu-id="50c93-109">[in] Hata iletisi en fazla uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="50c93-109">[in] The maximum length of the error message.</span></span>  
  
 `psa`  
 <span data-ttu-id="50c93-110">[in] İletide kullanılacak ek parametreler güvenli bir dizi.</span><span class="sxs-lookup"><span data-stu-id="50c93-110">[in] A safe array of additional parameters to be used in the message.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="50c93-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="50c93-111">Return Value</span></span>  
  
|<span data-ttu-id="50c93-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="50c93-112">HRESULT</span></span>|<span data-ttu-id="50c93-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="50c93-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="50c93-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="50c93-114">S_OK</span></span>|<span data-ttu-id="50c93-115">`FormatEventInfo` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="50c93-115">`FormatEventInfo` returned successfully.</span></span>|  
|<span data-ttu-id="50c93-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="50c93-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="50c93-117">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="50c93-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="50c93-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="50c93-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="50c93-119">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="50c93-119">The call timed out.</span></span>|  
|<span data-ttu-id="50c93-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="50c93-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="50c93-121">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="50c93-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="50c93-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="50c93-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="50c93-123">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="50c93-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="50c93-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="50c93-124">E_FAIL</span></span>|<span data-ttu-id="50c93-125">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="50c93-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="50c93-126">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="50c93-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="50c93-127">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="50c93-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="50c93-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="50c93-128">Requirements</span></span>  
 <span data-ttu-id="50c93-129">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50c93-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50c93-130">**Üst bilgi:** IValidator.idl, IValidator.h</span><span class="sxs-lookup"><span data-stu-id="50c93-130">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="50c93-131">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="50c93-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="50c93-132">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50c93-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50c93-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="50c93-133">See also</span></span>
- [<span data-ttu-id="50c93-134">ICLRErrorReportingManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="50c93-134">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
- [<span data-ttu-id="50c93-135">ICLRValidator Arabirimi</span><span class="sxs-lookup"><span data-stu-id="50c93-135">ICLRValidator Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)
