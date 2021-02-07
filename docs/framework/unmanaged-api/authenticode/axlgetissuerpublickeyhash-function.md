---
description: 'Hakkında daha fazla bilgi edinin: _AxlGetIssuerPublicKeyHash Işlevi'
title: _AxlGetIssuerPublicKeyHash İşlevi
ms.date: 03/30/2017
api_name:
- _AxlGetIssuerPublicKeyHash
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: fb626b41-b888-4625-84c3-2c02b5e3866f
topic_type:
- apiref
ms.openlocfilehash: 586a072b33376a2fdade119fe3db0f48addfa3f5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747367"
---
# <a name="_axlgetissuerpublickeyhash-function"></a><span data-ttu-id="919c1-103">\_Axlgetıserpublickeyhash Işlevi</span><span class="sxs-lookup"><span data-stu-id="919c1-103">\_AxlGetIssuerPublicKeyHash Function</span></span>

<span data-ttu-id="919c1-104">Belirtilen sertifikayı imzalamak için kullanılan özel anahtarla ilişkili ortak anahtarın SHA-1 karmasını alır.</span><span class="sxs-lookup"><span data-stu-id="919c1-104">Retrieves the SHA-1 hash of the public key associated with the private key that is used to sign the specified certificate.</span></span>

## <a name="syntax"></a><span data-ttu-id="919c1-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="919c1-105">Syntax</span></span>

```cpp
HRESULT _AxlGetIssuerPublicKeyHash (
    [in]  IN PCRYPT_DATA_BLOB   pChainContext,
    [out] LPWSTR                *ppwszPublicKeyHash
);
```

## <a name="parameters"></a><span data-ttu-id="919c1-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="919c1-106">Parameters</span></span>

 `pChainContext`\
 <span data-ttu-id="919c1-107">'ndaki CSP ortak anahtar blobu.</span><span class="sxs-lookup"><span data-stu-id="919c1-107">[in] The CSP public key blob.</span></span> <span data-ttu-id="919c1-108">[CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) yapısına bakın.</span><span class="sxs-lookup"><span data-stu-id="919c1-108">See the [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) structure.</span></span>

 `ppwszPublicKeyHash`\
 <span data-ttu-id="919c1-109">dışı Onaltılık kodlanmış ortak anahtar belirtecini almak için bir WCHAR \* işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="919c1-109">[out] A pointer to WCHAR \* to receive the hex-encoded public key token.</span></span>

## <a name="return-value"></a><span data-ttu-id="919c1-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="919c1-110">Return Value</span></span>

 <span data-ttu-id="919c1-111">`S_OK` işlev başarılı olursa; Aksi takdirde `S_FALSE` .</span><span class="sxs-lookup"><span data-stu-id="919c1-111">`S_OK` if the function succeeds; otherwise `S_FALSE`.</span></span>

## <a name="requirements"></a><span data-ttu-id="919c1-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="919c1-112">Requirements</span></span>

<span data-ttu-id="919c1-113">**Bütünleştirilmiş kod**: clr.dll</span><span class="sxs-lookup"><span data-stu-id="919c1-113">**Assembly**: clr.dll</span></span>

## <a name="see-also"></a><span data-ttu-id="919c1-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="919c1-114">See also</span></span>

- [<span data-ttu-id="919c1-115">Authenticode</span><span class="sxs-lookup"><span data-stu-id="919c1-115">Authenticode</span></span>](index.md)
