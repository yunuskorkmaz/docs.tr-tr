---
title: Windows Forms ve WPF Birlikte Çalışabilirlik Giriş Mimarisi
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
ms.openlocfilehash: 250f34e3e5420a613bc7b1035c62af90665e71ee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33549065"
---
# <a name="windows-forms-and-wpf-interoperability-input-architecture"></a>Windows Forms ve WPF Birlikte Çalışabilirlik Giriş Mimarisi
Arasındaki birlikte çalışabilirlik [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] her iki teknolojinin uygun klavye giriş işlemesine sahip olmasını gerektirir. Bu konu, klavye ve ileti karma uygulamalarında sorunsuz birlikte çalışabilirliği sağlamak için işleme bu teknolojilerin nasıl uygulamak açıklar.  
  
 Bu konu, aşağıdaki alt bölümleri içerir:  
  
-   Kalıcı olmayan formlar ve iletişim kutuları  
  
-   WindowsFormsHost Klavye ve ileti işleme  
  
-   ElementHost klavye ve ileti işleme  
  
## <a name="modeless-forms-and-dialog-boxes"></a>Kalıcı olmayan formlar ve iletişim kutuları  
 Çağrı <xref:System.Windows.Forms.Integration.WindowsFormsHost.EnableWindowsFormsInterop%2A> yöntemi <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesinin kalıcı olmayan bir form veya iletişim kutusunu açmak için bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-tabanlı.  
  
 Çağrı <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A> yöntemi <xref:System.Windows.Forms.Integration.ElementHost> bir geçici açmak için Denetim [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sayfasındaki bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]-tabanlı.  
  
## <a name="windowsformshost-keyboard-and-message-processing"></a>WindowsFormsHost Klavye ve ileti işleme  
 Tarafından barındırılan bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-tabanlı uygulama [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] klavye ve ileti işleme aşağıdakilerden oluşur:  
  
-   <xref:System.Windows.Forms.Integration.WindowsFormsHost> Sınıfı gelen iletileri alır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tarafından uygulanan ileti döngüsü <xref:System.Windows.Interop.ComponentDispatcher> sınıfı.  
  
-   <xref:System.Windows.Forms.Integration.WindowsFormsHost> Sınıfı bir yedek oluşturur [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] sıradan emin olmak için ileti döngüsü [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] klavye işleme oluşur.  
  
