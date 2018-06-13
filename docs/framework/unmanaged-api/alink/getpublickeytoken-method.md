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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 94a473d00110c07615ccdfc98bb8944e40dc30e3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405479"
---
# <a name="getpublickeytoken-method"></a>GetPublicKeyToken Metodu
Belirtilen keyfile veya anahtar kapsayıcısı için ortak anahtar belirteci alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetPublicKeyToken(  
    LPCWSTR pszKeyFile,  
    LPCWSTR pszKeyContainer,  
    void* pvPublicKeyToken,  
    DWORD* pcbPublicKeyToken  
) PURE;  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pszKeyFile`  
 Anahtar adı.  
  
 `pszKeyContainer`  
 Anahtar kapsayıcı adı.  
  
 `pvPublicKeyToken`  
 Burada depolanması için anahtar belirteci, adres.  
  
 `pcbPublicKeyToken`  
 Tarafından gösterilen arabelleğin bayt cinsinden boyutu belirtir `pvPublicKeyToken`. Return sırasında kullanılan bayt gerçek sayısını içerir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 ALink.h gerektirir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IALink2 Arabirimi](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [IALink Arabirimi](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [ALink API](../../../../docs/framework/unmanaged-api/alink/index.md)
