---
title: StrongNameSignatureGeneration İşlevi
ms.date: 03/30/2017
api_name:
- StrongNameSignatureGeneration
api_location:
- mscoree.dll
- mscorsn.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureGeneration
helpviewer_keywords:
- StrongNameSignatureGeneration function [.NET Framework strong naming]
ms.assetid: 839b765c-3e41-44ce-bf1b-dc10453db18e
ms.openlocfilehash: 9ab6fcb64e4654302e411d4dcc587df2e0bf1dc1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125186"
---
# <a name="strongnamesignaturegeneration-function"></a>StrongNameSignatureGeneration İşlevi
Belirtilen derleme için bir tanımlayıcı ad imzası oluşturur.  
  
 Bu işlev kullanım dışı bırakıldı. Bunun yerine [ICLRStrongName:: StrongNameSignatureGeneration](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md) metodunu kullanın.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
BOOLEAN StrongNameSignatureGeneration (   
    [in]  LPCWSTR   wszFilePath,  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbSignatureBlob,  
    [out] ULONG     *pcbSignatureBlob  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `wszFilePath`  
 'ndaki Tanımlayıcı ad imzasının üretilecektir derlemenin bildirimini içeren dosyanın yolu.  
  
 `wszKeyContainer`  
 'ndaki Ortak/özel anahtar çiftini içeren anahtar kapsayıcısının adı.  
  
 `pbKeyBlob` null ise, `wszKeyContainer` şifreleme hizmeti sağlayıcısı 'nda (CSP) geçerli bir kapsayıcı belirtmesi gerekir. Bu durumda, kapsayıcıda depolanan anahtar çifti dosyayı imzalamak için kullanılır.  
  
 `pbKeyBlob` null değilse, anahtar çiftinin anahtar ikili büyük nesne (BLOB) içinde yer aldığı varsayılır.  
  
 Anahtarlar 1024-bit Rivest-Shamir-Adtaman (RSA) imzalama anahtarları olmalıdır. Şu anda başka türde anahtarlar desteklenmiyor.  
  
 `pbKeyBlob`  
 'ndaki Ortak/özel anahtar çifti işaretçisi. Bu çift, Win32 `CryptExportKey` işlevi tarafından oluşturulan biçimdedir. `pbKeyBlob` null ise, `wszKeyContainer` tarafından belirtilen anahtar kapsayıcısının anahtar çiftini içermesi varsayılır.  
  
 `cbKeyBlob`  
 'ndaki `pbKeyBlob`bayt cinsinden boyutu.  
  
 `ppbSignatureBlob`  
 dışı Ortak dil çalışma zamanının imzayı döndürdüğü konuma yönelik bir işaretçi. `ppbSignatureBlob` null ise, çalışma zamanı imzayı `wszFilePath`tarafından belirtilen dosyada depolar.  
  
 `ppbSignatureBlob` null değilse, ortak dil çalışma zamanı, imzanın döndürüleceği alanı ayırır. Çağıranın, [StrongNameFreeBuffer](strongnamefreebuffer-function.md) işlevini kullanarak bu alanı boşaltmalıdır.  
  
 `pcbSignatureBlob`  
 dışı Döndürülen imzanın bayt cinsinden boyutu.  
  
## <a name="return-value"></a>Dönüş Değeri  
 başarılı tamamlamada `true`; Aksi takdirde, `false`.  
  
## <a name="remarks"></a>Açıklamalar  
 İmza boyutunu imzayı oluşturmadan hesaplamak için `wszFilePath` null değerini belirtin.  
  
 İmza, doğrudan dosyada depolanabilir veya çağırana döndürülür.  
  
 `StrongNameSignatureGeneration` işlevi başarıyla tamamlanmazsa, en son oluşturulan hatayı almak için [StrongNameErrorInfo](strongnameerrorinfo-function.md) işlevini çağırın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** StrongName. h  
  
 **Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [StrongNameSignatureGeneration Yöntemi](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md)
- [StrongNameSignatureGenerationEx Yöntemi](../hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [ICLRStrongName Arabirimi](../hosting/iclrstrongname-interface.md)
