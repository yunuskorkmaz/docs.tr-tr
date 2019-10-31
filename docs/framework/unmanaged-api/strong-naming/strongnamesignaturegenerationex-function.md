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
ms.openlocfilehash: e8f63a6379af8f2b7b88c511840622d49d65d587
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141579"
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
  
 `pbKeyBlob` null ise, `wszKeyContainer` şifreleme hizmeti sağlayıcısı 'nda (CSP) geçerli bir kapsayıcı belirtmesi gerekir. Bu durumda, kapsayıcıda depolanan anahtar çifti dosyayı imzalamak için kullanılır.  
  
 `pbKeyBlob` null değilse, anahtar çiftinin anahtar ikili büyük nesne (BLOB) içinde yer aldığı varsayılır.  
  
 `pbKeyBlob`  
 'ndaki Ortak/özel anahtar çifti işaretçisi. Bu çift, Win32 `CryptExportKey` işlevi tarafından oluşturulan biçimdedir. `pbKeyBlob` null ise, `wszKeyContainer` tarafından belirtilen anahtar kapsayıcısının anahtar çiftini içermesi varsayılır.  
  
 `cbKeyBlob`  
 'ndaki `pbKeyBlob`bayt cinsinden boyutu.  
  
 `ppbSignatureBlob`  
 dışı Ortak dil çalışma zamanının imzayı döndürdüğü konuma yönelik bir işaretçi. `ppbSignatureBlob` null ise, çalışma zamanı imzayı `wszFilePath`tarafından belirtilen dosyada depolar.  
  
 `ppbSignatureBlob` null değilse, ortak dil çalışma zamanı, imzanın döndürüleceği alanı ayırır. Çağıranın, [StrongNameFreeBuffer](strongnamefreebuffer-function.md) işlevini kullanarak bu alanı boşaltmalıdır.  
  
 `pcbSignatureBlob`  
 dışı Döndürülen imzanın bayt cinsinden boyutu.  
  
 `dwFlags`  
 'ndaki Aşağıdaki değerlerden biri veya daha fazlası:  
  
- `SN_SIGN_ALL_FILES` (0x00000001)-bağlı modüller için tüm karmaların yeniden hesaplanması.  
  
- `SN_TEST_SIGN` (0x00000002)-derlemeyi test-imzalayın.  
  
## <a name="return-value"></a>Dönüş Değeri  
 başarılı tamamlamada `true`; Aksi takdirde, `false`.  
  
## <a name="remarks"></a>Açıklamalar  
 İmza boyutunu imzayı oluşturmadan hesaplamak için `wszFilePath` null değerini belirtin.  
  
 İmza doğrudan dosyada depolanabilir veya çağırana geri döndürülebilir.  
  
 `SN_SIGN_ALL_FILES` belirtilirse, ancak ortak anahtar dahil edilmez (hem `pbKeyBlob` hem de `wszFilePath` null ise), bağlantılı modüllerin karmaları yeniden hesaplanır, ancak derleme yeniden imzalanmamıştır.  
  
 `SN_TEST_SIGN` belirtilirse, derlemenin tanımlayıcı bir adla imzalandığını göstermek için ortak dil çalışma zamanı üst bilgisi değiştirilmez.  
  
 `StrongNameSignatureGenerationEx` işlevi başarıyla tamamlanmazsa, en son oluşturulan hatayı almak için [StrongNameErrorInfo](strongnameerrorinfo-function.md) işlevini çağırın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** StrongName. h  
  
 **Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [StrongNameSignatureGenerationEx Yöntemi](../hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [StrongNameSignatureGeneration Yöntemi](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md)
- [ICLRStrongName Arabirimi](../hosting/iclrstrongname-interface.md)
