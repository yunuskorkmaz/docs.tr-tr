---
title: Win32 ve WPF Arasında İleti Döngüleri Paylaşma
ms.date: 03/30/2017
helpviewer_keywords:
- Win32 code [WPF], sharing message loops
- message loops [WPF]
- sharing message loops [WPF]
- interoperability [WPF], Win32
ms.assetid: 39ee888c-e5ec-41c8-b11f-7b851a554442
ms.openlocfilehash: 74055ec3facb7db9145c4c0e969d57da24eccbc8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59115082"
---
# <a name="sharing-message-loops-between-win32-and-wpf"></a>Win32 ve WPF Arasında İleti Döngüleri Paylaşma
Bu konu ile birlikte çalışabilirlik için bir ileti döngüsü uygulanacağını açıklar [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], varolan kullanılarak ileti döngüsü <xref:System.Windows.Threading.Dispatcher> veya üzerinde ayrı bir ileti döngüsü oluşturarak [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] kodunuzun tarafında.  
  
## <a name="componentdispatcher-and-the-message-loop"></a>ComponentDispatcher ve ileti döngüsü  
 Birlikte çalışabilirlik ve klavye olay desteği için normal bir senaryo uygulamaktır <xref:System.Windows.Interop.IKeyboardInputSink>, veya alt Sınıflama zaten uygulayan sınıflardan <xref:System.Windows.Interop.IKeyboardInputSink>, gibi <xref:System.Windows.Interop.HwndSource> veya <xref:System.Windows.Interop.HwndHost>. Ancak, tüm olası ileti döngüsü gereksinimleriniz arasında birlikte çalışabilirlik sınırlarınız ileti alma ve gönderme olabilir klavye havuz desteği adres değil. Bir uygulama ileti döngüsü mimarisinin resmileştirin yardımcı olmak için [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] sağlar <xref:System.Windows.Interop.ComponentDispatcher> izlemek bir ileti döngüsü için basit bir protokol tanımlayan sınıf.  
  
 <xref:System.Windows.Interop.ComponentDispatcher> bazı üyeleri ortaya koyar statik bir sınıftır. Her yöntem kapsamını örtük olarak çağıran iş parçacığına bağlıdır. İleti döngüsü bazıları çağırmalıdır [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] kritik zamanlarda (sonraki bölümde tanımlanmaktadır).  
  
 <xref:System.Windows.Interop.ComponentDispatcher> diğer bileşenleri (örneğin, klavye havuz) dinlemek olayları sağlar. <xref:System.Windows.Threading.Dispatcher> Çağrıları tüm uygun sınıf <xref:System.Windows.Interop.ComponentDispatcher> uygun bir dizide yöntemleri. Kendi ileti döngüsü uyguluyorsanız, kodunuzu çağırmadan sorumludur <xref:System.Windows.Interop.ComponentDispatcher> benzer bir biçimde yöntemleri.  
  
 Çağırma <xref:System.Windows.Interop.ComponentDispatcher> bir iş parçacığı üzerinde yöntemleri yalnızca o iş parçacığı üzerinde kayıtlı olan olay işleyicilerini çağırma.  
  
## <a name="writing-message-loops"></a>İleti döngüsü yazma  
 Bir denetim listesi aşağıdadır <xref:System.Windows.Interop.ComponentDispatcher> üyeleri kendi ileti döngüsü yazarsanız kullanırsınız:  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.PushModal%2A>: iş parçacığı kalıcı olduğunu belirtmek için bu ileti döngünüz çağırmalıdır.  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.PopModal%2A>: iş parçacığı kalıcı döndürüldü belirtmek için ileti döngüsü çağırmalıdır.  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.RaiseIdle%2A>:, ileti döngüsü olduğunu belirten çağırmalıdır <xref:System.Windows.Interop.ComponentDispatcher> tetiklemelidir <xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle> olay. <xref:System.Windows.Interop.ComponentDispatcher> oluşturmaz <xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle> varsa <xref:System.Windows.Interop.ComponentDispatcher.IsThreadModal%2A> olduğu `true`, ancak ileti döngüleri çağırmayı seçebilir <xref:System.Windows.Interop.ComponentDispatcher.RaiseIdle%2A> bile <xref:System.Windows.Interop.ComponentDispatcher> kalıcı durumundayken içinde yanıt veremez.  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.RaiseThreadMessage%2A>: yeni bir ileti kullanılabilir olduğunu belirtmek için ileti döngüsü çağırmalıdır. Dönüş değeri belirten bir dinleyici için olup olmadığını bir <xref:System.Windows.Interop.ComponentDispatcher> olay işlenen ileti. Varsa <xref:System.Windows.Interop.ComponentDispatcher.RaiseThreadMessage%2A> döndürür `true` (işlenmiş) dağıtıcısı daha fazla ileti ile hiçbir işlem yapmamanız. Dönüş değeri ise `false`, dağıtıcı çağırmak için beklenen [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] işlevi `TranslateMessage`, ardından çağırın `DispatchMessage`.  
  
