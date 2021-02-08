---
description: ': ICLRStrongName:: StrongNameGetPublicKey Yöntemi hakkında daha fazla bilgi edinin'
title: ICLRStrongName::StrongNameGetPublicKey Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameGetPublicKey
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameGetPublicKey
helpviewer_keywords:
- StrongNameGetPublicKey method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameGetPublicKey method [.NET Framework hosting]
ms.assetid: a31dcaa9-a404-4c1d-8cc7-081827c52935
topic_type:
- apiref
ms.openlocfilehash: 7be64e145f1e26a1260e2b23fd9fe5f97e289478
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799609"
---
# <a name="iclrstrongnamestrongnamegetpublickey-method"></a>ICLRStrongName::StrongNameGetPublicKey Yöntemi

Ortak/özel anahtar çiftinden ortak anahtarı alır. Anahtar çifti, bir şifreleme hizmeti sağlayıcısı (CSP) içinde anahtar kapsayıcı adı olarak veya ham bir bayt koleksiyonu olarak sağlanabilir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT StrongNameGetPublicKey (
    [in]  LPCWSTR   szKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `szKeyContainer`  
 'ndaki Ortak/özel anahtar çiftini içeren anahtar kapsayıcısının adı. `pbKeyBlob`Null ise, `szKeyContainer` CSP içinde geçerli bir kapsayıcı belirtmeniz gerekir. Bu durumda, [ICLRStrongName:: StrongNameGetPublicKey](iclrstrongname-strongnamegetpublickey-method.md) yöntemi kapsayıcıda depolanan anahtar çiftinden ortak anahtarı ayıklar.  
  
 `pbKeyBlob`Null değilse, anahtar çiftinin anahtar ikili büyük nesne (blob) içinde yer aldığı varsayılır.  
  
 Anahtarlar 1024-bit Rivest-Shamir-Adtaman (RSA) imzalama anahtarları olmalıdır. Şu anda başka türde anahtarlar desteklenmiyor.  
  
 `pbKeyBlob`  
 'ndaki Ortak/özel anahtar çifti işaretçisi. Bu çift Win32 işlevi tarafından oluşturulan biçimdedir `CryptExportKey` . `pbKeyBlob`Null ise, tarafından belirtilen anahtar kapsayıcının `szKeyContainer` anahtar çiftini içermesi varsayılır.  
  
 `cbKeyBlob`  
 'ndaki Bayt cinsinden boyutu `pbKeyBlob` .  
  
 `ppbPublicKeyBlob`  
 dışı Döndürülen ortak anahtar blobu. `ppbPublicKeyBlob`Parametresi ortak dil çalışma zamanı tarafından ayrılır ve çağırana döndürülür. Çağıranın, [ICLRStrongName:: StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) metodunu kullanarak belleği boşaltmalıdır.  
  
 `pcbPublicKeyBlob`  
 dışı Döndürülen ortak anahtar BLOBUNUN boyutu.  
  
## <a name="return-value"></a>Dönüş Değeri  

 `S_OK` Yöntem başarıyla tamamlanırsa; Aksi takdirde, hata belirten bir HRESULT değeri (bkz. bir liste için [genel HRESULT değerleri](/windows/win32/seccrypto/common-hresult-values) ).  
  
## <a name="remarks"></a>Açıklamalar  

 Ortak anahtar, [PublicKeyBlob](../strong-naming/publickeyblob-structure.md) yapısında bulunur.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MetaHost. h  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [StrongNameTokenFromPublicKey Yöntemi](iclrstrongname-strongnametokenfrompublickey-method.md)
- [PublicKeyBlob Yapısı](../strong-naming/publickeyblob-structure.md)
- [ICLRStrongName Arabirimi](iclrstrongname-interface.md)
