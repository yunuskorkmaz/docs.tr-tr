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
ms.openlocfilehash: 6c58a0726e0869178838999c6b000e0ad975f145
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140611"
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
|`SigAlgId`|Ortak anahtarın imza algoritmasının (WinCrypt. h içinde tanımlanan `ALG_ID`türü) tanımlayıcı.|  
|`HashAlgId`|Ortak anahtarın karma algoritma (WinCrypt. h içinde tanımlanan `ALG_ID`türü) için tanımlayıcı.|  
|`cbPublicKey`|Anahtarın bayt cinsinden uzunluğu.|  
|`PublicKey`|CryptoAPI tarafından döndürülen biçimdeki anahtar değerini içeren değişken uzunlukta bir bayt dizisi.|  
  
## <a name="remarks"></a>Açıklamalar  
 `PublicKeyBlob` yapısı, [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md)ve Public/Private anahtar çiftinin ortak anahtarını temsil eden diğer tanımlayıcı ad işlevleri tarafından kullanılır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** StrongName. h  
  
 **Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [StrongNameGetPublicKey İşlevi](strongnamegetpublickey-function.md)
- [StrongNameSignatureGeneration İşlevi](strongnamesignaturegeneration-function.md)
