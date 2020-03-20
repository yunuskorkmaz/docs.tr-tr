---
title: StrongNameGetPublicKeyEx Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRStrongName2.StrongNameGetPublicKeyEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StrongNameGetPublicKeyEx
helpviewer_keywords:
- StrongNameGetPublicKeyEx method, ICLRStrongName2 interface [.NET Framework hosting]
- ICLRStrongName2::StrongNameGetPublicKeyEx method [.NET Framework hosting]
ms.assetid: 63d8260c-fb32-4f8f-a357-768afd570f68
topic_type:
- apiref
ms.openlocfilehash: 93afe1afd9ea9637d039a8b4a4e81267d49c08b6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176233"
---
# <a name="strongnamegetpublickeyex-method"></a>StrongNameGetPublicKeyEx Yöntemi
Ortak anahtarı ortak/özel anahtar çiftinden alır ve karma algoritma ve imza algoritması belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT StrongNameGetPublicKey (
    [in]  LPCWSTR   pwzKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
    [in]  ULONG     uHashAlgId,  
    [in]  ULONG     uReserved,  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pwzKeyContainer`  
 [içinde] Ortak/özel anahtar çiftini içeren anahtar kapsayıcısının adı. Null `pbKeyBlob` ise, `szKeyContainer` şifreleme hizmet sağlayıcısı (CSP) içinde geçerli bir kapsayıcı belirtilmelidir. Bu durumda, `StrongNameGetPublicKeyEx` yöntem kapsayıcıda depolanan anahtar çiftinden ortak anahtarı ayıklar.  
  
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
  
 `uHashAlgId`  
 [içinde] Derleme karma algoritması. Kabul edilen değerler listesi için Açıklamalar bölümüne bakın.  
  
 `uReserved`  
 [içinde] İleride kullanım için ayrılmış; varsayılan olarak null.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `S_OK`yöntem başarıyla tamamlanırsa; aksi takdirde, başarısızlığı gösteren bir HRESULT değeri (liste için [Ortak HRESULT Değerleri'ne](/windows/win32/seccrypto/common-hresult-values) bakın).  
  
## <a name="remarks"></a>Açıklamalar  
 Ortak anahtar [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) yapısında yer almaktadır.  
  
## <a name="remarks"></a>Açıklamalar  
 Aşağıdaki `uHashAlgId` tabloda parametre için kabul edilen değerler kümesi gösterilmektedir.  
  
|Adı|Değer|  
|----------|-----------|  
|None|0|  
|SHA-1|0x8004|  
|SHA-256|0x800c|  
|ŞA-384|0x800d|  
|ŞAH- 512|0x800e|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** MetaHost.h  
  
 **Kütüphane:** MSCorEE.dll bir kaynak olarak dahil  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [StrongNameTokenFromPublicKey Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [PublicKeyBlob Yapısı](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
- [ICLRStrongName Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
- [StrongNameGetPublicKey Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)
