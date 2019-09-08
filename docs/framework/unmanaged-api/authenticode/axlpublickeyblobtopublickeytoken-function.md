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
ms.openlocfilehash: b4d720480e4c8b21b3aa56ce81634a26ac9c75de
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70776679"
---
# <a name="_axlpublickeyblobtopublickeytoken-function"></a>\_AxlPublicKeyBlobToPublicKeyToken Işlevi
Bir CSP PUBLICKEYBLOB biçiminden tanımlayıcı ad ortak anahtar belirtecini hesaplar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT _AxlPublicKeyBlobToPublicKeyToken (  
    [in]  PCCERT_CHAIN_CONTEXT   pCspPublicKeyBlob,  
    [out] LPWSTR                 *ppwszPublicKeyToken  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pCspPublicKeyBlob`  
 'ndaki CSP ortak anahtar blobu.  
  
 `ppwszPublicKeyHash`  
 dışı Onaltılık kodlanmış ortak anahtar karmasını almak için bir WCHAR * işaretçisi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `S_OK`işlev başarılı olursa; Aksi `S_FALSE`takdirde.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Authenticode](index.md)
