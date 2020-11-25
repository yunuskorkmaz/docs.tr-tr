---
title: GetPublicKeyToken Metodu
ms.date: 03/30/2017
api_name:
- IALink2.GetPublicKeyToken
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetPublicKeyToken
helpviewer_keywords:
- GetPublicKeyToken method
ms.assetid: 4a16374c-94b0-47b0-9fed-88c2b0cdccd4
topic_type:
- apiref
ms.openlocfilehash: e41be6407076a2609a83a5be3b0c42d28914ec38
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720348"
---
# <a name="getpublickeytoken-method"></a>GetPublicKeyToken Metodu

Belirli bir keyfile veya anahtar kapsayıcısı için ortak anahtar belirtecini alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetPublicKeyToken(  
    LPCWSTR pszKeyFile,  
    LPCWSTR pszKeyContainer,  
    void* pvPublicKeyToken,  
    DWORD* pcbPublicKeyToken  
) PURE;  
```  
  
## <a name="parameters"></a>Parametreler  

 `pszKeyFile`  
 Anahtarın dosya adı.  
  
 `pszKeyContainer`  
 Anahtar kapsayıcısının adı.  
  
 `pvPublicKeyToken`  
 Anahtar belirtecinin depolanacağı adres.  
  
 `pcbPublicKeyToken`  
 Tarafından gösterilen arabelleğin boyutunu bayt cinsinden belirtir `pvPublicKeyToken` . Dönüş sonrasında, kullanılan gerçek bayt sayısını içerir.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Yöntem başarılı olursa S_OK döndürür.  
  
## <a name="requirements"></a>Gereksinimler  

 ALink. h gerektirir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IALink2 Arabirimi](ialink2-interface.md)
- [IALink Arabirimi](ialink-interface.md)
- [ALink API](index.md)
