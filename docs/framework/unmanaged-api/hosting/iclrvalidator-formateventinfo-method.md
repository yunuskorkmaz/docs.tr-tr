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
ms.openlocfilehash: a3f52deab4d0c8ca56fae2e65912217e51abe58a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95715881"
---
# <a name="iclrvalidatorformateventinfo-method"></a><span data-ttu-id="8b678-102">ICLRValidator::FormatEventInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8b678-102">ICLRValidator::FormatEventInfo Method</span></span>

<span data-ttu-id="8b678-103">Belirtilen doğrulama hatası hakkında ayrıntılı bir ileti alır.</span><span class="sxs-lookup"><span data-stu-id="8b678-103">Gets a detailed message about the specified validation error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b678-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="8b678-104">Syntax</span></span>  
  
```cpp  
HRESULT FormatEventInfo (  
    [in] HRESULT            hVECode,  
    [in] VEContext          Context,  
    [in, out] LPWSTR        msg,  
    [in] unsigned long      ulMaxLength,  
    [in] SAFEARRAY(VARIANT) psa  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8b678-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8b678-105">Parameters</span></span>  

 `hVECode`  
 <span data-ttu-id="8b678-106">'ndaki Doğrulama hata işleyicisine geçirilen HRESULT değeri.</span><span class="sxs-lookup"><span data-stu-id="8b678-106">[in] The HRESULT value that was passed to the validation error handler.</span></span>  
  
 `Context`  
 <span data-ttu-id="8b678-107">'ndaki `VEContext` Doğrulama hatalarıyla ilgili bağlam bilgilerini içeren bir örnek.</span><span class="sxs-lookup"><span data-stu-id="8b678-107">[in] A `VEContext` instance that contains context information about the validation errors.</span></span>  
  
 `msg`  
 <span data-ttu-id="8b678-108">[in, out] Kolay hata iletisi.</span><span class="sxs-lookup"><span data-stu-id="8b678-108">[in, out] The friendly error message.</span></span>  
  
 `ulMaxLength`  
 <span data-ttu-id="8b678-109">'ndaki Hata iletisinin en fazla uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="8b678-109">[in] The maximum length of the error message.</span></span>  
  
 `psa`  
 <span data-ttu-id="8b678-110">'ndaki İletide kullanılacak ek parametrelerin güvenli bir dizisi.</span><span class="sxs-lookup"><span data-stu-id="8b678-110">[in] A safe array of additional parameters to be used in the message.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8b678-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8b678-111">Return Value</span></span>  
  
|<span data-ttu-id="8b678-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8b678-112">HRESULT</span></span>|<span data-ttu-id="8b678-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8b678-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8b678-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="8b678-114">S_OK</span></span>|<span data-ttu-id="8b678-115">`FormatEventInfo` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="8b678-115">`FormatEventInfo` returned successfully.</span></span>|  
|<span data-ttu-id="8b678-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8b678-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8b678-117">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="8b678-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8b678-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8b678-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8b678-119">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="8b678-119">The call timed out.</span></span>|  
|<span data-ttu-id="8b678-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8b678-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8b678-121">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="8b678-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8b678-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8b678-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8b678-123">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="8b678-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8b678-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8b678-124">E_FAIL</span></span>|<span data-ttu-id="8b678-125">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="8b678-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8b678-126">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="8b678-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8b678-127">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="8b678-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8b678-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8b678-128">Requirements</span></span>  

 <span data-ttu-id="8b678-129">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b678-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b678-130">**Üst bilgi:** IValidator. IDL, IValidator. h</span><span class="sxs-lookup"><span data-stu-id="8b678-130">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="8b678-131">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="8b678-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8b678-132">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b678-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b678-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8b678-133">See also</span></span>

- [<span data-ttu-id="8b678-134">ICLRErrorReportingManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8b678-134">ICLRErrorReportingManager Interface</span></span>](iclrerrorreportingmanager-interface.md)
- [<span data-ttu-id="8b678-135">ICLRValidator Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8b678-135">ICLRValidator Interface</span></span>](iclrvalidator-interface.md)
