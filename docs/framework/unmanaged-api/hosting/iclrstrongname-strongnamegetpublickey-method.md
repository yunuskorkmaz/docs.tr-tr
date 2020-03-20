---
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
ms.openlocfilehash: cb96c7e17627205db0573e56fc8c2a29e7717434
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181931"
---
# <a name="iclrstrongnamestrongnamegetpublickey-method"></a>ICLRStrongName::StrongNameGetPublicKey Yöntemi
Ortak anahtarı genel/özel anahtar çiftinden alır. Anahtar çifti, bir şifreleme hizmet sağlayıcısı (CSP) içinde önemli bir kapsayıcı adı olarak veya ham bir bayt koleksiyonu olarak sağlanabilir.  
  
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
 [içinde] Ortak/özel anahtar çiftini içeren anahtar kapsayıcısının adı. Null `pbKeyBlob` ise, `szKeyContainer` CSP içinde geçerli bir kapsayıcı belirtmelidir. Bu durumda, [ICLRStrongName::StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md) yöntemi, kapsayıcıda depolanan anahtar çiftinden ortak anahtarı ayıklar.  
  
 Null `pbKeyBlob` değilse, anahtar çiftinin anahtar ikili büyük nesnesinde (BLOB) bulunduğu varsayılır.  
  
 Anahtarlar 1024 bit Rivest-Shamir-Adleman (RSA) imzalama anahtarları olmalıdır. Şu anda başka anahtar türü desteklenmez.  
  
 `pbKeyBlob`  
 [içinde] Ortak/özel anahtar çiftine işaretçi. Bu çift Win32 `CryptExportKey` işlevi tarafından oluşturulan biçimdedir. Null `pbKeyBlob` ise, tarafından `szKeyContainer` belirtilen anahtar kapsayıcı anahtar çiftini içerdiği varsayılır.  
  
 `cbKeyBlob`  
 [içinde] Boyutu, bayt, ve. `pbKeyBlob`  
  
 `ppbPublicKeyBlob`  
 [çıkış] Döndürülen ortak anahtar BLOB. `ppbPublicKeyBlob` Parametre ortak dil çalışma zamanı tarafından ayrılır ve arayana döndürülür. Arayan ICLRStrongName kullanarak bellek serbest [gerekir::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) yöntemi.  
  
 `pcbPublicKeyBlob`  
 [çıkış] Döndürülen ortak anahtar BLOB boyutu.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `S_OK`yöntem başarıyla tamamlanırsa; aksi takdirde, başarısızlığı gösteren bir HRESULT değeri (liste için [Ortak HRESULT Değerleri'ne](/windows/win32/seccrypto/common-hresult-values) bakın).  
  
## <a name="remarks"></a>Açıklamalar  
 Ortak anahtar [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) yapısında yer almaktadır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** MetaHost.h  
  
 **Kütüphane:** MSCorEE.dll bir kaynak olarak dahil  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [StrongNameTokenFromPublicKey Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [PublicKeyBlob Yapısı](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
- [ICLRStrongName Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
