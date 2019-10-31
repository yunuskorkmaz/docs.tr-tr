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
ms.openlocfilehash: 7cd25a24533b04dc45ee734f9e9639391311405a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73099739"
---
# <a name="certverifyauthenticodelicense-function"></a><span data-ttu-id="88fc3-102">CertVerifyAuthenticodeLicense İşlevi</span><span class="sxs-lookup"><span data-stu-id="88fc3-102">CertVerifyAuthenticodeLicense Function</span></span>
<span data-ttu-id="88fc3-103">Authenticode XrML lisansının geçerliliğini doğrular.</span><span class="sxs-lookup"><span data-stu-id="88fc3-103">Verifies the validity of an Authenticode XrML license.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88fc3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="88fc3-104">Syntax</span></span>  
  
```cpp  
HRESULT CertVerifyAuthenticodeLicense (  
    [in]   PCRYPT_DATA_BLOB                   pLicenseBlob,  
    [in]   OPTIONAL DWORD                     dwFlags,  
    [out]  PAXL_AUTHENTICODE_SIGNER_INFO      pSignerInfo,  
    [out]  PAXL_AUTHENTICODE_TIMESTAMPER_INFO pTimestamperInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="88fc3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="88fc3-105">Parameters</span></span>  
 `pLicenseBlob`  
 <span data-ttu-id="88fc3-106">'ndaki Doğrulanacak olan Authenticode XrML lisansı.</span><span class="sxs-lookup"><span data-stu-id="88fc3-106">[in] The Authenticode XrML license to be verified.</span></span>  
  
 <span data-ttu-id="88fc3-107">Bkz. [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) yapısı.</span><span class="sxs-lookup"><span data-stu-id="88fc3-107">See the [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) structure.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="88fc3-108">'ndaki Seçim.</span><span class="sxs-lookup"><span data-stu-id="88fc3-108">[in] Optional.</span></span> <span data-ttu-id="88fc3-109">Aşağıdaki değerlerden oluşan bir bileşim:</span><span class="sxs-lookup"><span data-stu-id="88fc3-109">A combination of following values:</span></span>  
  
- <span data-ttu-id="88fc3-110">AXL_REVOCATION_NO_CHECK</span><span class="sxs-lookup"><span data-stu-id="88fc3-110">AXL_REVOCATION_NO_CHECK</span></span>  
  
- <span data-ttu-id="88fc3-111">AXL_REVOCATION_CHECK_END_CERT_ONLY</span><span class="sxs-lookup"><span data-stu-id="88fc3-111">AXL_REVOCATION_CHECK_END_CERT_ONLY</span></span>  
  
- <span data-ttu-id="88fc3-112">AXL_REVOCATION_CHECK_ENTIRE_CHAIN</span><span class="sxs-lookup"><span data-stu-id="88fc3-112">AXL_REVOCATION_CHECK_ENTIRE_CHAIN</span></span>  
  
- <span data-ttu-id="88fc3-113">AXL_URL_CACHE_ONLY_RETRIEVAL</span><span class="sxs-lookup"><span data-stu-id="88fc3-113">AXL_URL_CACHE_ONLY_RETRIEVAL</span></span>  
  
- <span data-ttu-id="88fc3-114">AXL_LIFETIME_SIGNING</span><span class="sxs-lookup"><span data-stu-id="88fc3-114">AXL_LIFETIME_SIGNING</span></span>  
  
- <span data-ttu-id="88fc3-115">AXL_TRUST_MICROSOFT_ROOT_ONLY</span><span class="sxs-lookup"><span data-stu-id="88fc3-115">AXL_TRUST_MICROSOFT_ROOT_ONLY</span></span>  
  
 `pSignerInfo`  
 <span data-ttu-id="88fc3-116">dışı İmzalayan bilgilerini almak için.</span><span class="sxs-lookup"><span data-stu-id="88fc3-116">[out] To receive the signer's information.</span></span> <span data-ttu-id="88fc3-117">Lisans imzalanmadıysa, `dwError` TRUST_E_NOSIGNATURE olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="88fc3-117">If the license wasn't signed, `dwError` is set to TRUST_E_NOSIGNATURE.</span></span> <span data-ttu-id="88fc3-118">Bu, kullandıktan sonra [CertFreeAuthenticodeSignerInfo](certfreeauthenticodesignerinfo-function.md) işlevini kullanarak kaynakların serbest bir şekilde kullanıma yönelik sorumluluğundadır.</span><span class="sxs-lookup"><span data-stu-id="88fc3-118">It is the caller's responsibility to free resources by using the [CertFreeAuthenticodeSignerInfo](certfreeauthenticodesignerinfo-function.md) function after use.</span></span>  
  
 <span data-ttu-id="88fc3-119">Bkz. [AXL_AUTHENTICODE_SIGNER_INFO yapısı](axl-authenticode-signer-info-structure.md).</span><span class="sxs-lookup"><span data-stu-id="88fc3-119">See [AXL_AUTHENTICODE_SIGNER_INFO Structure](axl-authenticode-signer-info-structure.md).</span></span>  
  
 `pTimestamperInfo`  
 <span data-ttu-id="88fc3-120">dışı Varsa, zaman Stamper 'ın bilgilerini almak için.</span><span class="sxs-lookup"><span data-stu-id="88fc3-120">[out] To receive time stamper's information, if available.</span></span> <span data-ttu-id="88fc3-121">Lisans zaman damgalı değilse, `dwError` TRUST_E_NOSIGNATURE olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="88fc3-121">If the license was not time-stamped, `dwError` is set to TRUST_E_NOSIGNATURE.</span></span> <span data-ttu-id="88fc3-122">Bu, kullandıktan sonra [CertFreeAuthenticodeTimestamperInfo](certfreeauthenticodetimestamperinfo-function.md) işlevini kullanarak kaynakların serbest bir şekilde kullanıma yönelik sorumluluğundadır.</span><span class="sxs-lookup"><span data-stu-id="88fc3-122">It is the caller's responsibility to free resources by using the [CertFreeAuthenticodeTimestamperInfo](certfreeauthenticodetimestamperinfo-function.md) function after use.</span></span>  
  
 <span data-ttu-id="88fc3-123">Bkz. [AXL_AUTHENTICODE_TIMESTAMPER_INFO yapısı](axl-authenticode-timestamper-info-structure.md).</span><span class="sxs-lookup"><span data-stu-id="88fc3-123">See [AXL_AUTHENTICODE_TIMESTAMPER_INFO Structure](axl-authenticode-timestamper-info-structure.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="88fc3-124">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="88fc3-124">Return Value</span></span>  
 <span data-ttu-id="88fc3-125">Başarılı olursa `S_OK` döndürür.</span><span class="sxs-lookup"><span data-stu-id="88fc3-125">Returns `S_OK` if successful.</span></span> <span data-ttu-id="88fc3-126">Aksi takdirde, bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="88fc3-126">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88fc3-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="88fc3-127">See also</span></span>

- [<span data-ttu-id="88fc3-128">Authenticode</span><span class="sxs-lookup"><span data-stu-id="88fc3-128">Authenticode</span></span>](index.md)
- [<span data-ttu-id="88fc3-129">GetHashFromHandle Yöntemi</span><span class="sxs-lookup"><span data-stu-id="88fc3-129">GetHashFromHandle Method</span></span>](../hosting/iclrstrongname-gethashfromhandle-method.md)
- [<span data-ttu-id="88fc3-130">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="88fc3-130">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
