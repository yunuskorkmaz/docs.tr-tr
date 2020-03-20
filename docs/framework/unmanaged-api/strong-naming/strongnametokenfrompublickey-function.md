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
ms.openlocfilehash: 20be3114908ef78966eead05ae8ba6333a491404
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175063"
---
# <a name="strongnametokenfrompublickey-function"></a>StrongNameTokenFromPublicKey İşlevi
Ortak anahtarı temsil eden bir belirteç alır. Güçlü bir ad belirteci, ortak anahtarın kısaltılmış biçimidir.  
  
 Bu işlev amortismana kaldırıldı. Bunun yerine [ICLRStrongName::StrongNameTokenFromPublicKey](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md) yöntemini kullanın.  
  
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
 [içinde] Güçlü ad imzasını oluşturmak için kullanılan anahtar çiftinin ortak bölümünü içeren [PublicKeyBlob](publickeyblob-structure.md) türünden bir yapı.  
  
 `cbPublicKeyBlob`  
 [içinde] Boyutu, bayt, ve. `pbPublicKeyBlob`  
  
 `ppbStrongNameToken`  
 [çıkış] Anahtara karşılık gelen güçlü ad `pbPublicKeyBlob`belirteci. Ortak dil çalışma süresi belirteci döndürmek için bellek ayırır. Arayan, [StrongNameFreeBuffer](strongnamefreebuffer-function.md) işlevini kullanarak bu belleği serbest etmelidir.  
  
 `pcbStrongNameToken`  
 [çıkış] Döndürülen güçlü ad belirteci boyutu, baytlar halinde.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `true`başarılı bir şekilde tamamlandığında; aksi `false`takdirde, .  
  
## <a name="remarks"></a>Açıklamalar  
 Güçlü bir ad belirteci, meta verilerde önemli bilgileri depolarken yer kazanmak için kullanılan ortak anahtarın kısaltılmış biçimidir. Özellikle, bağlı derleme başvurmak için derleme başvurularında güçlü ad belirteçleri kullanılır.  
  
 `StrongNameTokenFromPublicKey` İşlev başarıyla tamamlanmamışsa, oluşturulan son hatayı almak için [StrongNameErrorInfo](strongnameerrorinfo-function.md) işlevini arayın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üstbilgi:** StrongName.h  
  
 **Kütüphane:** mscoree.dll'de kaynak olarak dahil  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [StrongNameTokenFromPublicKey Yöntemi](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [StrongNameGetPublicKey Yöntemi](../hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [PublicKeyBlob Yapısı](publickeyblob-structure.md)
