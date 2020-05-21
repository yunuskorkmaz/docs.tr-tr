---
title: ICLRStrongName::StrongNameSignatureGenerationEx Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureGenerationEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureGenerationEx
helpviewer_keywords:
- ICLRStrongName::StrongNameSignatureGenerationEx method [.NET Framework hosting]
- StrongNameSignatureGenerationEx method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: c3f34584-c6e2-41fd-bb44-e44da8546309
topic_type:
- apiref
ms.openlocfilehash: 3529eceb179cc4b08d39f83d97d001a16e716918
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83763065"
---
# <a name="iclrstrongnamestrongnamesignaturegenerationex-method"></a>ICLRStrongName::StrongNameSignatureGenerationEx Yöntemi
Belirtilen bayrağa göre belirtilen derleme için bir tanımlayıcı ad imzası üretir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp
HRESULT StrongNameSignatureGenerationEx (  
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
  
 `ppbSignatureBlob`Null değilse, ortak dil çalışma zamanı, imzanın geri döndürüleceği alanı ayırır. Çağıranın [ICLRStrongName:: StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) metodunu kullanarak bu alanı boşaltmalıdır.  
  
 `pcbSignatureBlob`  
 dışı Döndürülen imzanın bayt cinsinden boyutu.  
  
 `dwFlags`  
 'ndaki Aşağıdaki değerlerden biri veya daha fazlası:  
  
- `SN_SIGN_ALL_FILES`(0x00000001)-bağlantılı modüller için tüm karmaların yeniden hesaplanması.  
  
- `SN_TEST_SIGN`(0x00000002)-derlemeyi test-imzala.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `S_OK`Yöntem başarıyla tamamlanırsa; Aksi takdirde, hata belirten bir HRESULT değeri (bkz. bir liste için [genel HRESULT değerleri](/windows/win32/seccrypto/common-hresult-values) ).  
  
## <a name="remarks"></a>Açıklamalar  
 İmza `wszFilePath` boyutunu imzayı oluşturmadan hesaplamak için null değerini belirtin.  
  
 İmza doğrudan dosyada depolanabilir veya çağırana geri döndürülebilir.  
  
 `SN_SIGN_ALL_FILES`Belirtilirse, ancak bir ortak anahtar dahil edilmez (hem hem de `pbKeyBlob` null ise `wszFilePath` ), bağlantılı modüllerin karmaları yeniden hesaplanır, ancak derleme yeniden imzalanmamıştır.  
  
 `SN_TEST_SIGN`Belirtilmişse, derlemenin tanımlayıcı bir adla imzalandığını göstermek için ortak dil çalışma zamanı üst bilgisi değiştirilmez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MetaHost. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [StrongNameSignatureGeneration Yöntemi](iclrstrongname-strongnamesignaturegeneration-method.md)
- [ICLRStrongName Arabirimi](iclrstrongname-interface.md)
