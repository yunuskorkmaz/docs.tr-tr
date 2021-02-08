---
description: 'Şu konuda daha fazla bilgi edinin: Certdoğrulamaları Yakimlik Kodulicense Işlevi'
title: CertVerifyAuthenticodeLicense İşlevi
ms.date: 03/30/2017
api_name:
- CertVerifyAuthenticodeLicense
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: 00118de7-33c6-41c4-8e1f-5d5e35e0da83
topic_type:
- apiref
ms.openlocfilehash: 0174223a4c1b984bf2d5d957219a85230fef8d0e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772854"
---
# <a name="certverifyauthenticodelicense-function"></a><span data-ttu-id="09309-103">CertVerifyAuthenticodeLicense İşlevi</span><span class="sxs-lookup"><span data-stu-id="09309-103">CertVerifyAuthenticodeLicense Function</span></span>

<span data-ttu-id="09309-104">Authenticode XrML lisansının geçerliliğini doğrular.</span><span class="sxs-lookup"><span data-stu-id="09309-104">Verifies the validity of an Authenticode XrML license.</span></span>

## <a name="syntax"></a><span data-ttu-id="09309-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="09309-105">Syntax</span></span>

```cpp
HRESULT CertVerifyAuthenticodeLicense (
    [in]   PCRYPT_DATA_BLOB                   pLicenseBlob,
    [in]   OPTIONAL DWORD                     dwFlags,
    [out]  PAXL_AUTHENTICODE_SIGNER_INFO      pSignerInfo,
    [out]  PAXL_AUTHENTICODE_TIMESTAMPER_INFO pTimestamperInfo
);
```

## <a name="parameters"></a><span data-ttu-id="09309-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="09309-106">Parameters</span></span>

 `pLicenseBlob`\
 <span data-ttu-id="09309-107">'ndaki Doğrulanacak olan Authenticode XrML lisansı.</span><span class="sxs-lookup"><span data-stu-id="09309-107">[in] The Authenticode XrML license to be verified.</span></span>

 <span data-ttu-id="09309-108">[CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) yapısına bakın.</span><span class="sxs-lookup"><span data-stu-id="09309-108">See the [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) structure.</span></span>

 `dwFlags`\
 <span data-ttu-id="09309-109">'ndaki Seçim.</span><span class="sxs-lookup"><span data-stu-id="09309-109">[in] Optional.</span></span> <span data-ttu-id="09309-110">Aşağıdaki değerlerden oluşan bir bileşim:</span><span class="sxs-lookup"><span data-stu-id="09309-110">A combination of following values:</span></span>

- <span data-ttu-id="09309-111">AXL_REVOCATION_NO_CHECK</span><span class="sxs-lookup"><span data-stu-id="09309-111">AXL_REVOCATION_NO_CHECK</span></span>

- <span data-ttu-id="09309-112">AXL_REVOCATION_CHECK_END_CERT_ONLY</span><span class="sxs-lookup"><span data-stu-id="09309-112">AXL_REVOCATION_CHECK_END_CERT_ONLY</span></span>

- <span data-ttu-id="09309-113">AXL_REVOCATION_CHECK_ENTIRE_CHAIN</span><span class="sxs-lookup"><span data-stu-id="09309-113">AXL_REVOCATION_CHECK_ENTIRE_CHAIN</span></span>

- <span data-ttu-id="09309-114">AXL_URL_CACHE_ONLY_RETRIEVAL</span><span class="sxs-lookup"><span data-stu-id="09309-114">AXL_URL_CACHE_ONLY_RETRIEVAL</span></span>

- <span data-ttu-id="09309-115">AXL_LIFETIME_SIGNING</span><span class="sxs-lookup"><span data-stu-id="09309-115">AXL_LIFETIME_SIGNING</span></span>

