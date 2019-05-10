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
ms.openlocfilehash: 10c3ced3bc69f12c107b8d49139f829fab4e312a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662218"
---
# <a name="windows-forms-and-wpf-interoperability-input-architecture"></a>Windows Forms ve WPF Birlikte Çalışabilirlik Giriş Mimarisi
Arasındaki birlikte çalışabilirlik [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hem teknolojiler uygun klavye giriş işleme sahip olmasını gerektirir. Bu konuda, bu teknolojiler, klavye ve karma uygulamalarda kesintisiz birlikte çalışabilirliği etkinleştirmek için işlenen ileti nasıl uygulamak açıklanmaktadır.  
  
 Bu konu aşağıdaki alt bölümleri içerir:  
  
- Kalıcı olmayan formlar ve iletişim kutuları  
  
- WindowsFormsHost Klavyesi ve ileti işleme  
  
- ElementHost Klavyesi ve ileti işleme  
  
## <a name="modeless-forms-and-dialog-boxes"></a>Kalıcı olmayan formlar ve iletişim kutuları  
 Çağrı <xref:System.Windows.Forms.Integration.WindowsFormsHost.EnableWindowsFormsInterop%2A> metodunda <xref:System.Windows.Forms.Integration.WindowsFormsHost> kalıcı olmayan bir form veya iletişim kutusunu açmak için öğe bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-tabanlı bir uygulama.  
  
 Çağrı <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A> metodunda <xref:System.Windows.Forms.Integration.ElementHost> bir geçici açmak için Denetim [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sayfasını bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]-tabanlı bir uygulama.  
  
## <a name="windowsformshost-keyboard-and-message-processing"></a>WindowsFormsHost Klavyesi ve ileti işleme  
 Tarafından barındırılan bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-tabanlı uygulama [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] klavye ve ileti işleme aşağıdakilerden oluşur:  
  
- <xref:System.Windows.Forms.Integration.WindowsFormsHost> Sınıfı gelen iletileri alır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tarafından uygulanan ileti döngüsü <xref:System.Windows.Interop.ComponentDispatcher> sınıfı.  
  
- <xref:System.Windows.Forms.Integration.WindowsFormsHost> Sınıfı oluşturur, bir vekil [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] sıradan emin olmak için ileti döngüsü [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] klavye işleme gerçekleşir.  
  
- <xref:System.Windows.Forms.Integration.WindowsFormsHost> Sınıfının Implements <xref:System.Windows.Interop.IKeyboardInputSink> odak yönetimi ile koordine etmek için arabirim [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
- <xref:System.Windows.Forms.Integration.WindowsFormsHost> Denetimleri kendilerini ve kendi ileti döngüleri başlatır.  
  
 Aşağıdaki bölümlerde bu parçaları işlem daha ayrıntılı açıklanmaktadır.  
  
### <a name="acquiring-messages-from-the-wpf-message-loop"></a>WPF ileti döngüsü gelen iletileri alma  
 <xref:System.Windows.Interop.ComponentDispatcher> Sınıfın uyguladığı ileti döngüsü Yöneticisi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. <xref:System.Windows.Interop.ComponentDispatcher> SAX önce Filtre iletileri dış istemcilere sağlamak kancaları [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] işler.  
  
 Birlikte çalışabilirlik uygulaması işler <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=nameWithType> sağlayan olay [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] önce iletileri işlemek için denetimleri [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrol eder.  
  
### <a name="surrogate-windows-forms-message-loop"></a>Vekil Windows Forms ileti döngüsü  
 Varsayılan olarak, <xref:System.Windows.Forms.Application?displayProperty=nameWithType> sınıfı içeren birincil ileti döngüsü için [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] uygulamalar. Birlikte çalışabilirlik sırasında [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ileti döngüsü iletileri işlemez. Bu nedenle, bu mantık üretilmelidir. İşleyici için <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=nameWithType> olay aşağıdaki adımları gerçekleştirir:  
  
1. Bir iletiyi kullanarak filtreler <xref:System.Windows.Forms.IMessageFilter> arabirimi.  
  
2. Çağrıları <xref:System.Windows.Forms.Control.PreProcessMessage%2A?displayProperty=nameWithType> yöntemi.  
  
3. Çevirir ve gerekirse ileti gönderir.  
  
4. İletiyi başka denetimler işlemezse barındırma denetimine ileti geçirir.  
  
### <a name="ikeyboardinputsink-implementation"></a>IKeyboardInputSink Uygulaması  
 Yedek ileti döngüsü klavye management işler. Bu nedenle, <xref:System.Windows.Interop.IKeyboardInputSink.TabInto%2A?displayProperty=nameWithType> yöntemdir yalnızca <xref:System.Windows.Interop.IKeyboardInputSink> uygulama gerektiren üye <xref:System.Windows.Forms.Integration.WindowsFormsHost> sınıfı.  
  
 Varsayılan olarak, <xref:System.Windows.Interop.HwndHost> sınıfı döndürür `false` için kendi <xref:System.Windows.Interop.HwndHost.System%23Windows%23Interop%23IKeyboardInputSink%23TabInto%2A> uygulaması. Bu denetiminden engelleyen bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimi bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimi.  
  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> Uygulaması <xref:System.Windows.Interop.IKeyboardInputSink.TabInto%2A?displayProperty=nameWithType> yöntemi aşağıdaki adımları gerçekleştirir:  
  
1. Bulduğu ilk veya son [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] tarafından bulunan denetim <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetimi odak alabilir. Denetim seçim geçişi bilgilere bağlıdır.  
  
2. Odağı denetimi için ayarlar ve döndürür `true`.  
  
3. Hiçbir denetim odağı alırsanız döndürür `false`.  
  
### <a name="windowsformshost-registration"></a>WindowsFormsHost kayıt  
 Zaman penceresi işlemek için bir <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetimi oluşturulur, <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetimi ileti döngüsü için kendi durum kaydeden bir iç statik yöntemini çağırır.  
  
 Kayıt sırasında <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetimi ileti döngüsü inceler. İleti döngüsünden başlatılmadı ise <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=nameWithType> olay işleyicisi oluşturulur. İleti döngüsünden çalışır durumda kabul <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=nameWithType> olay işleyicisi eklenir.  
  
 Pencere tanıtıcısı yok edildiğinde, <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetim kendisini kaydından kaldırır.  
  
## <a name="elementhost-keyboard-and-message-processing"></a>ElementHost Klavyesi ve ileti işleme  
 Tarafından barındırılan bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] uygulama [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] klavye ve ileti işleme aşağıdakilerden oluşur:  
  
- <xref:System.Windows.Interop.HwndSource>, <xref:System.Windows.Interop.IKeyboardInputSink>, ve <xref:System.Windows.Interop.IKeyboardInputSite> arabirimi uygulamaları.  
  
- Sekme ve ok tuşları.  
  
- Komut anahtarları ve iletişim kutusunu anahtarları.  
  
- [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hızlandırıcı işleme.  
  
 Aşağıdaki bölümlerde bu bölümlerinde daha ayrıntılı açıklanmaktadır.  
  
### <a name="interface-implementations"></a>Arabirim uygulamaları  
 İçinde [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)], klavye iletileri odaklanmış denetimi için Pencere işleyicisi yönlendirilir. İçinde <xref:System.Windows.Forms.Integration.ElementHost> denetimi, bu iletileri barındırılan öğenin yönlendirilir. Bunu gerçekleştirmek için <xref:System.Windows.Forms.Integration.ElementHost> denetim sağlayan bir <xref:System.Windows.Interop.HwndSource> örneği. Varsa <xref:System.Windows.Forms.Integration.ElementHost> denetim odağa, <xref:System.Windows.Interop.HwndSource> örneği tarafından işlenebilir böylece çoğu klavye yönlendiren [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.InputManager> sınıfı.  
  
 <xref:System.Windows.Interop.HwndSource> Sınıfının Implements <xref:System.Windows.Interop.IKeyboardInputSink> ve <xref:System.Windows.Interop.IKeyboardInputSite> arabirimleri.  
  
 Klavye ile birlikte çalışabilirlik kullanır uygulamaya <xref:System.Windows.Interop.IKeyboardInputSite.OnNoMoreTabStops%2A> tanıtıcı SEKME tuşunu veya ok yönteme anahtar barındırılan öğeler dışında odak giriş.  
  
### <a name="tabbing-and-arrow-keys"></a>Tabbing ve ok tuşları  
 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Seçim mantığını eşlenmiş durumda <xref:System.Windows.Interop.HwndSource.System%23Windows%23Interop%23IKeyboardInputSink%23TabInto%2A> ve <xref:System.Windows.Interop.IKeyboardInputSite.OnNoMoreTabStops%2A> Gezinti SEKMESİ ve ok uygulamaya yönelik yöntemleri anahtar. Geçersiz kılma <xref:System.Windows.Forms.Integration.ElementHost.Select%2A> yöntemi bu eşlemeyi gerçekleştirir.  
  
### <a name="command-keys-and-dialog-box-keys"></a>Komut anahtarlar ve iletişim kutusunu anahtarlar  
 Vermek [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ilk komut anahtarları ve iletişim anahtarlarını işleme olanağı [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] komut ön işleme bağlı olduğu <xref:System.Windows.Interop.IKeyboardInputSink.TranslateAccelerator%2A> yöntemi. Geçersiz kılma <xref:System.Windows.Forms.Control.ProcessCmdKey%2A?displayProperty=nameWithType> yöntemi iki teknolojiyi bağlar.  
  
 İle <xref:System.Windows.Interop.IKeyboardInputSink.TranslateAccelerator%2A> yöntemi, barındırılan öğelerini WM_KEYDOWN, WM_KEYUP, WM_SYSKEYDOWN veya SEKMESİNDE, ENTER, ESC ve ok tuşları gibi komut anahtarları dahil olmak üzere, WM_SYSKEYUP gibi herhangi bir anahtar ileti işleyebilir. Anahtar ileti işlenmezse gönderilmeden [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hiyerarşiye işleme.  
  
### <a name="accelerator-processing"></a>Hızlandırıcı işleme  
 Hızlandırıcıları doğru bir şekilde işlemek için [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hızlandırıcı işleme bağlı, için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.AccessKeyManager> sınıfı. Ayrıca, tüm WM_CHAR iletileri barındırılan öğelerine doğru yönlendirilmelidir.  
  
 Çünkü varsayılan <xref:System.Windows.Interop.HwndSource> uygulaması <xref:System.Windows.Interop.IKeyboardInputSink.TranslateChar%2A> yöntemi döndürür `false`, WM_CHAR iletileri, aşağıdaki mantık kullanılarak işlenir:  
  
- <xref:System.Windows.Forms.Control.IsInputChar%2A?displayProperty=nameWithType> Yöntemi geçersiz kılınmıştır barındırılan öğelerine tüm WM_CHAR iletileri iletilen emin olmak için.  
  
- ALT tuşuna basıldığında, ileti WM_SYSCHAR'dır. [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Bu iletiyi üzerinden önişle değil <xref:System.Windows.Forms.Control.IsInputChar%2A> yöntemi. Bu nedenle, <xref:System.Windows.Forms.Control.ProcessMnemonic%2A> yöntemi geçersiz kılınmıştır Sorgulanacak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.AccessKeyManager> kayıtlı Hızlandırıcı için. Kayıtlı bir Hızlandırıcı bulunursa <xref:System.Windows.Input.AccessKeyManager> işler.  
  
- ALT tuşunu basılı değilse, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.InputManager> sınıfı işlenmemiş giriş işler. Giriş bir Hızlandırıcı ise <xref:System.Windows.Input.AccessKeyManager> işler. <xref:System.Windows.Input.InputManager.PostProcessInput> Olayı işlenmemiş olan WM_CHAR iletileri için işlenir.  
  
 Kullanıcı ALT tuşuna bastığında Hızlandırıcı görsel ipuçları tüm form üzerinde gösterilmektedir. Bu davranışı destekleyen tüm <xref:System.Windows.Forms.Integration.ElementHost> active form üzerinde denetimleri bağımsız olarak, Denetim odağa WM_SYSKEYDOWN iletileri alırsınız.  
  
 İletileri yalnızca gönderildiği <xref:System.Windows.Forms.Integration.ElementHost> etkin formdaki denetimleri.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Integration.WindowsFormsHost.EnableWindowsFormsInterop%2A>
- <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A>
- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [İzlenecek yol: WPF'de Windows Forms bileşik denetimini barındırma](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [İzlenecek yol: WPF bileşik denetimini Windows Forms içinde barındırma](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [WPF ve Win32 Birlikte Çalışması](wpf-and-win32-interoperation.md)
