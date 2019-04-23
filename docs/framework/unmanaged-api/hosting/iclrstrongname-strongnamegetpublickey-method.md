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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2acade14f9d30ca7bf0d098d6f58c80a367f621c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59213019"
---
# <a name="iclrstrongnamestrongnamegetpublickey-method"></a>ICLRStrongName::StrongNameGetPublicKey Yöntemi
Bir ortak/özel anahtar çiftinden ortak anahtarı alır. Bir anahtar çifti, şifreleme hizmeti sağlayıcısı (CSP) içinde bir anahtar kapsayıcısı adını veya ham bayt koleksiyonu olarak sağlanabilir.  
  
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
  
## <a name="parameters"></a>Parametreler  
 `szKeyContainer`  
 [in] Ortak/özel anahtar çiftini içeren anahtar kapsayıcısının adı. Varsa `pbKeyBlob` boş `szKeyContainer` CSP Geçerli kapsayıcıda belirtmeniz gerekir. Bu durumda, [Iclrstrongname::strongnamegetpublickey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md) yöntemi, bir kapsayıcıda depolanan bir anahtar çifti öğesinden ortak anahtarı ayıklar.  
  
 Varsa `pbKeyBlob` anahtar çiftini varsayılır anahtar ikili büyük nesne içinde (BLOB) dahil edilmek üzere null değil.  
  
 Anahtarları 1024 bit Rivest-Shamir-Adleman (RSA) imzalama anahtarı olması gerekir. Anahtarlar başka tür bu zaman desteklenir.  
  
 `pbKeyBlob`  
 [in] Ortak/özel anahtar çifti için bir işaretçi. Win32 oluşturulan biçimde bu çiftidir `CryptExportKey` işlevi. Varsa `pbKeyBlob` null, belirtilen anahtar kapsayıcısı olan `szKeyContainer` anahtar çiftini içerdiği varsayılır.  
  
 `cbKeyBlob`  
 [in] Bayt cinsinden boyutu, `pbKeyBlob`.  
  
 `ppbPublicKeyBlob`  
 [out] Döndürülen ortak anahtarı BLOB. `ppbPublicKeyBlob` Parametre ortak dil çalışma zamanı tarafından ayrılmış ve arayana döndürülür. Arayanın bellek kullanarak ücretsiz gerekir [Iclrstrongname::strongnamefreebuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) yöntemi.  
  
 `pcbPublicKeyBlob`  
 [out] Döndürülen ortak anahtarı BLOB boyutu.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `S_OK` yöntemi başarıyla tamamlandı Aksi takdirde hata olduğunu gösteren HRESULT değerini (bkz [ortak HRESULT değerlerini](https://go.microsoft.com/fwlink/?LinkId=213878) bir listesi için).  
  
## <a name="remarks"></a>Açıklamalar  
 Ortak anahtarı içeren bir [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) yapısı.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MetaHost.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [StrongNameTokenFromPublicKey Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [PublicKeyBlob Yapısı](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
- [ICLRStrongName Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
