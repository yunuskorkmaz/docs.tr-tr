---
title: Windows Forms ve WPF birlikte çalışma giriş mimarisi
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- input architecture [WPF interoperability]
- messages [WPF]
- Windows Forms [WPF], interoperability with
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
- modeless forms [WPF]
- ElementHost keyboard and messages [WPF]
- keyboard interoperation [WPF]
- WindowsFormsHost keyboard and messages [WPF]
- modeless dialog boxes [WPF]
ms.assetid: 0eb6f137-f088-4c5e-9e37-f96afd28f235
ms.openlocfilehash: 1c7027947d24c847ee298022344e02ce0bbff764
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794087"
---
# <a name="windows-forms-and-wpf-interoperability-input-architecture"></a>Windows Forms ve WPF Birlikte Çalışabilirlik Giriş Mimarisi
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve Windows Forms arasında birlikte çalışabilirlik, her iki teknolojinin de uygun klavye girişi işlemesine sahip olmasını gerektirir. Bu konuda, bu teknolojilerin karma uygulamalarda sorunsuz birlikte çalışabilirliği etkinleştirmek için klavye ve ileti işleme nasıl uygulandığı açıklanmaktadır.  
  
 Bu konu, aşağıdaki alt bölümleri içerir:  
  
- Modsuz formlar ve Iletişim kutuları  
  
- WindowsFormsHost klavye ve Ileti Işleme  
  
- ElementHost Klavye ve Ileti Işleme  
  
## <a name="modeless-forms-and-dialog-boxes"></a>Modsuz formlar ve Iletişim kutuları  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]tabanlı bir uygulamadan kalıcı olmayan bir form veya iletişim kutusu açmak için <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesindeki <xref:System.Windows.Forms.Integration.WindowsFormsHost.EnableWindowsFormsInterop%2A> yöntemi çağırın.  
  
 Windows Forms tabanlı bir uygulamada kalıcı olmayan bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sayfası açmak için <xref:System.Windows.Forms.Integration.ElementHost> denetimindeki <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A> yöntemi çağırın.  
  
## <a name="windowsformshost-keyboard-and-message-processing"></a>WindowsFormsHost klavye ve Ileti Işleme  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]tabanlı bir uygulama tarafından barındırıldığında klavye ve ileti işleme Windows Forms aşağıdakilerden oluşur:  
  
- <xref:System.Windows.Forms.Integration.WindowsFormsHost> sınıfı, <xref:System.Windows.Interop.ComponentDispatcher> sınıfı tarafından uygulanan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ileti döngüsünden gelen iletileri alır.  
  
- <xref:System.Windows.Forms.Integration.WindowsFormsHost> sınıfı, sıradan Windows Forms klavye işlemenin gerçekleşmesini sağlamak için bir yedek Windows Forms ileti döngüsü oluşturur.  
  
- <xref:System.Windows.Forms.Integration.WindowsFormsHost> sınıfı, odak yönetimini [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]koordine etmek için <xref:System.Windows.Interop.IKeyboardInputSink> arabirimini uygular.  
  
- <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetimleri kendilerini kaydeder ve ileti döngülerini başlatır.  
  
 Aşağıdaki bölümlerde işlemin bu bölümleri daha ayrıntılı olarak açıklanır.  
  
