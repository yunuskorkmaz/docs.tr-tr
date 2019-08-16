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
ms.openlocfilehash: eca6c5fc61d4f7e80046102a560d228fc01e5292
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69038411"
---
# <a name="_axlrsakeyvaluetopublickeytoken-function"></a><span data-ttu-id="a2e60-102">\_AxlRSAKeyValueToPublicKeyToken işlevi</span><span class="sxs-lookup"><span data-stu-id="a2e60-102">\_AxlRSAKeyValueToPublicKeyToken function</span></span>

<span data-ttu-id="a2e60-103">Bir mod ve üs değeri bir tanımlayıcı ad ortak anahtar belirtecine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="a2e60-103">Converts a Modulus and Exponent to a strong name public key token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2e60-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a2e60-104">Syntax</span></span>  
  
```cpp  
HRESULT _AxlRSAKeyValueToPublicKeyToken (  
    [in]  PCRYPT_DATA_BLOB pModulusBlob,  
    [in]  PCRYPT_DATA_BLOB pExponentBlob,  
    [out] LPWSTR           *ppwszPublicKeyToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a2e60-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a2e60-105">Parameters</span></span>  
 `pModulusBlob`  
 <span data-ttu-id="a2e60-106">'ndaki Base64 kodlu mod Blobu ( \<Mod > öğesinden).</span><span class="sxs-lookup"><span data-stu-id="a2e60-106">[in] The base64-encoded Modulus blob (from the \<Modulus> element).</span></span>  <span data-ttu-id="a2e60-107">Bkz. [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) yapısı.</span><span class="sxs-lookup"><span data-stu-id="a2e60-107">See the [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) structure.</span></span>  
  
 `pExponentBlob`  
 <span data-ttu-id="a2e60-108">'ndaki Base64 ile kodlanmış üs Blobu ( \<üs > öğesinden).</span><span class="sxs-lookup"><span data-stu-id="a2e60-108">[in] The base64-encoded Exponent blob (from the \<Exponent> element).</span></span> <span data-ttu-id="a2e60-109">Bkz. [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) yapısı.</span><span class="sxs-lookup"><span data-stu-id="a2e60-109">See the [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) structure.</span></span>  
  
 `ppwszPublicKeyToken`  
 <span data-ttu-id="a2e60-110">dışı Onaltılık kodlanmış ortak anahtar belirtecini almak için bir WCHAR \* işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="a2e60-110">[out] A pointer to WCHAR \* to receive the hex-encoded public key token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a2e60-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a2e60-111">Return Value</span></span>  
 <span data-ttu-id="a2e60-112">`S_OK`işlev başarılı olursa.</span><span class="sxs-lookup"><span data-stu-id="a2e60-112">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="a2e60-113">Aksi takdirde, bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="a2e60-113">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2e60-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a2e60-114">See also</span></span>

- [<span data-ttu-id="a2e60-115">Authenticode</span><span class="sxs-lookup"><span data-stu-id="a2e60-115">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
