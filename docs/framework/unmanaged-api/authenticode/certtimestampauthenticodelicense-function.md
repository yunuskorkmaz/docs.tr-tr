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
ms.openlocfilehash: 3c5e803c874e1254510f75189846d7cb12cb1ee2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132467"
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
 dışı Base64 ile kodlanmış zaman damgası imzasını almak için CRYPT_DATA_BLOB işaretçisi. Bu, `pTimestampSignatureBlob`->`pbData` kullandıktan sonra `HepFree()` ile ücretsiz olarak kullanmanın sorumluluğundadır. Bkz. [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) yapısı.  
  
## <a name="remarks"></a>Açıklamalar  
 Zaman damgası imzası aslında, içeriği lisansın imzasıyla olan SignatureValue 'un ikili biçimi olan PKCS #7 SignedData iletisidir. Temelde, bu, lisansın sayaç imzası olarak görev yapar.  
  
## <a name="return-value"></a>Dönüş Değeri  
 işlev başarılı olursa `S_OK`. Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Authenticode](index.md)
