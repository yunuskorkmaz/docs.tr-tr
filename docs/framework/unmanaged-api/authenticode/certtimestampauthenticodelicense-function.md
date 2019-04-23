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
ms.openlocfilehash: 5ac7cf92fb9c57491ff45e664513c0e82f22db9f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59111728"
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
  
## <a name="parameters"></a>Parametreler  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [Authenticode](../../../../docs/framework/unmanaged-api/authenticode/index.md)
