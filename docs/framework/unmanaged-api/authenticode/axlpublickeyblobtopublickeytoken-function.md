---
title: _AxlPublicKeyBlobToPublicKeyToken İşlevi
ms.date: 03/30/2017
api_name:
- _AxlPublicKeyBlobToPublicKeyToken
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: 2d92a746-d68c-4f53-a16e-727f071a2d80
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1b2535441da173ee13653c68f25039fd1431261a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61948960"
---
# <a name="axlpublickeyblobtopublickeytoken-function"></a>_AxlPublicKeyBlobToPublicKeyToken İşlevi
Tanımlayıcı ad ortak anahtar belirteci, bir CSP PUBLICKEYBLOB biçiminden hesaplar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT _AxlPublicKeyBlobToPublicKeyToken (  
    [in]  PCCERT_CHAIN_CONTEXT   pCspPublicKeyBlob,  
    [out] LPWSTR                 *ppwszPublicKeyToken  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pCspPublicKeyBlob`  
 [in] CSP ortak anahtar blob'u.  
  
 `ppwszPublicKeyHash`  
 [out] WCHAR işaretçisi * onaltılık kodlanmış ortak anahtar karması almak için.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `S_OK` işlev başarılı olursa; Aksi takdirde `S_FALSE`.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Authenticode](../../../../docs/framework/unmanaged-api/authenticode/index.md)
