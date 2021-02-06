---
description: ': ICLRValidator:: FormatEventInfo Yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 3d8d1eff8c638517e201905d0313ee824490acf4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99636799"
---
# <a name="iclrvalidatorformateventinfo-method"></a><span data-ttu-id="e20e5-103">ICLRValidator::FormatEventInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e20e5-103">ICLRValidator::FormatEventInfo Method</span></span>

<span data-ttu-id="e20e5-104">Belirtilen doğrulama hatası hakkında ayrıntılı bir ileti alır.</span><span class="sxs-lookup"><span data-stu-id="e20e5-104">Gets a detailed message about the specified validation error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e20e5-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e20e5-105">Syntax</span></span>  
  
```cpp  
HRESULT FormatEventInfo (  
    [in] HRESULT            hVECode,  
    [in] VEContext          Context,  
    [in, out] LPWSTR        msg,  
    [in] unsigned long      ulMaxLength,  
    [in] SAFEARRAY(VARIANT) psa  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e20e5-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e20e5-106">Parameters</span></span>  

 `hVECode`  
 <span data-ttu-id="e20e5-107">'ndaki Doğrulama hata işleyicisine geçirilen HRESULT değeri.</span><span class="sxs-lookup"><span data-stu-id="e20e5-107">[in] The HRESULT value that was passed to the validation error handler.</span></span>  
  
 `Context`  
 <span data-ttu-id="e20e5-108">'ndaki `VEContext` Doğrulama hatalarıyla ilgili bağlam bilgilerini içeren bir örnek.</span><span class="sxs-lookup"><span data-stu-id="e20e5-108">[in] A `VEContext` instance that contains context information about the validation errors.</span></span>  
  
 `msg`  
 <span data-ttu-id="e20e5-109">[in, out] Kolay hata iletisi.</span><span class="sxs-lookup"><span data-stu-id="e20e5-109">[in, out] The friendly error message.</span></span>  
  
 `ulMaxLength`  
 <span data-ttu-id="e20e5-110">'ndaki Hata iletisinin en fazla uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="e20e5-110">[in] The maximum length of the error message.</span></span>  
  
 `psa`  
 <span data-ttu-id="e20e5-111">'ndaki İletide kullanılacak ek parametrelerin güvenli bir dizisi.</span><span class="sxs-lookup"><span data-stu-id="e20e5-111">[in] A safe array of additional parameters to be used in the message.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e20e5-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e20e5-112">Return Value</span></span>  
  
|<span data-ttu-id="e20e5-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e20e5-113">HRESULT</span></span>|<span data-ttu-id="e20e5-114">Description</span><span class="sxs-lookup"><span data-stu-id="e20e5-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e20e5-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="e20e5-115">S_OK</span></span>|<span data-ttu-id="e20e5-116">`FormatEventInfo` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="e20e5-116">`FormatEventInfo` returned successfully.</span></span>|  
|<span data-ttu-id="e20e5-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e20e5-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e20e5-118">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="e20e5-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e20e5-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e20e5-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e20e5-120">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="e20e5-120">The call timed out.</span></span>|  
|<span data-ttu-id="e20e5-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e20e5-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e20e5-122">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="e20e5-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e20e5-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e20e5-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e20e5-124">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="e20e5-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e20e5-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e20e5-125">E_FAIL</span></span>|<span data-ttu-id="e20e5-126">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="e20e5-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e20e5-127">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="e20e5-127">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e20e5-128">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="e20e5-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e20e5-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e20e5-129">Requirements</span></span>  

 <span data-ttu-id="e20e5-130">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e20e5-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e20e5-131">**Üst bilgi:** IValidator. IDL, IValidator. h</span><span class="sxs-lookup"><span data-stu-id="e20e5-131">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="e20e5-132">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="e20e5-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e20e5-133">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e20e5-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e20e5-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e20e5-134">See also</span></span>

- [<span data-ttu-id="e20e5-135">ICLRErrorReportingManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e20e5-135">ICLRErrorReportingManager Interface</span></span>](iclrerrorreportingmanager-interface.md)
- [<span data-ttu-id="e20e5-136">ICLRValidator Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e20e5-136">ICLRValidator Interface</span></span>](iclrvalidator-interface.md)
