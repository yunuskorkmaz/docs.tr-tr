---
description: ': IValidator:: FormatEventInfo Yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 28ecf9ab2b14cd2fdd178a4ad9d8e218f7038a9d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99680167"
---
# <a name="ivalidatorformateventinfo-method"></a><span data-ttu-id="4d7ac-103">IValidator::FormatEventInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4d7ac-103">IValidator::FormatEventInfo Method</span></span>

<span data-ttu-id="4d7ac-104">Belirtilen doğrulama hatasına karşılık gelen hata iletisini alır.</span><span class="sxs-lookup"><span data-stu-id="4d7ac-104">Gets the error message corresponding to the specified validation error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d7ac-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4d7ac-105">Syntax</span></span>  
  
```cpp  
HRESULT FormatEventInfo(  
    [in] HRESULT            hVECode,  
    [in] VEContext          Context,  
    [in, out] LPWSTR        msg,  
    [in] unsigned long      ulMaxLength,  
    [in] SAFEARRAY(VARIANT) psa  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4d7ac-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4d7ac-106">Parameters</span></span>  

 `hVECode`  
 <span data-ttu-id="4d7ac-107">'ndaki Doğrulama hata işleyicisine geçirilen HRESULT değeri.</span><span class="sxs-lookup"><span data-stu-id="4d7ac-107">[in] The HRESULT value that was passed to the validation error handler.</span></span>  
  
 `Context`  
 <span data-ttu-id="4d7ac-108">'ndaki `VEContext` Doğrulama hatası hakkında bağlam bilgilerini içeren bir örnek.</span><span class="sxs-lookup"><span data-stu-id="4d7ac-108">[in] A `VEContext` instance that contains context information about the validation error.</span></span>  
  
 `msg`  
 <span data-ttu-id="4d7ac-109">[in, out] Döndürülen hata iletisini içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="4d7ac-109">[in, out] A string that contains the returned error message.</span></span>  
  
 `ulMaxLength`  
 <span data-ttu-id="4d7ac-110">'ndaki Hata iletisinin en fazla uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="4d7ac-110">[in] The maximum length of the error message.</span></span>  
  
 `psa`  
 <span data-ttu-id="4d7ac-111">'ndaki Hatayı açıklayan ek parametreler içeren bir güvenli dizi.</span><span class="sxs-lookup"><span data-stu-id="4d7ac-111">[in] A safe array that contains additional parameters describing the error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d7ac-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4d7ac-112">Requirements</span></span>  

 <span data-ttu-id="4d7ac-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4d7ac-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d7ac-114">**Üst bilgi:** IValidator. IDL, IValidator. h</span><span class="sxs-lookup"><span data-stu-id="4d7ac-114">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="4d7ac-115">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="4d7ac-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4d7ac-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d7ac-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
