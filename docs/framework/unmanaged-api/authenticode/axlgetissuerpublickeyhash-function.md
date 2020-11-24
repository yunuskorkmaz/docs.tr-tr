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
ms.openlocfilehash: 49674e43109108e41b135cecbec061ad61e14865
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679968"
---
# <a name="_axlgetissuerpublickeyhash-function"></a>\_Axlgetıserpublickeyhash Işlevi

Belirtilen sertifikayı imzalamak için kullanılan özel anahtarla ilişkili ortak anahtarın SHA-1 karmasını alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT _AxlGetIssuerPublicKeyHash (  
    [in]  IN PCRYPT_DATA_BLOB   pChainContext,  
    [out] LPWSTR                *ppwszPublicKeyHash  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pChainContext`  
 'ndaki CSP ortak anahtar blobu. [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) yapısına bakın.  
  
 `ppwszPublicKeyHash`  
 dışı Onaltılık kodlanmış ortak anahtar belirtecini almak için bir WCHAR * işaretçisi.  
  
## <a name="return-value"></a>Dönüş Değeri  

 `S_OK` işlev başarılı olursa; Aksi takdirde `S_FALSE` .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Authenticode](index.md)
