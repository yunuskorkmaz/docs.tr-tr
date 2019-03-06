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
ms.openlocfilehash: dbc70f58fddfad6e7e7271802b8b01d2b52ab25a
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57370104"
---
# <a name="troubleshooting-hybrid-applications"></a>Karma Uygulama Sorunlarını Giderme
<a name="introduction"></a> Bu konuda kullanan karma uygulamalar yazma olduğunda oluşabilecek bazı yaygın sorunlar listelenmiştir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] teknolojileri.  
  

  
<a name="overlapping_controls"></a>   
## <a name="overlapping-controls"></a>Örtüşen Denetimler  
 Beklediğiniz gibi denetimleri çakışmaması. [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Her denetim için ayrı bir HWND kullanır. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir sayfadaki tüm içerik için bir HWND kullanır. Bu uygulama farkı çakışan beklenmeyen davranışlara neden olur.  
  
 A [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetiminde barındırılan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] üst kısmındaki her zaman görünür [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriği.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] barındırılan içeriğin bir <xref:System.Windows.Forms.Integration.ElementHost> denetimi görünür z-sıralamasını <xref:System.Windows.Forms.Integration.ElementHost> denetimi. Üst üste mümkündür <xref:System.Windows.Forms.Integration.ElementHost> denetimleri ancak barındırılan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik birleşmez veya etkileşim.  
  
<a name="child_property"></a>   
## <a name="child-property"></a>Alt özellik  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> Ve <xref:System.Windows.Forms.Integration.ElementHost> sınıfları yalnızca tek bir alt denetimin veya öğeyi barındırabilir. Birden fazla denetim ya da öğe barındırmak için bir kapsayıcı alt içeriğin kullanmanız gerekir. Örneğin, ekleyebilirsiniz [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] düğmesi ve onay kutusu denetimleri için bir <xref:System.Windows.Forms.Panel?displayProperty=nameWithType> denetlemek ve panele atayın bir <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetimin <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A> özelliği. Ancak, düğme ve onay kutusu denetimleri ayrı olarak aynı ekleyemezsiniz <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetimi.  
  
<a name="scaling"></a>   
## <a name="scaling"></a>Ölçeklendirme  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] farklı ölçeklendirme modelleri vardır. Bazı [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ölçeklendirme dönüştürmeleri için anlamlı [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimleri, ama sıklıkla başkalarını değildir. Örneğin, bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimini 0 çalışır, ancak aynı denetimi sıfır olmayan bir değere geri ölçeklendirme denerseniz, denetimin boyutu 0 olarak kalır. Daha fazla bilgi için [için WindowsFormsHost Öğesi düzeni etkenleri](layout-considerations-for-the-windowsformshost-element.md).  
  
<a name="adapter"></a>   
## <a name="adapter"></a>Bağdaştırıcı  
 Çalışırken karışıklık olabilir <xref:System.Windows.Forms.Integration.WindowsFormsHost> ve <xref:System.Windows.Forms.Integration.ElementHost> sınıfları çünkü gizli bir kapsayıcıya içerirler. Hem <xref:System.Windows.Forms.Integration.WindowsFormsHost> ve <xref:System.Windows.Forms.Integration.ElementHost> sınıfları adlı gizli bir kapsayıcıya sahip bir *bağdaştırıcısı*, içeriği barındırmak için kullandıkları. İçin <xref:System.Windows.Forms.Integration.WindowsFormsHost> bağdaştırıcısı öğesi türetilir <xref:System.Windows.Forms.ContainerControl?displayProperty=nameWithType> sınıfı. İçin <xref:System.Windows.Forms.Integration.ElementHost> bağdaştırıcısı denetimi türetilir <xref:System.Windows.Controls.DockPanel> öğesi. Birlikte çalışabilirlik diğer konu başlıklarında bağdaştırıcıya başvurular gördüğünüzde bu açıklanan kapsayıcıdır.  
  
<a name="nesting"></a>   
## <a name="nesting"></a>İç içe geçirme  
 İç içe bir <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi içinde bir <xref:System.Windows.Forms.Integration.ElementHost> denetimi desteklenmiyor. İç içe bir <xref:System.Windows.Forms.Integration.ElementHost> içinde denetleyen bir <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi de desteklenmez.  
  
<a name="focus"></a>   
## <a name="focus"></a>Odağı  
 Odak içinde farklı çalışır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)], bir karma uygulama sorunlarını odaklanmak anlamına meydana gelebilir. Örneğin, odak içinde varsa bir <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi ve ya da en aza indirmek ve sayfasını geri yüklemek veya bir kalıcı iletişim kutusunu göster, içindeki odak <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi kaybolabilir. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğesine odak yine de sahip, ancak denetimin içindeki olmayabilir.  
  
 Veri doğrulama odak tarafından da etkilenir. Doğrulama çalışır bir <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi, ancak çalışmıyor tanesi sekme olarak <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi veya iki farklı arasında <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğeleri.  
  
