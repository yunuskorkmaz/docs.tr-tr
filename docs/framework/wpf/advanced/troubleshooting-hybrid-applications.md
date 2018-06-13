---
title: Karma Uygulama Sorunlarını Giderme
ms.date: 03/30/2017
helpviewer_keywords:
- overlapping controls [WPF]
- Windows Forms [WPF], interoperability with
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
- hybrid applications [WPF interoperability]
- message loops [WPF]
ms.assetid: f440c23f-fa5d-4d5a-852f-ba61150e6405
ms.openlocfilehash: 878761c030d4950e53ee24b76f7e29101584143a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33549039"
---
# <a name="troubleshooting-hybrid-applications"></a>Karma Uygulama Sorunlarını Giderme
<a name="introduction"></a> Bu konuda, hem kullanan karma uygulamalar yazarken oluşabilecek bazı yaygın sorunlar listelenmiştir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] teknolojileri.  
  

  
<a name="overlapping_controls"></a>   
## <a name="overlapping-controls"></a>Çakışma denetimleri  
 Beklediğiniz gibi denetimleri çakışmaması. [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Her denetim için ayrı bir HWND kullanır. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir sayfadaki tüm içerik için bir HWND kullanır. Bu uygulama farkı beklenmeyen çakışan davranışlarına neden olur.  
  
 A [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetiminde barındırılan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] her zaman üstünde görünür [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriği.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] İçerik barındırılan bir <xref:System.Windows.Forms.Integration.ElementHost> denetimi görünür z-sıralamasını <xref:System.Windows.Forms.Integration.ElementHost> denetim. Üst üste mümkündür <xref:System.Windows.Forms.Integration.ElementHost> denetimleri ancak barındırılan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik bırakmaz birleştirin veya etkileşim.  
  
<a name="child_property"></a>   
## <a name="child-property"></a>Alt özelliği  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> Ve <xref:System.Windows.Forms.Integration.ElementHost> sınıfları, yalnızca bir tek alt denetim veya öğeyi barındırabilir. Birden fazla denetim veya öğeyi barındırmak için alt içeriği olarak bir kapsayıcı kullanmanız gerekir. Örneğin, ekleyebilirsiniz [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] düğme ve onay kutusu denetimleri için bir <xref:System.Windows.Forms.Panel?displayProperty=nameWithType> denetlemek ve paneline atayın bir <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetimin <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A> özelliği. Ancak, düğme ve onay kutusu denetimleri ayrı olarak aynı ekleyemezsiniz <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetim.  
  
<a name="scaling"></a>   
## <a name="scaling"></a>ölçeklendirme  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] farklı ölçekleme modelleri vardır. Bazı [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ölçekleme dönüşümleri için anlamlı [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimleri ancak diğerleri değildir. Örneğin, ölçekleme bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimini 0 çalışır, ancak aynı denetimi sıfır olmayan bir değer geri ölçeklendirmeye çalışırsanız, denetimin boyutu 0 olarak kalır. Daha fazla bilgi için bkz: [yerleşim konuları WindowsFormsHost Öğesi için](../../../../docs/framework/wpf/advanced/layout-considerations-for-the-windowsformshost-element.md).  
  
<a name="adapter"></a>   
## <a name="adapter"></a>Bağdaştırıcı  
 Çalışırken karışıklığı olabilir <xref:System.Windows.Forms.Integration.WindowsFormsHost> ve <xref:System.Windows.Forms.Integration.ElementHost> gizli bir kapsayıcıya içerdiğinden sınıfları. Hem <xref:System.Windows.Forms.Integration.WindowsFormsHost> ve <xref:System.Windows.Forms.Integration.ElementHost> sınıfları adlı gizli bir kapsayıcıya sahip bir *bağdaştırıcısı*, içeriği barındırmak için kullanın. İçin <xref:System.Windows.Forms.Integration.WindowsFormsHost> bağdaştırıcı öğesinden türer <xref:System.Windows.Forms.ContainerControl?displayProperty=nameWithType> sınıfı. İçin <xref:System.Windows.Forms.Integration.ElementHost> bağdaştırıcı denetimi türer <xref:System.Windows.Controls.DockPanel> öğesi. Diğer birlikte çalışılabilirlik konularında bağdaştırıcıya başvurular gördüğünüzde, bu ne açıklanan kapsayıcıdır.  
  
<a name="nesting"></a>   
## <a name="nesting"></a>İç içe geçme  
 İç içe bir <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğe içinde bir <xref:System.Windows.Forms.Integration.ElementHost> denetim desteklenmiyor. İç içe bir <xref:System.Windows.Forms.Integration.ElementHost> içinde denetleyen bir <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi de desteklenmez.  
  
<a name="focus"></a>   
## <a name="focus"></a>Odağı  
 Odağı içinde farklı çalışır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)], bir karma uygulamada oluşabileceği sorunları odaklanan anlamına gelir. İçinde odağınız varsa, örneğin, bir <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi ve ya da en aza indirmek ve sayfayı geri yüklemek veya bir modal iletişim kutusunu göster, içindeki odak <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi kaybolabilir. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğesi hala odağa sahip, ancak bunun içindeki denetim olmayabilir.  
  
 Veri doğrulama da odak tarafından etkilenir. Doğrulama çalışır bir <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi, ancak çalışmıyor dışı sekme olarak <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi, iki farklı arasında veya <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğeleri.  
  
