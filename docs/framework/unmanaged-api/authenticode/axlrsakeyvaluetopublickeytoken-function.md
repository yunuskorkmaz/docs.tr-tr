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
ms.openlocfilehash: 5c1e2bfc7fd55e807af68744e28faa473daea772
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674222"
---
# <a name="_axlrsakeyvaluetopublickeytoken-function"></a><span data-ttu-id="b369a-102">\_AxlRSAKeyValueToPublicKeyToken işlevi</span><span class="sxs-lookup"><span data-stu-id="b369a-102">\_AxlRSAKeyValueToPublicKeyToken function</span></span>

<span data-ttu-id="b369a-103">Bir mod ve üs değeri bir tanımlayıcı ad ortak anahtar belirtecine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="b369a-103">Converts a Modulus and Exponent to a strong name public key token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b369a-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="b369a-104">Syntax</span></span>  
  
```cpp  
HRESULT _AxlRSAKeyValueToPublicKeyToken (  
    [in]  PCRYPT_DATA_BLOB pModulusBlob,  
    [in]  PCRYPT_DATA_BLOB pExponentBlob,  
    [out] LPWSTR           *ppwszPublicKeyToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b369a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b369a-105">Parameters</span></span>  

 `pModulusBlob`  
 <span data-ttu-id="b369a-106">'ndaki Base64 ile kodlanmış mod Blobu (öğesinden \<Modulus> ).</span><span class="sxs-lookup"><span data-stu-id="b369a-106">[in] The base64-encoded Modulus blob (from the \<Modulus> element).</span></span>  <span data-ttu-id="b369a-107">[CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) yapısına bakın.</span><span class="sxs-lookup"><span data-stu-id="b369a-107">See the [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) structure.</span></span>  
  
 `pExponentBlob`  
 <span data-ttu-id="b369a-108">'ndaki Base64 ile kodlanmış üs Blobu (öğesinden \<Exponent> ).</span><span class="sxs-lookup"><span data-stu-id="b369a-108">[in] The base64-encoded Exponent blob (from the \<Exponent> element).</span></span> <span data-ttu-id="b369a-109">[CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) yapısına bakın.</span><span class="sxs-lookup"><span data-stu-id="b369a-109">See the [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) structure.</span></span>  
  
 `ppwszPublicKeyToken`  
 <span data-ttu-id="b369a-110">dışı Onaltılık kodlanmış ortak anahtar belirtecini almak için bir WCHAR \* işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="b369a-110">[out] A pointer to WCHAR \* to receive the hex-encoded public key token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b369a-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b369a-111">Return Value</span></span>  

 <span data-ttu-id="b369a-112">`S_OK` işlev başarılı olursa.</span><span class="sxs-lookup"><span data-stu-id="b369a-112">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="b369a-113">Aksi takdirde, bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="b369a-113">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b369a-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b369a-114">See also</span></span>

- [<span data-ttu-id="b369a-115">Authenticode</span><span class="sxs-lookup"><span data-stu-id="b369a-115">Authenticode</span></span>](index.md)
