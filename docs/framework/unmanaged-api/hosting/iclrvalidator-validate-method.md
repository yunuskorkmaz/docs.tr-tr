---
title: ICLRValidator::Validate Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRValidator.Validate
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRValidator::Validate
helpviewer_keywords:
- Validate method, ICLRValidator interface [.NET Framework hosting]
- ICLRValidator::Validate method [.NET Framework hosting]
ms.assetid: 0b1b432a-d234-4002-839b-81366c3a8bdc
topic_type:
- apiref
ms.openlocfilehash: 427895ffea94e6c657d775ebdeb8571070a61c6e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178058"
---
# <a name="iclrvalidatorvalidate-method"></a><span data-ttu-id="095ab-102">ICLRValidator::Validate Yöntemi</span><span class="sxs-lookup"><span data-stu-id="095ab-102">ICLRValidator::Validate Method</span></span>
<span data-ttu-id="095ab-103">Belirtilen dosyadaki taşınabilir yürütülebilir (PE) veya Microsoft ara dilini (MSIL) doğrular.</span><span class="sxs-lookup"><span data-stu-id="095ab-103">Validates the portable executable (PE) or Microsoft intermediate language (MSIL) in the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="095ab-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="095ab-104">Syntax</span></span>  
  
```cpp  
HRESULT Validate (  
    [in] IVEHandler        *veh,  
    [in] unsigned long      ulAppDomainId,  
    [in] unsigned long      ulFlags,  
    [in] unsigned long      ulMaxError,  
    [in] unsigned long      token,  
    [in] LPWSTR             fileName,  
    [in, size_is(ulSize)] BYTE *pe,  
    [in] unsigned long      ulSize  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="095ab-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="095ab-105">Parameters</span></span>  
 `veh`  
 <span data-ttu-id="095ab-106">[içinde] Doğrulama hatalarını `IVEHandler` işleyen bir örneğin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="095ab-106">[in] A pointer to an `IVEHandler` instance that handles validation errors.</span></span>  
  
 `ulAppDomainId`  
 <span data-ttu-id="095ab-107">[içinde] Geçerli <xref:System.AppDomain>için tanımlayıcı .</span><span class="sxs-lookup"><span data-stu-id="095ab-107">[in] The identifier for the current <xref:System.AppDomain>.</span></span>  
  
 `ulFlags`  
 <span data-ttu-id="095ab-108">[içinde] Yapılması gereken doğrulama türünü gösteren [ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) değerlerinin birleşimi.</span><span class="sxs-lookup"><span data-stu-id="095ab-108">[in] A combination of [ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) values, indicating the kind of validation that should be performed.</span></span>  
  
 `ulMaxError`  
 <span data-ttu-id="095ab-109">[içinde] Doğrulamadan çıkmadan önce izin verilebilen maksimum hata sayısı.</span><span class="sxs-lookup"><span data-stu-id="095ab-109">[in] The maximum number of errors to allow before exiting the validation.</span></span>  
  
 `token`  
 <span data-ttu-id="095ab-110">[içinde] Kullanılma -yan.</span><span class="sxs-lookup"><span data-stu-id="095ab-110">[in] Unused.</span></span>  
  
 `fileName`  
 <span data-ttu-id="095ab-111">[içinde] Doğrulanacak dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="095ab-111">[in] The name of the file to be validated.</span></span>  
  
 `pe`  
 <span data-ttu-id="095ab-112">[içinde] Dosya arabelleği için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="095ab-112">[in] A pointer to the file buffer.</span></span>  
  
 `ulSize`  
 <span data-ttu-id="095ab-113">[içinde] Doğrulanacak dosyanın boyutu, baytlar halinde.</span><span class="sxs-lookup"><span data-stu-id="095ab-113">[in] The size, in bytes, of the file to be validated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="095ab-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="095ab-114">Return Value</span></span>  
  
|<span data-ttu-id="095ab-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="095ab-115">HRESULT</span></span>|<span data-ttu-id="095ab-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="095ab-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="095ab-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="095ab-117">S_OK</span></span>|<span data-ttu-id="095ab-118">`Validate`başarıyla döndürülür.</span><span class="sxs-lookup"><span data-stu-id="095ab-118">`Validate` returned successfully.</span></span>|  
|<span data-ttu-id="095ab-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="095ab-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="095ab-120">Ortak dil çalışma süresi (CLR) bir işleme yüklenmedi veya CLR yönetilen kodu çalıştıramadığı veya aramayı başarıyla işleyemediği bir durumdadır.</span><span class="sxs-lookup"><span data-stu-id="095ab-120">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="095ab-121">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="095ab-121">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="095ab-122">Arama zaman doldu.</span><span class="sxs-lookup"><span data-stu-id="095ab-122">The call timed out.</span></span>|  
|<span data-ttu-id="095ab-123">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="095ab-123">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="095ab-124">Arayan kilidin sahibi değildir.</span><span class="sxs-lookup"><span data-stu-id="095ab-124">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="095ab-125">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="095ab-125">HOST_E_ABANDONED</span></span>|<span data-ttu-id="095ab-126">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="095ab-126">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="095ab-127">E_faıl</span><span class="sxs-lookup"><span data-stu-id="095ab-127">E_FAIL</span></span>|<span data-ttu-id="095ab-128">Bilinmeyen bir felaket hatası meydana geldi.</span><span class="sxs-lookup"><span data-stu-id="095ab-128">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="095ab-129">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="095ab-129">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="095ab-130">Barındırma yöntemleri sonraki aramalar HOST_E_CLRNOTAVAILABLE döndürün.</span><span class="sxs-lookup"><span data-stu-id="095ab-130">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="095ab-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="095ab-131">Requirements</span></span>  
 <span data-ttu-id="095ab-132">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="095ab-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="095ab-133">**Üstbilgi:** IValidator.idl, IValidator.h</span><span class="sxs-lookup"><span data-stu-id="095ab-133">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="095ab-134">**Kütüphane:** MSCorEE.dll bir kaynak olarak dahil</span><span class="sxs-lookup"><span data-stu-id="095ab-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="095ab-135">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="095ab-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="095ab-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="095ab-136">See also</span></span>

- [<span data-ttu-id="095ab-137">ICLRValidator Arabirimi</span><span class="sxs-lookup"><span data-stu-id="095ab-137">ICLRValidator Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)