-   <xref:System.Windows.Forms.Integration.WindowsFormsHost> Uygulayan sınıf <xref:System.Windows.Interop.IKeyboardInputSink> ile odak yönetimini koordine etmek için arabirim [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
-   <xref:System.Windows.Forms.Integration.WindowsFormsHost> Denetimleri kendilerini ve kendi ileti döngüleri başlatır.  
  
 Aşağıdaki bölümlerde bu işlem daha ayrıntılı bölümlerini açıklanmaktadır.  
  
### <a name="acquiring-messages-from-the-wpf-message-loop"></a>WPF ileti döngüsü gelen iletileri alma  
 <xref:System.Windows.Interop.ComponentDispatcher> Sınıfı için ileti döngü yöneticisini uygulayan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. <xref:System.Windows.Interop.ComponentDispatcher> SAX önce iletilerine filtre uygulamak için dış istemcileri etkinleştirmek için kancalar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bunları işler.  
  
 Birlikte çalışabilirlik uygulaması işler <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=nameWithType> sağlayan olay [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] önce iletileri işlemek için denetimleri [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrol eder.  
  
### <a name="surrogate-windows-forms-message-loop"></a>Yedek Windows Forms ileti döngüsü  
 Varsayılan olarak, <xref:System.Windows.Forms.Application?displayProperty=nameWithType> sınıfı için birincil ileti döngüsü içerir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] uygulamalar. Birlikte çalışma sırasında [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ileti döngüsü iletilerini işlemez. Bu nedenle, bu mantığı üretilmelidir. İşleyici için <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=nameWithType> olay aşağıdaki adımları gerçekleştirir:  
  
1.  İletiyi kullanarak filtreler <xref:System.Windows.Forms.IMessageFilter> arabirimi.  
  
2.  Çağrıları <xref:System.Windows.Forms.Control.PreProcessMessage%2A?displayProperty=nameWithType> yöntemi.  
  
3.  Çevirir ve gerekli olduğunda ileti gönderir.  
  
4.  Başka denetimler iletiyi işlemezse iletiyi barındırma denetimine geçirir.  
  
### <a name="ikeyboardinputsink-implementation"></a>IKeyboardInputSink Uygulaması  
 Yedek ileti döngüsü klavye yönetimini işler. Bu nedenle, <xref:System.Windows.Interop.IKeyboardInputSink.TabInto%2A?displayProperty=nameWithType> yöntemdir yalnızca <xref:System.Windows.Interop.IKeyboardInputSink> uygulama gerektiren üye <xref:System.Windows.Forms.Integration.WindowsFormsHost> sınıfı.  
  
 Varsayılan olarak, <xref:System.Windows.Interop.HwndHost> sınıf döndürür `false` için kendi <xref:System.Windows.Interop.HwndHost.System%23Windows%23Interop%23IKeyboardInputSink%23TabInto%2A> uygulaması. Bu denetiminden engelleyen bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimini bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetim.  
  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> Uyarlamasını <xref:System.Windows.Interop.IKeyboardInputSink.TabInto%2A?displayProperty=nameWithType> yöntemi aşağıdaki adımları gerçekleştirir:  
  
1.  İlk bulur veya son [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] tarafından bulunan denetim <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetimi ve, odak alabilir. Denetim seçim çapraz geçişi bilgilere bağlıdır.  
  
2.  Odağı denetimi için ayarlar ve döndürür `true`.  
  
3.  Hiçbir denetim odağı alırsanız döndürür `false`.  
  
### <a name="windowsformshost-registration"></a>WindowsFormsHost Kaydı  
 Ne zaman penceresi işlemek için bir <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetimi oluşturulur, <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetimi kendi durum ileti döngüsü için kaydeder bir iç statik yöntemini çağırır.  
  
 Kayıt sırasında <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetim ileti döngüsü inceler. İleti döngüsü başlatılmadı, <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=nameWithType> olay işleyicisi oluşturulur. İleti döngüsü çalışır durumda olduğu kabul edildiği <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=nameWithType> olay işleyicisi eklenmiş olmasıdır.  
  
 Pencere işleyicisi kaldırıldığı zaman <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetimi kendisini kayıttan kaldırır.  
  
## <a name="elementhost-keyboard-and-message-processing"></a>ElementHost klavye ve ileti işleme  
 Tarafından barındırılan bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] uygulama [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] klavye ve ileti işleme aşağıdakilerden oluşur:  
  
-   <xref:System.Windows.Interop.HwndSource>, <xref:System.Windows.Interop.IKeyboardInputSink>, ve <xref:System.Windows.Interop.IKeyboardInputSite> arabirimi uygulamaları.  
  
-   Sekme ve ok tuşları.  
  
-   Komut tuşları ve iletişim kutusunu anahtarları.  
  
-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hızlandırıcı işleme.  
  
 Aşağıdaki bölümlerde bu bölümleri daha ayrıntılı açıklanmıştır.  
  
### <a name="interface-implementations"></a>Arabirim uygulamaları  
 İçinde [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)], klavye iletileri odaklı denetimin pencere tanıtıcısı yönlendirilir. İçinde <xref:System.Windows.Forms.Integration.ElementHost> denetim bu iletileri barındırılan öğeye yönlendirilir. Bunu başarmak için <xref:System.Windows.Forms.Integration.ElementHost> denetim sağlayan bir <xref:System.Windows.Interop.HwndSource> örneği. Varsa <xref:System.Windows.Forms.Integration.ElementHost> denetimi odağa, <xref:System.Windows.Interop.HwndSource> örneği tarafından işlenebilir böylece çoğu klavye yönlendirir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.InputManager> sınıfı.  
  
 <xref:System.Windows.Interop.HwndSource> Uygulayan sınıf <xref:System.Windows.Interop.IKeyboardInputSink> ve <xref:System.Windows.Interop.IKeyboardInputSite> arabirimleri.  
  
 Klavye ile birlikte çalışabilirlik dayanır uygulanmasına <xref:System.Windows.Interop.IKeyboardInputSite.OnNoMoreTabStops%2A> tanıtıcı SEKME tuşuna ve ok yönteme odak barındırılan öğeleri dışında giriş anahtar.  
  
