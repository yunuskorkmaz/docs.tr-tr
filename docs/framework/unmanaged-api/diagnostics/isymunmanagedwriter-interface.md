---
title: ISymUnmanagedWriter Arabirimi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter
helpviewer_keywords:
- ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: 7d6733ec-f081-4166-bc17-de09e16dc304
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4ac95cd5b79a2e1762fa9adf29d4d7926ab4ab7a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59150590"
---
# <a name="isymunmanagedwriter-interface"></a>ISymUnmanagedWriter Arabirimi
Sembol yazıcıyı temsil eder ve belgeler, dizi noktaları, sözcük kapsamları ve değişkenleri tanımlamak için yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Abort Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-abort-method.md)|Sembolleri sembol deposuna taahhüt vermek zorunda kalmadan sembol yazıcı kapatır.|  
|[Close Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-close-method.md)|Sembolleri sembol deposuna uyguladıktan sonra sembol yazıcı kapatır.|  
|[CloseMethod Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)|Geçerli yöntemi kapatır. Bir yöntem kapatıldıktan sonra daha fazla sembol içinde tanımlanabilir.|  
|[CloseNamespace Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closenamespace-method.md)|Kapatır, ad alanı en son açıldı.|  
|[CloseScope Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md)|Geçerli sözcük kapsamı kapatır.|  
|[DefineConstant Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineconstant-method.md)|Sabit değer için bir ad tanımlar.|  
|[DefineDocument Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definedocument-method.md)|Kaynak belge tanımlar.|  
|[DefineField Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definefield-method.md)|Bir yöntem içinde değil tek bir değişkeni tanımlar.|  
|[DefineGlobalVariable Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineglobalvariable-method.md)|Tek bir genel değişken tanımlar.|  
|[DefineLocalVariable Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definelocalvariable-method.md)|Tek bir değişken, geçerli sözlü kapsamda tanımlar.|  
|[DefineParameter Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineparameter-method.md)|Tek bir parametre, geçerli yöntemi tanımlar.|  
|[DefineSequencePoints Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definesequencepoints-method.md)|Bir dizi noktaları geçerli yöntemi içinde grubunu tanımlar.|  
|[GetDebugInfo Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md)|Hata ayıklama dizin girdisi taşınabilir yürütülebilir (PE) dosya üst bilgisinde yazmak bir derleyici için gerekli bilgileri döndürür.|  
|[Initialize Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize-method.md)|İle bu yazıcısı ilişkilendirilecek olan meta veri verici arabirimi ayarlar ve hata ayıklama sembolleri yazılacağı çıktı dosyası adını ayarlar.|  
|[Initialize2 Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize2-method.md)|İle bu yazıcısı ilişkilendirilecek olan meta veri verici arabirimi ayarlar, hangi hata ayıklama sembolleri yazılır ve program veritabanı (PDB) dosyasının son konumunu ayarlar çıktı dosyası adını ayarlar.|  
|[OpenMethod Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)|Hangi sembolün üretileceği bilgi yayılan bir yöntem açılır.|  
|[OpenNamespace Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-opennamespace-method.md)|Yeni bir ad alanı açılır.|  
|[OpenScope Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md)|Yeni bir sözcük kapsamı geçerli yöntemde açılır.|  
|[RemapToken Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-remaptoken-method.md)|Sembol yazıcı meta veriler gösteriliyordu gibi meta veri belirteci eşleştirilmiş bildirir.|  
|[SetMethodSourceRange Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setmethodsourcerange-method.md)|Gerçek başlangıç ve bitiş bir kaynak dosyası içinde bir yöntemin belirtir.|  
|[SetScopeRange Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md)|Sözcük Belirtilen kapsam için uzaklık aralığı tanımlar.|  
|[SetSymAttribute Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setsymattribute-method.md)|Adını alan özel bir öznitelik tanımlar.|  
|[SetUserEntryPoint Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setuserentrypoint-method.md)|Bu modülü için giriş noktası kullanıcı tanımlı bir yöntemini belirtir.|  
|[UsingNamespace Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-usingnamespace-method.md)|Tam ad alanı adı verilen açık sözlü kapsamda kullanılmakta olduğunu belirtir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tanılama Simge Deposu Arabirimleri](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedWriter2 Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)
- [ISymUnmanagedWriter3 Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
