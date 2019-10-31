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
ms.openlocfilehash: 6d5ad995b55a3cde6363b297df6b8faf72689468
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132482"
---
# <a name="_axlgetissuerpublickeyhash-function"></a>\_Axlgetıserpublickeyhash Işlevi
Belirtilen sertifikayı imzalamak için kullanılan özel anahtarla ilişkili ortak anahtarın SHA-1 karmasını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT _AxlGetIssuerPublicKeyHash (  
    [in]  IN PCRYPT_DATA_BLOB   pChainContext,  
    [out] LPWSTR                *ppwszPublicKeyHash  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pChainContext`  
 'ndaki CSP ortak anahtar blobu. Bkz. [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) yapısı.  
  
 `ppwszPublicKeyHash`  
 dışı Onaltılık kodlanmış ortak anahtar belirtecini almak için bir WCHAR * işaretçisi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 işlev başarılı olursa `S_OK`; Aksi takdirde `S_FALSE`.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Authenticode](index.md)
