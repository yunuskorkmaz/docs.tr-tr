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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: abbf893b3d49101b5cc9d38ffc31b171ff023f8a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59146932"
---
# <a name="certverifyauthenticodelicense-function"></a><span data-ttu-id="c0e87-102">CertVerifyAuthenticodeLicense İşlevi</span><span class="sxs-lookup"><span data-stu-id="c0e87-102">CertVerifyAuthenticodeLicense Function</span></span>
<span data-ttu-id="c0e87-103">Authenticode XrML lisans geçerliliğini doğrular.</span><span class="sxs-lookup"><span data-stu-id="c0e87-103">Verifies the validity of an Authenticode XrML license.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0e87-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c0e87-104">Syntax</span></span>  
  
```  
HRESULT CertVerifyAuthenticodeLicense (  
    [in]   PCRYPT_DATA_BLOB                   pLicenseBlob,  
    [in]   OPTIONAL DWORD                     dwFlags,  
    [out]  PAXL_AUTHENTICODE_SIGNER_INFO      pSignerInfo,  
    [out]  PAXL_AUTHENTICODE_TIMESTAMPER_INFO pTimestamperInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c0e87-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c0e87-105">Parameters</span></span>  
 `pLicenseBlob`  
 <span data-ttu-id="c0e87-106">[in] Doğrulanacak Authenticode XrML lisans.</span><span class="sxs-lookup"><span data-stu-id="c0e87-106">[in] The Authenticode XrML license to be verified.</span></span>  
  
 <span data-ttu-id="c0e87-107">Bkz: [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) yapısı.</span><span class="sxs-lookup"><span data-stu-id="c0e87-107">See the [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) structure.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="c0e87-108">[in] İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="c0e87-108">[in] Optional.</span></span> <span data-ttu-id="c0e87-109">Aşağıdaki değerleri birleşimi:</span><span class="sxs-lookup"><span data-stu-id="c0e87-109">A combination of following values:</span></span>  
  
-   <span data-ttu-id="c0e87-110">AXL_REVOCATION_NO_CHECK</span><span class="sxs-lookup"><span data-stu-id="c0e87-110">AXL_REVOCATION_NO_CHECK</span></span>  
  
-   <span data-ttu-id="c0e87-111">AXL_REVOCATION_CHECK_END_CERT_ONLY</span><span class="sxs-lookup"><span data-stu-id="c0e87-111">AXL_REVOCATION_CHECK_END_CERT_ONLY</span></span>  
  
-   <span data-ttu-id="c0e87-112">AXL_REVOCATION_CHECK_ENTIRE_CHAIN</span><span class="sxs-lookup"><span data-stu-id="c0e87-112">AXL_REVOCATION_CHECK_ENTIRE_CHAIN</span></span>  
  
-   <span data-ttu-id="c0e87-113">AXL_URL_CACHE_ONLY_RETRIEVAL</span><span class="sxs-lookup"><span data-stu-id="c0e87-113">AXL_URL_CACHE_ONLY_RETRIEVAL</span></span>  
  
-   <span data-ttu-id="c0e87-114">AXL_LIFETIME_SIGNING</span><span class="sxs-lookup"><span data-stu-id="c0e87-114">AXL_LIFETIME_SIGNING</span></span>  
  
-   <span data-ttu-id="c0e87-115">AXL_TRUST_MICROSOFT_ROOT_ONLY</span><span class="sxs-lookup"><span data-stu-id="c0e87-115">AXL_TRUST_MICROSOFT_ROOT_ONLY</span></span>  
  
 `pSignerInfo`  
 <span data-ttu-id="c0e87-116">[out] İmzalayanın bilgilerini almak için.</span><span class="sxs-lookup"><span data-stu-id="c0e87-116">[out] To receive the signer's information.</span></span> <span data-ttu-id="c0e87-117">Lisans değildi açtıysanız `dwError` TRUST_E_NOSIGNATURE için ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="c0e87-117">If the license wasn't signed, `dwError` is set to TRUST_E_NOSIGNATURE.</span></span> <span data-ttu-id="c0e87-118">Bunu kullanarak kaynakları serbest bırakacak arayanın sorumluluğundadır [Certfreeauthenticodesignerınfo](../../../../docs/framework/unmanaged-api/authenticode/certfreeauthenticodesignerinfo-function.md) işlevinden sonra kullanın.</span><span class="sxs-lookup"><span data-stu-id="c0e87-118">It is the caller's responsibility to free resources by using the [CertFreeAuthenticodeSignerInfo](../../../../docs/framework/unmanaged-api/authenticode/certfreeauthenticodesignerinfo-function.md) function after use.</span></span>  
  
 <span data-ttu-id="c0e87-119">Bkz: [axl_authentıcode_sıgner_ınfo yapısı](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md).</span><span class="sxs-lookup"><span data-stu-id="c0e87-119">See [AXL_AUTHENTICODE_SIGNER_INFO Structure](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md).</span></span>  
  
 `pTimestamperInfo`  
 <span data-ttu-id="c0e87-120">[out] Varsa zaman stamper'ın bilgi almak için.</span><span class="sxs-lookup"><span data-stu-id="c0e87-120">[out] To receive time stamper's information, if available.</span></span> <span data-ttu-id="c0e87-121">Lisans zaman damgalı değilse `dwError` TRUST_E_NOSIGNATURE için ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="c0e87-121">If the license was not time-stamped, `dwError` is set to TRUST_E_NOSIGNATURE.</span></span> <span data-ttu-id="c0e87-122">Bunu kullanarak kaynakları serbest bırakacak arayanın sorumluluğundadır [Certfreeauthenticodetimestamperınfo](../../../../docs/framework/unmanaged-api/authenticode/certfreeauthenticodetimestamperinfo-function.md) işlevinden sonra kullanın.</span><span class="sxs-lookup"><span data-stu-id="c0e87-122">It is the caller's responsibility to free resources by using the [CertFreeAuthenticodeTimestamperInfo](../../../../docs/framework/unmanaged-api/authenticode/certfreeauthenticodetimestamperinfo-function.md) function after use.</span></span>  
  
 <span data-ttu-id="c0e87-123">Bkz: [axl_authentıcode_tımestamper_ınfo yapısı](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md).</span><span class="sxs-lookup"><span data-stu-id="c0e87-123">See [AXL_AUTHENTICODE_TIMESTAMPER_INFO Structure](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c0e87-124">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c0e87-124">Return Value</span></span>  
 <span data-ttu-id="c0e87-125">Döndürür `S_OK` başarılı olursa.</span><span class="sxs-lookup"><span data-stu-id="c0e87-125">Returns `S_OK` if successful.</span></span> <span data-ttu-id="c0e87-126">Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="c0e87-126">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0e87-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c0e87-127">See also</span></span>

- [<span data-ttu-id="c0e87-128">Authenticode</span><span class="sxs-lookup"><span data-stu-id="c0e87-128">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
- [<span data-ttu-id="c0e87-129">GetHashFromHandle Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c0e87-129">GetHashFromHandle Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromhandle-method.md)
- [<span data-ttu-id="c0e87-130">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c0e87-130">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
