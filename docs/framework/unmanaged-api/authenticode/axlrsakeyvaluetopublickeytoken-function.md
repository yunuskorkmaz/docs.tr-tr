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
ms.openlocfilehash: e09391af9b5d71cfa423b3bf1a2b307117d0dee1
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43517604"
---
# <a name="axlrsakeyvaluetopublickeytoken-function"></a><span data-ttu-id="e3e71-102">\_AxlRSAKeyValueToPublicKeyToken işlevi</span><span class="sxs-lookup"><span data-stu-id="e3e71-102">\_AxlRSAKeyValueToPublicKeyToken function</span></span>

<span data-ttu-id="e3e71-103">Tanımlayıcı ad bir ortak anahtar belirteci için bir mod ve üs dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="e3e71-103">Converts a Modulus and Exponent to a strong name public key token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3e71-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e3e71-104">Syntax</span></span>  
  
```  
HRESULT _AxlRSAKeyValueToPublicKeyToken (  
    [in]  PCRYPT_DATA_BLOB pModulusBlob,  
    [in]  PCRYPT_DATA_BLOB pExponentBlob,  
    [out] LPWSTR           *ppwszPublicKeyToken  
);  
```  
  
### <a name="parameters"></a><span data-ttu-id="e3e71-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e3e71-105">Parameters</span></span>  
 `pModulusBlob`  
 <span data-ttu-id="e3e71-106">[in] Base64 kodlamalı Modulus blob (gelen \<Modulus > öğesi).</span><span class="sxs-lookup"><span data-stu-id="e3e71-106">[in] The base64-encoded Modulus blob (from the \<Modulus> element).</span></span>  <span data-ttu-id="e3e71-107">Bkz: [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) yapısı.</span><span class="sxs-lookup"><span data-stu-id="e3e71-107">See the [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) structure.</span></span>  
  
 `pExponentBlob`  
 <span data-ttu-id="e3e71-108">[in] Base64 kodlamalı üs blob (gelen \<üs > öğesi).</span><span class="sxs-lookup"><span data-stu-id="e3e71-108">[in] The base64-encoded Exponent blob (from the \<Exponent> element).</span></span> <span data-ttu-id="e3e71-109">Bkz: [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) yapısı.</span><span class="sxs-lookup"><span data-stu-id="e3e71-109">See the [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) structure.</span></span>  
  
 `ppwszPublicKeyToken`  
 <span data-ttu-id="e3e71-110">[out] WCHAR işaretçisi \* onaltılık kodlanmış ortak anahtar belirteci almak için.</span><span class="sxs-lookup"><span data-stu-id="e3e71-110">[out] A pointer to WCHAR \* to receive the hex-encoded public key token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e3e71-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e3e71-111">Return Value</span></span>  
 <span data-ttu-id="e3e71-112">`S_OK` işlev başarılı olursa.</span><span class="sxs-lookup"><span data-stu-id="e3e71-112">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="e3e71-113">Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="e3e71-113">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3e71-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e3e71-114">See Also</span></span>  
 [<span data-ttu-id="e3e71-115">Authenticode</span><span class="sxs-lookup"><span data-stu-id="e3e71-115">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
