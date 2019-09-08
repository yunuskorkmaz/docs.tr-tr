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
# <a name="certtimestampauthenticodelicense-function"></a>CertTimestampAuthenticodeLicense İşlevi
Zaman damgalarının Authenticode XrML lisansı.  
  
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
 'ndaki Zaman damgalı olarak imzalanan Authenticode XrML lisansı. Bkz. [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) yapısı.  
  
 `pwszTimestampURI`  
 'ndaki Zaman damgası sunucusunun URI 'SI.  
  
 `pTimestampSignatureBlob`  
 dışı Base64 ile kodlanmış zaman damgası imzasını almak için CRYPT_DATA_BLOB işaretçisi. Bu, `pTimestampSignatureBlob` `HepFree()` kullandıktan sonra, çağıranın ücretsiz -> `pbData` olarak kullanılacağı sorumluluğudur. Bkz. [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) yapısı.  
  
## <a name="remarks"></a>Açıklamalar  
 Zaman damgası imzası aslında, içeriği lisansın imzasıyla olan SignatureValue 'un ikili biçimi olan PKCS #7 SignedData iletisidir. Temelde, bu, lisansın sayaç imzası olarak görev yapar.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `S_OK`işlev başarılı olursa. Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Authenticode](index.md)
