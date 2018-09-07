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
ms.openlocfilehash: fd77a8a81718837d55f3018564d0f4ba8fdc95ee
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44080332"
---
# <a name="certtimestampauthenticodelicense-function"></a>CertTimestampAuthenticodeLicense İşlevi
Zaman damgaları Authenticode XrML bir lisans.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT CertTimestampAuthenticodeLicense (  
    [in]  PCRYPT_DATA_BLOB   pSignedLicenseBlob,  
    [in]  LPCWSTR            pwszTimestampURI,  
    [out] PCRYPT_DATA_BLOB   pTimestampSignatureBlob  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pSignedLicenseBlob`  
 [in] Zaman damgası olarak imzalı Authenticode XrML lisans. Bkz: [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) yapısı.  
  
 `pwszTimestampURI`  
 [in] Zaman damgası sunucusunun URI'si.  
  
 `pTimestampSignatureBlob`  
 [out] CRYPT_DATA_BLOB base64 kodlamalı zaman damgası imza almak için bir işaretçi. Bu ücretsiz çağrı sahibinin sorumluluğundadır `pTimestampSignatureBlob` -> `pbData` ile `HepFree()` kullandıktan sonra. Bkz: [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) yapısı.  
  
## <a name="remarks"></a>Açıklamalar  
 Zaman damgası imza gerçekten içerikleri SignatureValue Lisans'ın imza gelen ikili biçimdir bir PKCS #7 SignedData ileti değil. Temel olarak, bu lisans bir karşı imza görevi yapar.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `S_OK` işlev başarılı olursa. Aksi takdirde bir hata kodu döndürür.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Authenticode](../../../../docs/framework/unmanaged-api/authenticode/index.md)