<a name="property_mapping"></a>   
## <a name="property-mapping"></a>Özellik eşlemesi  
 Bazı özellik eşlemeleri farklı uygulamalar arasında köprü için kapsamlı yorumlama gerektirir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] teknolojileri. Özellik eşlemeleri yazı tiplerini, renk ve diğer özellikleri değişikliklere tepki vermek kodunuzu etkinleştirin. Özellik eşlemeleri için dinleme tarafından genel olarak, çalışma *özelliği*değişti olayları veya*özelliği*çağrı ve alt denetim veya onun bağdaştırıcısı üzerindeki uygun özellikleri ayarlayarak değiştirildi. Daha fazla bilgi için bkz: [Windows Forms ve WPF özellik eşlemesi](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md).  
  
<a name="layoutrelated_properties_on_hosted_content"></a>   
## <a name="layout-related-properties-on-hosted-content"></a>Barındırılan içerik üzerinde düzeni ilgili Özellikler  
 Zaman <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A?displayProperty=nameWithType> veya <xref:System.Windows.Forms.Integration.ElementHost.Child%2A?displayProperty=nameWithType> özelliği atandığında, barındırılan içerik düzeni ile ilgili çeşitli özelliklerini otomatik olarak ayarlanır. Bu içerik özelliklerini değiştirmek, beklenmeyen Düzen davranışlarına neden olabilir.  
  
 Barındırılan içeriğiniz doldurmak için yerleştirilir <xref:System.Windows.Forms.Integration.WindowsFormsHost> ve <xref:System.Windows.Forms.Integration.ElementHost> üst. Bu dolgu davranışını etkinleştirmek için alt özelliğini ayarladığınızda çeşitli özellikler ayarlanır. Aşağıdaki tablo, içerik özellikleri tarafından belirlenen listeleri <xref:System.Windows.Forms.Integration.ElementHost> ve <xref:System.Windows.Forms.Integration.WindowsFormsHost> sınıfları.  
  
|Ana sınıf|İçerik özellikleri|  
|----------------|------------------------|  
|<xref:System.Windows.Forms.Integration.ElementHost>|<xref:System.Windows.FrameworkElement.Height%2A><br /><br /> <xref:System.Windows.FrameworkElement.Width%2A><br /><br /> <xref:System.Windows.FrameworkElement.Margin%2A><br /><br /> <xref:System.Windows.FrameworkElement.VerticalAlignment%2A><br /><br /> <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>|  
|<xref:System.Windows.Forms.Integration.WindowsFormsHost>|<xref:System.Windows.Forms.Control.Margin%2A><br /><br /> <xref:System.Windows.Forms.Control.Dock%2A><br /><br /> <xref:System.Windows.Forms.Control.AutoSize%2A><br /><br /> <xref:System.Windows.Forms.Control.Location%2A><br /><br /> <xref:System.Windows.Forms.Control.MaximumSize%2A>|  
  
 Bu özellikler doğrudan barındırılan içerik üzerinde ayarlı değil. Daha fazla bilgi için bkz: [yerleşim konuları WindowsFormsHost Öğesi için](../../../../docs/framework/wpf/advanced/layout-considerations-for-the-windowsformshost-element.md).  
  
