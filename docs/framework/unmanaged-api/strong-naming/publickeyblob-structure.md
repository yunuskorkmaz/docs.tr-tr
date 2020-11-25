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
ms.openlocfilehash: 42cd3cc22fbbb8eb3d5ac44544fce36650b6461f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705936"
---
# <a name="publickeyblob-structure"></a>PublicKeyBlob Yapısı

Ortak/özel anahtar çiftinin ortak anahtarını ikili biçimde temsil eder.  
  
## <a name="syntax"></a>Syntax  
  
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
|`SigAlgId`|Ortak anahtarın imza algoritması için tanımlayıcı ( `ALG_ID` Örneğin, WinCrypt. h içinde tanımlanmıştır).|  
|`HashAlgId`|Ortak anahtarın karma algoritmasının ( `ALG_ID` WinCrypt. h içinde tanımlanan türü) tanımlayıcı.|  
|`cbPublicKey`|Anahtarın bayt cinsinden uzunluğu.|  
|`PublicKey`|CryptoAPI tarafından döndürülen biçimdeki anahtar değerini içeren değişken uzunlukta bir bayt dizisi.|  
  
## <a name="remarks"></a>Açıklamalar  

 `PublicKeyBlob`Yapı, [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md)ve ortak/özel anahtar çiftinin ortak anahtarını temsil eden diğer tanımlayıcı ad işlevleri tarafından kullanılır.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** StrongName. h  
  
 **Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [StrongNameGetPublicKey İşlevi](strongnamegetpublickey-function.md)
- [StrongNameSignatureGeneration İşlevi](strongnamesignaturegeneration-function.md)
