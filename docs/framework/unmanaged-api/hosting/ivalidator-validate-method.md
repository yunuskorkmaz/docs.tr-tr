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
ms.openlocfilehash: 8ae47eac713fbee30ea543538957b12460b8e1fc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123279"
---
# <a name="ivalidatorvalidate-method"></a><span data-ttu-id="b1e26-102">IValidator::Validate Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b1e26-102">IValidator::Validate Method</span></span>
<span data-ttu-id="b1e26-103">Belirtilen Taşınabilir çalıştırılabilir (PE) veya Microsoft ara dili (MSIL) dosyasını doğrular.</span><span class="sxs-lookup"><span data-stu-id="b1e26-103">Validates the specified portable executable (PE) or Microsoft intermediate language (MSIL) file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1e26-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b1e26-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="b1e26-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b1e26-105">Parameters</span></span>  
 `veh`  
 <span data-ttu-id="b1e26-106">'ndaki Doğrulama hatalarını işleyen `IVEHandler` örneğine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b1e26-106">[in] A pointer to an `IVEHandler` instance that handles validation errors.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="b1e26-107">'ndaki Dosyanın yüklendiği uygulama etki alanına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b1e26-107">[in] A pointer to the application domain in which the file is loaded.</span></span>  
  
 `ulFlags`  
 <span data-ttu-id="b1e26-108">'ndaki Gerçekleştirilmesi gereken doğrulamaları belirten, [ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) değerlerinin bit düzeyinde birleşimi.</span><span class="sxs-lookup"><span data-stu-id="b1e26-108">[in] A bitwise combination of [ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) values, indicating the validations that should be performed.</span></span>  
  
 `ulMaxError`  
 <span data-ttu-id="b1e26-109">'ndaki Doğrulamadan çıkmadan önce izin verilen en fazla hata sayısı.</span><span class="sxs-lookup"><span data-stu-id="b1e26-109">[in] The maximum number of errors to allow before exiting the validation.</span></span>  
  
 `token`  
 <span data-ttu-id="b1e26-110">'ndaki Kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="b1e26-110">[in] Not used.</span></span>  
  
 `fileName`  
 <span data-ttu-id="b1e26-111">'ndaki Doğrulanacak dosyanın adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="b1e26-111">[in] A string that specifies the name of the file to be validated.</span></span>  
  
 `pe`  
 <span data-ttu-id="b1e26-112">'ndaki Dosyanın depolandığı bellek arabelleğine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b1e26-112">[in] A pointer to the memory buffer in which the file is stored.</span></span>  
  
 `ulSize`  
 <span data-ttu-id="b1e26-113">'ndaki Doğrulanacak dosyanın bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="b1e26-113">[in] The size, in bytes, of the file to be validated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1e26-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b1e26-114">Requirements</span></span>  
 <span data-ttu-id="b1e26-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1e26-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1e26-116">**Üst bilgi:** IValidator. IDL, IValidator. h</span><span class="sxs-lookup"><span data-stu-id="b1e26-116">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="b1e26-117">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="b1e26-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b1e26-118">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1e26-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
