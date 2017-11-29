---
title: "ICLRStrongName::StrongNameGetPublicKey Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName.StrongNameGetPublicKey
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::StrongNameGetPublicKey
helpviewer_keywords:
- StrongNameGetPublicKey method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameGetPublicKey method [.NET Framework hosting]
ms.assetid: a31dcaa9-a404-4c1d-8cc7-081827c52935
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4b7ace87a5eff5235d85507bda649e55ea18fd93
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrstrongnamestrongnamegetpublickey-method"></a>ICLRStrongName::StrongNameGetPublicKey Yöntemi
Ortak anahtarı bir genel/özel anahtar çifti alır. Anahtar çifti, şifreleme hizmeti sağlayıcısı (CSP) içinde bir anahtar kapsayıcı adı veya ham bayt koleksiyonu olarak sağlanabilir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT StrongNameGetPublicKey (   
    [in]  LPCWSTR   szKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `szKeyContainer`  
 [in] Ortak/özel anahtar çiftini içeren anahtar kapsayıcı adı. Varsa `pbKeyBlob` null, `szKeyContainer` CSP Geçerli kapsayıcıda belirtmeniz gerekir. Bu durumda, [Iclrstrongname::strongnamegetpublickey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md) yöntemi kapsayıcısında depolanan anahtar çifti gelen ortak anahtarı ayıklar.  
  
 Varsa `pbKeyBlob` anahtar çifti varsayılır anahtar ikili büyük nesne (BLOB) dahil edilmek üzere null değil.  
  
 1024 bit Rivest-Shamir-Adleman (RSA) anahtarları İmzalama anahtarları olmalıdır. Başka tür anahtarları şu anda desteklenir.  
  
 `pbKeyBlob`  
 [in] Ortak/özel anahtar çifti için bir işaretçi. Bu çiftidir Win32 tarafından oluşturulan biçiminde `CryptExportKey` işlevi. Varsa `pbKeyBlob` null, belirtilen anahtar kapsayıcısı olan `szKeyContainer` anahtar çiftini içeren varsayılır.  
  
 `cbKeyBlob`  
 [in] Bayt olarak boyutu, `pbKeyBlob`.  
  
 `ppbPublicKeyBlob`  
 [out] Döndürülen ortak anahtarı BLOB. `ppbPublicKeyBlob` Parametresi ortak dil çalışma zamanı tarafından ayrılmış ve yapana. Kullanarak, çağıran belleği serbest gerekir [Iclrstrongname::strongnamefreebuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) yöntemi.  
  
 `pcbPublicKeyBlob`  
 [out] Döndürülen ortak anahtarı BLOB boyutu.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `S_OK`Yöntem başarıyla tamamlandı Aksi takdirde hata belirten bir HRESULT değeri (bkz [ortak HRESULT değerleri](http://go.microsoft.com/fwlink/?LinkId=213878) bir listesi için).  
  
## <a name="remarks"></a>Açıklamalar  
 Ortak anahtar içeren bir [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) yapısı.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MetaHost.h  
  
 **Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [StrongNameTokenFromPublicKey yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)  
 [PublicKeyBlob yapısı](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)  
 [Iclrstrongname arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
