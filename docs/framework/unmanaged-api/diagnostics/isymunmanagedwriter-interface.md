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
ms.openlocfilehash: 8f0bbd26bde562df5482d167c9d2775e01426f55
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610060"
---
# <a name="isymunmanagedwriter-interface"></a>ISymUnmanagedWriter Arabirimi
Bir sembol yazıcısını temsil eder ve belgeleri, dizi noktalarını, sözcük temelli kapsamları ve değişkenleri tanımlamak için yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Abort Yöntemi](isymunmanagedwriter-abort-method.md)|Sembol deposuna sembolleri kaydetmeden sembol yazıcısını kapatır.|  
|[Close yöntemi](isymunmanagedwriter-close-method.md)|Sembolleri sembol deposuna kaydettikten sonra sembol yazıcısını kapatır.|  
|[CloseMethod Yöntemi](isymunmanagedwriter-closemethod-method.md)|Geçerli yöntemi kapatır. Bir yöntem kapatıldıktan sonra bunun içinde başka semboller tanımlanamaz.|  
|[CloseNamespace Yöntemi](isymunmanagedwriter-closenamespace-method.md)|En son açılan ad alanını kapatır.|  
|[CloseScope Yöntemi](isymunmanagedwriter-closescope-method.md)|Geçerli sözcük temelli kapsamı kapatır.|  
|[DefineConstant Yöntemi](isymunmanagedwriter-defineconstant-method.md)|Sabit değer için bir ad tanımlar.|  
|[DefineDocument Yöntemi](isymunmanagedwriter-definedocument-method.md)|Bir kaynak belge tanımlar.|  
|[DefineField Yöntemi](isymunmanagedwriter-definefield-method.md)|Bir yöntem içinde olmayan tek bir değişkeni tanımlar.|  
|[DefineGlobalVariable Yöntemi](isymunmanagedwriter-defineglobalvariable-method.md)|Tek bir genel değişkeni tanımlar.|  
|[DefineLocalVariable Yöntemi](isymunmanagedwriter-definelocalvariable-method.md)|Geçerli sözcük kapsamındaki tek bir değişkeni tanımlar.|  
|[DefineParameter Yöntemi](isymunmanagedwriter-defineparameter-method.md)|Geçerli yöntemde tek bir parametre tanımlar.|  
|[DefineSequencePoints Yöntemi](isymunmanagedwriter-definesequencepoints-method.md)|Geçerli yöntem içindeki bir dizi noktası grubunu tanımlar.|  
|[GetDebugInfo Yöntemi](isymunmanagedwriter-getdebuginfo-method.md)|Bir derleyicinin taşınabilir yürütülebilir (PE) dosya üstbilgisine hata ayıklama dizini girişini yazması için gereken bilgileri döndürür.|  
|[Initialize Yöntemi](isymunmanagedwriter-initialize-method.md)|Bu yazıcının ilişkilendirileceği meta veri verici arabirimini ayarlar ve hata ayıklama simgelerinin yazılacağı çıkış dosyası adını ayarlar.|  
|[Initialize2 Yöntemi](isymunmanagedwriter-initialize2-method.md)|Bu yazıcının ilişkilendirileceği meta veri verici arabirimini ayarlar, hata ayıklama simgelerinin yazılacağı çıkış dosyası adını ayarlar ve program veritabanı (PDB) dosyasının son konumunu ayarlar.|  
|[OpenMethod Yöntemi](isymunmanagedwriter-openmethod-method.md)|Sembol bilgisinin yayıldığını bir yöntem açar.|  
|[OpenNamespace Yöntemi](isymunmanagedwriter-opennamespace-method.md)|Yeni bir ad alanı açar.|  
|[OpenScope Yöntemi](isymunmanagedwriter-openscope-method.md)|Geçerli yöntemde yeni bir sözlü kapsam açar.|  
|[RemapToken Yöntemi](isymunmanagedwriter-remaptoken-method.md)|Meta veri yayıldığından, meta veri belirtecinin yeniden eşlenme olduğunu sembol yazıcısına bildirir.|  
|[SetMethodSourceRange Yöntemi](isymunmanagedwriter-setmethodsourcerange-method.md)|Kaynak dosya içindeki bir yöntemin doğru başlangıcını ve sonunu belirtir.|  
|[SetScopeRange Yöntemi](isymunmanagedwriter-setscoperange-method.md)|Belirtilen sözcük temelli kapsamın fark aralığını tanımlar.|  
|[SetSymAttribute Yöntemi](isymunmanagedwriter-setsymattribute-method.md)|Özel bir özniteliği adına göre tanımlar.|  
|[SetUserEntryPoint Yöntemi](isymunmanagedwriter-setuserentrypoint-method.md)|Bu modülün giriş noktası olan Kullanıcı tanımlı yöntemi belirtir.|  
|[UsingNamespace Yöntemi](isymunmanagedwriter-usingnamespace-method.md)|Verilen tam ad alanı adının şu anda açık olan sözlü kapsam içinde kullanıldığını belirtir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi:** CorSym. IDL, CorSym. h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tanılama Simge Deposu Arabirimleri](diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedWriter2 Arabirimi](isymunmanagedwriter2-interface.md)
- [ISymUnmanagedWriter3 Arabirimi](isymunmanagedwriter3-interface.md)
