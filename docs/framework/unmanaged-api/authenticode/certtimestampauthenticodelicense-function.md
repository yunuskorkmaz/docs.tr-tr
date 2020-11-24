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
ms.openlocfilehash: fc1a99572406a38aee8133d6435134b78a134175
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674105"
---
# <a name="certtimestampauthenticodelicense-function"></a>CertTimestampAuthenticodeLicense İşlevi

Zaman damgalarının Authenticode XrML lisansı.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT CertTimestampAuthenticodeLicense (  
    [in]  PCRYPT_DATA_BLOB   pSignedLicenseBlob,  
    [in]  LPCWSTR            pwszTimestampURI,  
    [out] PCRYPT_DATA_BLOB   pTimestampSignatureBlob  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pSignedLicenseBlob`  
 'ndaki Zaman damgalı olarak imzalanan Authenticode XrML lisansı. [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) yapısına bakın.  
  
 `pwszTimestampURI`  
 'ndaki Zaman damgası sunucusunun URI 'SI.  
  
 `pTimestampSignatureBlob`  
 dışı Base64 ile kodlanmış zaman damgası imzasını almak için CRYPT_DATA_BLOB işaretçisi. Bu, `pTimestampSignatureBlob` -> `pbData` kullandıktan sonra, çağıranın ücretsiz olarak kullanılacağı sorumluluğudur `HepFree()` . [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) yapısına bakın.  
  
## <a name="remarks"></a>Açıklamalar  

 Zaman damgası imzası aslında, içeriği lisansın imzasıyla olan SignatureValue 'un ikili biçimi olan PKCS #7 SignedData iletisidir. Temelde, bu, lisansın sayaç imzası olarak görev yapar.  
  
## <a name="return-value"></a>Dönüş Değeri  

 `S_OK` işlev başarılı olursa. Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Authenticode](index.md)
