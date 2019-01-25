---
title: CertTimestampAuthenticodeLicense İşlevi
ms.date: 03/30/2017
api_name:
- CertTimestampAuthenticodeLicense
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: d468325a-21c5-43ce-8567-84e342b22308
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9987640f988f2239a01d2dfdbcd6b1684579d8bc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54601514"
---
# <a name="certtimestampauthenticodelicense-function"></a><span data-ttu-id="7cf36-102">CertTimestampAuthenticodeLicense İşlevi</span><span class="sxs-lookup"><span data-stu-id="7cf36-102">CertTimestampAuthenticodeLicense Function</span></span>
<span data-ttu-id="7cf36-103">Zaman damgaları Authenticode XrML bir lisans.</span><span class="sxs-lookup"><span data-stu-id="7cf36-103">Time-stamps an Authenticode XrML license.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7cf36-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7cf36-104">Syntax</span></span>  
  
```  
HRESULT CertTimestampAuthenticodeLicense (  
    [in]  PCRYPT_DATA_BLOB   pSignedLicenseBlob,  
    [in]  LPCWSTR            pwszTimestampURI,  
    [out] PCRYPT_DATA_BLOB   pTimestampSignatureBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7cf36-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7cf36-105">Parameters</span></span>  
 `pSignedLicenseBlob`  
 <span data-ttu-id="7cf36-106">[in] Zaman damgası olarak imzalı Authenticode XrML lisans.</span><span class="sxs-lookup"><span data-stu-id="7cf36-106">[in] The signed Authenticode XrML license to be time-stamped.</span></span> <span data-ttu-id="7cf36-107">Bkz: [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) yapısı.</span><span class="sxs-lookup"><span data-stu-id="7cf36-107">See the [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) structure.</span></span>  
  
 `pwszTimestampURI`  
 <span data-ttu-id="7cf36-108">[in] Zaman damgası sunucusunun URI'si.</span><span class="sxs-lookup"><span data-stu-id="7cf36-108">[in] The time-stamp server's URI.</span></span>  
  
 `pTimestampSignatureBlob`  
 <span data-ttu-id="7cf36-109">[out] CRYPT_DATA_BLOB base64 kodlamalı zaman damgası imza almak için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7cf36-109">[out] A pointer to CRYPT_DATA_BLOB to receive the base64-encoded time-stamp signature.</span></span> <span data-ttu-id="7cf36-110">Bu ücretsiz çağrı sahibinin sorumluluğundadır `pTimestampSignatureBlob` -> `pbData` ile `HepFree()` kullandıktan sonra.</span><span class="sxs-lookup"><span data-stu-id="7cf36-110">It is the caller's responsibility to free `pTimestampSignatureBlob`->`pbData` with `HepFree()` after use.</span></span> <span data-ttu-id="7cf36-111">Bkz: [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) yapısı.</span><span class="sxs-lookup"><span data-stu-id="7cf36-111">See the [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7cf36-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7cf36-112">Remarks</span></span>  
 <span data-ttu-id="7cf36-113">Zaman damgası imza gerçekten içerikleri SignatureValue Lisans'ın imza gelen ikili biçimdir bir PKCS #7 SignedData ileti değil.</span><span class="sxs-lookup"><span data-stu-id="7cf36-113">The time-stamp signature is actually a PKCS #7 SignedData message whose content is the binary form of the SignatureValue from the license's signature.</span></span> <span data-ttu-id="7cf36-114">Temel olarak, bu lisans bir karşı imza görevi yapar.</span><span class="sxs-lookup"><span data-stu-id="7cf36-114">Basically, this acts as a counter-signature of the license.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7cf36-115">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7cf36-115">Return Value</span></span>  
 <span data-ttu-id="7cf36-116">`S_OK` işlev başarılı olursa.</span><span class="sxs-lookup"><span data-stu-id="7cf36-116">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="7cf36-117">Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="7cf36-117">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cf36-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7cf36-118">See also</span></span>
- [<span data-ttu-id="7cf36-119">Authenticode</span><span class="sxs-lookup"><span data-stu-id="7cf36-119">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
