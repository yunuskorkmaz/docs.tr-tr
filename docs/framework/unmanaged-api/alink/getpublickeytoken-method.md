---
title: GetPublicKeyToken Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink2.GetPublicKeyToken
api_location: alink.dll
api_type: COM
f1_keywords: GetPublicKeyToken
helpviewer_keywords: GetPublicKeyToken method
ms.assetid: 4a16374c-94b0-47b0-9fed-88c2b0cdccd4
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5f41c8088f095802cf35239afab279d6324adb55
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
 [Ialink2 arabirimi](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [Ialink arabirimi](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [ALink API](../../../../docs/framework/unmanaged-api/alink/index.md)
