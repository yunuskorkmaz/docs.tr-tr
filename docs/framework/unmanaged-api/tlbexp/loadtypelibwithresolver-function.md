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
ms.openlocfilehash: adbb5eca3b7ffa36d0c963d0dacc3b2afdb664d4
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75935557"
---
# <a name="loadtypelibwithresolver-function"></a>LoadTypeLibWithResolver İşlevi
Bir tür kitaplığını yükler ve dahili olarak başvurulan tüm tür kitaplıklarını çözümlemek için sağlanan [ıtypeelibresolver arabirimini](itypelibresolver-interface.md) kullanır.  
  
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
 'ndaki Tür kitaplığının dosya yolu.  
  
 `regkind`  
 'ndaki Tür kitaplığının nasıl kaydedildiğini denetleyen bir [regkind numaralandırma](/windows/win32/api/oleauto/ne-oleauto-regkind) bayrağı. Olası değerleri şunlardır:  
  
- `REGKIND_DEFAULT`: varsayılan kayıt davranışını kullanın.  
  
- `REGKIND_REGISTER`: Bu tür kitaplığını kaydedin.  
  
- `REGKIND_NONE`: Bu tür kitaplığını kaydetme.  
  
 `pTlbResolver`  
 'ndaki [Itypeelibresolver arabiriminin](itypelibresolver-interface.md)uygulanması için bir işaretçi.  
  
 `pptlib`  
 dışı Yüklenmekte olan tür kitaplığına bir başvuru.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Aşağıdaki tabloda listelenen HRESULT değerlerinden biri.  
  
|Dönüş değeri|Açıklama|  
|------------------|-------------|  
|`S_OK`|Başarılı.|  
|`E_OUTOFMEMORY`|Bellek yetersiz.|  
|`E_POINTER`|İşaretçilerin bir veya daha fazlası geçersiz.|  
|`E_INVALIDARG`|Bağımsız değişkenlerden biri veya birkaçı geçersiz.|  
|`TYPE_E_IOERROR`|İşlev dosyaya yazamadı.|  
|`TYPE_E_REGISTRYACCESS`|Sistem kayıt veritabanı açılamadı.|  
|`TYPE_E_INVALIDSTATE`|Tür kitaplığı açılamadı.|  
|`TYPE_E_CANTLOADLIBRARY`|Tür kitaplığı veya DLL yüklenemedi.|  
  
## <a name="remarks"></a>Açıklamalar  
 [Tlbexp. exe (tür kitaplığı verme programı)](../../tools/tlbexp-exe-type-library-exporter.md) , derlemeden tür kitaplığı dönüştürme işlemi sırasında `LoadTypeLibWithResolver` işlevini çağırır.  
  
 Bu işlev, kayıt defterine en az erişimli olan belirtilen tür kitaplığını yükler. Bu işlev daha sonra, her birinin yüklenmesi ve üst tür kitaplığına eklenmesi gereken dahili olarak Başvurulmuş tür kitaplıkları için tür kitaplığını inceler.  
  
 Başvurulan bir tür kitaplığının yüklenebilmesi için, başvuru dosyası yolunun tam dosya yoluna çözülmesi gerekir. Bu, `pTlbResolver` parametresine geçirilen [ıtypeelibresolver arabirimi](itypelibresolver-interface.md)tarafından verilen [resolvettypeınfo yöntemi](resolvetypelib-method.md) aracılığıyla gerçekleştirilir.  
  
 Başvurulan tür kitaplığının tam dosya yolu bilindiğinde `LoadTypeLibWithResolver` işlevi yüklenir ve başvurulan tür kitaplığını üst tür kitaplığına ekler ve birleştirilmiş bir ana tür kitaplığı oluşturur.  
  
 İşlev, iç başvurulan tüm tür kitaplıklarını çözümleyip yükledikten sonra, `pptlib` parametresinde ana çözümlenen tür kitaplığına bir başvuru döndürür.  
  
 `LoadTypeLibWithResolver` işlevi genellikle [Tlbexp. exe (tür kitaplığı verme programı)](../../tools/tlbexp-exe-type-library-exporter.md)tarafından çağrılır ve bu, `pTlbResolver` parametresinde kendi Iç [ITypeLibResolver arabirimi](itypelibresolver-interface.md) uygulamasını sağlar.  
  
 `LoadTypeLibWithResolver` doğrudan çağırırsanız, kendi [ITypeLibResolver arabirimi](itypelibresolver-interface.md) uygulamanızı sağlamanız gerekir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** TlbRef. h  
  
 **Kitaplık:** TlbRef. lib  
  
 **.NET Framework sürümü:** 3,5, 3,0, 2,0  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tlbexp Yardımcı İşlevleri](index.md)
- [LoadTypeLibEx Işlevi](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
