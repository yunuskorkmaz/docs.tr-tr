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
ms.openlocfilehash: b197aa539e60a9dbcee55cf190c44b45da3a5fb4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402021"
---
# <a name="axlgetissuerpublickeyhash-function"></a>_AxlGetIssuerPublicKeyHash İşlevi
Belirtilen sertifika imzalamak için kullanılan özel anahtar ile ilişkili ortak anahtarın SHA-1 karma alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT _AxlGetIssuerPublicKeyHash (  
    [in]  IN PCRYPT_DATA_BLOB   pChainContext,  
    [out] LPWSTR                *ppwszPublicKeyHash  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pChainContext`  
 [in] CSP ortak anahtarı blob. Bkz: [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) yapısı.  
  
 `ppwszPublicKeyHash`  
 [out] Bir işaretçi WCHAR * onaltılık kodlanmış ortak anahtar belirteci almak için.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `S_OK` işlev başarılı olursa; Aksi takdirde `S_FALSE`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Authenticode](../../../../docs/framework/unmanaged-api/authenticode/index.md)
