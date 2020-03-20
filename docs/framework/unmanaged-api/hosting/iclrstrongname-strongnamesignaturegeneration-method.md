---
title: ICLRStrongName::StrongNameSignatureGeneration Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureGeneration
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureGeneration
helpviewer_keywords:
- StrongNameSignatureGeneration method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameSignatureGeneration method [.NET Framework hosting]
ms.assetid: 4cdb1284-947a-4ed4-94c1-c5ff5cdfce56
topic_type:
- apiref
ms.openlocfilehash: e58ac181c4e472c469076b880ff71e0c6afa30fe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178047"
---
# <a name="iclrstrongnamestrongnamesignaturegeneration-method"></a>ICLRStrongName::StrongNameSignatureGeneration Yöntemi
Belirtilen derleme için güçlü bir ad imzası oluşturur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT StrongNameSignatureGeneration (
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
  
 Null `ppbSignatureBlob` değilse, ortak dil çalışma zamanı imzayı döndürmek için alan ayırır. Arayan ICLRStrongName kullanarak bu alanı boşaltmak [gerekir::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) yöntemi.  
  
 `pcbSignatureBlob`  
 [çıkış] Döndürülen imzanın baytlar halindeki boyutu.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `S_OK`yöntem başarıyla tamamlanırsa; aksi takdirde, başarısızlığı gösteren bir HRESULT değeri (liste için [Ortak HRESULT Değerleri'ne](/windows/win32/seccrypto/common-hresult-values) bakın).  
  
## <a name="remarks"></a>Açıklamalar  
 İmza oluşturmadan imzanın boyutunu hesaplamak için `wszFilePath` null belirtin.  
  
 İmza doğrudan dosyada depolanabilir veya arayana döndürülebilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** MetaHost.h  
  
 **Kütüphane:** MSCorEE.dll bir kaynak olarak dahil  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [StrongNameSignatureGenerationEx Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [ICLRStrongName Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
