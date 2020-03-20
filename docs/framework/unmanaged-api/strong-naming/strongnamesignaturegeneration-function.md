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
ms.openlocfilehash: d7f481e5c61ec65d2e7414bd47227866f3435028
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176909"
---
# <a name="strongnamesignaturegeneration-function"></a>StrongNameSignatureGeneration İşlevi
Belirtilen derleme için güçlü bir ad imzası oluşturur.  
  
 Bu işlev amortismana kaldırıldı. Bunun yerine [ICLRStrongName::StrongNameSignatureGeneration](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md) yöntemini kullanın.  
  
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
 [içinde] Güçlü ad imzasının oluşturulacağı derlemenin bildirimini içeren dosyaya giden yol.  
  
 `wszKeyContainer`  
 [içinde] Ortak/özel anahtar çiftini içeren anahtar kapsayıcısının adı.  
  
 Null `pbKeyBlob` ise, `wszKeyContainer` şifreleme hizmet sağlayıcısı (CSP) içinde geçerli bir kapsayıcı belirtilmelidir. Bu durumda, dosyayı imzalamak için kapsayıcıda depolanan anahtar çifti kullanılır.  
  
 Null `pbKeyBlob` değilse, anahtar çiftinin anahtar ikili büyük nesnesinde (BLOB) bulunduğu varsayılır.  
  
 Anahtarlar 1024 bit Rivest-Shamir-Adleman (RSA) imzalama anahtarları olmalıdır. Şu anda başka anahtar türü desteklenmez.  
  
 `pbKeyBlob`  
 [içinde] Ortak/özel anahtar çiftine işaretçi. Bu çift Win32 `CryptExportKey` işlevi tarafından oluşturulan biçimdedir. Null `pbKeyBlob` ise, tarafından `wszKeyContainer` belirtilen anahtar kapsayıcı anahtar çiftini içerdiği varsayılır.  
  
 `cbKeyBlob`  
 [içinde] Boyutu, bayt, ve. `pbKeyBlob`  
  
 `ppbSignatureBlob`  
 [çıkış] Ortak dil çalışma zamanının imzayı döndürdettiği konuma işaretçi. Null `ppbSignatureBlob` ise, çalışma zamanı tarafından belirtilen dosyada `wszFilePath`imzayı depolar.  
  
 Null `ppbSignatureBlob` değilse, ortak dil çalışma zamanı imzayı döndürmek için alan ayırır. Arayan, [StrongNameFreeBuffer](strongnamefreebuffer-function.md) işlevini kullanarak bu alanı boşaltmalıdır.  
  
 `pcbSignatureBlob`  
 [çıkış] Döndürülen imzanın baytlar halindeki boyutu.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `true`başarılı bir şekilde tamamlandığında; aksi `false`takdirde, .  
  
## <a name="remarks"></a>Açıklamalar  
 İmza oluşturmadan imzanın boyutunu hesaplamak için `wszFilePath` null belirtin.  
  
 İmza doğrudan dosyada depolanabilir veya arayana döndürülebilir.  
  
 `StrongNameSignatureGeneration` İşlev başarıyla tamamlanmamışsa, oluşturulan son hatayı almak için [StrongNameErrorInfo](strongnameerrorinfo-function.md) işlevini arayın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üstbilgi:** StrongName.h  
  
 **Kütüphane:** MsCorEE.dll bir kaynak olarak dahil  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [StrongNameSignatureGeneration Yöntemi](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md)
- [StrongNameSignatureGenerationEx Yöntemi](../hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [ICLRStrongName Arabirimi](../hosting/iclrstrongname-interface.md)
