---
title: StrongNameGetPublicKey İşlevi
ms.date: 03/30/2017
api_name:
- StrongNameGetPublicKey
api_location:
- mscoree.dll
- mscorsn.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameGetPublicKey
helpviewer_keywords:
- StrongNameGetPublicKey function [.NET Framework strong naming]
ms.assetid: 5b58c87f-3f72-40df-9b9a-291076931cc3
topic_type:
- apiref
ms.openlocfilehash: fcdd4a3f07b4499fd2388b5d165c409da9150466
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176935"
---
# <a name="strongnamegetpublickey-function"></a>StrongNameGetPublicKey İşlevi
Ortak anahtarı özel/ortak anahtar çiftinden alır. Anahtar çifti, bir şifreleme hizmet sağlayıcısı (CSP) içinde önemli bir kapsayıcı adı olarak veya ham bir bayt koleksiyonu olarak sağlanabilir.  
  
 Bu işlev amortismana kaldırıldı. Bunun yerine [ICLRStrongName::StrongNameGetPublicKey](../hosting/iclrstrongname-strongnamegetpublickey-method.md) yöntemini kullanın.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
BOOLEAN StrongNameGetPublicKey (
    [in]  LPCWSTR   szKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `szKeyContainer`  
 [içinde] Ortak/özel anahtar çiftini içeren anahtar kapsayıcısının adı. Null `pbKeyBlob` ise, `szKeyContainer` CSP içinde geçerli bir kapsayıcı belirtmelidir. Bu durumda, `StrongNameGetPublicKey` ortak anahtarı kapsayıcıda depolanan anahtar çiftinden ayıklar.  
  
 Null `pbKeyBlob` değilse, anahtar çiftinin anahtar ikili büyük nesnesinde (BLOB) bulunduğu varsayılır.  
  
 Anahtarlar 1024 bit Rivest-Shamir-Adleman (RSA) imzalama anahtarları olmalıdır. Şu anda başka anahtar türü desteklenmez.  
  
 `pbKeyBlob`  
 [içinde] Ortak/özel anahtar çiftine işaretçi. Bu çift Win32 `CryptExportKey` işlevi tarafından oluşturulan biçimdedir. Null `pbKeyBlob` ise, tarafından `szKeyContainer` belirtilen anahtar kapsayıcı anahtar çiftini içerdiği varsayılır.  
  
 `cbKeyBlob`  
 [içinde] Boyutu, bayt, ve. `pbKeyBlob`  
  
 `ppbPublicKeyBlob`  
 [çıkış] Döndürülen ortak anahtar BLOB. `ppbPublicKeyBlob` Parametre ortak dil çalışma zamanı tarafından ayrılır ve arayana döndürülür. Arayan [StrongNameFreeBuffer](strongnamefreebuffer-function.md) işlevini kullanarak belleği serbest etmelidir.  
  
 `pcbPublicKeyBlob`  
 [çıkış] Döndürülen ortak anahtar BLOB boyutu.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `true`başarılı bir şekilde tamamlandığında; aksi `false`takdirde, .  
  
## <a name="remarks"></a>Açıklamalar  
 Ortak anahtar [PublicKeyBlob](publickeyblob-structure.md) yapısında yer almaktadır.  
  
 `StrongNameGetPublicKey` İşlev başarıyla tamamlanmamışsa, oluşturulan son hatayı almak için [StrongNameErrorInfo](strongnameerrorinfo-function.md) işlevini arayın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üstbilgi:** StrongName.h  
  
 **Kütüphane:** MsCorEE.dll bir kaynak olarak dahil  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [StrongNameGetPublicKey Yöntemi](../hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [StrongNameTokenFromPublicKey Yöntemi](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [ICLRStrongName Arabirimi](../hosting/iclrstrongname-interface.md)
- [PublicKeyBlob Yapısı](publickeyblob-structure.md)
