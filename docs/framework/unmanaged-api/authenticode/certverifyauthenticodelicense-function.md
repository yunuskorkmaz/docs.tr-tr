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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59146932"
---
# <a name="certverifyauthenticodelicense-function"></a>CertVerifyAuthenticodeLicense İşlevi
Authenticode XrML lisans geçerliliğini doğrular.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT CertVerifyAuthenticodeLicense (  
    [in]   PCRYPT_DATA_BLOB                   pLicenseBlob,  
    [in]   OPTIONAL DWORD                     dwFlags,  
    [out]  PAXL_AUTHENTICODE_SIGNER_INFO      pSignerInfo,  
    [out]  PAXL_AUTHENTICODE_TIMESTAMPER_INFO pTimestamperInfo  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pLicenseBlob`  
 [in] Doğrulanacak Authenticode XrML lisans.  
  
 Bkz: [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) yapısı.  
  
 `dwFlags`  
 [in] İsteğe bağlı. Aşağıdaki değerleri birleşimi:  
  
-   AXL_REVOCATION_NO_CHECK  
  
-   AXL_REVOCATION_CHECK_END_CERT_ONLY  
  
-   AXL_REVOCATION_CHECK_ENTIRE_CHAIN  
  
-   AXL_URL_CACHE_ONLY_RETRIEVAL  
  
-   AXL_LIFETIME_SIGNING  
  
-   AXL_TRUST_MICROSOFT_ROOT_ONLY  
  
 `pSignerInfo`  
 [out] İmzalayanın bilgilerini almak için. Lisans değildi açtıysanız `dwError` TRUST_E_NOSIGNATURE için ayarlanır. Bunu kullanarak kaynakları serbest bırakacak arayanın sorumluluğundadır [Certfreeauthenticodesignerınfo](../../../../docs/framework/unmanaged-api/authenticode/certfreeauthenticodesignerinfo-function.md) işlevinden sonra kullanın.  
  
 Bkz: [axl_authentıcode_sıgner_ınfo yapısı](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md).  
  
 `pTimestamperInfo`  
 [out] Varsa zaman stamper'ın bilgi almak için. Lisans zaman damgalı değilse `dwError` TRUST_E_NOSIGNATURE için ayarlanır. Bunu kullanarak kaynakları serbest bırakacak arayanın sorumluluğundadır [Certfreeauthenticodetimestamperınfo](../../../../docs/framework/unmanaged-api/authenticode/certfreeauthenticodetimestamperinfo-function.md) işlevinden sonra kullanın.  
  
 Bkz: [axl_authentıcode_tımestamper_ınfo yapısı](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md).  
  
## <a name="return-value"></a>Dönüş Değeri  
 Döndürür `S_OK` başarılı olursa. Aksi takdirde bir hata kodu döndürür.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Authenticode](../../../../docs/framework/unmanaged-api/authenticode/index.md)
- [GetHashFromHandle Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromhandle-method.md)
- [ICLRStrongName Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
