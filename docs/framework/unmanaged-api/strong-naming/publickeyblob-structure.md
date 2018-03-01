---
title: "PublicKeyBlob Yapısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b1f04c692b7549c4d7d8d431591eeb867b673d9a
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="publickeyblob-structure"></a>PublicKeyBlob Yapısı
, İkili dosya biçiminde bir genel/özel anahtar çifti ortak anahtarını temsil eder.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
|`SigAlgId`|İmza algoritmasının tanımlayıcıyı (tür `ALG_ID`, WinCrypt.h içinde tanımlandığı gibi) ortak anahtarın.|  
|`HashAlgId`|Karma algoritmasının tanımlayıcıyı (tür `ALG_ID`, WinCrypt.h içinde tanımlandığı gibi) ortak anahtarın.|  
|`cbPublicKey`|Anahtar bayt cinsinden uzunluğu.|  
|`PublicKey`|CryptoAPI tarafından döndürülen biçimindeki anahtar değerini içeren bir değişken uzunlukta bayt dizisi.|  
  
## <a name="remarks"></a>Açıklamalar  
 `PublicKeyBlob` Yapısı tarafından kullanılan [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md), [StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md)ve bir genel/özel anahtar çifti ortak anahtarını temsil etmek için diğer güçlü ad işlevleri.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** StrongName.h  
  
 **Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [StrongNameGetPublicKey İşlevi](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md)  
 [StrongNameSignatureGeneration İşlevi](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md)  
 [Güçlü adlandırma yapıları](http://msdn.microsoft.com/library/4b041a2f-fd12-4b91-aacd-bc3b34a5124d)
