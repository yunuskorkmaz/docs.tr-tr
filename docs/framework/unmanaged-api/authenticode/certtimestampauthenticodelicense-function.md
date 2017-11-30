---
title: "CertTimestampAuthenticodeLicense İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CertTimestampAuthenticodeLicense
api_location: clr.dll
api_type: DLLExport
ms.assetid: d468325a-21c5-43ce-8567-84e342b22308
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 42ec863e9accbd2156b6eeed5857ff86075cf0a5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
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
 [in] Zaman damgalı olmasını imzalı Authenticode XrML lisans. Bkz: [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) yapısı.  
  
 `pwszTimestampURI`  
 [in] Zaman damgası sunucunun URI.  
  
 `pTimestampSignatureBlob`  
 [out] Base64 ile kodlanmış zaman damgası imza almaya CRYPT_DATA_BLOB gösteren bir işaretçi. Bunu serbest yapanın sorumluluğundadır `pTimestampSignatureBlob` -> `pbData` ile `HepFree()` kullandıktan sonra. Bkz: [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) yapısı.  
  
## <a name="remarks"></a>Açıklamalar  
 Zaman damgası imza gerçekten içerikleri lisans 's imzasından SignatureValue ikili biçiminde olan bir PKCS #7 SignedData ileti değil. Temel olarak, bu lisans karşı imza olarak davranır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `S_OK`işlev başarılı olursa. Aksi takdirde bir hata kodu döndürür.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Authenticode](../../../../docs/framework/unmanaged-api/authenticode/index.md)
