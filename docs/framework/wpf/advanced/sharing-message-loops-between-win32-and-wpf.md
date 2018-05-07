---
title: Win32 ve WPF Arasında İleti Döngüleri Paylaşma
ms.date: 03/30/2017
helpviewer_keywords:
- Win32 code [WPF], sharing message loops
- message loops [WPF]
- sharing message loops [WPF]
- interoperability [WPF], Win32
ms.assetid: 39ee888c-e5ec-41c8-b11f-7b851a554442
ms.openlocfilehash: 35a908cc26e6b70c9acd8732521837f2b20eaf5b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="sharing-message-loops-between-win32-and-wpf"></a>Win32 ve WPF Arasında İleti Döngüleri Paylaşma
Bu konu ile birlikte çalışma için bir ileti döngüsü uygulamak açıklar [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], varolan kullanarak ya da ileti döngüsü <xref:System.Windows.Threading.Dispatcher> veya üzerinde ayrı bir ileti döngüsü oluşturarak [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] kodunuzun tarafında.  
  
## <a name="componentdispatcher-and-the-message-loop"></a>ComponentDispatcher ve ileti döngüsü  
 Birlikte çalışabilirlik ve klavye olay desteği için normal bir senaryo uygulamaktır <xref:System.Windows.Interop.IKeyboardInputSink>, veya alt zaten uygulamak sınıflardan <xref:System.Windows.Interop.IKeyboardInputSink>, gibi <xref:System.Windows.Interop.HwndSource> veya <xref:System.Windows.Interop.HwndHost>. Ancak, klavye havuzu desteği iletiler birlikte çalışabilirlik sınırlarında gönderilip alınırken olabilir tüm olası ileti döngüsü gereksinimlerini adresi değil. Bir uygulama ileti döngüsü mimarisinin resmileştirin yardımcı olmak için [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] sağlar <xref:System.Windows.Interop.ComponentDispatcher> izlemek bir ileti döngüsü için basit bir protokol tanımlayan sınıfı.  
  
 <xref:System.Windows.Interop.ComponentDispatcher> birkaç üye sunan statik bir sınıftır. Her yöntemin kapsamı örtük olarak çağıran iş parçacığı bağlıdır. Bir ileti döngüsü bazıları çağırmalısınız [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] kritik saatler (sonraki bölümde tanımlanan şekilde).  
  
 <xref:System.Windows.Interop.ComponentDispatcher> diğer bileşenleri (örneğin, klavye havuzu) dinlediği olayları sağlar. <xref:System.Windows.Threading.Dispatcher> Sınıfı çağrıları tüm uygun <xref:System.Windows.Interop.ComponentDispatcher> uygun bir sıra yöntemleri. İleti döngünüz uyguluyorsanız, kodunuzu çağırmadan sorumludur <xref:System.Windows.Interop.ComponentDispatcher> benzer bir şekilde yöntemleri.  
  
 Çağırma <xref:System.Windows.Interop.ComponentDispatcher> bir iş parçacığı üzerinde yöntemleri yalnızca o iş parçacığı üzerinde kayıtlı olan olay işleyicileri çağırma.  
  
## <a name="writing-message-loops"></a>İleti döngüsü yazma  
 Bir listesi aşağıda verilmektedir <xref:System.Windows.Interop.ComponentDispatcher> kullanacağınız kendi ileti döngüsü yazma üyeleri:  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.PushModal%2A>: ileti döngünüz iş parçacığının kalıcı olduğunu belirtmek için bunu çağırmalıdır.  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.PopModal%2A>: ileti döngünüz iş parçacığı kalıcı döndü belirtmek için bunu çağırmalıdır.  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.RaiseIdle%2A>: ileti döngünüz belirtmek için bunu çağırmalıdır <xref:System.Windows.Interop.ComponentDispatcher> tetiklemelidir <xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle> olay. <xref:System.Windows.Interop.ComponentDispatcher> oluşturmaz <xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle> varsa <xref:System.Windows.Interop.ComponentDispatcher.IsThreadModal%2A> olan `true`, ancak ileti döngüleri çağırmayı seçebilir <xref:System.Windows.Interop.ComponentDispatcher.RaiseIdle%2A> olsa bile <xref:System.Windows.Interop.ComponentDispatcher> kalıcı durumundayken içinde yanıt veremez.  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.RaiseThreadMessage%2A>: ileti döngünüz yeni bir ileti kullanılabilir olduğunu belirtmek için bunu çağırmalıdır. Dönüş değerini gösteren bir dinleyici olup olmadığını bir <xref:System.Windows.Interop.ComponentDispatcher> olay işlenen ileti. Varsa <xref:System.Windows.Interop.ComponentDispatcher.RaiseThreadMessage%2A> döndürür `true` (işlenmiş) dağıtıcı iletiyle daha fazla şey yapmanız gerekir. Dönüş değeri ise `false`, dağıtıcı çağırmak için beklenen [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] işlevi `TranslateMessage`, ardından çağıran `DispatchMessage`.  
  
