---
title: LoadTypeLibWithResolver İşlevi
ms.date: 03/30/2017
api_name:
- LoadTypeLibWithResolver
api_location:
- TlbRef.dll
api_type:
- DLLExport
f1_keywords:
- LoadTypeLibWithResolver
helpviewer_keywords:
- LoadTypeLibWithResolver function [.NET Framework]
ms.assetid: 7123a89b-eb9b-463a-a552-a081e33b0a3a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5d2f5ad2afb2e73acead82369782f142aa10aac3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782706"
---
# <a name="loadtypelibwithresolver-function"></a>LoadTypeLibWithResolver İşlevi
Bir tür kitaplığı yükler ve sağlanan kullanan [Itypelibresolver arabirimi](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) tüm dahili olarak başvurulan tür kitaplıkları çözümlenecek.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT LoadTypeLibWithResolver(  
    [in]  LPCOLESTR           szFile,  
    [in]  REGKIND             regkind,  
    [in]  ITypeLibResolver   *pTlbResolver,  
    [out] ITypeLib          **pptlib);  
```  
  
## <a name="parameters"></a>Parametreler  
 `szFile`  
 [in] Tür kitaplığı dosyasının yolu.  
  
 `regkind`  
 [in] A [REGKIND numaralandırma](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/ne-oleauto-tagregkind) nasıl bir tür kitaplığı kaydedilmemiş denetleyen bayrak. Olası değerleri şunlardır:  
  
- `REGKIND_DEFAULT`: Varsayılan kayıt davranışı kullanın.  
  
- `REGKIND_REGISTER`: Bu tür kitaplığına kaydedin.  
  
- `REGKIND_NONE`: Bu tür kitaplığı kaydetmeyin.  
  
 `pTlbResolver`  
 [in] Uygulanmasına yönelik bir işaretçi [Itypelibresolver arabirimi](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md).  
  
 `pptlib`  
 [out] Yüklenmekte tür kitaplığına bir başvuru.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Aşağıdaki tabloda listelenen HRESULT değerlerinden biri.  
  
|Dönüş değeri|Açıklama|  
|------------------|-------------|  
|`S_OK`|Başarılı.|  
|`E_OUTOFMEMORY`|Bellek yetersiz.|  
|`E_POINTER`|Bir veya daha fazla işaretçileri geçersizdir.|  
|`E_INVALIDARG`|Bir veya daha fazla bağımsız değişken geçersiz.|  
|`TYPE_E_IOERROR`|İşlevi, dosyaya yazılamadı.|  
|`TYPE_E_REGISTRYACCESS`|Sistem kayıt veritabanı açılamadı.|  
|`TYPE_E_INVALIDSTATE`|Tür kitaplığı dosyası açılamadı.|  
|`TYPE_E_CANTLOADLIBRARY`|Tür kitaplığı veya DLL yüklenemedi.|  
  
## <a name="remarks"></a>Açıklamalar  
 [Tlbexp.exe (tür kitaplığı dışarı Aktarıcı)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) çağrıları `LoadTypeLibWithResolver` derleme için tür kitaplığını dönüştürme işlemi sırasında işlevi.  
  
 Bu işlev, belirtilen tür kitaplığı ile en az düzeyde erişim kayıt defterine yükler. İşlev, her biri gerekir yüklenebilir ve üst tür kitaplığına eklenen dahili olarak başvurulan tür kitaplıkları için tür kitaplığı ardından inceler.  
  
 Başvurulan tür kitaplığının yüklenmeden önce bir tam dosya yolu başvurusu dosya yoluna çözümlenmelidir. Bu aracılığıyla gerçekleştirilir [ResolveTypeLib yöntemi](../../../../docs/framework/unmanaged-api/tlbexp/resolvetypelib-method.md) tarafından sağlanan [Itypelibresolver arabirimi](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md), içinde geçirilen `pTlbResolver` parametresi.  
  
 Başvurulan tür kitaplığının tam dosya yolunu bilindiğinde `LoadTypeLibWithResolver` işlevi yükler ve başvurulan tür kitaplığının bir birleşik asıl tür kütüphanesi oluşturuluyor üst türü, ekler.  
  
 İşlevi, çözümler ve tüm dahili olarak başvurulan tür kitaplıklarını yükler sonra ana çözümlenen tür kitaplığına bir başvuru döndürür. `pptlib` parametresi.  
  
 `LoadTypeLibWithResolver` İşlev çağrılan genellikle [Tlbexp.exe (tür kitaplığı dışarı Aktarıcı)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md), kendi iç sağladığı [Itypelibresolver arabirimi](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) uygulamasında `pTlbResolver` parametre.  
  
 Eğer `LoadTypeLibWithResolver` doğrudan, kendi sağlamalısınız [Itypelibresolver arabirimi](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) uygulaması.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** TlbRef.h  
  
 **Kitaplığı:** TlbRef.lib  
  
 **.NET framework sürümü:** 3.5, 3.0, 2.0  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tlbexp Yardımcı İşlevleri](../../../../docs/framework/unmanaged-api/tlbexp/index.md)
- [LoadTypeLibEx işlevi](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
