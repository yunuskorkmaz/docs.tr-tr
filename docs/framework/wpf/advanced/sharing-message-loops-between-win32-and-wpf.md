---
title: Win32 ve WPF Arasında İleti Döngüleri Paylaşma
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- Win32 code [WPF], sharing message loops
- message loops [WPF]
- sharing message loops [WPF]
- interoperability [WPF], Win32
ms.assetid: 39ee888c-e5ec-41c8-b11f-7b851a554442
ms.openlocfilehash: e1b96284d69645876d3e383beb03a2cc540d8b7b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731713"
---
# <a name="sharing-message-loops-between-win32-and-wpf"></a>Win32 ve WPF Arasında İleti Döngüleri Paylaşma
Bu konu, birlikte [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]çalışabilirlik için bir ileti döngüsünün nasıl uygulanacağını, <xref:System.Windows.Threading.Dispatcher> ' de var olan ileti döngüsü kullanımını kullanarak ya da birlikte çalışma kodunuzun Win32 tarafında ayrı bir ileti döngüsü oluşturarak açıklar.  
  
## <a name="componentdispatcher-and-the-message-loop"></a>ComponentDispatcher ve Ileti döngüsü  
 Birlikte çalışabilirlik ve klavye olay desteği için normal bir senaryo, <xref:System.Windows.Interop.IKeyboardInputSink>veya <xref:System.Windows.Interop.HwndSource> ya da <xref:System.Windows.Interop.HwndHost>gibi <xref:System.Windows.Interop.IKeyboardInputSink>daha önceden uygulayan sınıflardan alt sınıflara uygular. Ancak, klavye havuzu desteği, birlikte çalışma sınırlarınız genelinde ileti gönderirken ve alırken sahip olabileceğiniz tüm olası ileti döngüsü gereksinimlerini gidermez. Bir uygulama iletisi döngüsü mimarisini şekillendirmaya yardımcı olmak için [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], bir ileti döngüsünün izlenecek basit bir protokolü tanımlayan <xref:System.Windows.Interop.ComponentDispatcher> sınıfını sağlar.  
  
 <xref:System.Windows.Interop.ComponentDispatcher>, birkaç üye sunan statik bir sınıftır. Her yöntemin kapsamı, çağıran iş parçacığına örtülü olarak bağlanır. Bir ileti döngüsü, bu API 'lerden bazılarını kritik zamanlarda çağırmalıdır (bir sonraki bölümde tanımlandığı gibi).  
  
 <xref:System.Windows.Interop.ComponentDispatcher>, diğer bileşenlerin (klavye havuzu gibi) dinleyebileceği olayları sağlar. <xref:System.Windows.Threading.Dispatcher> sınıfı uygun bir sırayla tüm uygun <xref:System.Windows.Interop.ComponentDispatcher> yöntemlerini çağırır. Kendi ileti döngünüzü uyguıyorsanız, kodunuz benzer bir şekilde <xref:System.Windows.Interop.ComponentDispatcher> Yöntemler çağrılmadan sorumludur.  
  
 <xref:System.Windows.Interop.ComponentDispatcher> yöntemlerinin bir iş parçacığında çağrılması, yalnızca o iş parçacığında kayıtlı olan olay işleyicilerini çağırır.  
  
## <a name="writing-message-loops"></a>Ileti döngüleri yazma  
 Aşağıda, kendi ileti döngünüzü yazarsanız kullanacağınız <xref:System.Windows.Interop.ComponentDispatcher> üyelerinin bir denetim listesi verilmiştir:  
  
- <xref:System.Windows.Interop.ComponentDispatcher.PushModal%2A>: ileti döngünüz, iş parçacığının kalıcı olduğunu göstermek için bunu çağırmalıdır.  
  
- <xref:System.Windows.Interop.ComponentDispatcher.PopModal%2A>: ileti döngünüz, iş parçacığının kalıcı olmayan olarak döndürüldüğünü göstermek için bunu çağırmalıdır.  
  
- <xref:System.Windows.Interop.ComponentDispatcher.RaiseIdle%2A>: ileti döngünüz, <xref:System.Windows.Interop.ComponentDispatcher> <xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle> olayını oluşturması gerektiğini belirtmek için bunu çağırmalıdır. <xref:System.Windows.Interop.ComponentDispatcher>, <xref:System.Windows.Interop.ComponentDispatcher.IsThreadModal%2A> `true`ise <xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle> yükseltmeyecektir, ancak ileti döngüleri, kalıcı durumundayken <xref:System.Windows.Interop.ComponentDispatcher.RaiseIdle%2A> yanıt veremese bile, <xref:System.Windows.Interop.ComponentDispatcher> çağırmayı tercih edebilir.  
  
- <xref:System.Windows.Interop.ComponentDispatcher.RaiseThreadMessage%2A>: ileti döngünüz, yeni bir iletinin kullanılabilir olduğunu göstermek için bunu çağırmalıdır. Dönüş değeri, <xref:System.Windows.Interop.ComponentDispatcher> olayına yönelik bir dinleyicinin iletiyi işlemediğini belirtir. <xref:System.Windows.Interop.ComponentDispatcher.RaiseThreadMessage%2A> `true` (işlenmiş) döndürürse, dağıtıcı iletiyle birlikte hiçbir şey yapmaz. Dönüş değeri `false`ise, Dispatcher 'ın Win32 işlev `TranslateMessage`çağırması beklenir ve ardından `DispatchMessage`çağırır.  
  
