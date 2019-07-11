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
ms.openlocfilehash: beb9a848a55c71259e4f7421658d56ae95a2f3e7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741220"
---
# <a name="certtimestampauthenticodelicense-function"></a>CertTimestampAuthenticodeLicense İşlevi
Zaman damgaları Authenticode XrML bir lisans.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
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