- <span data-ttu-id="09309-116">AXL_TRUST_MICROSOFT_ROOT_ONLY</span><span class="sxs-lookup"><span data-stu-id="09309-116">AXL_TRUST_MICROSOFT_ROOT_ONLY</span></span>

 `pSignerInfo`\
 <span data-ttu-id="09309-117">dışı İmzalayan bilgilerini almak için.</span><span class="sxs-lookup"><span data-stu-id="09309-117">[out] To receive the signer's information.</span></span> <span data-ttu-id="09309-118">Lisans imzalanmamışsa, `dwError` TRUST_E_NOSIGNATURE olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="09309-118">If the license wasn't signed, `dwError` is set to TRUST_E_NOSIGNATURE.</span></span> <span data-ttu-id="09309-119">Bu, kullandıktan sonra [CertFreeAuthenticodeSignerInfo](certfreeauthenticodesignerinfo-function.md) işlevini kullanarak kaynakların serbest bir şekilde kullanıma yönelik sorumluluğundadır.</span><span class="sxs-lookup"><span data-stu-id="09309-119">It is the caller's responsibility to free resources by using the [CertFreeAuthenticodeSignerInfo](certfreeauthenticodesignerinfo-function.md) function after use.</span></span>

 <span data-ttu-id="09309-120">Bkz. [AXL_AUTHENTICODE_SIGNER_INFO yapısı](axl-authenticode-signer-info-structure.md).</span><span class="sxs-lookup"><span data-stu-id="09309-120">See [AXL_AUTHENTICODE_SIGNER_INFO Structure](axl-authenticode-signer-info-structure.md).</span></span>

 `pTimestamperInfo`\
 <span data-ttu-id="09309-121">dışı Varsa, zaman Stamper 'ın bilgilerini almak için.</span><span class="sxs-lookup"><span data-stu-id="09309-121">[out] To receive time stamper's information, if available.</span></span> <span data-ttu-id="09309-122">Lisans zaman damgalı değilse, `dwError` TRUST_E_NOSIGNATURE olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="09309-122">If the license was not time-stamped, `dwError` is set to TRUST_E_NOSIGNATURE.</span></span> <span data-ttu-id="09309-123">Bu, kullandıktan sonra [CertFreeAuthenticodeTimestamperInfo](certfreeauthenticodetimestamperinfo-function.md) işlevini kullanarak kaynakların serbest bir şekilde kullanıma yönelik sorumluluğundadır.</span><span class="sxs-lookup"><span data-stu-id="09309-123">It is the caller's responsibility to free resources by using the [CertFreeAuthenticodeTimestamperInfo](certfreeauthenticodetimestamperinfo-function.md) function after use.</span></span>

 <span data-ttu-id="09309-124">Bkz. [AXL_AUTHENTICODE_TIMESTAMPER_INFO yapısı](axl-authenticode-timestamper-info-structure.md).</span><span class="sxs-lookup"><span data-stu-id="09309-124">See [AXL_AUTHENTICODE_TIMESTAMPER_INFO Structure](axl-authenticode-timestamper-info-structure.md).</span></span>

## <a name="return-value"></a><span data-ttu-id="09309-125">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="09309-125">Return Value</span></span>

 <span data-ttu-id="09309-126">`S_OK`Başarılı olursa döndürür.</span><span class="sxs-lookup"><span data-stu-id="09309-126">Returns `S_OK` if successful.</span></span> <span data-ttu-id="09309-127">Aksi takdirde, bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="09309-127">Otherwise, returns an error code.</span></span>

## <a name="requirements"></a><span data-ttu-id="09309-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="09309-128">Requirements</span></span>

<span data-ttu-id="09309-129">**Bütünleştirilmiş kod**: clr.dll</span><span class="sxs-lookup"><span data-stu-id="09309-129">**Assembly**: clr.dll</span></span>

## <a name="see-also"></a><span data-ttu-id="09309-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="09309-130">See also</span></span>

- [<span data-ttu-id="09309-131">Authenticode</span><span class="sxs-lookup"><span data-stu-id="09309-131">Authenticode</span></span>](index.md)
- [<span data-ttu-id="09309-132">GetHashFromHandle Yöntemi</span><span class="sxs-lookup"><span data-stu-id="09309-132">GetHashFromHandle Method</span></span>](../hosting/iclrstrongname-gethashfromhandle-method.md)
- [<span data-ttu-id="09309-133">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="09309-133">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