### <a name="tabbing-and-arrow-keys"></a>Tabbing ve ok tuşları  
 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Seçme mantığı eşleştirilir <xref:System.Windows.Interop.HwndSource.System%23Windows%23Interop%23IKeyboardInputSink%23TabInto%2A> ve <xref:System.Windows.Interop.IKeyboardInputSite.OnNoMoreTabStops%2A> sekme ve ok uygulamaya yönelik yöntemleri Gezinti anahtar. Geçersiz kılma <xref:System.Windows.Forms.Integration.ElementHost.Select%2A> yöntemi bu eşlemeyi gerçekleştirir.  
  
### <a name="command-keys-and-dialog-box-keys"></a>Komut anahtarlar ve iletişim kutusunu tuşları  
 Vermek için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] komut anahtarları ve iletişim anahtarlarını işlemek için ilk Fırsat [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] komutu ön işleme bağlı <xref:System.Windows.Interop.IKeyboardInputSink.TranslateAccelerator%2A> yöntemi. Geçersiz kılma <xref:System.Windows.Forms.Control.ProcessCmdKey%2A?displayProperty=nameWithType> yöntemi iki teknolojiyi bağlar.  
  
 İle <xref:System.Windows.Interop.IKeyboardInputSink.TranslateAccelerator%2A> yöntemi, barındırılan öğelerini WM_KEYDOWN, WM_KEYUP, WM_SYSKEYDOWN veya WM_SYSKEYUP, sekme, ENTER, ESC ve ok tuşları gibi komut anahtarları dahil olmak gibi herhangi bir anahtar iletisi işleyebilir. Anahtar ileti işlenmedi, gönderilmeden [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hiyerarşiye işleme.  
  
### <a name="accelerator-processing"></a>Hızlandırıcı işleme  
 Hızlandırıcıları doğru şekilde işlemek için [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hızlandırıcı işleme bağlı, için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.AccessKeyManager> sınıfı. Ayrıca, tüm WM_CHAR iletileri barındırılan öğelerine doğru yönlendirilmelidir.  
  
 Çünkü varsayılan <xref:System.Windows.Interop.HwndSource> uyarlamasını <xref:System.Windows.Interop.IKeyboardInputSink.TranslateChar%2A> yöntemi döndürür `false`, WM_CHAR iletileri aşağıdaki mantık kullanılarak işlenir:  
  
-   <xref:System.Windows.Forms.Control.IsInputChar%2A?displayProperty=nameWithType> Tüm WM_CHAR iletileri barındırılan öğeleri iletilen emin olmak için yöntem geçersiz.  
  
-   ALT tuşuna basılana, ileti WM_SYSCHAR'dır. [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Bu iletiyi üzerinden önişle değil <xref:System.Windows.Forms.Control.IsInputChar%2A> yöntemi. Bu nedenle, <xref:System.Windows.Forms.Control.ProcessMnemonic%2A> yöntemi geçersiz kılınmıştır sorguya [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.AccessKeyManager> kayıtlı Hızlandırıcı için. Kayıtlı Hızlandırıcı bulunursa, <xref:System.Windows.Input.AccessKeyManager> işler.  
  
-   ALT tuşuna basılı değilse, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.InputManager> sınıfı işlenmeyen girişi işler. Giriş bir kısayol tuşu ise <xref:System.Windows.Input.AccessKeyManager> işler. <xref:System.Windows.Input.InputManager.PostProcessInput> Olayı işlenmemiş olan WM_CHAR iletileri için işlenir.  
  
 Kullanıcı ALT tuşuna bastığında Hızlandırıcı görsel ipuçları tüm form üzerinde gösterilir. Bu davranış desteklemek için tüm <xref:System.Windows.Forms.Integration.ElementHost> etkin form üzerinde denetimleri denetim bağımsız olarak odağa sahip WM_SYSKEYDOWN iletileri alır.  
  
 İletileri yalnızca gönderilir <xref:System.Windows.Forms.Integration.ElementHost> etkin formdaki denetimler.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost.EnableWindowsFormsInterop%2A>  
 <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [İzlenecek yol: WPF'de Windows Forms Bileşik Denetimini Barındırma](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [İzlenecek yol: WPF Bileşik Denetimini Windows Forms İçinde Barındırma](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)  
 [WPF ve Win32 Birlikte Çalışması](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)
