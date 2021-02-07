---
description: 'Hakkında daha fazla bilgi edinin: _AxlRSAKeyValueToPublicKeyToken işlevi'
title: _AxlRSAKeyValueToPublicKeyToken işlevi
ms.date: 03/30/2017
api_name:
- _AxlRSAKeyValueToPublicKeyToken
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: d60f19fe-7bec-47ba-b60e-ba9ce66abf8c
topic_type:
- apiref
ms.openlocfilehash: 01fc4cdc1d9985375748307ca2d7fff97191c908
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747276"
---
# <a name="_axlrsakeyvaluetopublickeytoken-function"></a><span data-ttu-id="d48d5-103">\_AxlRSAKeyValueToPublicKeyToken işlevi</span><span class="sxs-lookup"><span data-stu-id="d48d5-103">\_AxlRSAKeyValueToPublicKeyToken function</span></span>

<span data-ttu-id="d48d5-104">Bir mod ve üs değeri bir tanımlayıcı ad ortak anahtar belirtecine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="d48d5-104">Converts a Modulus and Exponent to a strong name public key token.</span></span>

## <a name="syntax"></a><span data-ttu-id="d48d5-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d48d5-105">Syntax</span></span>

```cpp
HRESULT _AxlRSAKeyValueToPublicKeyToken (
    [in]  PCRYPT_DATA_BLOB pModulusBlob,
    [in]  PCRYPT_DATA_BLOB pExponentBlob,
    [out] LPWSTR           *ppwszPublicKeyToken
);
```

## <a name="parameters"></a><span data-ttu-id="d48d5-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d48d5-106">Parameters</span></span>

 `pModulusBlob`\
 <span data-ttu-id="d48d5-107">'ndaki Base64 ile kodlanmış mod Blobu (öğesinden \<Modulus> ).</span><span class="sxs-lookup"><span data-stu-id="d48d5-107">[in] The base64-encoded Modulus blob (from the \<Modulus> element).</span></span>  <span data-ttu-id="d48d5-108">[CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) yapısına bakın.</span><span class="sxs-lookup"><span data-stu-id="d48d5-108">See the [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) structure.</span></span>

 `pExponentBlob`\
 <span data-ttu-id="d48d5-109">'ndaki Base64 ile kodlanmış üs Blobu (öğesinden \<Exponent> ).</span><span class="sxs-lookup"><span data-stu-id="d48d5-109">[in] The base64-encoded Exponent blob (from the \<Exponent> element).</span></span> <span data-ttu-id="d48d5-110">[CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) yapısına bakın.</span><span class="sxs-lookup"><span data-stu-id="d48d5-110">See the [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) structure.</span></span>

 `ppwszPublicKeyToken`\
 <span data-ttu-id="d48d5-111">dışı Onaltılık kodlanmış ortak anahtar belirtecini almak için bir WCHAR \* işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="d48d5-111">[out] A pointer to WCHAR \* to receive the hex-encoded public key token.</span></span>

## <a name="return-value"></a><span data-ttu-id="d48d5-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d48d5-112">Return Value</span></span>

 <span data-ttu-id="d48d5-113">`S_OK` işlev başarılı olursa.</span><span class="sxs-lookup"><span data-stu-id="d48d5-113">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="d48d5-114">Aksi takdirde, bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="d48d5-114">Otherwise, returns an error code.</span></span>

## <a name="requirements"></a><span data-ttu-id="d48d5-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d48d5-115">Requirements</span></span>

<span data-ttu-id="d48d5-116">**Bütünleştirilmiş kod**: clr.dll</span><span class="sxs-lookup"><span data-stu-id="d48d5-116">**Assembly**: clr.dll</span></span>

## <a name="see-also"></a><span data-ttu-id="d48d5-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d48d5-117">See also</span></span>

- [<span data-ttu-id="d48d5-118">Authenticode</span><span class="sxs-lookup"><span data-stu-id="d48d5-118">Authenticode</span></span>](index.md)
