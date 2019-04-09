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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 559c265c70c199e64782ba185d4925d293d6a778
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59158697"
---
# <a name="iclrvalidatorvalidate-method"></a><span data-ttu-id="e8337-102">ICLRValidator::Validate Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e8337-102">ICLRValidator::Validate Method</span></span>
<span data-ttu-id="e8337-103">Taşınabilir yürütülebilir (PE) veya belirtilen dosyadaki Microsoft Ara dilini (MSIL) doğrular.</span><span class="sxs-lookup"><span data-stu-id="e8337-103">Validates the portable executable (PE) or Microsoft intermediate language (MSIL) in the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8337-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e8337-104">Syntax</span></span>  
  
```  
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
  
## <a name="parameters"></a><span data-ttu-id="e8337-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e8337-105">Parameters</span></span>  
 `veh`  
 <span data-ttu-id="e8337-106">[in] Bir işaretçi bir `IVEHandler` doğrulama hatalarını işleyen örneği.</span><span class="sxs-lookup"><span data-stu-id="e8337-106">[in] A pointer to an `IVEHandler` instance that handles validation errors.</span></span>  
  
 `ulAppDomainId`  
 <span data-ttu-id="e8337-107">[in] Geçerli bir tanımlayıcı <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="e8337-107">[in] The identifier for the current <xref:System.AppDomain>.</span></span>  
  
 `ulFlags`  
 <span data-ttu-id="e8337-108">[in] Bir birleşimi [ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) gerçekleştirilmelidir doğrulama türünü belirten değer.</span><span class="sxs-lookup"><span data-stu-id="e8337-108">[in] A combination of [ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) values, indicating the kind of validation that should be performed.</span></span>  
  
 `ulMaxError`  
 <span data-ttu-id="e8337-109">[in] Doğrulama çıkmadan önce izin vermek için hataları sayısı.</span><span class="sxs-lookup"><span data-stu-id="e8337-109">[in] The maximum number of errors to allow before exiting the validation.</span></span>  
  
 `token`  
 <span data-ttu-id="e8337-110">[in] Kullanılmayan.</span><span class="sxs-lookup"><span data-stu-id="e8337-110">[in] Unused.</span></span>  
  
 `fileName`  
 <span data-ttu-id="e8337-111">[in] Doğrulanacak olan dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="e8337-111">[in] The name of the file to be validated.</span></span>  
  
 `pe`  
 <span data-ttu-id="e8337-112">[in] Dosya arabellek için işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e8337-112">[in] A pointer to the file buffer.</span></span>  
  
 `ulSize`  
 <span data-ttu-id="e8337-113">[in] Doğrulanacak dosyasının bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="e8337-113">[in] The size, in bytes, of the file to be validated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e8337-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e8337-114">Return Value</span></span>  
  
|<span data-ttu-id="e8337-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e8337-115">HRESULT</span></span>|<span data-ttu-id="e8337-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e8337-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e8337-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="e8337-117">S_OK</span></span>|`Validate` <span data-ttu-id="e8337-118">başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="e8337-118">returned successfully.</span></span>|  
|<span data-ttu-id="e8337-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e8337-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e8337-120">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="e8337-120">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e8337-121">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e8337-121">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e8337-122">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="e8337-122">The call timed out.</span></span>|  
|<span data-ttu-id="e8337-123">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e8337-123">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e8337-124">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="e8337-124">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e8337-125">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e8337-125">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e8337-126">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="e8337-126">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e8337-127">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e8337-127">E_FAIL</span></span>|<span data-ttu-id="e8337-128">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="e8337-128">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e8337-129">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="e8337-129">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e8337-130">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="e8337-130">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e8337-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e8337-131">Requirements</span></span>  
 <span data-ttu-id="e8337-132">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e8337-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8337-133">**Üst bilgi:** IValidator.idl, IValidator.h</span><span class="sxs-lookup"><span data-stu-id="e8337-133">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="e8337-134">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="e8337-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="e8337-135">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="e8337-135">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e8337-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e8337-136">See also</span></span>

- [<span data-ttu-id="e8337-137">ICLRValidator Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e8337-137">ICLRValidator Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)
