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
ms.openlocfilehash: 4f9981c4cf2e45795576024b797f93831324dbc9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741272"
---
# <a name="axlrsakeyvaluetopublickeytoken-function"></a><span data-ttu-id="ce5f8-102">\_AxlRSAKeyValueToPublicKeyToken işlevi</span><span class="sxs-lookup"><span data-stu-id="ce5f8-102">\_AxlRSAKeyValueToPublicKeyToken function</span></span>

<span data-ttu-id="ce5f8-103">Tanımlayıcı ad bir ortak anahtar belirteci için bir mod ve üs dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="ce5f8-103">Converts a Modulus and Exponent to a strong name public key token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce5f8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ce5f8-104">Syntax</span></span>  
  
```cpp  
HRESULT _AxlRSAKeyValueToPublicKeyToken (  
    [in]  PCRYPT_DATA_BLOB pModulusBlob,  
    [in]  PCRYPT_DATA_BLOB pExponentBlob,  
    [out] LPWSTR           *ppwszPublicKeyToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ce5f8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ce5f8-105">Parameters</span></span>  
 `pModulusBlob`  
 <span data-ttu-id="ce5f8-106">[in] Base64 kodlamalı Modulus blob (gelen \<Modulus > öğesi).</span><span class="sxs-lookup"><span data-stu-id="ce5f8-106">[in] The base64-encoded Modulus blob (from the \<Modulus> element).</span></span>  <span data-ttu-id="ce5f8-107">Bkz: [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) yapısı.</span><span class="sxs-lookup"><span data-stu-id="ce5f8-107">See the [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) structure.</span></span>  
  
 `pExponentBlob`  
 <span data-ttu-id="ce5f8-108">[in] Base64 kodlamalı üs blob (gelen \<üs > öğesi).</span><span class="sxs-lookup"><span data-stu-id="ce5f8-108">[in] The base64-encoded Exponent blob (from the \<Exponent> element).</span></span> <span data-ttu-id="ce5f8-109">Bkz: [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) yapısı.</span><span class="sxs-lookup"><span data-stu-id="ce5f8-109">See the [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) structure.</span></span>  
  
 `ppwszPublicKeyToken`  
 <span data-ttu-id="ce5f8-110">[out] WCHAR işaretçisi \* onaltılık kodlanmış ortak anahtar belirteci almak için.</span><span class="sxs-lookup"><span data-stu-id="ce5f8-110">[out] A pointer to WCHAR \* to receive the hex-encoded public key token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ce5f8-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ce5f8-111">Return Value</span></span>  
 <span data-ttu-id="ce5f8-112">`S_OK` işlev başarılı olursa.</span><span class="sxs-lookup"><span data-stu-id="ce5f8-112">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="ce5f8-113">Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="ce5f8-113">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce5f8-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ce5f8-114">See also</span></span>

- [<span data-ttu-id="ce5f8-115">Authenticode</span><span class="sxs-lookup"><span data-stu-id="ce5f8-115">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