<a name="property_mapping"></a>   
## <a name="property-mapping"></a>Özellik eşleme  
 Farklı uygulamalar arasında köprü oluşturulacağını kapsamlı yorumlama bazı özellik eşlemeleri gerektirir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] teknolojileri. Özellik eşlemeleri yazı tiplerini, renkleri ve diğer özellikleri değişikliklere tepki vermek kodunuzu etkinleştirin. Genel olarak, özellik eşlemeleri için dinleyerek çalışır *özelliği*değişti olayları veya*özelliği*çağrıları ve alt denetim veya onun bağdaştırıcısı uygun özelliklerde ayarı değiştirildi. Daha fazla bilgi için [Windows Forms ve WPF özelliğini eşleme](windows-forms-and-wpf-property-mapping.md).  
  
<a name="layoutrelated_properties_on_hosted_content"></a>   
## <a name="layout-related-properties-on-hosted-content"></a>Barındırılan içerik Düzenle ilgili özellikleri  
 Zaman <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A?displayProperty=nameWithType> veya <xref:System.Windows.Forms.Integration.ElementHost.Child%2A?displayProperty=nameWithType> özelliği atandığında, barındırılan içerik Düzenle ilgili çeşitli özelliklerini otomatik olarak ayarlanır. Bu içerik özelliklerini değiştirme Düzen beklenmeyen davranışlara neden olabilir.  
  
 Barındırılan içerik doldurmak için yerleştirildiğini <xref:System.Windows.Forms.Integration.WindowsFormsHost> ve <xref:System.Windows.Forms.Integration.ElementHost> üst. Alt özellik ayarladığınızda bu doldurma davranışı etkinleştirmek için çeşitli özellikler ayarlanır. Aşağıdaki tablo, içerik özellikleri tarafından ayarlanan listeleri <xref:System.Windows.Forms.Integration.ElementHost> ve <xref:System.Windows.Forms.Integration.WindowsFormsHost> sınıfları.  
  
|Konak sınıfı|İçerik özellikleri|  
|----------------|------------------------|  
|<xref:System.Windows.Forms.Integration.ElementHost>|<xref:System.Windows.FrameworkElement.Height%2A><br /><br /> <xref:System.Windows.FrameworkElement.Width%2A><br /><br /> <xref:System.Windows.FrameworkElement.Margin%2A><br /><br /> <xref:System.Windows.FrameworkElement.VerticalAlignment%2A><br /><br /> <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>|  
|<xref:System.Windows.Forms.Integration.WindowsFormsHost>|<xref:System.Windows.Forms.Control.Margin%2A><br /><br /> <xref:System.Windows.Forms.Control.Dock%2A><br /><br /> <xref:System.Windows.Forms.Control.AutoSize%2A><br /><br /> <xref:System.Windows.Forms.Control.Location%2A><br /><br /> <xref:System.Windows.Forms.Control.MaximumSize%2A>|  
  
 Bu özellikler, doğrudan barındırılan içerik üzerinde ayarlı değil. Daha fazla bilgi için [için WindowsFormsHost Öğesi düzeni etkenleri](layout-considerations-for-the-windowsformshost-element.md).  
  
<a name="navigation_applications"></a>   
## <a name="navigation-applications"></a>Gezinti uygulamaları  
 Gezinti uygulamalar kullanıcı durumunu korumak değil. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğesi içinde bir gezinti uygulaması kullanıldığında denetimlerini yeniden oluşturur. Kullanıcı sayfasını barındıran uzağa gittiğinde oluşur alt denetimlerini yeniden <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesini ve ardından döner. İçinde kullanıcı tarafından yazılan herhangi bir içeriği kaybolacak.  
  
