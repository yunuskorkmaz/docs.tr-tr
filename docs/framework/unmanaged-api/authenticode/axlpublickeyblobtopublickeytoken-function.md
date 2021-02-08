---
description: 'Hakkında daha fazla bilgi edinin: _AxlPublicKeyBlobToPublicKeyToken Işlevi'
title: _AxlPublicKeyBlobToPublicKeyToken İşlevi
ms.date: 03/30/2017
api_name:
- _AxlPublicKeyBlobToPublicKeyToken
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: 2d92a746-d68c-4f53-a16e-727f071a2d80
topic_type:
- apiref
ms.openlocfilehash: df0b484bad64051eb892d4898a6c90777cc2d5cf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781941"
---
# <a name="_axlpublickeyblobtopublickeytoken-function"></a><span data-ttu-id="1c439-103">\_AxlPublicKeyBlobToPublicKeyToken Işlevi</span><span class="sxs-lookup"><span data-stu-id="1c439-103">\_AxlPublicKeyBlobToPublicKeyToken Function</span></span>

<span data-ttu-id="1c439-104">Bir CSP PUBLICKEYBLOB biçiminden tanımlayıcı ad ortak anahtar belirtecini hesaplar.</span><span class="sxs-lookup"><span data-stu-id="1c439-104">Computes the strong name public key token from a CSP PUBLICKEYBLOB format.</span></span>

## <a name="syntax"></a><span data-ttu-id="1c439-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1c439-105">Syntax</span></span>

```cpp
HRESULT _AxlPublicKeyBlobToPublicKeyToken (
    [in]  PCCERT_CHAIN_CONTEXT   pCspPublicKeyBlob,
    [out] LPWSTR                 *ppwszPublicKeyToken
);
```

## <a name="parameters"></a><span data-ttu-id="1c439-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1c439-106">Parameters</span></span>

 `pCspPublicKeyBlob`\
 <span data-ttu-id="1c439-107">'ndaki CSP ortak anahtar blobu.</span><span class="sxs-lookup"><span data-stu-id="1c439-107">[in] The CSP public key blob.</span></span>

 `ppwszPublicKeyHash`\
 <span data-ttu-id="1c439-108">dışı Onaltılık kodlanmış ortak anahtar karmasını almak için bir WCHAR \* işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="1c439-108">[out] A pointer to WCHAR \* to receive the hex-encoded public key hash.</span></span>

## <a name="return-value"></a><span data-ttu-id="1c439-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1c439-109">Return Value</span></span>

 <span data-ttu-id="1c439-110">`S_OK` işlev başarılı olursa; Aksi takdirde `S_FALSE` .</span><span class="sxs-lookup"><span data-stu-id="1c439-110">`S_OK` if the function succeeds; otherwise `S_FALSE`.</span></span>

## <a name="requirements"></a><span data-ttu-id="1c439-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1c439-111">Requirements</span></span>

<span data-ttu-id="1c439-112">**Bütünleştirilmiş kod**: clr.dll</span><span class="sxs-lookup"><span data-stu-id="1c439-112">**Assembly**: clr.dll</span></span>

## <a name="see-also"></a><span data-ttu-id="1c439-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1c439-113">See also</span></span>

- [<span data-ttu-id="1c439-114">Authenticode</span><span class="sxs-lookup"><span data-stu-id="1c439-114">Authenticode</span></span>](index.md)
