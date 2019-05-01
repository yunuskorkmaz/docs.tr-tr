---
title: Tanılama Sembol Deposu Arabirimleri
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- diagnostics symbol store interfaces [.NET Framework]
- interfaces [.NET Framework], diagnostics symbol store
- unmanaged interfaces [.NET Framework], diagnostics symbol store
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: f96987d5-e6a5-478b-ac5e-302e16545cce
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6fca7359888b8b73b2e1cf709ab708d71abf0db6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61787900"
---
# <a name="diagnostics-symbol-store-interfaces"></a>Tanılama Sembol Deposu Arabirimleri
Bu konuda, bir hata ayıklayıcı tarafından kullanım için sembol bilgisi oluşturmak bir derleyiciyi etkinleştir yönetilmeyen arabirimler açıklanmaktadır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [IBindingDisplay Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)  
 Çalışan uygulamayı geçerli bağlama bilgilerini görüntülemek için yöntemler sağlar.  
  
 [IDebugAutoAttach Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/idebugautoattach-interface.md)  
 Hata ayıklayıcı sunucu çağrılan otomatik iliştirme için arabirimi tanımlar.  
  
 [INotifyConnection2 Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)  
 Kaydetme ve bağlantı bildirim kaynağı kaydını kaldırmak için kullanılan yöntemler bildirir.  
  
 [INotifySink2 Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)  
 Havuz bildirim için yöntemleri bildirir.  
  
 [INotifySource2 Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)  
 Bildirim filtreleri ayarlamak için bir yöntem bildirir.  
  
 [ISymENCUnmanagedMethod Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)  
 Düzenle ve devam et özelliği için bilgi sağlar.  
  
 [ISymUnmanagedAsyncMethod Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)  
 Bu bir arabirimdir okuma tamamlayan [Isymunmanagedasyncmethodpropertieswriter arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md).  
  
 [ISymUnmanagedAsyncMethodPropertiesWriter Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)  
 İsteğe bağlı zaman uyumsuz yöntem bilgileri yöntemi sembol başına tanımlanmasına olanak tanır. Açılan bir yöntemle kullanmanız gerekir (diğer bir deyişle, yapılan çağrılar arasında [OpenMethod yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)ve [CloseMethod yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)).  
  
 [ISymUnmanagedBinder Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)  
 Yönetilmeyen kod için bir simge bağlayıcı temsil eder.  
  
 [ISymUnmanagedBinder2 Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)  
 Yönetilmeyen kod için bir simge bağlayıcı temsil eder ve genişleten `ISymUnmanagedBinder` arabirimi.  
  
 [ISymUnmanagedBinder3 Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)  
 Yönetilmeyen kod için bir simge bağlayıcı temsil eder ve genişleten `ISymUnmanagedBinder` arabirimi.  
  
 [ISymUnmanagedConstant Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)  
 Yönetilmeyen sabitleri erişim sağlar.  
  
 [ISymUnmanagedDispose Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddispose-interface.md)  
 Yönetilmeyen kaynakları siler.  
  
 [ISymUnmanagedDocument Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)  
 Bir sembol deposu tarafından başvurulan bir belgeyi temsil eder.  
  
 [ISymUnmanagedDocumentWriter Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocumentwriter-interface.md)  
 Bir sembol deposu tarafından başvurulan bir belge için yazma yöntemleri sağlar.  
  
 [ISymUnmanagedENCUpdate Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)  
 Düzenle ve devam et özelliği için yöntemler sağlar.  
  
 [ISymUnmanagedMethod Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)  
 Sembol deposundaki bir yöntemi temsil eder.  
  
 [ISymUnmanagedNamespace Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)  
 Bir ad alanı temsil eder.  
  
 [ISymUnmanagedReader Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)  
 Belgeler, yöntemler ve değişkenler bir sembol deposundaki erişim sağlayan bir sembol okuyucu temsil eder.  
  
 [ISymUnmanagedReader2 Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)  
 Bir sembol okuyucu yöntemi verilen token metody ve bir düzenleme ve kopyalama sürüm numarasını alır.  
  
 [ISymUnmanagedReaderSymbolSearchInfo Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreadersymbolsearchinfo-interface.md)  
 Sembol arama bilgilerini almak için yöntemler sağlar.  
  
 [ISymUnmanagedScope Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)  
 Bir sözlü kapsamda bir yöntemi temsil eder.  
  
 [ISymUnmanagedScope2 Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)  
 Bir sözcük kapsamı içindeki bir yöntemi temsil eder ve genişleten `ISymUnmanagedScope` arabirim yöntemleriyle kapsamında tanımlanmış sabitleri hakkında bilgi edinin...  
  
 [ISymUnmanagedSourceServerModule Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsourceservermodule-interface.md)  
 Kaynak sunucu verileri için bir modül sağlar.  
  
 [ISymUnmanagedSymbolSearchInfo Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md)  
 Arama yolu hakkında bilgi almak için yöntemler sağlar.  
  
 [ISymUnmanagedVariable Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)  
 Bir parametre, yerel bir değişken veya bir alan gibi bir değişkeni temsil eder.  
  
 [ISymUnmanagedWriter Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 Sembol yazıcıyı temsil eder ve belgeler, dizi noktaları, sözcük kapsamları ve değişkenleri tanımlamak için yöntemler sağlar.  
  
 [ISymUnmanagedWriter2 Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)  
 Sembol yazıcıyı temsil eder ve belgeler, dizi noktaları, sözcük kapsamları ve değişkenleri tanımlamak için yöntemler sağlar. Genişletir `ISymUnmanagedWriter` arabirimi.  
  
 [ISymUnmanagedWriter3 Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)  
 Sembol yazıcıyı temsil eder ve belgeler, dizi noktaları, sözcük kapsamları ve değişkenleri tanımlamak için yöntemler sağlar. Genişletir `ISymUnmanagedWriter` arabirimi.  
  
 [ISymUnmanagedWriter4 Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)  
 Isymunmanagedwriter4 arabirimi.  
  
 [ISymUnmanagedWriter5 Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)  
 Isymunmanagedwriter5 arabirimi.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Tanılama Simge Deposu Sabit Listeleri](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)  
  
 [Tanılama Simge Deposu Yapıları](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)  
  
 [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