## <a name="using-componentdispatcher-and-existing-message-handling"></a>İleti işleme var ve ComponentDispatcher kullanma  
 Bir listesi aşağıda verilmektedir <xref:System.Windows.Interop.ComponentDispatcher> devralınan güveniyorsanız kullanacağınız üyeleri [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ileti döngüsü.  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.IsThreadModal%2A>: uygulama kalıcı olup olmadığını döndürür (örn., kalıcı ileti döngüsü gönderilen). <xref:System.Windows.Interop.ComponentDispatcher> sınıf sayısını bulundurur, bu nedenle bu durumu izleyebilir <xref:System.Windows.Interop.ComponentDispatcher.PushModal%2A> ve <xref:System.Windows.Interop.ComponentDispatcher.PopModal%2A> ileti döngüsü gelen çağrıları.  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage> ve <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage> olayları temsilci etkinleştirmeleri için standart kuralları izler. Temsilciler belirtilmemiş sırayla çağrılır ve ilk iletiyi işlenmiş olarak işaretler olsa bile tüm temsilciler çağrılır.  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle>: boşta işlem için uygun ve etkili bir zamanı belirtir (iş parçacığı için bekleyen başka iletiler yoktur). <xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle> iş parçacığı kalıcı ise oluşturulmaz.  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage>: ileti göndericisinin işlediği tüm iletiler için oluşturulur.  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage>: sırasında işlenmemiş olan tüm iletiler için yükseltilmiş <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage>.  
  
 Bir ileti kabul sonra işlenmiş IF <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage> olay veya <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage> olayı `handled` olay verileri başvuruya göre geçirilen parametre `true`. Olay işleyicileri göz ardı ileti edilmediğini `handled` olan `true`, farklı bir işleyici işlenen ileti ilk anlamına gelir. Her iki olayın olay işleyicileri iletiyi değiştirebilir. Dağıtıcı değiştirilmiş iletisi ve değil özgün değişmeden iletisi dağıtmalıdır. <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage> Tüm dinleyicileri ancak mimari amaç teslim yalnızca hangi iletilerin hedeflendiği çağırma iletisine yanıt kodunu HWND içeren üst düzey pencere olmasıdır.  
  
## <a name="how-hwndsource-treats-componentdispatcher-events"></a>HwndSource ComponentDispatcher olaylarını nasıl işler  
 Varsa <xref:System.Windows.Interop.HwndSource> (üst HWND), bir üst düzey penceresi ile kaydeder <xref:System.Windows.Interop.ComponentDispatcher>. Varsa <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage> ortaya çıkar ve ileti yöneliktir <xref:System.Windows.Interop.HwndSource> veya alt öğe pencerelerini <xref:System.Windows.Interop.HwndSource> çağrıları kendi <xref:System.Windows.Interop.HwndSource.System%23Windows%23Interop%23IKeyboardInputSink%23TranslateAccelerator%2A>, <xref:System.Windows.Interop.IKeyboardInputSink.TranslateChar%2A>, <xref:System.Windows.Interop.IKeyboardInputSink.OnMnemonic%2A> klavye havuzu dizisini.  
  
 Varsa <xref:System.Windows.Interop.HwndSource> hiçbir işleme olmayacaktır (sahip bir üst HWND) bir üst düzey penceresi değil. Yalnızca üst düzey penceresi işleme yapmak için beklenen bir durumdur ve var. bir üst düzey penceresi klavye havuzu desteği ile birlikte çalışabilirlik her senaryo bir parçası olarak olması beklenir.  
  
 Varsa <xref:System.Windows.Interop.HwndHost.WndProc%2A> üzerinde bir <xref:System.Windows.Interop.HwndSource> çağrılır ilk çağrılan bir uygun klavye havuzu yöntemi, uygulamanızı daha yüksek düzey klavye olayları gibi alacak <xref:System.Windows.UIElement.KeyDown>. Ancak, hangi erişim anahtar desteği gibi istenen klavye girişi model özellikleri bozar hiçbir klavye havuzu yöntemi çağrılır. İleti döngüsü düzgün ilgili iş parçacığı bildirim değil çünkü bu durum oluşabilir <xref:System.Windows.Interop.ComponentDispatcher>, veya üst HWND klavye havuzu cevaplarını çağırma kullanılamaz.  
  
 Kullanarak bu iletiyi kancaları eklediyseniz klavye havuzuna giden bir ileti HWND gönderilebilir değil <xref:System.Windows.Interop.HwndSource.AddHook%2A> yöntemi. İleti doğrudan gönderilen ileti göndericisi düzeyinde işlenen `DispatchMessage` işlevi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Interop.ComponentDispatcher>  
 <xref:System.Windows.Interop.IKeyboardInputSink>  
 [WPF ve Win32 Birlikte Çalışması](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)  
 [İş Parçacığı Modeli](../../../../docs/framework/wpf/advanced/threading-model.md)  
 [Girişe Genel Bakış](../../../../docs/framework/wpf/advanced/input-overview.md)
