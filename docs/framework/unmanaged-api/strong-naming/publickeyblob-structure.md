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
ms.openlocfilehash: 75ba3fd634b108c996e848f48000ffcd0600b00c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67774590"
---
# <a name="publickeyblob-structure"></a>PublicKeyBlob Yapısı
, İkili biçimde bir ortak/özel anahtar çifti ortak anahtarını temsil eder.  
  
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
|`SigAlgId`|İmza algoritması için olan tanımlayıcıyla (tür `ALG_ID`, WinCrypt.h içinde tanımlandığı şekilde) ortak anahtarın.|  
|`HashAlgId`|Karma algoritması için olan tanımlayıcıyla (tür `ALG_ID`, WinCrypt.h içinde tanımlandığı şekilde) ortak anahtarın.|  
|`cbPublicKey`|Anahtarın bayt cinsinden uzunluğu.|  
|`PublicKey`|CryptoAPI tarafından verilen biçim anahtar değerini içeren bir değişken uzunluklu bayt dizisi.|  
  
## <a name="remarks"></a>Açıklamalar  
 `PublicKeyBlob` Yapısı tarafından kullanılan [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md), [StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md), bir ortak/özel anahtar çifti ortak anahtarını temsil etmek için İşlevler ve diğerleri tanımlayıcı ad.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** StrongName.h  
  
 **Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [StrongNameGetPublicKey İşlevi](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md)
- [StrongNameSignatureGeneration İşlevi](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md)
