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
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="diagnostics-symbol-store-interfaces"></a>Tanılama Sembol Deposu Arabirimleri
Bu konuda, bir hata ayıklayıcısı tarafından kullanılmak üzere sembol bilgileri oluşturmak bir derleyici etkinleştirmek yönetilmeyen arabirimler açıklanmaktadır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [IBindingDisplay Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)  
 Çalışan uygulama geçerli bağlama bilgilerini görüntüleme yöntemleri sağlar.  
  
 [IDebugAutoAttach Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/idebugautoattach-interface.md)  
 Bir sunucu çağrılan hata ayıklayıcı otomatik eklemek için arabirimi tanımlar.  
  
 [INotifyConnection2 Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)  
 Kaydetme ve bağlantı bildirim kaynağı kaydını kaldırmak için kullanılan yöntemler bildirir.  
  
 [INotifySink2 Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)  
 Havuz bildirim için yöntemleri bildirir.  
  
 [INotifySource2 Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)  
 Bildirim filtreleri ayarlamak için bir yöntem bildirir.  
  
 [ISymENCUnmanagedMethod Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)  
 Düzenle ve devam et özelliği için bilgiler sağlar.  
  
 [ISymUnmanagedAsyncMethod Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)  
 Bu bir arabirimdir okuma tamamlayan [Isymunmanagedasyncmethodpropertieswriter arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md).  
  
 [ISymUnmanagedAsyncMethodPropertiesWriter Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)  
 İsteğe bağlı zaman uyumsuz yöntem bilgileri yöntemi simge başına tanımlanmasına olanak tanır. İle açılmış bir yöntem kullanmanız gerekir (diğer bir deyişle, yapılan çağrılar arasında [OpenMethod yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)ve [CloseMethod yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)).  
  
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
 Sembol deposu tarafından başvurulan bir belgeyi temsil eder.  
  
 [ISymUnmanagedDocumentWriter Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocumentwriter-interface.md)  
 Sembol deposu tarafından başvurulan bir belge için yazma yöntemleri sağlar.  
  
 [ISymUnmanagedENCUpdate Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)  
 Düzenle ve devam et özelliği için yöntemleri sağlar.  
  
 [ISymUnmanagedMethod Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)  
 Sembol deposu içinde yöntemi temsil eder.  
  
 [ISymUnmanagedNamespace Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)  
 Bir ad alanı temsil eder.  
  
 [ISymUnmanagedReader Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)  
 Belgeler, yöntemleri ve sembol deposu değişkenler erişim sağlayan bir simge okuyucuyu temsil eder.  
  
 [ISymUnmanagedReader2 Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)  
 Verilen bir yöntem belirteci ve bir düzenleme ve kopyalama sürüm numarası bir simge okuyucu yöntemi alır.  
  
 [ISymUnmanagedReaderSymbolSearchInfo Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreadersymbolsearchinfo-interface.md)  
 Sembol arama bilgilerini alma yöntemleri sağlar.  
  
 [ISymUnmanagedScope Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)  
 Bir yöntem sözcük kapsamında temsil eder.  
  
 [ISymUnmanagedScope2 Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)  
 Bir sözcük kapsamı içinde bir yöntemi gösterir ve genişletir `ISymUnmanagedScope` arabirimi yöntemleriyle kapsamı içinde tanımlanan sabitleri hakkında bilgi edinin...  
  
 [ISymUnmanagedSourceServerModule Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsourceservermodule-interface.md)  
 Kaynak sunucu veriler için bir modül sağlar.  
  
 [ISymUnmanagedSymbolSearchInfo Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md)  
 Arama yolu hakkında bilgi edinme yöntemleri sağlar.  
  
 [ISymUnmanagedVariable Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)  
 Bir parametre, yerel bir değişken ya da bir alan gibi bir değişkeni temsil eder.  
  
 [ISymUnmanagedWriter Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 Sembol yazıcıyı temsil eder ve belgeleri, sıralama noktaları, sözcük kapsamlar ve değişkenleri tanımlamak için yöntemler sağlar.  
  
 [ISymUnmanagedWriter2 Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)  
 Sembol yazıcıyı temsil eder ve belgeleri, sıralama noktaları, sözcük kapsamlar ve değişkenleri tanımlamak için yöntemler sağlar. Genişletir `ISymUnmanagedWriter` arabirimi.  
  
 [ISymUnmanagedWriter3 Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)  
 Sembol yazıcıyı temsil eder ve belgeleri, sıralama noktaları, sözcük kapsamlar ve değişkenleri tanımlamak için yöntemler sağlar. Genişletir `ISymUnmanagedWriter` arabirimi.  
  
 [ISymUnmanagedWriter4 Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)  
 Isymunmanagedwriter4 arabirimi.  
  
 [ISymUnmanagedWriter5 Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)  
 Isymunmanagedwriter5 arabirimi.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Tanılama Simge Deposu Sabit Listeleri](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)  
  
 [Tanılama Simge Deposu Yapıları](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)  
  
 [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
