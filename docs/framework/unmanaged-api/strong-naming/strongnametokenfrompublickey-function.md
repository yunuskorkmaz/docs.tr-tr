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
ms.openlocfilehash: 197504cbb0dd66c0cf43dee718026fc63e918d60
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798857"
---
# <a name="strongnametokenfrompublickey-function"></a>StrongNameTokenFromPublicKey İşlevi
Ortak anahtarı temsil eden bir belirteç alır. Tanımlayıcı ad belirteci, ortak anahtarın kısaltılmış biçimidir.  
  
 Bu işlev kullanım dışı bırakıldı. Bunun yerine [ICLRStrongName:: StrongNameTokenFromPublicKey](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md) yöntemini kullanın.  
  
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
 'ndaki Tanımlayıcı ad imzasını oluşturmak için kullanılan anahtar çiftinin ortak bölümünü içeren [PublicKeyBlob](publickeyblob-structure.md) türünde bir yapı.  
  
 `cbPublicKeyBlob`  
 'ndaki Bayt cinsinden boyutu `pbPublicKeyBlob`.  
  
 `ppbStrongNameToken`  
 dışı Geçilen anahtara karşılık gelen tanımlayıcı ad belirteci `pbPublicKeyBlob`. Ortak dil çalışma zamanı, belirtecin döndürüleceği belleği ayırır. Çağıranın bu belleği [StrongNameFreeBuffer](strongnamefreebuffer-function.md) işlevini kullanarak boşaltmalıdır.  
  
 `pcbStrongNameToken`  
 dışı Döndürülen tanımlayıcı ad belirtecinin bayt cinsinden boyutu.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `true`başarıyla tamamlandığında; Aksi takdirde `false`,.  
  
## <a name="remarks"></a>Açıklamalar  
 Tanımlayıcı ad belirteci, anahtar bilgilerini meta verilerde depolarken alan kazanmak için kullanılan bir ortak anahtarın kısaltılmış biçimidir. Özellikle, tanımlayıcı ad belirteçleri, bağımlı derlemeye başvurmak için derleme başvurularında kullanılır.  
  
 İşlev başarıyla tamamlanmazsa, en son oluşturulan hatayı almak için [StrongNameErrorInfo işlevini çağırın.](strongnameerrorinfo-function.md) `StrongNameTokenFromPublicKey`  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi** StrongName. h  
  
 **Kitaplığı** Mscoree. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [StrongNameTokenFromPublicKey Yöntemi](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [StrongNameGetPublicKey Yöntemi](../hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [PublicKeyBlob Yapısı](publickeyblob-structure.md)
