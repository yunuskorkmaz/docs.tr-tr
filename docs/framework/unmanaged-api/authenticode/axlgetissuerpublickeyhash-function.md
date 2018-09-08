---
title: _AxlGetIssuerPublicKeyHash İşlevi
ms.date: 03/30/2017
api_name:
- _AxlGetIssuerPublicKeyHash
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: fb626b41-b888-4625-84c3-2c02b5e3866f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 408b71bf38427d12418e05f8b509fe841bc95ef1
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44191865"
---
# <a name="axlgetissuerpublickeyhash-function"></a>_AxlGetIssuerPublicKeyHash İşlevi
Belirtilen sertifika imzalamak için kullanılan özel anahtarıyla ilişkilendirilmiş ortak anahtar SHA-1 karmasını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT _AxlGetIssuerPublicKeyHash (  
    [in]  IN PCRYPT_DATA_BLOB   pChainContext,  
    [out] LPWSTR                *ppwszPublicKeyHash  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pChainContext`  
 [in] CSP ortak anahtar blob'u. Bkz: [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) yapısı.  
  
 `ppwszPublicKeyHash`  
 [out] WCHAR işaretçisi * onaltılık kodlanmış ortak anahtar belirteci almak için.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `S_OK` işlev başarılı olursa; Aksi takdirde `S_FALSE`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Authenticode](../../../../docs/framework/unmanaged-api/authenticode/index.md)
