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
ms.openlocfilehash: bdb691570a9a2bf7bd2bb21af500b06c10b0bc53
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448529"
---
# <a name="diagnostics-symbol-store-interfaces"></a>Tanılama Sembol Deposu Arabirimleri
Bu konuda, bir derleyicinin hata ayıklayıcı tarafından kullanılmak üzere sembol bilgisi oluşturmasını sağlayan yönetilmeyen arabirimler açıklanmaktadır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [IBindingDisplay Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)  
 Çalışan uygulamayla ilgili geçerli bağlama bilgilerini görüntüleyen yöntemler sağlar.  
  
 [IDebugAutoAttach Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/idebugautoattach-interface.md)  
 Sunucu tarafından çağrılan bir hata ayıklayıcı otomatik iliştirme arabirimini tanımlar.  
  
 [INotifyConnection2 Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)  
 Bağlantı bildirim kaynağını kaydetme ve kaydını silme yöntemlerini bildirir.  
  
 [INotifySink2 Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)  
 Havuz bildirimi için yöntemler bildirir.  
  
 [INotifySource2 Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)  
 Bildirim filtrelerini ayarlamak için bir yöntem bildirir.  
  
 [ISymENCUnmanagedMethod Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)  
 Düzenle ve devam et özelliği hakkında bilgi sağlar.  
  
 [ISymUnmanagedAsyncMethod Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)  
 Bu arabirim, [ıvmunmanagedasyncmethodpropertieswriter arabirimini](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)tamamlayan okuma işlemi.  
  
 [ISymUnmanagedAsyncMethodPropertiesWriter Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)  
 Yöntem simgesi başına isteğe bağlı zaman uyumsuz yöntem bilgilerinin tanımına izin verir. , Bir açık yöntemle kullanılmalıdır (diğer bir deyişle, [OpenMethod yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)ve [CloseMethod yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)çağrıları arasında).  
  
 [ISymUnmanagedBinder Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)  
 Yönetilmeyen kod için bir sembol cildi temsil eder.  
  
 [ISymUnmanagedBinder2 Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)  
 Yönetilmeyen kod için bir sembol cildi temsil eder ve `ISymUnmanagedBinder` arabirimini genişletir.  
  
 [ISymUnmanagedBinder3 Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)  
 Yönetilmeyen kod için bir sembol cildi temsil eder ve `ISymUnmanagedBinder` arabirimini genişletir.  
  
 [ISymUnmanagedConstant Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)  
 Yönetilmeyen sabitlere erişim sağlar.  
  
 [ISymUnmanagedDispose Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddispose-interface.md)  
 Yönetilmeyen kaynakları ortadan kaldırın.  
  
 [ISymUnmanagedDocument Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)  
 Bir sembol deposu tarafından başvurulan bir belgeyi temsil eder.  
  
 [ISymUnmanagedDocumentWriter Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocumentwriter-interface.md)  
 Sembol deposu tarafından başvurulan bir belgeye yazmak için yöntemler sağlar.  
  
 [ISymUnmanagedENCUpdate Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)  
 Düzenle ve devam et özelliği için yöntemler sağlar.  
  
 [ISymUnmanagedMethod Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)  
 Sembol deposu içindeki bir yöntemi temsil eder.  
  
 [ISymUnmanagedNamespace Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)  
 Bir ad alanını temsil eder.  
  
 [ISymUnmanagedReader Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)  
 Bir sembol deposu içindeki belgelere, yöntemlere ve değişkenlere erişim sağlayan bir sembol okuyucuyu temsil eder.  
  
 [ISymUnmanagedReader2 Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)  
 Bir yöntem belirteci ve bir düzenleme ve kopyalama sürümü numarası verilen bir sembol okuyucu yöntemini alır.  
  
 [ISymUnmanagedReaderSymbolSearchInfo Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreadersymbolsearchinfo-interface.md)  
 Sembol arama bilgilerini alan yöntemler sağlar.  
  
 [ISymUnmanagedScope Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)  
 Bir yöntem içindeki bir sözcük temelli kapsamı temsil eder.  
  
 [ISymUnmanagedScope2 Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)  
 Bir yöntem içindeki bir sözcük temelli kapsamı temsil eder ve `ISymUnmanagedScope` arabirimini kapsam içinde tanımlanan sabitler hakkında bilgi alan yöntemlerle genişletir.  
  
 [ISymUnmanagedSourceServerModule Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsourceservermodule-interface.md)  
 Bir modül için kaynak sunucu verisi sağlar.  
  
 [ISymUnmanagedSymbolSearchInfo Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md)  
 Arama yolu hakkında bilgi almak için yöntemler sağlar.  
  
 [ISymUnmanagedVariable Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)  
 Bir parametre, yerel değişken veya bir alan gibi bir değişkeni temsil eder.  
  
 [ISymUnmanagedWriter Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 Bir sembol yazıcısını temsil eder ve belgeleri, dizi noktalarını, sözcük temelli kapsamları ve değişkenleri tanımlamak için yöntemler sağlar.  
  
 [ISymUnmanagedWriter2 Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)  
 Bir sembol yazıcısını temsil eder ve belgeleri, dizi noktalarını, sözcük temelli kapsamları ve değişkenleri tanımlamak için yöntemler sağlar. `ISymUnmanagedWriter` arabirimini genişletir.  
  
 [ISymUnmanagedWriter3 Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)  
 Bir sembol yazıcısını temsil eder ve belgeleri, dizi noktalarını, sözcük temelli kapsamları ve değişkenleri tanımlamak için yöntemler sağlar. `ISymUnmanagedWriter` arabirimini genişletir.  
  
 [ISymUnmanagedWriter4 Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)  
 ISymUnmanagedWriter4 arabirimi.  
  
 [ISymUnmanagedWriter5 Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)  
 ISymUnmanagedWriter5 arabirimi.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Tanılama Simge Deposu Sabit Listeleri](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)  
  
 [Tanılama Simge Deposu Yapıları](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)  
  
 [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
