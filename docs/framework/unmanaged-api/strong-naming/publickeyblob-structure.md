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
ms.openlocfilehash: 3b00bf8295a635871bd7263928ff21c97053cc39
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176961"
---
# <a name="publickeyblob-structure"></a>PublicKeyBlob Yapısı
İkili biçimde, ortak/özel anahtar çiftinin ortak anahtarını temsil eder.  
  
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
|`SigAlgId`|Ortak anahtarın imza algoritması (winCrypt.h'de tanımlandığı gibi türü) `ALG_ID`tanımlayıcısı.|  
|`HashAlgId`|Ortak anahtarın karma algoritması (türü `ALG_ID`, WinCrypt.h'de tanımlandığı şekilde) tanımlayıcısı.|  
|`cbPublicKey`|Baytlarda anahtarın uzunluğu.|  
|`PublicKey`|CryptoAPI tarafından döndürülen biçimdeki anahtar değerini içeren değişken uzunlukta bayt dizisi.|  
  
## <a name="remarks"></a>Açıklamalar  
 Yapı, `PublicKeyBlob` genel/özel anahtar çiftinin ortak anahtarını temsil etmek için [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md)ve diğer güçlü ad işlevleri tarafından kullanılır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üstbilgi:** StrongName.h  
  
 **Kütüphane:** MsCorEE.dll bir kaynak olarak dahil  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [StrongNameGetPublicKey İşlevi](strongnamegetpublickey-function.md)
- [StrongNameSignatureGeneration İşlevi](strongnamesignaturegeneration-function.md)
