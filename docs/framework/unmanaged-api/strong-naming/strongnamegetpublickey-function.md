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
ms.openlocfilehash: c97cc0c1d4c022583d0823abeff998e2ed5f719e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95710980"
---
# <a name="strongnamegetpublickey-function"></a>StrongNameGetPublicKey İşlevi

Özel/ortak anahtar çiftinden ortak anahtarı alır. Anahtar çifti, bir şifreleme hizmeti sağlayıcısı (CSP) içinde anahtar kapsayıcı adı olarak veya ham bir bayt koleksiyonu olarak sağlanabilir.  
  
 Bu işlev kullanım dışı bırakıldı. Bunun yerine [ICLRStrongName:: StrongNameGetPublicKey](../hosting/iclrstrongname-strongnamegetpublickey-method.md) metodunu kullanın.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
 'ndaki Ortak/özel anahtar çiftini içeren anahtar kapsayıcısının adı. `pbKeyBlob`Null ise, `szKeyContainer` CSP içinde geçerli bir kapsayıcı belirtmeniz gerekir. Bu durumda, `StrongNameGetPublicKey` kapsayıcıda depolanan anahtar çiftinden ortak anahtarı ayıklar.  
  
 `pbKeyBlob`Null değilse, anahtar çiftinin anahtar ikili büyük nesne (blob) içinde yer aldığı varsayılır.  
  
 Anahtarlar 1024-bit Rivest-Shamir-Adtaman (RSA) imzalama anahtarları olmalıdır. Şu anda başka türde anahtarlar desteklenmiyor.  
  
 `pbKeyBlob`  
 'ndaki Ortak/özel anahtar çifti işaretçisi. Bu çift Win32 işlevi tarafından oluşturulan biçimdedir `CryptExportKey` . `pbKeyBlob`Null ise, tarafından belirtilen anahtar kapsayıcının `szKeyContainer` anahtar çiftini içermesi varsayılır.  
  
 `cbKeyBlob`  
 'ndaki Bayt cinsinden boyutu `pbKeyBlob` .  
  
 `ppbPublicKeyBlob`  
 dışı Döndürülen ortak anahtar blobu. `ppbPublicKeyBlob`Parametresi ortak dil çalışma zamanı tarafından ayrılır ve çağırana döndürülür. Çağıranın, [StrongNameFreeBuffer](strongnamefreebuffer-function.md) işlevini kullanarak belleği boşaltmalıdır.  
  
 `pcbPublicKeyBlob`  
 dışı Döndürülen ortak anahtar BLOBUNUN boyutu.  
  
## <a name="return-value"></a>Dönüş Değeri  

 `true` başarıyla tamamlandığında; Aksi takdirde, `false` .  
  
## <a name="remarks"></a>Açıklamalar  

 Ortak anahtar, [PublicKeyBlob](publickeyblob-structure.md) yapısında bulunur.  
  
 `StrongNameGetPublicKey`İşlev başarıyla tamamlanmazsa, en son oluşturulan hatayı almak Için [StrongNameErrorInfo](strongnameerrorinfo-function.md) işlevini çağırın.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** StrongName. h  
  
 **Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [StrongNameGetPublicKey Yöntemi](../hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [StrongNameTokenFromPublicKey Yöntemi](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [ICLRStrongName Arabirimi](../hosting/iclrstrongname-interface.md)
- [PublicKeyBlob Yapısı](publickeyblob-structure.md)
