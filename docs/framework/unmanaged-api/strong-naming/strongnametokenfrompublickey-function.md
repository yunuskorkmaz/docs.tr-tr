---
title: StrongNameTokenFromPublicKey İşlevi
ms.date: 03/30/2017
api_name:
- StrongNameTokenFromPublicKey
api_location:
- mscoree.dll
- mscorsn.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type:
- COM
f1_keywords:
- StrongNameTokenFromPublicKey
helpviewer_keywords:
- StrongNameTokenFromPublicKey function [.NET Framework strong naming]
ms.assetid: 997e9e57-abb2-4217-bf20-1df621a75add
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 68be16c559431de871dc9ddb1963897b0927d49a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67783161"
---
# <a name="strongnametokenfrompublickey-function"></a>StrongNameTokenFromPublicKey İşlevi
Bir ortak anahtar temsil eden bir belirteç alır. Genel anahtar kısaltılmış bir tanımlayıcı ad belirtecidir.  
  
 Bu işlev kullanım dışı bırakıldı. Kullanım [Iclrstrongname::strongnametokenfrompublickey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md) yöntemi yerine.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
BOOLEANStrongNameTokenFromPublicKey (   
    [in]  BYTE    *pbPublicKeyBlob,  
    [in]  ULONG   cbPublicKeyBlob,  
    [out] BYTE    **ppbStrongNameToken,  
    [out] ULONG   *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pbPublicKeyBlob`  
 [in] Türünden bir yapıyı [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) tanımlayıcı ad imzası oluşturmak için kullanılan anahtar çiftinden ortak kısmını içerir.  
  
 `cbPublicKeyBlob`  
 [in] Bayt cinsinden boyutu, `pbPublicKeyBlob`.  
  
 `ppbStrongNameToken`  
 [out] Anahtarına karşılık gelen tanımlayıcı ad belirteç geçirilen `pbPublicKeyBlob`. Ortak dil çalışma zamanı, bir belirteç döndürecek şekilde bellek ayırır. Çağıranın bu bellek kullanarak ücretsiz gerekir [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) işlevi.  
  
 `pcbStrongNameToken`  
 [out] Döndürülen tanımlayıcı ad belirtecinin bayt cinsinden boyutu.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `true` başarıyla tamamlandığında; Aksi takdirde, `false`.  
  
## <a name="remarks"></a>Açıklamalar  
 Tanımlayıcı ad anahtar bilgilerini meta verileri depolarken alanından tasarruf etmek için kullanılan genel anahtar kısaltılmış belirtecidir. Özellikle, tanımlayıcı ad belirteçleri, derleme başvurularını bağımlı derlemeye başvurmak için kullanılır.  
  
 Varsa `StrongNameTokenFromPublicKey` işlevi değil başarıyla tamamlanması, çağrı [Strongnameerrorınfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) oluşturulan son hatayı alması için işlevi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** StrongName.h  
  
 **Kitaplığı:** Bir kaynak olarak mscoree.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [StrongNameTokenFromPublicKey Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [StrongNameGetPublicKey Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [PublicKeyBlob Yapısı](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
