---
title: "CertVerifyAuthenticodeLicense İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CertVerifyAuthenticodeLicense
api_location: clr.dll
api_type: DLLExport
ms.assetid: 00118de7-33c6-41c4-8e1f-5d5e35e0da83
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bab3a3bcee52a302345ccdcfad81e7f67efdd8d5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="certverifyauthenticodelicense-function"></a><span data-ttu-id="87b10-102">CertVerifyAuthenticodeLicense İşlevi</span><span class="sxs-lookup"><span data-stu-id="87b10-102">CertVerifyAuthenticodeLicense Function</span></span>
<span data-ttu-id="87b10-103">Authenticode XrML lisans geçerliliğini doğrular.</span><span class="sxs-lookup"><span data-stu-id="87b10-103">Verifies the validity of an Authenticode XrML license.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87b10-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="87b10-104">Syntax</span></span>  
  
```  
HRESULT CertVerifyAuthenticodeLicense (  
    [in]   PCRYPT_DATA_BLOB                   pLicenseBlob,  
    [in]   OPTIONAL DWORD                     dwFlags,  
    [out]  PAXL_AUTHENTICODE_SIGNER_INFO      pSignerInfo,  
    [out]  PAXL_AUTHENTICODE_TIMESTAMPER_INFO pTimestamperInfo  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="87b10-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="87b10-105">Parameters</span></span>  
 `pLicenseBlob`  
 <span data-ttu-id="87b10-106">[in] Doğrulanacak Authenticode XrML lisans.</span><span class="sxs-lookup"><span data-stu-id="87b10-106">[in] The Authenticode XrML license to be verified.</span></span>  
  
 <span data-ttu-id="87b10-107">Bkz: [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) yapısı.</span><span class="sxs-lookup"><span data-stu-id="87b10-107">See the [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) structure.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="87b10-108">[in] İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="87b10-108">[in] Optional.</span></span> <span data-ttu-id="87b10-109">Aşağıdaki değerleri birleşimi:</span><span class="sxs-lookup"><span data-stu-id="87b10-109">A combination of following values:</span></span>  
  
-   <span data-ttu-id="87b10-110">AXL_REVOCATION_NO_CHECK</span><span class="sxs-lookup"><span data-stu-id="87b10-110">AXL_REVOCATION_NO_CHECK</span></span>  
  
-   <span data-ttu-id="87b10-111">AXL_REVOCATION_CHECK_END_CERT_ONLY</span><span class="sxs-lookup"><span data-stu-id="87b10-111">AXL_REVOCATION_CHECK_END_CERT_ONLY</span></span>  
  
-   <span data-ttu-id="87b10-112">AXL_REVOCATION_CHECK_ENTIRE_CHAIN</span><span class="sxs-lookup"><span data-stu-id="87b10-112">AXL_REVOCATION_CHECK_ENTIRE_CHAIN</span></span>  
  
-   <span data-ttu-id="87b10-113">AXL_URL_CACHE_ONLY_RETRIEVAL</span><span class="sxs-lookup"><span data-stu-id="87b10-113">AXL_URL_CACHE_ONLY_RETRIEVAL</span></span>  
  
-   <span data-ttu-id="87b10-114">AXL_LIFETIME_SIGNING</span><span class="sxs-lookup"><span data-stu-id="87b10-114">AXL_LIFETIME_SIGNING</span></span>  
  
-   <span data-ttu-id="87b10-115">AXL_TRUST_MICROSOFT_ROOT_ONLY</span><span class="sxs-lookup"><span data-stu-id="87b10-115">AXL_TRUST_MICROSOFT_ROOT_ONLY</span></span>  
  
 `pSignerInfo`  
 <span data-ttu-id="87b10-116">[out] İmzalayan bilgilerini almak için.</span><span class="sxs-lookup"><span data-stu-id="87b10-116">[out] To receive the signer's information.</span></span> <span data-ttu-id="87b10-117">Lisans değildi kaydolduysanız `dwError` TRUST_E_NOSIGNATURE için ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="87b10-117">If the license wasn't signed, `dwError` is set to TRUST_E_NOSIGNATURE.</span></span> <span data-ttu-id="87b10-118">Bunu kullanarak kaynakları serbest yapanın sorumluluğundadır [Certfreeauthenticodesignerınfo](../../../../docs/framework/unmanaged-api/authenticode/certfreeauthenticodesignerinfo-function.md) kullandıktan sonra işlevi.</span><span class="sxs-lookup"><span data-stu-id="87b10-118">It is the caller's responsibility to free resources by using the [CertFreeAuthenticodeSignerInfo](../../../../docs/framework/unmanaged-api/authenticode/certfreeauthenticodesignerinfo-function.md) function after use.</span></span>  
  
 <span data-ttu-id="87b10-119">Bkz: [axl_authentıcode_sıgner_ınfo yapısı](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md).</span><span class="sxs-lookup"><span data-stu-id="87b10-119">See [AXL_AUTHENTICODE_SIGNER_INFO Structure](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md).</span></span>  
  
 `pTimestamperInfo`  
 <span data-ttu-id="87b10-120">[out] Varsa zaman stamper'ın bilgi almak için.</span><span class="sxs-lookup"><span data-stu-id="87b10-120">[out] To receive time stamper's information, if available.</span></span> <span data-ttu-id="87b10-121">Lisans zaman damgalı olmadıysa `dwError` TRUST_E_NOSIGNATURE için ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="87b10-121">If the license was not time-stamped, `dwError` is set to TRUST_E_NOSIGNATURE.</span></span> <span data-ttu-id="87b10-122">Bunu kullanarak kaynakları serbest yapanın sorumluluğundadır [Certfreeauthenticodetimestamperınfo](../../../../docs/framework/unmanaged-api/authenticode/certfreeauthenticodetimestamperinfo-function.md) kullandıktan sonra işlevi.</span><span class="sxs-lookup"><span data-stu-id="87b10-122">It is the caller's responsibility to free resources by using the [CertFreeAuthenticodeTimestamperInfo](../../../../docs/framework/unmanaged-api/authenticode/certfreeauthenticodetimestamperinfo-function.md) function after use.</span></span>  
  
 <span data-ttu-id="87b10-123">Bkz: [axl_authentıcode_tımestamper_ınfo yapısı](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md).</span><span class="sxs-lookup"><span data-stu-id="87b10-123">See [AXL_AUTHENTICODE_TIMESTAMPER_INFO Structure](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="87b10-124">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="87b10-124">Return Value</span></span>  
 <span data-ttu-id="87b10-125">Döndürür `S_OK` başarılı olursa.</span><span class="sxs-lookup"><span data-stu-id="87b10-125">Returns `S_OK` if successful.</span></span> <span data-ttu-id="87b10-126">Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="87b10-126">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87b10-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="87b10-127">See Also</span></span>  
 [<span data-ttu-id="87b10-128">Authenticode</span><span class="sxs-lookup"><span data-stu-id="87b10-128">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)  
 [<span data-ttu-id="87b10-129">GetHashFromHandle Yöntemi</span><span class="sxs-lookup"><span data-stu-id="87b10-129">GetHashFromHandle Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromhandle-method.md)  
 [<span data-ttu-id="87b10-130">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="87b10-130">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
