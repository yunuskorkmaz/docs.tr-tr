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
ms.openlocfilehash: 96dae519d73505a30c8593e9883da7338525ea2c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708529"
---
# <a name="strongnamesignaturegenerationex-function"></a>StrongNameSignatureGenerationEx İşlevi

Belirtilen bayrağa göre belirtilen derleme için bir tanımlayıcı ad imzası üretir.  
  
 Bu işlev kullanım dışı bırakıldı. Bunun yerine [ICLRStrongName:: StrongNameSignatureGenerationEx](../hosting/iclrstrongname-strongnamesignaturegenerationex-method.md) metodunu kullanın.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
  
 `pbKeyBlob`Null ise, `wszKeyContainer` şifreleme hizmet sağlayıcısı (CSP) içinde geçerli bir kapsayıcı belirtmeniz gerekir. Bu durumda, kapsayıcıda depolanan anahtar çifti dosyayı imzalamak için kullanılır.  
  
 `pbKeyBlob`Null değilse, anahtar çiftinin anahtar ikili büyük nesne (blob) içinde yer aldığı varsayılır.  
  
 `pbKeyBlob`  
 'ndaki Ortak/özel anahtar çifti işaretçisi. Bu çift Win32 işlevi tarafından oluşturulan biçimdedir `CryptExportKey` . `pbKeyBlob`Null ise, tarafından belirtilen anahtar kapsayıcının `wszKeyContainer` anahtar çiftini içermesi varsayılır.  
  
 `cbKeyBlob`  
 'ndaki Bayt cinsinden boyutu `pbKeyBlob` .  
  
 `ppbSignatureBlob`  
 dışı Ortak dil çalışma zamanının imzayı döndürdüğü konuma yönelik bir işaretçi. `ppbSignatureBlob`Null ise, çalışma zamanı imzayı tarafından belirtilen dosyada depolar `wszFilePath` .  
  
 `ppbSignatureBlob`Null değilse, ortak dil çalışma zamanı, imzanın geri döndürüleceği alanı ayırır. Çağıranın, [StrongNameFreeBuffer](strongnamefreebuffer-function.md) işlevini kullanarak bu alanı boşaltmalıdır.  
  
 `pcbSignatureBlob`  
 dışı Döndürülen imzanın bayt cinsinden boyutu.  
  
 `dwFlags`  
 'ndaki Aşağıdaki değerlerden biri veya daha fazlası:  
  
- `SN_SIGN_ALL_FILES` (0x00000001)-bağlantılı modüller için tüm karmaların yeniden hesaplanması.  
  
- `SN_TEST_SIGN` (0x00000002)-derlemeyi test-imzala.  
  
## <a name="return-value"></a>Dönüş Değeri  

 `true` başarıyla tamamlandığında; Aksi takdirde, `false` .  
  
## <a name="remarks"></a>Açıklamalar  

 İmza `wszFilePath` boyutunu imzayı oluşturmadan hesaplamak için null değerini belirtin.  
  
 İmza doğrudan dosyada depolanabilir veya çağırana geri döndürülebilir.  
  
 `SN_SIGN_ALL_FILES`Belirtilirse, ancak bir ortak anahtar dahil edilmez (hem hem de `pbKeyBlob` null ise `wszFilePath` ), bağlantılı modüllerin karmaları yeniden hesaplanır, ancak derleme yeniden imzalanmamıştır.  
  
 `SN_TEST_SIGN`Belirtilmişse, derlemenin tanımlayıcı bir adla imzalandığını göstermek için ortak dil çalışma zamanı üst bilgisi değiştirilmez.  
  
 `StrongNameSignatureGenerationEx`İşlev başarıyla tamamlanmazsa, en son oluşturulan hatayı almak Için [StrongNameErrorInfo](strongnameerrorinfo-function.md) işlevini çağırın.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** StrongName. h  
  
 **Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [StrongNameSignatureGenerationEx Yöntemi](../hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [StrongNameSignatureGeneration Yöntemi](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md)
- [ICLRStrongName Arabirimi](../hosting/iclrstrongname-interface.md)
