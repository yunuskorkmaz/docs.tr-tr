---
title: "StrongNameSignatureGenerationEx İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- StrongNameSignatureGenerationEx
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureGenerationEx
helpviewer_keywords:
- StrongNameSignatureGenerationEx function [.NET Framework strong naming]
ms.assetid: 9a75469e-aa49-4e32-ad48-3bafd5202f09
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4f68befd145649e6d8921e160d302cdb81000a9a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="strongnamesignaturegenerationex-function"></a>StrongNameSignatureGenerationEx İşlevi
Belirtilen bayrakları göre belirtilen derleme için bir tanımlayıcı ad imzası oluşturur.  
  
 Bu işlev kullanım dışı bırakıldı. Kullanım [Iclrstrongname::strongnamesignaturegenerationex](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md) yöntemi yerine.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
BOOLEAN StrongNameSignatureGenerationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbSignatureBlob,  
    [out] ULONG     *pcbSignatureBlob,  
    [in]  DWORD     dwFlags  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `wszFilePath`  
 [in] Tanımlayıcı ad imzası oluşturulmayacak derleme bildirimi içeren dosyanın yolu.  
  
 `wszKeyContainer`  
 [in] Ortak/özel anahtar çiftini içeren anahtar kapsayıcı adı.  
  
 Varsa `pbKeyBlob` null, `wszKeyContainer` şifreleme hizmeti sağlayıcısı (CSP) geçerli bir kapsayıcıda belirtmeniz gerekir. Bu durumda, kapsayıcısında depolanan anahtar çifti dosyasını imzalamak için kullanılır.  
  
 Varsa `pbKeyBlob` anahtar çifti varsayılır anahtar ikili büyük nesne (BLOB) dahil edilmek üzere null değil.  
  
 `pbKeyBlob`  
 [in] Ortak/özel anahtar çifti için bir işaretçi. Bu çiftidir Win32 tarafından oluşturulan biçiminde `CryptExportKey` işlevi. Varsa `pbKeyBlob` null, belirtilen anahtar kapsayıcısı olan `wszKeyContainer` anahtar çiftini içeren varsayılır.  
  
 `cbKeyBlob`  
 [in] Bayt olarak boyutu, `pbKeyBlob`.  
  
 `ppbSignatureBlob`  
 [out] Ortak dil çalışma zamanı imza döndüğü konuma bir işaretçi. Varsa `ppbSignatureBlob` olduğu çalışma zamanı tarafından belirtilen dosyada imza null depolar `wszFilePath`.  
  
 Varsa `ppbSignatureBlob` olan null, ortak dil çalışma zamanı imza döndürmek üzere alan ayırır. Arayan kullanarak bu alanı boş gerekir [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) işlevi.  
  
 `pcbSignatureBlob`  
 [out] Döndürülen imza bayt cinsinden boyutu.  
  
 `dwFlags`  
 [in] Bir veya daha fazla aşağıdaki değerlerden biri:  
  
-   `SN_SIGN_ALL_FILES`(0x00000001) - bağlantılı modülleri için tüm karmaları yeniden hesaplamak.  
  
-   `SN_TEST_SIGN`(0x00000002) - test-oturum derleme.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `true`başarılı tamamlanma; Aksi takdirde `false`.  
  
## <a name="remarks"></a>Açıklamalar  
 İçin null belirtin `wszFilePath` imza oluşturmadan imza boyutu hesaplanamadı.  
  
 İmza ya da doğrudan dosyasında depolanan veya yapana.  
  
 Varsa `SN_SIGN_ALL_FILES` belirtildi ancak bir ortak anahtar dahil değildir (her ikisi de `pbKeyBlob` ve `wszFilePath` null) bağlantılı modülleri için karmaları yeniden ancak derleme yeniden imzalı değil.  
  
 Varsa `SN_TEST_SIGN` belirtilirse, ortak dil çalışma zamanı üstbilgisi derleme tanımlayıcı bir ad ile imzalı olduğunu belirtmek için değişiklik yok.  
  
 Varsa `StrongNameSignatureGenerationEx` işlevi yok başarıyla tamamlanması, çağrı [Strongnameerrorınfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) son oluşturulan hata alınacak işlev.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** StrongName.h  
  
 **Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [StrongNameSignatureGenerationEx Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)  
 [StrongNameSignatureGeneration Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md)  
 [ICLRStrongName Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
