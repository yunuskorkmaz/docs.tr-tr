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
ms.openlocfilehash: 3d8ab96c758b946684af78bfa21822fdaf96530a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786977"
---
# <a name="certverifyauthenticodelicense-function"></a>CertVerifyAuthenticodeLicense İşlevi
Authenticode XrML lisansının geçerliliğini doğrular.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT CertVerifyAuthenticodeLicense (  
    [in]   PCRYPT_DATA_BLOB                   pLicenseBlob,  
    [in]   OPTIONAL DWORD                     dwFlags,  
    [out]  PAXL_AUTHENTICODE_SIGNER_INFO      pSignerInfo,  
    [out]  PAXL_AUTHENTICODE_TIMESTAMPER_INFO pTimestamperInfo  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pLicenseBlob`  
 'ndaki Doğrulanacak olan Authenticode XrML lisansı.  
  
 Bkz. [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) yapısı.  
  
 `dwFlags`  
 'ndaki Seçim. Aşağıdaki değerlerden oluşan bir bileşim:  
  
- AXL_REVOCATION_NO_CHECK  
  
- AXL_REVOCATION_CHECK_END_CERT_ONLY  
  
- AXL_REVOCATION_CHECK_ENTIRE_CHAIN  
  
- AXL_URL_CACHE_ONLY_RETRIEVAL  
  
- AXL_LIFETIME_SIGNING  
  
- AXL_TRUST_MICROSOFT_ROOT_ONLY  
  
 `pSignerInfo`  
 dışı İmzalayan bilgilerini almak için. Lisans imzalanmadıysa, `dwError` TRUST_E_NOSIGNATURE olarak ayarlanır. Bu, kullandıktan sonra [CertFreeAuthenticodeSignerInfo](certfreeauthenticodesignerinfo-function.md) işlevini kullanarak kaynakların serbest bir şekilde kullanıma yönelik sorumluluğundadır.  
  
 Bkz. [AXL_AUTHENTICODE_SIGNER_INFO yapısı](axl-authenticode-signer-info-structure.md).  
  
 `pTimestamperInfo`  
 dışı Varsa, zaman Stamper 'ın bilgilerini almak için. Lisans zaman damgalı değilse, `dwError` TRUST_E_NOSIGNATURE olarak ayarlanır. Bu, kullandıktan sonra [CertFreeAuthenticodeTimestamperInfo](certfreeauthenticodetimestamperinfo-function.md) işlevini kullanarak kaynakların serbest bir şekilde kullanıma yönelik sorumluluğundadır.  
  
 Bkz. [AXL_AUTHENTICODE_TIMESTAMPER_INFO yapısı](axl-authenticode-timestamper-info-structure.md).  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı `S_OK` olursa döndürür. Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Authenticode](index.md)
- [GetHashFromHandle Yöntemi](../hosting/iclrstrongname-gethashfromhandle-method.md)
- [ICLRStrongName Arabirimi](../hosting/iclrstrongname-interface.md)