### <a name="acquiring-messages-from-the-wpf-message-loop"></a>WPF Ileti döngüsünden Iletiler alınıyor  
 <xref:System.Windows.Interop.ComponentDispatcher> sınıfı, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]için ileti döngüsü yöneticisini uygular. <xref:System.Windows.Interop.ComponentDispatcher> sınıfı, dış istemcilerin iletileri işleyerek önce iletileri filtrelemesine olanak tanımak için kancalar sağlar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Birlikte çalışabilirlik uygulama, Windows Forms denetimlerinin [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimleri yapmadan önce iletileri işlemesini sağlayan <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=nameWithType> olayını işler.  
  
### <a name="surrogate-windows-forms-message-loop"></a>Vekil Windows Forms Ileti döngüsü  
 Varsayılan olarak, <xref:System.Windows.Forms.Application?displayProperty=nameWithType> sınıfı Windows Forms uygulamalar için birincil ileti döngüsünü içerir. Birlikte çalışma sırasında Windows Forms ileti döngüsü iletileri işlemez. Bu nedenle, bu mantığın yeniden oluşturulması gerekir. <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=nameWithType> olay işleyicisi aşağıdaki adımları gerçekleştirir:  
  
1. <xref:System.Windows.Forms.IMessageFilter> arabirimini kullanarak iletiyi filtreler.  
  
2. <xref:System.Windows.Forms.Control.PreProcessMessage%2A?displayProperty=nameWithType> yöntemini çağırır.  
  
3. Gerekiyorsa iletiyi çevirir ve dağıtır.  
  
4. İletiyi hiçbir başka denetim işleirse barındırma denetimine geçirir.  
  
### <a name="ikeyboardinputsink-implementation"></a>IKeyboardInputSink uygulaması  
 Vekil ileti döngüsü, klavye yönetimini işler. Bu nedenle, <xref:System.Windows.Interop.IKeyboardInputSink.TabInto%2A?displayProperty=nameWithType> yöntemi <xref:System.Windows.Forms.Integration.WindowsFormsHost> sınıfında bir uygulama gerektiren tek <xref:System.Windows.Interop.IKeyboardInputSink> üyesidir.  
  
 Varsayılan olarak, <xref:System.Windows.Interop.HwndHost> sınıfı <xref:System.Windows.Interop.HwndHost.System%23Windows%23Interop%23IKeyboardInputSink%23TabInto%2A> uygulamasının `false` döndürür. Bu, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetiminden Windows Forms denetimine kadar sekmeye engel olur.  
  
 <xref:System.Windows.Interop.IKeyboardInputSink.TabInto%2A?displayProperty=nameWithType> yönteminin <xref:System.Windows.Forms.Integration.WindowsFormsHost> uygulanması aşağıdaki adımları gerçekleştirir:  
  
1. <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetiminin içerdiği ve odak alabilen ilk veya son Windows Forms denetimini bulur. Denetim seçimi çapraz geçiş bilgilerine bağlıdır.  
  
2. Odağı denetime ayarlar ve `true`döndürür.  
  
3. Hiçbir denetim odağı alamıyorsa, `false`döndürür.  
  
### <a name="windowsformshost-registration"></a>WindowsFormsHost kaydı  
 Bir <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetimine pencere tutamacı oluşturulduğunda, <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetimi ileti döngüsünün varlığını kaydeden bir iç statik yöntemi çağırır.  
  
 Kayıt sırasında, <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetimi ileti döngüsünü inceler. İleti döngüsü başlatılmamışsa <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=nameWithType> olay işleyicisi oluşturulur. İleti döngüsü, <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=nameWithType> olay işleyicisi eklendiğinde çalışıyor olarak kabul edilir.  
  
 Pencere tanıtıcısı yok edildiğinde, <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetimi kendisini kayıttan kaldırır.  
  
## <a name="elementhost-keyboard-and-message-processing"></a>ElementHost Klavye ve Ileti Işleme  
 Windows Forms bir uygulama tarafından barındırıldığında klavye ve ileti işleme [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aşağıdakilerden oluşur:  
  
- <xref:System.Windows.Interop.HwndSource>, <xref:System.Windows.Interop.IKeyboardInputSink>ve <xref:System.Windows.Interop.IKeyboardInputSite> arabirim uygulamaları.  
  
- Sekme ve ok tuşları.  
  
- Komut tuşları ve iletişim kutusu anahtarları.  
  
- Hızlandırıcı işleme Windows Forms.  
  
 Aşağıdaki bölümlerde bu parçalar daha ayrıntılı olarak açıklanır.  
  
### <a name="interface-implementations"></a>Arabirim Uygulamaları  
 Windows Forms, klavye iletileri odağa sahip olan denetimin pencere tanıtıcısına yönlendirilir. <xref:System.Windows.Forms.Integration.ElementHost> denetiminde, bu iletiler barındırılan öğeye yönlendirilir. Bunu gerçekleştirmek için <xref:System.Windows.Forms.Integration.ElementHost> denetimi <xref:System.Windows.Interop.HwndSource> bir örnek sağlar. <xref:System.Windows.Forms.Integration.ElementHost> denetimi odağa sahipse, <xref:System.Windows.Interop.HwndSource> örneği çoğu klavye girişini [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.InputManager> sınıfı tarafından işlenebilmesi için yönlendirir.  
  
 <xref:System.Windows.Interop.HwndSource> sınıfı <xref:System.Windows.Interop.IKeyboardInputSink> ve <xref:System.Windows.Interop.IKeyboardInputSite> arabirimlerini uygular.  
  
 Klavye birlikte çalışma, odağı barındırılan öğelerin dışına kayan TAB tuşu ve ok tuşu girişini işlemek için <xref:System.Windows.Interop.IKeyboardInputSite.OnNoMoreTabStops%2A> yöntemini uygulamaya dayanır.  
  
### <a name="tabbing-and-arrow-keys"></a>Sekme ve ok tuşları  
 Windows Forms seçim mantığı, sekme ve ok tuşu gezintisi uygulamak için <xref:System.Windows.Interop.HwndSource.System%23Windows%23Interop%23IKeyboardInputSink%23TabInto%2A> ve <xref:System.Windows.Interop.IKeyboardInputSite.OnNoMoreTabStops%2A> yöntemlerine eşlenir. <xref:System.Windows.Forms.Integration.ElementHost.Select%2A> yöntemi geçersiz kılmak bu eşlemeyi gerçekleştirir.  
  
### <a name="command-keys-and-dialog-box-keys"></a>Komut tuşları ve Iletişim kutusu anahtarları  
 Komut anahtarlarını ve iletişim anahtarlarını işlemek için ilk fırsatı [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vermek için, Windows Forms komut ön işlemesi <xref:System.Windows.Interop.IKeyboardInputSink.TranslateAccelerator%2A> yöntemine bağlanır. <xref:System.Windows.Forms.Control.ProcessCmdKey%2A?displayProperty=nameWithType> yöntemi geçersiz kılındığında iki teknoloji bağlanır.  
  
 <xref:System.Windows.Interop.IKeyboardInputSink.TranslateAccelerator%2A> yöntemiyle barındırılan öğeler, sekme, ENTER, ESC ve ok tuşları gibi komut tuşları da dahil olmak üzere WM_KEYDOWN, WM_KEYUP, WM_SYSKEYDOWN veya WM_SYSKEYUP gibi herhangi bir anahtar iletisi işleyebilir. Bir anahtar ileti işlenmezse, işleme için Windows Forms üst hiyerarşisi gönderilir.  
  
### <a name="accelerator-processing"></a>Hızlandırıcı Işleme  
 Hızlandırıcıyı doğru bir şekilde işlemek için Windows Forms hızlandırıcı işleme [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.AccessKeyManager> sınıfına bağlanmalıdır. Ayrıca, tüm WM_CHAR iletileri barındırılan öğelere doğru şekilde yönlendirilmelidir.  
  
 <xref:System.Windows.Interop.IKeyboardInputSink.TranslateChar%2A> yönteminin varsayılan <xref:System.Windows.Interop.HwndSource> uygulanması `false`döndürdüğünden WM_CHAR iletileri aşağıdaki mantık kullanılarak işlenir:  
  
- Tüm WM_CHAR iletilerinin barındırılan öğelere iletilmesini sağlamak için <xref:System.Windows.Forms.Control.IsInputChar%2A?displayProperty=nameWithType> yöntemi geçersiz kılınır.  
  
- ALT tuşuna basıldığında ileti WM_SYSCHAR. Windows Forms, bu iletiyi <xref:System.Windows.Forms.Control.IsInputChar%2A> yöntemi aracılığıyla önceden işlemez. Bu nedenle <xref:System.Windows.Forms.Control.ProcessMnemonic%2A> yöntemi, kayıtlı bir hızlandırıcının [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.AccessKeyManager> sorgulamak için geçersiz kılınır. Kayıtlı bir hızlandırıcı bulunursa <xref:System.Windows.Input.AccessKeyManager> işler.  
  
- ALT tuşuna basılsa, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.InputManager> sınıfı işlenmemiş girişi işler. Giriş bir Hızlandırıcı ise, <xref:System.Windows.Input.AccessKeyManager> onu işler. <xref:System.Windows.Input.InputManager.PostProcessInput> olay işlenmemiş WM_CHAR iletiler için işlenir.  
  
 Kullanıcı ALT tuşuna bastığında Hızlandırıcı görsel ipuçları formun tamamına gösterilir. Bu davranışı desteklemek için, etkin formdaki tüm <xref:System.Windows.Forms.Integration.ElementHost> denetimleri, hangi denetimin odağa bakılmaksızın WM_SYSKEYDOWN iletileri alır.  
  
 Mesajlar yalnızca etkin formdaki <xref:System.Windows.Forms.Integration.ElementHost> denetimlerine gönderilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Integration.WindowsFormsHost.EnableWindowsFormsInterop%2A>
- <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A>
- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [İzlenecek yol: WPF'de Windows Forms Bileşik Denetimini Barındırma](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [İzlenecek yol: WPF Bileşik Denetimini Windows Forms İçinde Barındırma](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [WPF ve Win32 Birlikte Çalışması](wpf-and-win32-interoperation.md)
