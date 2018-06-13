---
title: IValidator::Validate Yöntemi
ms.date: 03/30/2017
api_name:
- IValidator.Validate
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- Validate
helpviewer_keywords:
- IValidator::Validate method [.NET Framework hosting]
- Validate method, IValidator interface [.NET Framework hosting]
ms.assetid: 7d68666a-fb73-4455-bebd-908d49a16abc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cf2c343db459879ca95372e104aee68b22dee6b0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33440623"
---
# <a name="ivalidatorvalidate-method"></a><span data-ttu-id="65300-102">IValidator::Validate Yöntemi</span><span class="sxs-lookup"><span data-stu-id="65300-102">IValidator::Validate Method</span></span>
<span data-ttu-id="65300-103">Belirtilen taşınabilir yürütülebilir (PE) ya da Microsoft Ara dili (MSIL) dosya doğrular.</span><span class="sxs-lookup"><span data-stu-id="65300-103">Validates the specified portable executable (PE) or Microsoft intermediate language (MSIL) file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65300-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="65300-104">Syntax</span></span>  
  
```  
HRESULT Validate (  
    [in] IVEHandler            *veh,  
    [in] IUnknown              *pAppDomain,  
    [in] unsigned long          ulFlags,  
    [in] unsigned long          ulMaxError,  
    [in] unsigned long          token,  
    [in] LPWSTR                 fileName,  
    [in, size_is(ulSize)] BYTE *pe,  
    [in] unsigned long          ulSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="65300-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="65300-105">Parameters</span></span>  
 `veh`  
 <span data-ttu-id="65300-106">[in] Bir işaretçi bir `IVEHandler` doğrulama hataları işleyen örneği.</span><span class="sxs-lookup"><span data-stu-id="65300-106">[in] A pointer to an `IVEHandler` instance that handles validation errors.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="65300-107">[in] Dosyayı yüklendiği uygulama etki alanı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="65300-107">[in] A pointer to the application domain in which the file is loaded.</span></span>  
  
 `ulFlags`  
 <span data-ttu-id="65300-108">[in] Bit düzeyinde bileşimini [ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) gerçekleştirilmelidir doğrulamaları belirten değer.</span><span class="sxs-lookup"><span data-stu-id="65300-108">[in] A bitwise combination of [ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) values, indicating the validations that should be performed.</span></span>  
  
 `ulMaxError`  
 <span data-ttu-id="65300-109">[in] Doğrulama çıkmadan önce izin vermek için hatası sayısı.</span><span class="sxs-lookup"><span data-stu-id="65300-109">[in] The maximum number of errors to allow before exiting the validation.</span></span>  
  
 `token`  
 <span data-ttu-id="65300-110">[in] Kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="65300-110">[in] Not used.</span></span>  
  
 `fileName`  
 <span data-ttu-id="65300-111">[in] Doğrulanacak dosyasının adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="65300-111">[in] A string that specifies the name of the file to be validated.</span></span>  
  
 `pe`  
 <span data-ttu-id="65300-112">[in] Dosyanın depolandığı bellek arabellek için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="65300-112">[in] A pointer to the memory buffer in which the file is stored.</span></span>  
  
 `ulSize`  
 <span data-ttu-id="65300-113">[in] Doğrulanacak dosyasının bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="65300-113">[in] The size, in bytes, of the file to be validated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65300-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="65300-114">Requirements</span></span>  
 <span data-ttu-id="65300-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65300-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65300-116">**Başlık:** IValidator.idl, IValidator.h</span><span class="sxs-lookup"><span data-stu-id="65300-116">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="65300-117">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="65300-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="65300-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65300-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65300-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="65300-119">See Also</span></span>  
 
