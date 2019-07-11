---
title: IValidator::FormatEventInfo Yöntemi
ms.date: 03/30/2017
api_name:
- IValidator.FormatEventInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- FormatEventInfo
helpviewer_keywords:
- IValidator::FormatEventInfo method [.NET Framework hosting]
- FormatEventInfo method, IValidator interface [.NET Framework hosting]
ms.assetid: 4c0c7477-05ba-461b-b21b-cbfba95f1db1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 31329a8674a9991a3f306eeff44ee3437ad64a5c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779438"
---
# <a name="ivalidatorformateventinfo-method"></a><span data-ttu-id="4eb94-102">IValidator::FormatEventInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4eb94-102">IValidator::FormatEventInfo Method</span></span>
<span data-ttu-id="4eb94-103">Belirtilen doğrulama hatası için karşılık gelen hata iletisini alır.</span><span class="sxs-lookup"><span data-stu-id="4eb94-103">Gets the error message corresponding to the specified validation error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4eb94-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4eb94-104">Syntax</span></span>  
  
```cpp  
HRESULT FormatEventInfo(  
    [in] HRESULT            hVECode,  
    [in] VEContext          Context,  
    [in, out] LPWSTR        msg,  
    [in] unsigned long      ulMaxLength,  
    [in] SAFEARRAY(VARIANT) psa  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4eb94-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4eb94-105">Parameters</span></span>  
 `hVECode`  
 <span data-ttu-id="4eb94-106">[in] Doğrulama hata işleyicisine geçirilen HRESULT değerini.</span><span class="sxs-lookup"><span data-stu-id="4eb94-106">[in] The HRESULT value that was passed to the validation error handler.</span></span>  
  
 `Context`  
 <span data-ttu-id="4eb94-107">[in] A `VEContext` doğrulama hatası ile ilgili bağlam bilgilerini içeren bir örneği.</span><span class="sxs-lookup"><span data-stu-id="4eb94-107">[in] A `VEContext` instance that contains context information about the validation error.</span></span>  
  
 `msg`  
 <span data-ttu-id="4eb94-108">[out içinde] Döndürülen hata iletisi içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="4eb94-108">[in, out] A string that contains the returned error message.</span></span>  
  
 `ulMaxLength`  
 <span data-ttu-id="4eb94-109">[in] Hata iletisi en fazla uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="4eb94-109">[in] The maximum length of the error message.</span></span>  
  
 `psa`  
 <span data-ttu-id="4eb94-110">[in] Hatayı açıklayan ek parametreler içeren güvenli bir dizi.</span><span class="sxs-lookup"><span data-stu-id="4eb94-110">[in] A safe array that contains additional parameters describing the error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4eb94-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4eb94-111">Requirements</span></span>  
 <span data-ttu-id="4eb94-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4eb94-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4eb94-113">**Üst bilgi:** IValidator.idl, IValidator.h</span><span class="sxs-lookup"><span data-stu-id="4eb94-113">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="4eb94-114">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="4eb94-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4eb94-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4eb94-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