<a name="message_loop_interoperation"></a>   
## <a name="message-loop-interoperation"></a>İleti döngüsü birlikte çalışabilirlik  
 İle çalışırken [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] beklendiği gibi ileti döngüleri, iletileri işlenmeyebilir. <xref:System.Windows.Forms.Integration.WindowsFormsHost.EnableWindowsFormsInterop%2A> Yöntemi tarafından çağrılır <xref:System.Windows.Forms.Integration.WindowsFormsHost> Oluşturucusu. Bu yöntem bir ileti filtresi ekler [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ileti döngüsü. Bu filtre çağırır <xref:System.Windows.Forms.Control.PreProcessMessage%2A?displayProperty=nameWithType> yöntemi, bir <xref:System.Windows.Forms.Control?displayProperty=nameWithType> ileti hedefi ve/ileti gönderileri çevirir.  
  
 Gösteriyorsa, bir <xref:System.Windows.Window> içinde bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ileti döngüsü ile <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType>, çağırmanızı sürece hiçbir şey yazamazsınız <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A> yöntemi. <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A> Yöntemi bir <xref:System.Windows.Window> ve ekler bir <xref:System.Windows.Forms.IMessageFilter?displayProperty=nameWithType>, anahtar ilgili iletileri, yeniden yönlendirmeler [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ileti döngüsü. Daha fazla bilgi için [Windows Forms ve WPF birlikte çalışabilirlik giriş mimarisi](windows-forms-and-wpf-interoperability-input-architecture.md).  
  
<a name="opacity_and_layering"></a>   
## <a name="opacity-and-layering"></a>Saydamlık ve katmanlama  
 <xref:System.Windows.Interop.HwndHost> Sınıfı katmanlamayı desteklemez. Bu ayar başka bir deyişle <xref:System.Windows.UIElement.Opacity%2A> özelliği <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi hiçbir etkisi ve hiç karışım diğer meydana gelir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] olan windows <xref:System.Windows.Window.AllowsTransparency%2A> kümesine `true`.  
  
<a name="dispose"></a>   
## <a name="dispose"></a>Dispose  
 Sınıfları düzgün bir şekilde elden değil, kaynakları sızabilir. Karma uygulamalarınızı emin <xref:System.Windows.Forms.Integration.WindowsFormsHost> ve <xref:System.Windows.Forms.Integration.ElementHost> sınıfları kaldırıldıklarından veya kaynakları dışarıya sızmasına neden olabilecek. [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] siler <xref:System.Windows.Forms.Integration.ElementHost> ne zaman denetimleri kalıcı olmayan <xref:System.Windows.Forms.Form> üst kapatır. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] siler <xref:System.Windows.Forms.Integration.WindowsFormsHost> uygulamanız kapandığında. Gösterilecek mümkündür bir <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesinde bir <xref:System.Windows.Window> içinde bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ileti döngüsü. Bu durumda, kodunuzu, uygulamanızın kapatılıyor uyarı almayabilir.  
  
<a name="enabling_visual_styles"></a>   
## <a name="enabling-visual-styles"></a>Görsel stilleri etkinleştirme  
 [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] görsel stillerin bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimi etkinleştirilmemiş olabilir. <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> Şablonunda yöntemi çağrıldığında bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] uygulama. Bu yöntemi kullanırsanız, varsayılan olarak, çağrılmaz ancak [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] bir proje oluşturmak için erişmenizi sağlayacak [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] Comctl32.dll sürüm 6.0 varsa denetimler için görsel stilleri. Çağırmalısınız <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> işleyiciler iş parçacığı üzerinde oluşturulmadan önce yöntemi. Daha fazla bilgi için [nasıl yapılır: Karma uygulamada görsel stilleri etkinleştirme](how-to-enable-visual-styles-in-a-hybrid-application.md).  
  
