---
title: CertVerifyAuthenticodeLicense İşlevi
ms.date: 03/30/2017
api_name:
- CertVerifyAuthenticodeLicense
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: 00118de7-33c6-41c4-8e1f-5d5e35e0da83
ms.openlocfilehash: 388814d1c63f048c0aa231a1d0058a390cba9493
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674066"
---
# <a name="certverifyauthenticodelicense-function"></a><span data-ttu-id="f2e78-102">CertVerifyAuthenticodeLicense İşlevi</span><span class="sxs-lookup"><span data-stu-id="f2e78-102">CertVerifyAuthenticodeLicense Function</span></span>

<span data-ttu-id="f2e78-103">Authenticode XrML lisansının geçerliliğini doğrular.</span><span class="sxs-lookup"><span data-stu-id="f2e78-103">Verifies the validity of an Authenticode XrML license.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2e78-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="f2e78-104">Syntax</span></span>  
  
```cpp  
HRESULT CertVerifyAuthenticodeLicense (  
    [in]   PCRYPT_DATA_BLOB                   pLicenseBlob,  
    [in]   OPTIONAL DWORD                     dwFlags,  
    [out]  PAXL_AUTHENTICODE_SIGNER_INFO      pSignerInfo,  
    [out]  PAXL_AUTHENTICODE_TIMESTAMPER_INFO pTimestamperInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f2e78-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f2e78-105">Parameters</span></span>  

 `pLicenseBlob`  
 <span data-ttu-id="f2e78-106">'ndaki Doğrulanacak olan Authenticode XrML lisansı.</span><span class="sxs-lookup"><span data-stu-id="f2e78-106">[in] The Authenticode XrML license to be verified.</span></span>  
  
 <span data-ttu-id="f2e78-107">[CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) yapısına bakın.</span><span class="sxs-lookup"><span data-stu-id="f2e78-107">See the [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) structure.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="f2e78-108">'ndaki Seçim.</span><span class="sxs-lookup"><span data-stu-id="f2e78-108">[in] Optional.</span></span> <span data-ttu-id="f2e78-109">Aşağıdaki değerlerden oluşan bir bileşim:</span><span class="sxs-lookup"><span data-stu-id="f2e78-109">A combination of following values:</span></span>  
  
- <span data-ttu-id="f2e78-110">AXL_REVOCATION_NO_CHECK</span><span class="sxs-lookup"><span data-stu-id="f2e78-110">AXL_REVOCATION_NO_CHECK</span></span>  
  
- <span data-ttu-id="f2e78-111">AXL_REVOCATION_CHECK_END_CERT_ONLY</span><span class="sxs-lookup"><span data-stu-id="f2e78-111">AXL_REVOCATION_CHECK_END_CERT_ONLY</span></span>  
  
- <span data-ttu-id="f2e78-112">AXL_REVOCATION_CHECK_ENTIRE_CHAIN</span><span class="sxs-lookup"><span data-stu-id="f2e78-112">AXL_REVOCATION_CHECK_ENTIRE_CHAIN</span></span>  
  
- <span data-ttu-id="f2e78-113">AXL_URL_CACHE_ONLY_RETRIEVAL</span><span class="sxs-lookup"><span data-stu-id="f2e78-113">AXL_URL_CACHE_ONLY_RETRIEVAL</span></span>  
  
- <span data-ttu-id="f2e78-114">AXL_LIFETIME_SIGNING</span><span class="sxs-lookup"><span data-stu-id="f2e78-114">AXL_LIFETIME_SIGNING</span></span>  
  
- <span data-ttu-id="f2e78-115">AXL_TRUST_MICROSOFT_ROOT_ONLY</span><span class="sxs-lookup"><span data-stu-id="f2e78-115">AXL_TRUST_MICROSOFT_ROOT_ONLY</span></span>  
  
 `pSignerInfo`  
 <span data-ttu-id="f2e78-116">dışı İmzalayan bilgilerini almak için.</span><span class="sxs-lookup"><span data-stu-id="f2e78-116">[out] To receive the signer's information.</span></span> <span data-ttu-id="f2e78-117">Lisans imzalanmamışsa, `dwError` TRUST_E_NOSIGNATURE olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="f2e78-117">If the license wasn't signed, `dwError` is set to TRUST_E_NOSIGNATURE.</span></span> <span data-ttu-id="f2e78-118">Bu, kullandıktan sonra [CertFreeAuthenticodeSignerInfo](certfreeauthenticodesignerinfo-function.md) işlevini kullanarak kaynakların serbest bir şekilde kullanıma yönelik sorumluluğundadır.</span><span class="sxs-lookup"><span data-stu-id="f2e78-118">It is the caller's responsibility to free resources by using the [CertFreeAuthenticodeSignerInfo](certfreeauthenticodesignerinfo-function.md) function after use.</span></span>  
  
 <span data-ttu-id="f2e78-119">Bkz. [AXL_AUTHENTICODE_SIGNER_INFO yapısı](axl-authenticode-signer-info-structure.md).</span><span class="sxs-lookup"><span data-stu-id="f2e78-119">See [AXL_AUTHENTICODE_SIGNER_INFO Structure](axl-authenticode-signer-info-structure.md).</span></span>  
  
 `pTimestamperInfo`  
 <span data-ttu-id="f2e78-120">dışı Varsa, zaman Stamper 'ın bilgilerini almak için.</span><span class="sxs-lookup"><span data-stu-id="f2e78-120">[out] To receive time stamper's information, if available.</span></span> <span data-ttu-id="f2e78-121">Lisans zaman damgalı değilse, `dwError` TRUST_E_NOSIGNATURE olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="f2e78-121">If the license was not time-stamped, `dwError` is set to TRUST_E_NOSIGNATURE.</span></span> <span data-ttu-id="f2e78-122">Bu, kullandıktan sonra [CertFreeAuthenticodeTimestamperInfo](certfreeauthenticodetimestamperinfo-function.md) işlevini kullanarak kaynakların serbest bir şekilde kullanıma yönelik sorumluluğundadır.</span><span class="sxs-lookup"><span data-stu-id="f2e78-122">It is the caller's responsibility to free resources by using the [CertFreeAuthenticodeTimestamperInfo](certfreeauthenticodetimestamperinfo-function.md) function after use.</span></span>  
  
 <span data-ttu-id="f2e78-123">Bkz. [AXL_AUTHENTICODE_TIMESTAMPER_INFO yapısı](axl-authenticode-timestamper-info-structure.md).</span><span class="sxs-lookup"><span data-stu-id="f2e78-123">See [AXL_AUTHENTICODE_TIMESTAMPER_INFO Structure](axl-authenticode-timestamper-info-structure.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f2e78-124">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f2e78-124">Return Value</span></span>  

 <span data-ttu-id="f2e78-125">`S_OK`Başarılı olursa döndürür.</span><span class="sxs-lookup"><span data-stu-id="f2e78-125">Returns `S_OK` if successful.</span></span> <span data-ttu-id="f2e78-126">Aksi takdirde, bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="f2e78-126">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2e78-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f2e78-127">See also</span></span>

- [<span data-ttu-id="f2e78-128">Authenticode</span><span class="sxs-lookup"><span data-stu-id="f2e78-128">Authenticode</span></span>](index.md)
- [<span data-ttu-id="f2e78-129">GetHashFromHandle Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f2e78-129">GetHashFromHandle Method</span></span>](../hosting/iclrstrongname-gethashfromhandle-method.md)
- [<span data-ttu-id="f2e78-130">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f2e78-130">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