<a name="navigation_applications"></a>   
## <a name="navigation-applications"></a>Gezinti uygulamaları  
 Gezinti uygulamaları kullanıcı durumunu korumak değil. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğesi bir gezinti uygulamasında kullanıldığında denetimlerini yeniden oluşturur. Alt denetimler yeniden kullanıcı barındıran sayfadan gittiğinde oluşur <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesini ve ardından döndürür. İçinde kullanıcı tarafından yazılan herhangi bir içerik kaybolur.  
  
<a name="message_loop_interoperation"></a>   
## <a name="message-loop-interoperation"></a>İleti döngüsü birlikte çalışma  
 İle çalışırken [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] beklendiği gibi ileti döngüleri, iletileri işlenmeyebilir. <xref:System.Windows.Forms.Integration.WindowsFormsHost.EnableWindowsFormsInterop%2A> Yöntemi çağrılır <xref:System.Windows.Forms.Integration.WindowsFormsHost> Oluşturucusu. Bu yöntem bir ileti filtresi ekler [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ileti döngüsü. Bu filtre çağırır <xref:System.Windows.Forms.Control.PreProcessMessage%2A?displayProperty=nameWithType> yöntemi, bir <xref:System.Windows.Forms.Control?displayProperty=nameWithType> ileti hedefi ve iletiyi çevirir/gönderir.  
  
 Gösteriyorsa, bir <xref:System.Windows.Window> içinde bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ileti döngüsü ile <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType>, çağırmanız sürece hiçbir şey yazamazsınız <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A> yöntemi. <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A> Metodu bir <xref:System.Windows.Window> ve ekleyen bir <xref:System.Windows.Forms.IMessageFilter?displayProperty=nameWithType>, anahtarı ilgili iletileri, yeniden yönlendirmeler [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ileti döngüsü. Daha fazla bilgi için bkz: [Windows Forms ve WPF birlikte çalışabilirlik giriş mimarisi](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-interoperability-input-architecture.md).  
  
<a name="opacity_and_layering"></a>   
## <a name="opacity-and-layering"></a>Saydamlık ve katmanlama  
 <xref:System.Windows.Interop.HwndHost> Sınıfı katmanlamayı desteklemez. Bu ayarı yani <xref:System.Windows.UIElement.Opacity%2A> özelliği <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi hiçbir etkisi ve hiç karışım diğer meydana gelir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] olan windows <xref:System.Windows.Window.AllowsTransparency%2A> kümesine `true`.  
  
<a name="dispose"></a>   
## <a name="dispose"></a>Dispose  
 Sınıfları düzgün atma değil, kaynakları sızıntısı. Karma uygulamalarınızı olduğundan emin olun <xref:System.Windows.Forms.Integration.WindowsFormsHost> ve <xref:System.Windows.Forms.Integration.ElementHost> sınıfları atıldı veya kaynakları sızıntısı. [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] siler <xref:System.Windows.Forms.Integration.ElementHost> ne zaman denetimleri kalıcı olmayan <xref:System.Windows.Forms.Form> üst kapanır. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] siler <xref:System.Windows.Forms.Integration.WindowsFormsHost> uygulamanız kapandığında. Göstermek olası bir <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesinde bir <xref:System.Windows.Window> içinde bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ileti döngüsü. Bu durumda, kodunuzu uygulamanızı kapatılıyor uyarı almayabilir.  
  
<a name="enabling_visual_styles"></a>   
## <a name="enabling-visual-styles"></a>Görsel stiller etkinleştirme  
 [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] görsel stilleri bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimi etkinleştirilmemiş olabilir. <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> Yöntemi için şablon olarak adlandırılan bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] uygulama. Bu yöntemi kullanırsanız, varsayılan olarak, çağrılmaz rağmen [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] bir proje oluşturmak için hatalarla [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] görsel stilleri denetimleri için sürüm 6.0 Comctl32.dll varsa. Çağırmalısınız <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> yöntemi işleyiciler iş parçacığı üzerinde oluşturulmadan önce. Daha fazla bilgi için bkz: [nasıl yapılır: görsel stiller etkinleştirmek karma uygulamada](../../../../docs/framework/wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md).  
  
