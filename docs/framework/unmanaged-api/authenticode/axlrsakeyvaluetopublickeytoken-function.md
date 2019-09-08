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
ms.openlocfilehash: 690035ffe0724d3987a198c78bf14e668527b98a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787025"
---
# <a name="_axlrsakeyvaluetopublickeytoken-function"></a><span data-ttu-id="880f1-102">\_AxlRSAKeyValueToPublicKeyToken işlevi</span><span class="sxs-lookup"><span data-stu-id="880f1-102">\_AxlRSAKeyValueToPublicKeyToken function</span></span>

<span data-ttu-id="880f1-103">Bir mod ve üs değeri bir tanımlayıcı ad ortak anahtar belirtecine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="880f1-103">Converts a Modulus and Exponent to a strong name public key token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="880f1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="880f1-104">Syntax</span></span>  
  
```cpp  
HRESULT _AxlRSAKeyValueToPublicKeyToken (  
    [in]  PCRYPT_DATA_BLOB pModulusBlob,  
    [in]  PCRYPT_DATA_BLOB pExponentBlob,  
    [out] LPWSTR           *ppwszPublicKeyToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="880f1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="880f1-105">Parameters</span></span>  
 `pModulusBlob`  
 <span data-ttu-id="880f1-106">'ndaki Base64 kodlu mod Blobu ( \<Mod > öğesinden).</span><span class="sxs-lookup"><span data-stu-id="880f1-106">[in] The base64-encoded Modulus blob (from the \<Modulus> element).</span></span>  <span data-ttu-id="880f1-107">Bkz. [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) yapısı.</span><span class="sxs-lookup"><span data-stu-id="880f1-107">See the [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) structure.</span></span>  
  
 `pExponentBlob`  
 <span data-ttu-id="880f1-108">'ndaki Base64 ile kodlanmış üs Blobu ( \<üs > öğesinden).</span><span class="sxs-lookup"><span data-stu-id="880f1-108">[in] The base64-encoded Exponent blob (from the \<Exponent> element).</span></span> <span data-ttu-id="880f1-109">Bkz. [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) yapısı.</span><span class="sxs-lookup"><span data-stu-id="880f1-109">See the [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) structure.</span></span>  
  
 `ppwszPublicKeyToken`  
 <span data-ttu-id="880f1-110">dışı Onaltılık kodlanmış ortak anahtar belirtecini almak için bir WCHAR \* işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="880f1-110">[out] A pointer to WCHAR \* to receive the hex-encoded public key token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="880f1-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="880f1-111">Return Value</span></span>  
 <span data-ttu-id="880f1-112">`S_OK`işlev başarılı olursa.</span><span class="sxs-lookup"><span data-stu-id="880f1-112">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="880f1-113">Aksi takdirde, bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="880f1-113">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="880f1-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="880f1-114">See also</span></span>

- [<span data-ttu-id="880f1-115">Authenticode</span><span class="sxs-lookup"><span data-stu-id="880f1-115">Authenticode</span></span>](index.md)
