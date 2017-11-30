---
title: "StrongNameTokenFromPublicKey İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameTokenFromPublicKey
api_location:
- mscoree.dll
- mscorsn.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type: COM
f1_keywords: StrongNameTokenFromPublicKey
helpviewer_keywords: StrongNameTokenFromPublicKey function [.NET Framework strong naming]
ms.assetid: 997e9e57-abb2-4217-bf20-1df621a75add
topic_type: apiref
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cfde09f6383646f24077c3bdc0efa4b31bc50ba0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="strongnametokenfrompublickey-function"></a>StrongNameTokenFromPublicKey İşlevi
Bir ortak anahtar temsil eden bir belirteci alır. Güçlü ad simgesi bir ortak anahtar kısaltılmış şeklidir.  
  
 Bu işlev kullanım dışı bırakıldı. Kullanım [Iclrstrongname::strongnametokenfrompublickey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md) yöntemi yerine.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
BOOLEANStrongNameTokenFromPublicKey (   
    [in]  BYTE    *pbPublicKeyBlob,  
    [in]  ULONG   cbPublicKeyBlob,  
    [out] BYTE    **ppbStrongNameToken,  
    [out] ULONG   *pcbStrongNameToken  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pbPublicKeyBlob`  
 [in] Türü yapısını [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) sağlam ad imzası oluşturmak için kullanılan anahtar çifti ortak kısmını içerir.  
  
 `cbPublicKeyBlob`  
 [in] Bayt olarak boyutu, `pbPublicKeyBlob`.  
  
 `ppbStrongNameToken`  
 [out] Güçlü ad belirtecin anahtarına karşılık gelen geçirilen `pbPublicKeyBlob`. Ortak dil çalışma zamanı, belirteç döndürmek bellek ayırır. Çağıranın bu bellek kullanarak serbest gerekir [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) işlevi.  
  
 `pcbStrongNameToken`  
 [out] Döndürülen güçlü ad belirtecin bayt cinsinden boyutu.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `true`başarılı tamamlanma; Aksi takdirde `false`.  
  
## <a name="remarks"></a>Açıklamalar  
 Güçlü ad simgesi anahtar bilgileri meta verilerde depolarken alanı kaydetmek için kullanılan bir ortak anahtar kısaltılmış şeklidir. Özellikle, güçlü ad simgeleri derleme başvurularını bağımlı derlemenin başvurmak için kullanılır.  
  
 Varsa `StrongNameTokenFromPublicKey` işlevi yok başarıyla tamamlanması, çağrı [Strongnameerrorınfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) son oluşturulan hata alınacak işlev.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** StrongName.h  
  
 **Kitaplığı:** bir kaynak olarak mscoree.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [StrongNameTokenFromPublicKey yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)  
 [StrongNameGetPublicKey yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)  
 [PublicKeyBlob yapısı](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
