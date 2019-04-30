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
ms.openlocfilehash: 9117a82dff48dcda8d96f0feb7b8c4a001fa17f1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763328"
---
# <a name="iclrvalidatorformateventinfo-method"></a><span data-ttu-id="e00ee-102">ICLRValidator::FormatEventInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e00ee-102">ICLRValidator::FormatEventInfo Method</span></span>
<span data-ttu-id="e00ee-103">Belirtilen doğrulama hatası hakkında ayrıntılı bir ileti alır.</span><span class="sxs-lookup"><span data-stu-id="e00ee-103">Gets a detailed message about the specified validation error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e00ee-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e00ee-104">Syntax</span></span>  
  
```  
HRESULT FormatEventInfo (  
    [in] HRESULT            hVECode,  
    [in] VEContext          Context,  
    [in, out] LPWSTR        msg,  
    [in] unsigned long      ulMaxLength,  
    [in] SAFEARRAY(VARIANT) psa  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e00ee-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e00ee-105">Parameters</span></span>  
 `hVECode`  
 <span data-ttu-id="e00ee-106">[in] Doğrulama hata işleyicisine geçirilen HRESULT değerini.</span><span class="sxs-lookup"><span data-stu-id="e00ee-106">[in] The HRESULT value that was passed to the validation error handler.</span></span>  
  
 `Context`  
 <span data-ttu-id="e00ee-107">[in] A `VEContext` doğrulama hataları hakkında bağlam bilgisi içeren örneği.</span><span class="sxs-lookup"><span data-stu-id="e00ee-107">[in] A `VEContext` instance that contains context information about the validation errors.</span></span>  
  
 `msg`  
 <span data-ttu-id="e00ee-108">[out içinde] Kolay hata iletisi.</span><span class="sxs-lookup"><span data-stu-id="e00ee-108">[in, out] The friendly error message.</span></span>  
  
 `ulMaxLength`  
 <span data-ttu-id="e00ee-109">[in] Hata iletisi en fazla uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="e00ee-109">[in] The maximum length of the error message.</span></span>  
  
 `psa`  
 <span data-ttu-id="e00ee-110">[in] İletide kullanılacak ek parametreler güvenli bir dizi.</span><span class="sxs-lookup"><span data-stu-id="e00ee-110">[in] A safe array of additional parameters to be used in the message.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e00ee-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e00ee-111">Return Value</span></span>  
  
|<span data-ttu-id="e00ee-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e00ee-112">HRESULT</span></span>|<span data-ttu-id="e00ee-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e00ee-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e00ee-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="e00ee-114">S_OK</span></span>|<span data-ttu-id="e00ee-115">`FormatEventInfo` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="e00ee-115">`FormatEventInfo` returned successfully.</span></span>|  
|<span data-ttu-id="e00ee-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e00ee-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e00ee-117">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="e00ee-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e00ee-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e00ee-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e00ee-119">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="e00ee-119">The call timed out.</span></span>|  
|<span data-ttu-id="e00ee-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e00ee-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e00ee-121">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="e00ee-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e00ee-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e00ee-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e00ee-123">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="e00ee-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e00ee-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e00ee-124">E_FAIL</span></span>|<span data-ttu-id="e00ee-125">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="e00ee-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e00ee-126">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="e00ee-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e00ee-127">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="e00ee-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e00ee-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e00ee-128">Requirements</span></span>  
 <span data-ttu-id="e00ee-129">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e00ee-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e00ee-130">**Üst bilgi:** IValidator.idl, IValidator.h</span><span class="sxs-lookup"><span data-stu-id="e00ee-130">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="e00ee-131">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="e00ee-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e00ee-132">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e00ee-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e00ee-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e00ee-133">See also</span></span>

- [<span data-ttu-id="e00ee-134">ICLRErrorReportingManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e00ee-134">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
- [<span data-ttu-id="e00ee-135">ICLRValidator Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e00ee-135">ICLRValidator Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)