## <a name="using-componentdispatcher-and-existing-message-handling"></a>ComponentDispatcher kullanarak ve var olan ileti işleme  
 Bir denetim listesi aşağıdadır <xref:System.Windows.Interop.ComponentDispatcher> üyeleri devralınan güveniyorsanız kullanacağınız [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ileti döngüsü.  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.IsThreadModal%2A>: uygulama kalıcı olup olmadığını döndürür (örneğin, kalıcı ileti döngüsü itilmiş). <xref:System.Windows.Interop.ComponentDispatcher> sınıf sayısını sürdüren nedeniyle bu durumu izleyebilir <xref:System.Windows.Interop.ComponentDispatcher.PushModal%2A> ve <xref:System.Windows.Interop.ComponentDispatcher.PopModal%2A> ileti döngüsünden gelen çağrıları.  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage> ve <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage> olayları temsilci çağrılarını standart kurallarını izler. Temsilciler, belirtilmemiş sırayla çağrılır ve ilk iletiyi işlenmiş olarak işaretler bile tüm temsilciler çağrılır.  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle>: boşta işlem için uygun ve etkili bir zamanı belirtir (iş parçacığı için bekleyen diğer ileti vardır). <xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle> iş parçacığı kalıcı ise oluşturulmaz.  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage>: ileti pompası işler tüm iletiler için oluşturulur.  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage>: sırasında işlenmemiş olan tüm iletiler için yükseltilmiş <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage>.  
  
 Bir iletiyi kabul işlenmiş IF <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage> olay veya <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage> olay `handled` olay verilerini başvuruya göre geçirilen parametre `true`. Olay işleyicileri varsa iletisini Yoksay `handled` olduğu `true`, farklı bir işleyici işlenen ileti ilk anlamına gelir. Her iki olayları için olay işleyicileri, ileti değiştirebilir. Dağıtıcı değiştirilmiş ileti ve değil değişmeden orijinal mesajın dağıtmalıdır. <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage> Tüm dinleyici, ancak mimari amaç için teslim yalnızca HWND, hedeflenen iletileri çağırmak iletisine yanıt kodunu içeren üst düzey pencere olmasıdır.  
  
## <a name="how-hwndsource-treats-componentdispatcher-events"></a>HwndSource ComponentDispatcher olayları nasıl işler?  
 Varsa <xref:System.Windows.Interop.HwndSource> (üst HWND), bir üst düzey pencere ile kaydolacak <xref:System.Windows.Interop.ComponentDispatcher>. Varsa <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage> oluşturulur, ve eğer ileti için <xref:System.Windows.Interop.HwndSource> veya alt pencereler <xref:System.Windows.Interop.HwndSource> çağrıları kendi <xref:System.Windows.Interop.HwndSource.System%23Windows%23Interop%23IKeyboardInputSink%23TranslateAccelerator%2A>, <xref:System.Windows.Interop.IKeyboardInputSink.TranslateChar%2A>, <xref:System.Windows.Interop.IKeyboardInputSink.OnMnemonic%2A> klavye havuz dizisi.  
  
 Varsa <xref:System.Windows.Interop.HwndSource> hiçbir işleme olacaktır (sahip bir üst HWND) bir üst düzey pencere değil. Yalnızca üst düzey pencere işleme yapmak için beklenen bir durumdur ve yok üst düzey pencere klavye havuz desteği ile birlikte çalışabilirlik her senaryo bir parçası olarak olması beklenir.  
  
 Varsa <xref:System.Windows.Interop.HwndHost.WndProc%2A> üzerinde bir <xref:System.Windows.Interop.HwndSource> çağrılır ilk çağrılan bir uygun klavye havuz yöntemi, uygulamanızın daha yüksek düzey klavye olaylarını gibi alacak <xref:System.Windows.UIElement.KeyDown>. Ancak, istenen klavye girişi model özelliklerini erişim anahtarı desteği gibi bozar hiçbir klavye havuzu yöntemi çağrılır. İleti döngüsünden düzgün ilgili iş parçacığı üzerinde bildirim değil çünkü bu gerçekleşebilir <xref:System.Windows.Interop.ComponentDispatcher>, veya üst HWND uygun klavye havuz yanıtları çağırmadı.  
  
 Kullanarak kancaları eklediyseniz klavye havuzuna giden bir ileti için HWND gönderilmeyebilir <xref:System.Windows.Interop.HwndSource.AddHook%2A> yöntemi. İletiyi doğrudan gönderilen ileti pompası düzeyinde işlenen `DispatchMessage` işlevi.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Interop.ComponentDispatcher>
- <xref:System.Windows.Interop.IKeyboardInputSink>
- [WPF ve Win32 Birlikte Çalışması](wpf-and-win32-interoperation.md)
- [İş Parçacığı Modeli](threading-model.md)
- [Girişe Genel Bakış](input-overview.md)