## <a name="using-componentdispatcher-and-existing-message-handling"></a>ComponentDispatcher ve mevcut Ileti Işlemeyi kullanma  
 Aşağıda, devralınan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ileti döngüsüne güveniyorsanız kullanacağınız <xref:System.Windows.Interop.ComponentDispatcher> üyelerinin bir denetim listesi verilmiştir.  
  
- <xref:System.Windows.Interop.ComponentDispatcher.IsThreadModal%2A>: uygulamanın kalıcı olup olmadığını döndürür (örneğin, bir kalıcı ileti döngüsü itilmiş). <xref:System.Windows.Interop.ComponentDispatcher> bu durumu izleyebilir, çünkü sınıfı ileti döngüsünden bir <xref:System.Windows.Interop.ComponentDispatcher.PushModal%2A> ve <xref:System.Windows.Interop.ComponentDispatcher.PopModal%2A> çağrıları tutar.  
  
- <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage> ve <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage> olayları, temsilci etkinleştirmeleri için standart kuralları izler. Temsilciler belirtilmemiş bir düzende çağrılır ve ilki iletiyi işlenmiş olarak işaretlese bile tüm temsilciler çağrılır.  
  
- <xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle>: boşta işleme (iş parçacığı için başka bir bekleyen ileti yoktur) için uygun ve verimli bir zaman gösterir. iş parçacığı kalıcı ise <xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle> oluşturulmaz.  
  
- <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage>: ileti göndericisinin işlediği tüm iletiler için oluşturuldu.  
  
- <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage>: <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage>sırasında işlenmemiş tüm iletiler için oluşturuldu.  
  
 <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage> olayı veya <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage> olayından sonra, olay verilerinde başvuruya göre geçirilen `handled` parametresi `true`olduğunda bir ileti işlenir. `handled` `true`olduğunda olay işleyicileri iletiyi yoksaymalıdır çünkü bu, önce farklı işleyicinin iletiyi işlediği anlamına gelir. Her iki olaya yönelik olay işleyicileri iletiyi değiştirebilir. Dağıtıcı değiştirilmiş iletiyi göndermeli ve özgün değiştirilmemiş iletiyi almalıdır. <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage> tüm dinleyicilerine teslim edilir, ancak mimari amaç yalnızca, hedeflenen iletilerin iletiye yanıt olarak kodu çağırması gereken HWND 'yi içeren en üst düzey pencere olur.  
  
## <a name="how-hwndsource-treats-componentdispatcher-events"></a>HwndSource ComponentDispatcher olaylarını nasıl değerlendirir  
 <xref:System.Windows.Interop.HwndSource> üst düzey bir pencere (üst HWND olmadan) ise, <xref:System.Windows.Interop.ComponentDispatcher>kaydedilir. <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage> harekete geçirilir ve ileti <xref:System.Windows.Interop.HwndSource> veya alt pencereler için tasarlanıyorsa, <xref:System.Windows.Interop.HwndSource> <xref:System.Windows.Interop.HwndSource.System%23Windows%23Interop%23IKeyboardInputSink%23TranslateAccelerator%2A>, <xref:System.Windows.Interop.IKeyboardInputSink.TranslateChar%2A><xref:System.Windows.Interop.IKeyboardInputSink.OnMnemonic%2A> klavye havuz sırasını çağırır.  
  
 <xref:System.Windows.Interop.HwndSource> en üst düzey bir pencere (üst HWND) değilse, hiçbir işleme uygulanmaz. Yalnızca üst düzey pencerenin işleme yapması beklenir ve birlikte çalışabilirlik senaryosunun parçası olarak klavye havuzu desteğiyle bir üst düzey pencere olması beklenir.  
  
 Bir <xref:System.Windows.Interop.HwndSource> üzerinde <xref:System.Windows.Interop.HwndHost.WndProc%2A>, ilk Çağrılmakta olan uygun bir klavye havuzu yöntemi olmadan çağrılırsa, uygulamanız <xref:System.Windows.UIElement.KeyDown>gibi daha üst düzey klavye olaylarını alır. Ancak, erişim anahtarı desteği gibi istenen klavye giriş modeli özelliklerini atladan klavye havuzu yöntemleri çağrılmaz. Bu durum ileti döngüsünün <xref:System.Windows.Interop.ComponentDispatcher>ilgili iş parçacığını doğru bir şekilde bilgilendirmediği veya üst HWND doğru klavye havuzu yanıtlarını çağırmadığı için meydana gelebilir.  
  
 <xref:System.Windows.Interop.HwndSource.AddHook%2A> yöntemi kullanılarak bu ileti için kancalar eklediyseniz, klavye havuzuna giden bir ileti HWND 'ye gönderilmeyebilir. İleti, ileti göndericisi düzeyinde doğrudan işlenmiş ve `DispatchMessage` işlevine gönderilmemiş olabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Interop.ComponentDispatcher>
- <xref:System.Windows.Interop.IKeyboardInputSink>
- [WPF ve Win32 Birlikte Çalışması](wpf-and-win32-interoperation.md)
- [İş Parçacığı Modeli](threading-model.md)
- [Girişe Genel Bakış](input-overview.md)
