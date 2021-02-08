---
description: 'Daha fazla bilgi edinin: CertTimestampAuthenticodeLicense Işlevi'
title: CertTimestampAuthenticodeLicense İşlevi
ms.date: 03/30/2017
api_name:
- CertTimestampAuthenticodeLicense
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: d468325a-21c5-43ce-8567-84e342b22308
topic_type:
- apiref
ms.openlocfilehash: 79b1a924a99a76c18e6434abfed0a90da71eb6f9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772930"
---
# <a name="certtimestampauthenticodelicense-function"></a><span data-ttu-id="b2c17-103">CertTimestampAuthenticodeLicense İşlevi</span><span class="sxs-lookup"><span data-stu-id="b2c17-103">CertTimestampAuthenticodeLicense Function</span></span>

<span data-ttu-id="b2c17-104">Zaman damgalarının Authenticode XrML lisansı.</span><span class="sxs-lookup"><span data-stu-id="b2c17-104">Time-stamps an Authenticode XrML license.</span></span>

## <a name="syntax"></a><span data-ttu-id="b2c17-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b2c17-105">Syntax</span></span>

```cpp
HRESULT CertTimestampAuthenticodeLicense (
    [in]  PCRYPT_DATA_BLOB   pSignedLicenseBlob,
    [in]  LPCWSTR            pwszTimestampURI,
    [out] PCRYPT_DATA_BLOB   pTimestampSignatureBlob
);
```

## <a name="parameters"></a><span data-ttu-id="b2c17-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b2c17-106">Parameters</span></span>

 `pSignedLicenseBlob`\
 <span data-ttu-id="b2c17-107">'ndaki Zaman damgalı olarak imzalanan Authenticode XrML lisansı.</span><span class="sxs-lookup"><span data-stu-id="b2c17-107">[in] The signed Authenticode XrML license to be time-stamped.</span></span> <span data-ttu-id="b2c17-108">[CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) yapısına bakın.</span><span class="sxs-lookup"><span data-stu-id="b2c17-108">See the [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) structure.</span></span>

 `pwszTimestampURI`\
 <span data-ttu-id="b2c17-109">'ndaki Zaman damgası sunucusunun URI 'SI.</span><span class="sxs-lookup"><span data-stu-id="b2c17-109">[in] The time-stamp server's URI.</span></span>

 `pTimestampSignatureBlob`\
 <span data-ttu-id="b2c17-110">dışı Base64 ile kodlanmış zaman damgası imzasını almak için CRYPT_DATA_BLOB işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="b2c17-110">[out] A pointer to CRYPT_DATA_BLOB to receive the base64-encoded time-stamp signature.</span></span> <span data-ttu-id="b2c17-111">Bu, `pTimestampSignatureBlob` -> `pbData` kullandıktan sonra, çağıranın ücretsiz olarak kullanılacağı sorumluluğudur `HepFree()` .</span><span class="sxs-lookup"><span data-stu-id="b2c17-111">It is the caller's responsibility to free `pTimestampSignatureBlob`->`pbData` with `HepFree()` after use.</span></span> <span data-ttu-id="b2c17-112">[CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) yapısına bakın.</span><span class="sxs-lookup"><span data-stu-id="b2c17-112">See the [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) structure.</span></span>

## <a name="remarks"></a><span data-ttu-id="b2c17-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b2c17-113">Remarks</span></span>

 <span data-ttu-id="b2c17-114">Zaman damgası imzası aslında, içeriği lisansın imzasıyla olan SignatureValue 'un ikili biçimi olan PKCS #7 SignedData iletisidir.</span><span class="sxs-lookup"><span data-stu-id="b2c17-114">The time-stamp signature is actually a PKCS #7 SignedData message whose content is the binary form of the SignatureValue from the license's signature.</span></span> <span data-ttu-id="b2c17-115">Temelde, bu, lisansın sayaç imzası olarak görev yapar.</span><span class="sxs-lookup"><span data-stu-id="b2c17-115">Basically, this acts as a counter-signature of the license.</span></span>

## <a name="return-value"></a><span data-ttu-id="b2c17-116">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b2c17-116">Return Value</span></span>

 <span data-ttu-id="b2c17-117">`S_OK` işlev başarılı olursa.</span><span class="sxs-lookup"><span data-stu-id="b2c17-117">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="b2c17-118">Aksi takdirde, bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="b2c17-118">Otherwise, returns an error code.</span></span>

## <a name="requirements"></a><span data-ttu-id="b2c17-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b2c17-119">Requirements</span></span>

<span data-ttu-id="b2c17-120">**Bütünleştirilmiş kod**: clr.dll</span><span class="sxs-lookup"><span data-stu-id="b2c17-120">**Assembly**: clr.dll</span></span>

## <a name="see-also"></a><span data-ttu-id="b2c17-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b2c17-121">See also</span></span>

- [<span data-ttu-id="b2c17-122">Authenticode</span><span class="sxs-lookup"><span data-stu-id="b2c17-122">Authenticode</span></span>](index.md)
