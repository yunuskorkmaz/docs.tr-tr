---
title: _AxlRSAKeyValueToPublicKeyToken işlevi
ms.date: 03/30/2017
api_name:
- _AxlRSAKeyValueToPublicKeyToken
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: d60f19fe-7bec-47ba-b60e-ba9ce66abf8c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 640940cea30b489683972debdd14b592d565ef4b
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57469697"
---
# <a name="axlrsakeyvaluetopublickeytoken-function"></a><span data-ttu-id="41f8e-102">\_AxlRSAKeyValueToPublicKeyToken işlevi</span><span class="sxs-lookup"><span data-stu-id="41f8e-102">\_AxlRSAKeyValueToPublicKeyToken function</span></span>

<span data-ttu-id="41f8e-103">Tanımlayıcı ad bir ortak anahtar belirteci için bir mod ve üs dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="41f8e-103">Converts a Modulus and Exponent to a strong name public key token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41f8e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="41f8e-104">Syntax</span></span>  
  
```  
HRESULT _AxlRSAKeyValueToPublicKeyToken (  
    [in]  PCRYPT_DATA_BLOB pModulusBlob,  
    [in]  PCRYPT_DATA_BLOB pExponentBlob,  
    [out] LPWSTR           *ppwszPublicKeyToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="41f8e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="41f8e-105">Parameters</span></span>  
 `pModulusBlob`  
 <span data-ttu-id="41f8e-106">[in] Base64 kodlamalı Modulus blob (gelen \<Modulus > öğesi).</span><span class="sxs-lookup"><span data-stu-id="41f8e-106">[in] The base64-encoded Modulus blob (from the \<Modulus> element).</span></span>  <span data-ttu-id="41f8e-107">Bkz: [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) yapısı.</span><span class="sxs-lookup"><span data-stu-id="41f8e-107">See the [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) structure.</span></span>  
  
 `pExponentBlob`  
 <span data-ttu-id="41f8e-108">[in] Base64 kodlamalı üs blob (gelen \<üs > öğesi).</span><span class="sxs-lookup"><span data-stu-id="41f8e-108">[in] The base64-encoded Exponent blob (from the \<Exponent> element).</span></span> <span data-ttu-id="41f8e-109">Bkz: [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) yapısı.</span><span class="sxs-lookup"><span data-stu-id="41f8e-109">See the [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) structure.</span></span>  
  
 `ppwszPublicKeyToken`  
 <span data-ttu-id="41f8e-110">[out] WCHAR işaretçisi \* onaltılık kodlanmış ortak anahtar belirteci almak için.</span><span class="sxs-lookup"><span data-stu-id="41f8e-110">[out] A pointer to WCHAR \* to receive the hex-encoded public key token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="41f8e-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="41f8e-111">Return Value</span></span>  
 <span data-ttu-id="41f8e-112">`S_OK` işlev başarılı olursa.</span><span class="sxs-lookup"><span data-stu-id="41f8e-112">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="41f8e-113">Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="41f8e-113">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41f8e-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="41f8e-114">See also</span></span>
- [<span data-ttu-id="41f8e-115">Authenticode</span><span class="sxs-lookup"><span data-stu-id="41f8e-115">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
