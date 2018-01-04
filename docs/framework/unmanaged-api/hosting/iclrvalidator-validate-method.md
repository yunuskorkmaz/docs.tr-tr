---
title: "ICLRValidator::Validate Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRValidator.Validate
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRValidator::Validate
helpviewer_keywords:
- Validate method, ICLRValidator interface [.NET Framework hosting]
- ICLRValidator::Validate method [.NET Framework hosting]
ms.assetid: 0b1b432a-d234-4002-839b-81366c3a8bdc
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7328fe62276de6c33464ab8cfc6d6a5f39ee710e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrvalidatorvalidate-method"></a><span data-ttu-id="63c49-102">ICLRValidator::Validate Yöntemi</span><span class="sxs-lookup"><span data-stu-id="63c49-102">ICLRValidator::Validate Method</span></span>
<span data-ttu-id="63c49-103">Taşınabilir yürütülebilir (PE) ya da Microsoft Ara dili (MSIL) belirtilen dosyada doğrular.</span><span class="sxs-lookup"><span data-stu-id="63c49-103">Validates the portable executable (PE) or Microsoft intermediate language (MSIL) in the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63c49-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="63c49-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="63c49-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="63c49-105">Parameters</span></span>  
 `veh`  
 <span data-ttu-id="63c49-106">[in] Bir işaretçi bir `IVEHandler` doğrulama hataları işleyen örneği.</span><span class="sxs-lookup"><span data-stu-id="63c49-106">[in] A pointer to an `IVEHandler` instance that handles validation errors.</span></span>  
  
 `ulAppDomainId`  
 <span data-ttu-id="63c49-107">[in] Geçerli tanımlayıcısını <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="63c49-107">[in] The identifier for the current <xref:System.AppDomain>.</span></span>  
  
 `ulFlags`  
 <span data-ttu-id="63c49-108">[in] Bir birleşimini [ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) gerçekleştirilmelidir doğrulama türünü belirten değer.</span><span class="sxs-lookup"><span data-stu-id="63c49-108">[in] A combination of [ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) values, indicating the kind of validation that should be performed.</span></span>  
  
 `ulMaxError`  
 <span data-ttu-id="63c49-109">[in] Doğrulama çıkmadan önce izin vermek için hatası sayısı.</span><span class="sxs-lookup"><span data-stu-id="63c49-109">[in] The maximum number of errors to allow before exiting the validation.</span></span>  
  
 `token`  
 <span data-ttu-id="63c49-110">[in] Kullanılmayan.</span><span class="sxs-lookup"><span data-stu-id="63c49-110">[in] Unused.</span></span>  
  
 `fileName`  
 <span data-ttu-id="63c49-111">[in] Doğrulanacak dosyasının adı.</span><span class="sxs-lookup"><span data-stu-id="63c49-111">[in] The name of the file to be validated.</span></span>  
  
 `pe`  
 <span data-ttu-id="63c49-112">[in] Dosya arabellek için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="63c49-112">[in] A pointer to the file buffer.</span></span>  
  
 `ulSize`  
 <span data-ttu-id="63c49-113">[in] Doğrulanacak dosyasının bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="63c49-113">[in] The size, in bytes, of the file to be validated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="63c49-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="63c49-114">Return Value</span></span>  
  
|<span data-ttu-id="63c49-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="63c49-115">HRESULT</span></span>|<span data-ttu-id="63c49-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="63c49-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="63c49-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="63c49-117">S_OK</span></span>|<span data-ttu-id="63c49-118">`Validate`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="63c49-118">`Validate` returned successfully.</span></span>|  
|<span data-ttu-id="63c49-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="63c49-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="63c49-120">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="63c49-120">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="63c49-121">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="63c49-121">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="63c49-122">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="63c49-122">The call timed out.</span></span>|  
|<span data-ttu-id="63c49-123">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="63c49-123">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="63c49-124">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="63c49-124">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="63c49-125">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="63c49-125">HOST_E_ABANDONED</span></span>|<span data-ttu-id="63c49-126">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="63c49-126">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="63c49-127">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="63c49-127">E_FAIL</span></span>|<span data-ttu-id="63c49-128">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="63c49-128">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="63c49-129">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="63c49-129">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="63c49-130">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="63c49-130">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="63c49-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="63c49-131">Requirements</span></span>  
 <span data-ttu-id="63c49-132">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63c49-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63c49-133">**Başlık:** IValidator.idl, IValidator.h</span><span class="sxs-lookup"><span data-stu-id="63c49-133">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="63c49-134">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="63c49-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="63c49-135">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63c49-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63c49-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="63c49-136">See Also</span></span>  
 [<span data-ttu-id="63c49-137">ICLRValidator Arabirimi</span><span class="sxs-lookup"><span data-stu-id="63c49-137">ICLRValidator Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)
