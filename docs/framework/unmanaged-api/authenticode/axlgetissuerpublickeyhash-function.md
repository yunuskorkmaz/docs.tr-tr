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
ms.openlocfilehash: 4b101a912eb58ed14f81d847ea2fd6ce9f22c065
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787091"
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
 `S_OK`işlev başarılı olursa; Aksi `S_FALSE`takdirde.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Authenticode](index.md)