<a name="licensed_controls"></a>   
## <a name="licensed-controls"></a>Lisanslı Denetimler  
 Lisanslı [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kullanıcıya bir ileti kutusunda lisans bilgilerini görüntüleyen denetimler için bir karma uygulama beklenmeyen davranışlara neden olabilir. Bazı lisanslı denetimler oluşturma işlemek için yanıt olarak bir iletişim kutusunu görüntüleyin. Örneğin, lisanslı bir denetim kullanıcının bir lisansı gereklidir ve kullanıcının denetimin deneme kullandığı kalan üç olduğunu bildirebilir.  
  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğesi türetilir <xref:System.Windows.Interop.HwndHost> sınıfı ve alt denetimin işleyicisi içinde oluşturulur <xref:System.Windows.Forms.Integration.WindowsFormsHost.BuildWindowCore%2A> yöntemi. <xref:System.Windows.Interop.HwndHost> Sınıf, işlenecek iletilerin izin vermiyor <xref:System.Windows.Forms.Integration.WindowsFormsHost.BuildWindowCore%2A> yöntemi, ancak bir iletişim kutusunu görüntüleme gönderilecek iletilerin neden olur. Lisans bu senaryoyu etkinleştirmek için çağrı <xref:System.Windows.Forms.Control.CreateControl%2A?displayProperty=nameWithType> yöntemi olarak atamadan önce denetimi <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğenin alt.  
  
<a name="wpf_designer"></a>   
## <a name="wpf-designer"></a>WPF Tasarımcısı  
 WPF İçerik kullanarak tasarlayabilirsiniz [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)]. Aşağıdaki bölümlerde ile karma uygulamalar yazma olduğunda oluşabilecek bazı yaygın sorunlar listesinde [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].  
  
### <a name="backcolortransparent-is-ignored-at-design-time"></a>Tasarım zamanında BackColorTransparent yok sayılır.  
 <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> Özellik tasarım zamanında beklendiği gibi çalışmayabilir.  
  
 Bir WPF denetiminde görünür bir üst öğe üzerinde değilse, WPF çalışma zamanı yok sayar <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> değeri. Bunun nedeni, <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> göz ardı çünkü <xref:System.Windows.Forms.Integration.ElementHost> ayrı bir nesne oluşturulur <xref:System.AppDomain>. Ancak, uygulama çalıştırıldığında <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> beklendiği gibi çalışmıyor.  
  
### <a name="design-time-error-list-appears-when-the-obj-folder-is-deleted"></a>Obj klasörü silindiğinde tasarım zamanı hata listesi görünür.  
 Obj klasörü silinirse, tasarım zamanı hata listesi görüntülenir.  
  
 Kullanarak tasarlarken <xref:System.Windows.Forms.Integration.ElementHost>, Windows Form Tasarımcısı hata ayıklama veya sürüm klasöründeki projenizin obj klasörü içinde oluşturulan dosyaları kullanır. Bu dosyaları silerseniz, tasarım zamanı hata listesi görüntülenir. Bu sorunu gidermek için projenizi yeniden derleyin. Daha fazla bilgi için [Windows Forms tasarımcısında tasarım zamanı hataları](../../winforms/controls/design-time-errors-in-the-windows-forms-designer.md).  
  
<a name="elementhost_and_ime"></a>   
## <a name="elementhost-and-ime"></a>ElementHost ve IME  
 WPF denetimleri barındırılan bir <xref:System.Windows.Forms.Integration.ElementHost> şu anda desteklemediği <xref:System.Windows.Forms.Control.ImeMode%2A> özelliği. Değişikliklerini <xref:System.Windows.Forms.Control.ImeMode%2A> barındırılan denetimler tarafından göz ardı edilir.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [WPF Tasarımcısı'nda birlikte çalışabilirlik](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb628658(v=vs.100))
- [Windows Forms ve WPF Birlikte Çalışabilirlik Giriş Mimarisi](windows-forms-and-wpf-interoperability-input-architecture.md)
- [Nasıl yapılır: Karma uygulamada görsel stilleri etkinleştirme](how-to-enable-visual-styles-in-a-hybrid-application.md)
- [WindowsFormsHost Öğesi için Düzen Konusunda Dikkat Edilmesi Gereken Noktalar](layout-considerations-for-the-windowsformshost-element.md)
- [Windows Forms ve WPF Özelliğini Eşleme](windows-forms-and-wpf-property-mapping.md)
- [Windows Forms Tasarımcısında Tasarım Zamanı Hataları](../../winforms/controls/design-time-errors-in-the-windows-forms-designer.md)
- [Geçiş ve Birlikte Çalışabilirlik](migration-and-interoperability.md)
