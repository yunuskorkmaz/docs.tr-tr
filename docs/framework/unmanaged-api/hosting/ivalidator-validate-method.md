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
ms.openlocfilehash: 1fba06360a0c31e0a7fa3e61de9793bad14650fa
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59127510"
---
# <a name="ivalidatorvalidate-method"></a><span data-ttu-id="ab185-102">IValidator::Validate Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ab185-102">IValidator::Validate Method</span></span>
<span data-ttu-id="ab185-103">Belirtilen taşınabilir yürütülebilir (PE) veya Microsoft Ara dili (MSIL) dosyası doğrular.</span><span class="sxs-lookup"><span data-stu-id="ab185-103">Validates the specified portable executable (PE) or Microsoft intermediate language (MSIL) file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab185-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ab185-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="ab185-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ab185-105">Parameters</span></span>  
 `veh`  
 <span data-ttu-id="ab185-106">[in] Bir işaretçi bir `IVEHandler` doğrulama hatalarını işleyen örneği.</span><span class="sxs-lookup"><span data-stu-id="ab185-106">[in] A pointer to an `IVEHandler` instance that handles validation errors.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="ab185-107">[in] Dosya yüklendiği uygulama etki alanı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ab185-107">[in] A pointer to the application domain in which the file is loaded.</span></span>  
  
 `ulFlags`  
 <span data-ttu-id="ab185-108">[in] Bitsel bir birleşimi [ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) gerçekleştirilmelidir Doğrulamalar gösteren değer.</span><span class="sxs-lookup"><span data-stu-id="ab185-108">[in] A bitwise combination of [ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) values, indicating the validations that should be performed.</span></span>  
  
 `ulMaxError`  
 <span data-ttu-id="ab185-109">[in] Doğrulama çıkmadan önce izin vermek için hataları sayısı.</span><span class="sxs-lookup"><span data-stu-id="ab185-109">[in] The maximum number of errors to allow before exiting the validation.</span></span>  
  
 `token`  
 <span data-ttu-id="ab185-110">[in] Kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="ab185-110">[in] Not used.</span></span>  
  
 `fileName`  
 <span data-ttu-id="ab185-111">[in] Doğrulanacak dosyasının adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="ab185-111">[in] A string that specifies the name of the file to be validated.</span></span>  
  
 `pe`  
 <span data-ttu-id="ab185-112">[in] Dosyanın depolandığı ara belleğe yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ab185-112">[in] A pointer to the memory buffer in which the file is stored.</span></span>  
  
 `ulSize`  
 <span data-ttu-id="ab185-113">[in] Doğrulanacak dosyasının bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="ab185-113">[in] The size, in bytes, of the file to be validated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab185-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ab185-114">Requirements</span></span>  
 <span data-ttu-id="ab185-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab185-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab185-116">**Üst bilgi:** IValidator.idl, IValidator.h</span><span class="sxs-lookup"><span data-stu-id="ab185-116">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="ab185-117">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="ab185-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="ab185-118">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="ab185-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