<a name="licensed_controls"></a>   
## <a name="licensed-controls"></a>Lisanslı Denetimler  
 Lisanslı [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] lisans bilgileri kullanıcıya bir ileti kutusu görüntüler denetimleri karma uygulama için beklenmeyen davranışlara neden olabilir. Bazı lisanslı denetimler oluşturma işlemeye yanıt olarak bir iletişim kutusunu görüntüleyin. Örneğin, lisanslı denetim kullanıcının bir lisansı gereklidir veya kullanıcının üç denetim deneme kullanımlarını kalan olduğunu bildirebilir.  
  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğesi türer <xref:System.Windows.Interop.HwndHost> sınıfı ve alt denetimin işleyicisi içinde oluşturulur <xref:System.Windows.Forms.Integration.WindowsFormsHost.BuildWindowCore%2A> yöntemi. <xref:System.Windows.Interop.HwndHost> Sınıfı iletileri işlenmesine izin verme <xref:System.Windows.Forms.Integration.WindowsFormsHost.BuildWindowCore%2A> yöntemi, ancak bir iletişim kutusunu görüntüleme ileti gönderilmesine neden olur. Bu lisans senaryosunu etkinleştirmek için arama <xref:System.Windows.Forms.Control.CreateControl%2A?displayProperty=nameWithType> yöntemi olarak atamadan önce denetimindeki <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğenin alt.  
  
<a name="wpf_designer"></a>   
## <a name="wpf-designer"></a>WPF Tasarımcısı  
 Kullanarak WPF içeriğinizi tasarlayabilirsiniz [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)]. Aşağıdaki bölümlerde ile karma uygulamalar yazarken oluşabilecek bazı yaygın sorunlar listesinde [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].  
  
### <a name="backcolortransparent-is-ignored-at-design-time"></a>Tasarım zamanında BackColorTransparent yok sayılır.  
 <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> Özelliği tasarım zamanında beklendiği gibi çalışmayabilir.  
  
 WPF denetimi görünür bir üst öğe üzerinde değilse, WPF çalışma zamanı yoksayar <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> değeri. Bunun nedeni, <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> göz ardı çünkü <xref:System.Windows.Forms.Integration.ElementHost> nesne ayrı bir oluşturulur <xref:System.AppDomain>. Ancak, uygulama çalıştırıldığında <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> beklendiği gibi çalışmıyor.  
  
### <a name="design-time-error-list-appears-when-the-obj-folder-is-deleted"></a>Obj klasörü silindiğinde tasarım zamanı hata listesi görünür  
 Obj klasörü silinirse, tasarım zamanı hata listesi görüntülenir.  
  
 Kullanarak tasarladığınızda <xref:System.Windows.Forms.Integration.ElementHost>, projenizin obj klasöründeki Debug veya Release klasöründeki oluşturulmuş dosyaları Windows Form Tasarımcısı kullanır. Bu dosyaları silerseniz, tasarım zamanı hata listesi görüntülenir. Bu sorunu gidermek için projenizi yeniden derleyin. Daha fazla bilgi için bkz: [Windows Formları tasarımcısında tasarım zamanı hataları](../../../../docs/framework/winforms/controls/design-time-errors-in-the-windows-forms-designer.md).  
  
<a name="elementhost_and_ime"></a>   
## <a name="elementhost-and-ime"></a>ElementHost ve IME  
 WPF denetimleri barındırılan bir <xref:System.Windows.Forms.Integration.ElementHost> şu anda desteklemediği <xref:System.Windows.Forms.Control.ImeMode%2A> özelliği. Değişikliklerini <xref:System.Windows.Forms.Control.ImeMode%2A> barındırılan denetimler tarafından göz ardı edilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [WPF Tasarımcısı'nda birlikte çalışabilirlik](http://msdn.microsoft.com/library/2cb7c1ca-2a75-463b-8801-fba81e2b7042)  
 [Windows Forms ve WPF Birlikte Çalışabilirlik Giriş Mimarisi](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-interoperability-input-architecture.md)  
 [Nasıl yapılır: Karma Uygulamada Görsel Stilleri Etkinleştirme](../../../../docs/framework/wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md)  
 [WindowsFormsHost Öğesi için Düzen Konusunda Dikkat Edilmesi Gereken Noktalar](../../../../docs/framework/wpf/advanced/layout-considerations-for-the-windowsformshost-element.md)  
 [Windows Forms ve WPF Özelliğini Eşleme](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md)  
 [Windows Forms Tasarımcısında Tasarım Zamanı Hataları](../../../../docs/framework/winforms/controls/design-time-errors-in-the-windows-forms-designer.md)  
 [Geçiş ve Birlikte Çalışabilirlik](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)
