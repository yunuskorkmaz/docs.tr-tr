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
ms.openlocfilehash: 89398c221dcf9d6f89027f15da4062bc7ed67e3f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798989"
---
# <a name="strongnamesignaturegenerationex-function"></a>StrongNameSignatureGenerationEx İşlevi
Belirtilen bayrağa göre belirtilen derleme için bir tanımlayıcı ad imzası üretir.  
  
 Bu işlev kullanım dışı bırakıldı. Bunun yerine [ICLRStrongName:: StrongNameSignatureGenerationEx](../hosting/iclrstrongname-strongnamesignaturegenerationex-method.md) metodunu kullanın.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
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
  
## <a name="parameters"></a>Parametreler  
 `wszFilePath`  
 'ndaki Tanımlayıcı ad imzasının üretilecektir derlemenin bildirimini içeren dosyanın yolu.  
  
 `wszKeyContainer`  
 'ndaki Ortak/özel anahtar çiftini içeren anahtar kapsayıcısının adı.  
  
 Null ise, `wszKeyContainer` şifreleme hizmet sağlayıcısı (CSP) içinde geçerli bir kapsayıcı belirtmeniz gerekir. `pbKeyBlob` Bu durumda, kapsayıcıda depolanan anahtar çifti dosyayı imzalamak için kullanılır.  
  
 `pbKeyBlob` Null değilse, anahtar çiftinin anahtar ikili büyük nesne (blob) içinde yer aldığı varsayılır.  
  
 `pbKeyBlob`  
 'ndaki Ortak/özel anahtar çifti işaretçisi. Bu çift Win32 `CryptExportKey` işlevi tarafından oluşturulan biçimdedir. Null ise, tarafından `wszKeyContainer` belirtilen anahtar kapsayıcının anahtar çiftini içermesi varsayılır. `pbKeyBlob`  
  
 `cbKeyBlob`  
 'ndaki Bayt cinsinden boyutu `pbKeyBlob`.  
  
 `ppbSignatureBlob`  
 dışı Ortak dil çalışma zamanının imzayı döndürdüğü konuma yönelik bir işaretçi. Null ise, çalışma zamanı imzayı tarafından `wszFilePath`belirtilen dosyada depolar. `ppbSignatureBlob`  
  
 `ppbSignatureBlob` Null değilse, ortak dil çalışma zamanı, imzanın geri döndürüleceği alanı ayırır. Çağıranın, [StrongNameFreeBuffer](strongnamefreebuffer-function.md) işlevini kullanarak bu alanı boşaltmalıdır.  
  
 `pcbSignatureBlob`  
 dışı Döndürülen imzanın bayt cinsinden boyutu.  
  
 `dwFlags`  
 'ndaki Aşağıdaki değerlerden biri veya daha fazlası:  
  
- `SN_SIGN_ALL_FILES`(0x00000001)-bağlantılı modüller için tüm karmaların yeniden hesaplanması.  
  
- `SN_TEST_SIGN`(0x00000002)-derlemeyi test-imzala.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `true`başarıyla tamamlandığında; Aksi takdirde `false`,.  
  
## <a name="remarks"></a>Açıklamalar  
 İmza boyutunu imzayı `wszFilePath` oluşturmadan hesaplamak için null değerini belirtin.  
  
 İmza doğrudan dosyada depolanabilir veya çağırana geri döndürülebilir.  
  
 Belirtilirse, ancak bir ortak anahtar dahil edilmez ( `wszFilePath` hem hem de `pbKeyBlob` null ise), bağlantılı modüllerin karmaları yeniden hesaplanır, ancak derleme yeniden imzalanmamıştır. `SN_SIGN_ALL_FILES`  
  
 `SN_TEST_SIGN` Belirtilmişse, derlemenin tanımlayıcı bir adla imzalandığını göstermek için ortak dil çalışma zamanı üst bilgisi değiştirilmez.  
  
 İşlev başarıyla tamamlanmazsa, en son oluşturulan hatayı almak için [StrongNameErrorInfo işlevini çağırın.](strongnameerrorinfo-function.md) `StrongNameSignatureGenerationEx`  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi** StrongName. h  
  
 **Kitaplığı** MsCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [StrongNameSignatureGenerationEx Yöntemi](../hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [StrongNameSignatureGeneration Yöntemi](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md)
- [ICLRStrongName Arabirimi](../hosting/iclrstrongname-interface.md)
