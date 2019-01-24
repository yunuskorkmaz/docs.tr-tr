---
title: StrongNameSignatureGenerationEx İşlevi
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 60825cb82097e6ec9c202efebe04a50b0f5a3771
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54508628"
---
# <a name="strongnamesignaturegenerationex-function"></a>StrongNameSignatureGenerationEx İşlevi
Belirtilen bayraklar göre belirtilen derleme için tanımlayıcı ad imzası oluşturur.  
  
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
 [in] Tanımlayıcı ad imzası oluşturulacak derleme bildirimi içeren dosyanın yolu.  
  
 `wszKeyContainer`  
 [in] Ortak/özel anahtar çiftini içeren anahtar kapsayıcısının adı.  
  
 Varsa `pbKeyBlob` boş `wszKeyContainer` şifreleme hizmeti sağlayıcısı (CSP) geçerli bir kapsayıcıda belirtmeniz gerekir. Bu durumda, bir kapsayıcıda depolanan bir anahtar çifti dosyasını imzalamak için kullanılır.  
  
 Varsa `pbKeyBlob` anahtar çiftini varsayılır anahtar ikili büyük nesne içinde (BLOB) dahil edilmek üzere null değil.  
  
 `pbKeyBlob`  
 [in] Ortak/özel anahtar çifti için bir işaretçi. Win32 oluşturulan biçimde bu çiftidir `CryptExportKey` işlevi. Varsa `pbKeyBlob` null, belirtilen anahtar kapsayıcısı olan `wszKeyContainer` anahtar çiftini içerdiği varsayılır.  
  
 `cbKeyBlob`  
 [in] Bayt cinsinden boyutu, `pbKeyBlob`.  
  
 `ppbSignatureBlob`  
 [out] Ortak dil çalışma zamanı imza döndüren konumu için bir işaretçi. Varsa `ppbSignatureBlob` olduğundan çalışma zamanı tarafından belirtilen dosyada imza null depolar `wszFilePath`.  
  
 Varsa `ppbSignatureBlob` olan null, ortak dil çalışma zamanı imza döndürmek alan ayırır. Çağıranın kullanarak bu alan boşaltmanız gerekir [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) işlevi.  
  
 `pcbSignatureBlob`  
 [out] Baytlarında döndürülen imza boyutu.  
  
 `dwFlags`  
 [in] Bir veya daha fazla aşağıdaki değerlerden biri:  
  
-   `SN_SIGN_ALL_FILES` (0x00000001) - bağlı olan modüller için tüm karmaları yeniden oynatmanız.  
  
-   `SN_TEST_SIGN` (0x00000002) - derlemeyi test imzalayın.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `true` başarıyla tamamlandığında; Aksi takdirde, `false`.  
  
## <a name="remarks"></a>Açıklamalar  
 İçin null belirtin `wszFilePath` imza oluşturmadan imza boyutunu hesaplamak için.  
  
 İmza ya da doğrudan dosyasında depolanan veya arayana döndürülür.  
  
 Varsa `SN_SIGN_ALL_FILES` belirtildi ancak ortak anahtar dahil değildir (her ikisi de `pbKeyBlob` ve `wszFilePath` null) karmalar bağlı modüller için ancak derleme yeniden imzalı değil.  
  
 Varsa `SN_TEST_SIGN` belirtilirse, derlemenin tanımlayıcı ad ile imzalı olduğunu belirtmek için ortak dil çalışma zamanı üst değiştirilmez.  
  
 Varsa `StrongNameSignatureGenerationEx` işlevi değil başarıyla tamamlanması, çağrı [Strongnameerrorınfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) oluşturulan son hatayı alması için işlevi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** StrongName.h  
  
 **Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [StrongNameSignatureGenerationEx Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [StrongNameSignatureGeneration Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md)
- [ICLRStrongName Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
