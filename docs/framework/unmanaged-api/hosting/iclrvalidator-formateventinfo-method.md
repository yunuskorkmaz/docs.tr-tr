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
ms.openlocfilehash: 164a8c15a501af44aabb95852400621f05bbe873
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762805"
---
# <a name="iclrvalidatorformateventinfo-method"></a><span data-ttu-id="a935d-102">ICLRValidator::FormatEventInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a935d-102">ICLRValidator::FormatEventInfo Method</span></span>
<span data-ttu-id="a935d-103">Belirtilen doğrulama hatası hakkında ayrıntılı bir ileti alır.</span><span class="sxs-lookup"><span data-stu-id="a935d-103">Gets a detailed message about the specified validation error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a935d-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="a935d-104">Syntax</span></span>  
  
```cpp  
HRESULT FormatEventInfo (  
    [in] HRESULT            hVECode,  
    [in] VEContext          Context,  
    [in, out] LPWSTR        msg,  
    [in] unsigned long      ulMaxLength,  
    [in] SAFEARRAY(VARIANT) psa  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a935d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a935d-105">Parameters</span></span>  
 `hVECode`  
 <span data-ttu-id="a935d-106">'ndaki Doğrulama hata işleyicisine geçirilen HRESULT değeri.</span><span class="sxs-lookup"><span data-stu-id="a935d-106">[in] The HRESULT value that was passed to the validation error handler.</span></span>  
  
 `Context`  
 <span data-ttu-id="a935d-107">'ndaki `VEContext`Doğrulama hatalarıyla ilgili bağlam bilgilerini içeren bir örnek.</span><span class="sxs-lookup"><span data-stu-id="a935d-107">[in] A `VEContext` instance that contains context information about the validation errors.</span></span>  
  
 `msg`  
 <span data-ttu-id="a935d-108">[in, out] Kolay hata iletisi.</span><span class="sxs-lookup"><span data-stu-id="a935d-108">[in, out] The friendly error message.</span></span>  
  
 `ulMaxLength`  
 <span data-ttu-id="a935d-109">'ndaki Hata iletisinin en fazla uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="a935d-109">[in] The maximum length of the error message.</span></span>  
  
 `psa`  
 <span data-ttu-id="a935d-110">'ndaki İletide kullanılacak ek parametrelerin güvenli bir dizisi.</span><span class="sxs-lookup"><span data-stu-id="a935d-110">[in] A safe array of additional parameters to be used in the message.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a935d-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a935d-111">Return Value</span></span>  
  
|<span data-ttu-id="a935d-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a935d-112">HRESULT</span></span>|<span data-ttu-id="a935d-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a935d-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a935d-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="a935d-114">S_OK</span></span>|<span data-ttu-id="a935d-115">`FormatEventInfo`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="a935d-115">`FormatEventInfo` returned successfully.</span></span>|  
|<span data-ttu-id="a935d-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a935d-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a935d-117">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="a935d-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a935d-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a935d-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a935d-119">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="a935d-119">The call timed out.</span></span>|  
|<span data-ttu-id="a935d-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a935d-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a935d-121">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="a935d-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a935d-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a935d-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a935d-123">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="a935d-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a935d-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a935d-124">E_FAIL</span></span>|<span data-ttu-id="a935d-125">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="a935d-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a935d-126">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="a935d-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a935d-127">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="a935d-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a935d-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a935d-128">Requirements</span></span>  
 <span data-ttu-id="a935d-129">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a935d-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a935d-130">**Üst bilgi:** IValidator. IDL, IValidator. h</span><span class="sxs-lookup"><span data-stu-id="a935d-130">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="a935d-131">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="a935d-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a935d-132">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a935d-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a935d-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a935d-133">See also</span></span>

- [<span data-ttu-id="a935d-134">ICLRErrorReportingManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a935d-134">ICLRErrorReportingManager Interface</span></span>](iclrerrorreportingmanager-interface.md)
- [<span data-ttu-id="a935d-135">ICLRValidator Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a935d-135">ICLRValidator Interface</span></span>](iclrvalidator-interface.md)
