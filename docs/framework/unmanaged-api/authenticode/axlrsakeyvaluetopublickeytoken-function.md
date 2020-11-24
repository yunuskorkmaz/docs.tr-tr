---
title: _AxlRSAKeyValueToPublicKeyToken işlevi
ms.date: 03/30/2017
api_name:
- _AxlRSAKeyValueToPublicKeyToken
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: d60f19fe-7bec-47ba-b60e-ba9ce66abf8c
ms.openlocfilehash: 5c1e2bfc7fd55e807af68744e28faa473daea772
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674222"
---
# <a name="_axlrsakeyvaluetopublickeytoken-function"></a>\_AxlRSAKeyValueToPublicKeyToken işlevi

Bir mod ve üs değeri bir tanımlayıcı ad ortak anahtar belirtecine dönüştürür.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT _AxlRSAKeyValueToPublicKeyToken (  
    [in]  PCRYPT_DATA_BLOB pModulusBlob,  
    [in]  PCRYPT_DATA_BLOB pExponentBlob,  
    [out] LPWSTR           *ppwszPublicKeyToken  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pModulusBlob`  
 'ndaki Base64 ile kodlanmış mod Blobu (öğesinden \<Modulus> ).  [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) yapısına bakın.  
  
 `pExponentBlob`  
 'ndaki Base64 ile kodlanmış üs Blobu (öğesinden \<Exponent> ). [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) yapısına bakın.  
  
 `ppwszPublicKeyToken`  
 dışı Onaltılık kodlanmış ortak anahtar belirtecini almak için bir WCHAR * işaretçisi.  
  
## <a name="return-value"></a>Dönüş Değeri  

 `S_OK` işlev başarılı olursa. Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Authenticode](index.md)
