---
title: "_AxlRSAKeyValueToPublicKeyToken İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: _AxlRSAKeyValueToPublicKeyToken
api_location: clr.dll
api_type: DLLExport
ms.assetid: d60f19fe-7bec-47ba-b60e-ba9ce66abf8c
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b1380f658d9c154d9ea41228cace5f9a3eed39b5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="axlrsakeyvaluetopublickeytoken-function"></a>_AxlRSAKeyValueToPublicKeyToken İşlevi
Tanımlayıcı adlı bir ortak anahtar belirteci için bir mod ve üs dönüştürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT _AxlRSAKeyValueToPublicKeyToken (  
    [in]  PCRYPT_DATA_BLOB pModulusBlob,  
    [in]  PCRYPT_DATA_BLOB pExponentBlob,  
    [out] LPWSTR           *ppwszPublicKeyToken  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pModulusBlob`  
 [in] Base64 ile kodlanmış Modulus blob (gelen \<Modulus > öğesi).  Bkz: [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) yapısı.  
  
 `pExponentBlob`  
 [in] Base64 ile kodlanmış üs blob (gelen \<üs > öğesi). Bkz: [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) yapısı.  
  
 `ppwszPublicKeyToken`  
 [out] Bir işaretçi WCHAR * onaltılık kodlanmış ortak anahtar belirteci almak için.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `S_OK`işlev başarılı olursa. Aksi takdirde bir hata kodu döndürür.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Authenticode](../../../../docs/framework/unmanaged-api/authenticode/index.md)
