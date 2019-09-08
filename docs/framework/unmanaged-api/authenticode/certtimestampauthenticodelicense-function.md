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
ms.openlocfilehash: aaf76d4c3d0f5fb59aeb35fae7a7020ee97b74d6
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70776483"
---
# <a name="certtimestampauthenticodelicense-function"></a><span data-ttu-id="8458d-102">CertTimestampAuthenticodeLicense İşlevi</span><span class="sxs-lookup"><span data-stu-id="8458d-102">CertTimestampAuthenticodeLicense Function</span></span>
<span data-ttu-id="8458d-103">Zaman damgalarının Authenticode XrML lisansı.</span><span class="sxs-lookup"><span data-stu-id="8458d-103">Time-stamps an Authenticode XrML license.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8458d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8458d-104">Syntax</span></span>  
  
```cpp  
HRESULT CertTimestampAuthenticodeLicense (  
    [in]  PCRYPT_DATA_BLOB   pSignedLicenseBlob,  
    [in]  LPCWSTR            pwszTimestampURI,  
    [out] PCRYPT_DATA_BLOB   pTimestampSignatureBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8458d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8458d-105">Parameters</span></span>  
 `pSignedLicenseBlob`  
 <span data-ttu-id="8458d-106">'ndaki Zaman damgalı olarak imzalanan Authenticode XrML lisansı.</span><span class="sxs-lookup"><span data-stu-id="8458d-106">[in] The signed Authenticode XrML license to be time-stamped.</span></span> <span data-ttu-id="8458d-107">Bkz. [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) yapısı.</span><span class="sxs-lookup"><span data-stu-id="8458d-107">See the [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) structure.</span></span>  
  
 `pwszTimestampURI`  
 <span data-ttu-id="8458d-108">'ndaki Zaman damgası sunucusunun URI 'SI.</span><span class="sxs-lookup"><span data-stu-id="8458d-108">[in] The time-stamp server's URI.</span></span>  
  
 `pTimestampSignatureBlob`  
 <span data-ttu-id="8458d-109">dışı Base64 ile kodlanmış zaman damgası imzasını almak için CRYPT_DATA_BLOB işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="8458d-109">[out] A pointer to CRYPT_DATA_BLOB to receive the base64-encoded time-stamp signature.</span></span> <span data-ttu-id="8458d-110">Bu, `pTimestampSignatureBlob` `HepFree()` kullandıktan sonra, çağıranın ücretsiz -> `pbData` olarak kullanılacağı sorumluluğudur.</span><span class="sxs-lookup"><span data-stu-id="8458d-110">It is the caller's responsibility to free `pTimestampSignatureBlob`->`pbData` with `HepFree()` after use.</span></span> <span data-ttu-id="8458d-111">Bkz. [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) yapısı.</span><span class="sxs-lookup"><span data-stu-id="8458d-111">See the [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8458d-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8458d-112">Remarks</span></span>  
 <span data-ttu-id="8458d-113">Zaman damgası imzası aslında, içeriği lisansın imzasıyla olan SignatureValue 'un ikili biçimi olan PKCS #7 SignedData iletisidir.</span><span class="sxs-lookup"><span data-stu-id="8458d-113">The time-stamp signature is actually a PKCS #7 SignedData message whose content is the binary form of the SignatureValue from the license's signature.</span></span> <span data-ttu-id="8458d-114">Temelde, bu, lisansın sayaç imzası olarak görev yapar.</span><span class="sxs-lookup"><span data-stu-id="8458d-114">Basically, this acts as a counter-signature of the license.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8458d-115">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8458d-115">Return Value</span></span>  
 <span data-ttu-id="8458d-116">`S_OK`işlev başarılı olursa.</span><span class="sxs-lookup"><span data-stu-id="8458d-116">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="8458d-117">Aksi takdirde, bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="8458d-117">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8458d-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8458d-118">See also</span></span>

- [<span data-ttu-id="8458d-119">Authenticode</span><span class="sxs-lookup"><span data-stu-id="8458d-119">Authenticode</span></span>](index.md)
