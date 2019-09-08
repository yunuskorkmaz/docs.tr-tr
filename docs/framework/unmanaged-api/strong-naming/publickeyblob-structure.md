---
title: PublicKeyBlob Yapısı
ms.date: 03/30/2017
api_name:
- PublicKeyBlob
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- PublicKeyBlob
helpviewer_keywords:
- PublicKeyBlob structure [.NET Framework strong naming]
ms.assetid: b9240712-829c-4c8d-9a09-a6e7aa63f63a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e66196e2bd2cb326ca3f5badc67bcf8d81e5fc3c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799167"
---
# <a name="publickeyblob-structure"></a>PublicKeyBlob Yapısı
Ortak/özel anahtar çiftinin ortak anahtarını ikili biçimde temsil eder.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef struct {  
    unsigned int SigAlgId;  
    unsigned int HashAlgId;  
    ULONG cbPublicKey;  
    BYTE PublicKey[1]  
} PublicKeyBlob;   
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`SigAlgId`|Ortak anahtarın imza algoritması için tanımlayıcı ( `ALG_ID`Örneğin, Wincrypt. h içinde tanımlanmıştır).|  
|`HashAlgId`|Ortak anahtarın karma algoritmasının (Wincrypt. h `ALG_ID`içinde tanımlanan türü) tanımlayıcı.|  
|`cbPublicKey`|Anahtarın bayt cinsinden uzunluğu.|  
|`PublicKey`|CryptoAPI tarafından döndürülen biçimdeki anahtar değerini içeren değişken uzunlukta bir bayt dizisi.|  
  
## <a name="remarks"></a>Açıklamalar  
 Yapı, [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md)ve ortak/özel anahtar çiftinin ortak anahtarını temsil eden diğer tanımlayıcı ad işlevleri tarafından kullanılır. `PublicKeyBlob`  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi** StrongName. h  
  
 **Kitaplığı** MsCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [StrongNameGetPublicKey İşlevi](strongnamegetpublickey-function.md)
- [StrongNameSignatureGeneration İşlevi](strongnamesignaturegeneration-function.md)
