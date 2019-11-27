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
ms.openlocfilehash: fc19ee25e903046daef376e4297c8feb3d01ad47
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427930"
---
# <a name="isymunmanagedwriter-interface"></a>ISymUnmanagedWriter Arabirimi
Bir sembol yazıcısını temsil eder ve belgeleri, dizi noktalarını, sözcük temelli kapsamları ve değişkenleri tanımlamak için yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Abort Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-abort-method.md)|Sembol deposuna sembolleri kaydetmeden sembol yazıcısını kapatır.|  
|[Close Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-close-method.md)|Sembolleri sembol deposuna kaydettikten sonra sembol yazıcısını kapatır.|  
|[CloseMethod Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)|Geçerli yöntemi kapatır. Bir yöntem kapatıldıktan sonra bunun içinde başka semboller tanımlanamaz.|  
|[CloseNamespace Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closenamespace-method.md)|En son açılan ad alanını kapatır.|  
|[CloseScope Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md)|Geçerli sözcük temelli kapsamı kapatır.|  
|[DefineConstant Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineconstant-method.md)|Sabit değer için bir ad tanımlar.|  
|[DefineDocument Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definedocument-method.md)|Bir kaynak belge tanımlar.|  
|[DefineField Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definefield-method.md)|Bir yöntem içinde olmayan tek bir değişkeni tanımlar.|  
|[DefineGlobalVariable Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineglobalvariable-method.md)|Tek bir genel değişkeni tanımlar.|  
|[DefineLocalVariable Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definelocalvariable-method.md)|Geçerli sözcük kapsamındaki tek bir değişkeni tanımlar.|  
|[DefineParameter Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineparameter-method.md)|Geçerli yöntemde tek bir parametre tanımlar.|  
|[DefineSequencePoints Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definesequencepoints-method.md)|Geçerli yöntem içindeki bir dizi noktası grubunu tanımlar.|  
|[GetDebugInfo Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md)|Bir derleyicinin taşınabilir yürütülebilir (PE) dosya üstbilgisine hata ayıklama dizini girişini yazması için gereken bilgileri döndürür.|  
|[Initialize Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize-method.md)|Bu yazıcının ilişkilendirileceği meta veri verici arabirimini ayarlar ve hata ayıklama simgelerinin yazılacağı çıkış dosyası adını ayarlar.|  
|[Initialize2 Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize2-method.md)|Bu yazıcının ilişkilendirileceği meta veri verici arabirimini ayarlar, hata ayıklama simgelerinin yazılacağı çıkış dosyası adını ayarlar ve program veritabanı (PDB) dosyasının son konumunu ayarlar.|  
|[OpenMethod Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)|Sembol bilgisinin yayıldığını bir yöntem açar.|  
|[OpenNamespace Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-opennamespace-method.md)|Yeni bir ad alanı açar.|  
|[OpenScope Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md)|Geçerli yöntemde yeni bir sözlü kapsam açar.|  
|[RemapToken Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-remaptoken-method.md)|Meta veri yayıldığından, meta veri belirtecinin yeniden eşlenme olduğunu sembol yazıcısına bildirir.|  
|[SetMethodSourceRange Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setmethodsourcerange-method.md)|Kaynak dosya içindeki bir yöntemin doğru başlangıcını ve sonunu belirtir.|  
|[SetScopeRange Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md)|Belirtilen sözcük temelli kapsamın fark aralığını tanımlar.|  
|[SetSymAttribute Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setsymattribute-method.md)|Özel bir özniteliği adına göre tanımlar.|  
|[SetUserEntryPoint Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setuserentrypoint-method.md)|Bu modülün giriş noktası olan Kullanıcı tanımlı yöntemi belirtir.|  
|[UsingNamespace Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-usingnamespace-method.md)|Verilen tam ad alanı adının şu anda açık olan sözlü kapsam içinde kullanıldığını belirtir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi:** CorSym. IDL, CorSym. h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tanılama Simge Deposu Arabirimleri](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedWriter2 Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)
- [ISymUnmanagedWriter3 Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
