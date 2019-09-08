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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ae87ebd0b8225f14ca029fac80528d47f5a866cf
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799066"
---
# <a name="strongnamegetpublickey-function"></a>StrongNameGetPublicKey İşlevi
Özel/ortak anahtar çiftinden ortak anahtarı alır. Anahtar çifti, bir şifreleme hizmeti sağlayıcısı (CSP) içinde anahtar kapsayıcı adı olarak veya ham bir bayt koleksiyonu olarak sağlanabilir.  
  
 Bu işlev kullanım dışı bırakıldı. Bunun yerine [ICLRStrongName:: StrongNameGetPublicKey](../hosting/iclrstrongname-strongnamegetpublickey-method.md) metodunu kullanın.  
  
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
 'ndaki Ortak/özel anahtar çiftini içeren anahtar kapsayıcısının adı. Null ise, `szKeyContainer` CSP içinde geçerli bir kapsayıcı belirtmeniz gerekir. `pbKeyBlob` Bu durumda, `StrongNameGetPublicKey` kapsayıcıda depolanan anahtar çiftinden ortak anahtarı ayıklar.  
  
 `pbKeyBlob` Null değilse, anahtar çiftinin anahtar ikili büyük nesne (blob) içinde yer aldığı varsayılır.  
  
 Anahtarlar 1024-bit Rivest-Shamir-Adtaman (RSA) imzalama anahtarları olmalıdır. Şu anda başka türde anahtarlar desteklenmiyor.  
  
 `pbKeyBlob`  
 'ndaki Ortak/özel anahtar çifti işaretçisi. Bu çift Win32 `CryptExportKey` işlevi tarafından oluşturulan biçimdedir. Null ise, tarafından `szKeyContainer` belirtilen anahtar kapsayıcının anahtar çiftini içermesi varsayılır. `pbKeyBlob`  
  
 `cbKeyBlob`  
 'ndaki Bayt cinsinden boyutu `pbKeyBlob`.  
  
 `ppbPublicKeyBlob`  
 dışı Döndürülen ortak anahtar blobu. `ppbPublicKeyBlob` Parametresi ortak dil çalışma zamanı tarafından ayrılır ve çağırana döndürülür. Çağıranın, [StrongNameFreeBuffer](strongnamefreebuffer-function.md) işlevini kullanarak belleği boşaltmalıdır.  
  
 `pcbPublicKeyBlob`  
 dışı Döndürülen ortak anahtar BLOBUNUN boyutu.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `true`başarıyla tamamlandığında; Aksi takdirde `false`,.  
  
## <a name="remarks"></a>Açıklamalar  
 Ortak anahtar, [PublicKeyBlob](publickeyblob-structure.md) yapısında bulunur.  
  
 İşlev başarıyla tamamlanmazsa, en son oluşturulan hatayı almak için [StrongNameErrorInfo işlevini çağırın.](strongnameerrorinfo-function.md) `StrongNameGetPublicKey`  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi** StrongName. h  
  
 **Kitaplığı** MsCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [StrongNameGetPublicKey Yöntemi](../hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [StrongNameTokenFromPublicKey Yöntemi](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [ICLRStrongName Arabirimi](../hosting/iclrstrongname-interface.md)
- [PublicKeyBlob Yapısı](publickeyblob-structure.md)
