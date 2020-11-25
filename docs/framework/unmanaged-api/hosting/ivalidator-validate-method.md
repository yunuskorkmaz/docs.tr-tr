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
ms.openlocfilehash: 3c59114f78af1aa8705318af093e47d4f03a82ce
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95699150"
---
# <a name="ivalidatorvalidate-method"></a><span data-ttu-id="9d03b-102">IValidator::Validate Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9d03b-102">IValidator::Validate Method</span></span>

<span data-ttu-id="9d03b-103">Belirtilen Taşınabilir çalıştırılabilir (PE) veya Microsoft ara dili (MSIL) dosyasını doğrular.</span><span class="sxs-lookup"><span data-stu-id="9d03b-103">Validates the specified portable executable (PE) or Microsoft intermediate language (MSIL) file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d03b-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="9d03b-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="9d03b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9d03b-105">Parameters</span></span>  

 `veh`  
 <span data-ttu-id="9d03b-106">'ndaki `IVEHandler` Doğrulama hatalarını işleyen bir örneğe yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9d03b-106">[in] A pointer to an `IVEHandler` instance that handles validation errors.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="9d03b-107">'ndaki Dosyanın yüklendiği uygulama etki alanına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9d03b-107">[in] A pointer to the application domain in which the file is loaded.</span></span>  
  
 `ulFlags`  
 <span data-ttu-id="9d03b-108">'ndaki Gerçekleştirilmesi gereken doğrulamaları belirten, [ValidatorFlags](validatorflags-enumeration.md) değerlerinin bit düzeyinde birleşimi.</span><span class="sxs-lookup"><span data-stu-id="9d03b-108">[in] A bitwise combination of [ValidatorFlags](validatorflags-enumeration.md) values, indicating the validations that should be performed.</span></span>  
  
 `ulMaxError`  
 <span data-ttu-id="9d03b-109">'ndaki Doğrulamadan çıkmadan önce izin verilen en fazla hata sayısı.</span><span class="sxs-lookup"><span data-stu-id="9d03b-109">[in] The maximum number of errors to allow before exiting the validation.</span></span>  
  
 `token`  
 <span data-ttu-id="9d03b-110">'ndaki Kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="9d03b-110">[in] Not used.</span></span>  
  
 `fileName`  
 <span data-ttu-id="9d03b-111">'ndaki Doğrulanacak dosyanın adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="9d03b-111">[in] A string that specifies the name of the file to be validated.</span></span>  
  
 `pe`  
 <span data-ttu-id="9d03b-112">'ndaki Dosyanın depolandığı bellek arabelleğine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9d03b-112">[in] A pointer to the memory buffer in which the file is stored.</span></span>  
  
 `ulSize`  
 <span data-ttu-id="9d03b-113">'ndaki Doğrulanacak dosyanın bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="9d03b-113">[in] The size, in bytes, of the file to be validated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d03b-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9d03b-114">Requirements</span></span>  

 <span data-ttu-id="9d03b-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d03b-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d03b-116">**Üst bilgi:** IValidator. IDL, IValidator. h</span><span class="sxs-lookup"><span data-stu-id="9d03b-116">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="9d03b-117">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="9d03b-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9d03b-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d03b-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
