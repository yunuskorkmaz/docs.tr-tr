---
description: ': IValidator:: Validate yöntemi hakkında daha fazla bilgi'
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
ms.openlocfilehash: 6df70274a788b949686fe2509b525c5a8b04089c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99680024"
---
# <a name="ivalidatorvalidate-method"></a><span data-ttu-id="82b1e-103">IValidator::Validate Yöntemi</span><span class="sxs-lookup"><span data-stu-id="82b1e-103">IValidator::Validate Method</span></span>

<span data-ttu-id="82b1e-104">Belirtilen Taşınabilir çalıştırılabilir (PE) veya Microsoft ara dili (MSIL) dosyasını doğrular.</span><span class="sxs-lookup"><span data-stu-id="82b1e-104">Validates the specified portable executable (PE) or Microsoft intermediate language (MSIL) file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82b1e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="82b1e-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="82b1e-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="82b1e-106">Parameters</span></span>  

 `veh`  
 <span data-ttu-id="82b1e-107">'ndaki `IVEHandler` Doğrulama hatalarını işleyen bir örneğe yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="82b1e-107">[in] A pointer to an `IVEHandler` instance that handles validation errors.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="82b1e-108">'ndaki Dosyanın yüklendiği uygulama etki alanına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="82b1e-108">[in] A pointer to the application domain in which the file is loaded.</span></span>  
  
 `ulFlags`  
 <span data-ttu-id="82b1e-109">'ndaki Gerçekleştirilmesi gereken doğrulamaları belirten, [ValidatorFlags](validatorflags-enumeration.md) değerlerinin bit düzeyinde birleşimi.</span><span class="sxs-lookup"><span data-stu-id="82b1e-109">[in] A bitwise combination of [ValidatorFlags](validatorflags-enumeration.md) values, indicating the validations that should be performed.</span></span>  
  
 `ulMaxError`  
 <span data-ttu-id="82b1e-110">'ndaki Doğrulamadan çıkmadan önce izin verilen en fazla hata sayısı.</span><span class="sxs-lookup"><span data-stu-id="82b1e-110">[in] The maximum number of errors to allow before exiting the validation.</span></span>  
  
 `token`  
 <span data-ttu-id="82b1e-111">'ndaki Kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="82b1e-111">[in] Not used.</span></span>  
  
 `fileName`  
 <span data-ttu-id="82b1e-112">'ndaki Doğrulanacak dosyanın adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="82b1e-112">[in] A string that specifies the name of the file to be validated.</span></span>  
  
 `pe`  
 <span data-ttu-id="82b1e-113">'ndaki Dosyanın depolandığı bellek arabelleğine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="82b1e-113">[in] A pointer to the memory buffer in which the file is stored.</span></span>  
  
 `ulSize`  
 <span data-ttu-id="82b1e-114">'ndaki Doğrulanacak dosyanın bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="82b1e-114">[in] The size, in bytes, of the file to be validated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82b1e-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="82b1e-115">Requirements</span></span>  

 <span data-ttu-id="82b1e-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="82b1e-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82b1e-117">**Üst bilgi:** IValidator. IDL, IValidator. h</span><span class="sxs-lookup"><span data-stu-id="82b1e-117">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="82b1e-118">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="82b1e-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="82b1e-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82b1e-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
