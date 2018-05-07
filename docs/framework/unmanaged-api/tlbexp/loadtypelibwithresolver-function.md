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
ms.openlocfilehash: 751794746e26bd8f0ec2cd6db2f62876e78674e5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="loadtypelibwithresolver-function"></a>LoadTypeLibWithResolver İşlevi
Tür kitaplığını yükler ve sağlanan kullanır [Itypelibresolver arabirimi](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) herhangi dahili olarak başvurulan tür kitaplıklarının çözümlemek için.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT LoadTypeLibWithResolver(  
    [in]  LPCOLESTR           szFile,  
    [in]  REGKIND             regkind,  
    [in]  ITypeLibResolver   *pTlbResolver,  
    [out] ITypeLib          **pptlib);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `szFile`  
 [in] Tür kitaplığı dosya yolu.  
  
 `regkind`  
 [in] A [REGKIND numaralandırma](https://msdn.microsoft.com/library/windows/desktop/ms221159.aspx) tür kitaplığının nasıl kayıtlı denetimleri bayrağı. Olası değerler şunlardır:  
  
-   `REGKIND_DEFAULT`: Varsayılan kayıt davranışı kullanın.  
  
-   `REGKIND_REGISTER`: Bu tür kitaplığının kaydı.  
  
-   `REGKIND_NONE`: Bu tür kitaplığı kaydı.  
  
 `pTlbResolver`  
 [in] Uygulaması için bir işaretçi [Itypelibresolver arabirimi](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md).  
  
 `pptlib`  
 [out] Yüklenmekte türü kitaplığına bir başvuru.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Aşağıdaki tabloda listelenen HRESULT değerlerinden biri.  
  
|Dönüş değeri|Açıklama|  
|------------------|-------------|  
|`S_OK`|Başarılı.|  
|`E_OUTOFMEMORY`|Bellek yetersiz.|  
|`E_POINTER`|Bir veya daha fazla işaretçileri geçersizdir.|  
|`E_INVALIDARG`|Bir veya daha fazla bağımsız değişken geçersiz.|  
|`TYPE_E_IOERROR`|İşlev dosyasına yazılamadı.|  
|`TYPE_E_REGISTRYACCESS`|Sistem kayıt veritabanı açılamadı.|  
|`TYPE_E_INVALIDSTATE`|Tür kitaplığı açılamadı.|  
|`TYPE_E_CANTLOADLIBRARY`|Tür kitaplığı veya DLL yüklenemedi.|  
  
## <a name="remarks"></a>Açıklamalar  
 [Tlbexp.exe (tür kitaplığı dışarı Aktarıcı)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) çağrıları `LoadTypeLibWithResolver` derleme için tür kitaplığı dönüştürme işlemi sırasında işlevi.  
  
 Bu işlev kayıt defterine en az düzeyde erişim ile belirtilen tür kitaplığı yükler. İşlev sonra her biri gerekir yüklenmesi ve üst tür kitaplığı'na eklenen dahili olarak başvurulan tür kitaplıkları için tür kitaplığı inceler.  
  
 Başvurulan tür kitaplığını yüklenmeden önce başvuru dosya yoluna bir tam dosya yolunu çözümlenmelidir. Bu aracılığıyla gerçekleştirilir [ResolveTypeLib yöntemi](../../../../docs/framework/unmanaged-api/tlbexp/resolvetypelib-method.md) tarafından sağlanan [Itypelibresolver arabirimi](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md), içinde geçirilen `pTlbResolver` parametresi.  
  
 Başvurulan tür kitaplığı tam dosya yolunu bilindiğinde `LoadTypeLibWithResolver` işlevi yükler ve başvurulan tür kitaplığı birleşik ana tür kitaplığı oluşturma üst tür kitaplığına ekler.  
  
 İşlev çözümler ve tüm dahili olarak başvurulan tür kitaplıklarını yükler sonra ana çözümlenmiş Tür Kitaplığı'nda bir başvuru döndürür `pptlib` parametresi.  
  
 `LoadTypeLibWithResolver` İşlev çağrılan genellikle [Tlbexp.exe (tür kitaplığı dışarı Aktarıcı)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md), kendi iç sağladığı [Itypelibresolver arabirimi](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) uygulamasında `pTlbResolver` parametre.  
  
 Çağırırsanız `LoadTypeLibWithResolver` doğrudan kendi sağlamanız gerekir [Itypelibresolver arabirimi](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) uygulaması.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** TlbRef.h  
  
 **Kitaplığı:** TlbRef.lib  
  
 **.NET framework sürümü:** 3.5, 3.0, 2.0  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Tlbexp Yardımcı İşlevleri](../../../../docs/framework/unmanaged-api/tlbexp/index.md)  
 [LoadTypeLibEx işlevi](https://msdn.microsoft.com/library/windows/desktop/ms221249\(v=vs.85\).aspx)
