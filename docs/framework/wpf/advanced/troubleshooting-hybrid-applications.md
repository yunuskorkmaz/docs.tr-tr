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
ms.openlocfilehash: 46d8f00f9328e9c0a4df596b709195ae42d651bf
ms.sourcegitcommit: 42ed59871db1f29a32b3d8e7abeb20e6eceeda7c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74960122"
---
# <a name="troubleshooting-hybrid-applications"></a>Karma Uygulama Sorunlarını Giderme
<a name="introduction"></a>Bu konuda, hem [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hem de [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] teknolojilerini kullanan karma uygulamalar yazarken oluşabilecek bazı yaygın sorunlar listelenmektedir.  

<a name="overlapping_controls"></a>   
## <a name="overlapping-controls"></a>Çakışan denetimler  
 Denetimler, bekledikleri gibi çakışmayabilir. [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] her denetim için ayrı bir HWND kullanır. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sayfadaki tüm içerikler için bir HWND kullanır. Bu uygulama farkı, beklenmeyen çakışan davranışlara neden olur.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] barındırılan [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimi her zaman [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriğinin üstünde görünür.  
  
 <xref:System.Windows.Forms.Integration.ElementHost> denetiminde barındırılan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerikler <xref:System.Windows.Forms.Integration.ElementHost> denetimin z düzeninde görüntülenir. <xref:System.Windows.Forms.Integration.ElementHost> denetimlerinin örtüşmesi mümkündür, ancak barındırılan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriği birleştirmez veya etkileşime almaz.  
  
<a name="child_property"></a>   
## <a name="child-property"></a>Alt özellik  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> ve <xref:System.Windows.Forms.Integration.ElementHost> sınıfları yalnızca tek bir alt denetim veya öğe barındırabilir. Birden fazla denetimi veya öğeyi barındırmak için alt içerik olarak bir kapsayıcı kullanmanız gerekir. Örneğin, bir <xref:System.Windows.Forms.Panel?displayProperty=nameWithType> denetimine [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] düğme ve onay kutusu denetimleri ekleyebilir ve sonra paneli bir <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetiminin <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A> özelliğine atayabilirsiniz. Ancak, düğme ve onay kutusu denetimlerini aynı <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetimine ayrı olarak ekleyemezsiniz.  
  
<a name="scaling"></a>   
## <a name="scaling"></a>Ölçeklendirme  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] farklı ölçekleme modellerine sahiptir. Bazı [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ölçeklendirme dönüştürmeleri [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimlerine göre anlamlıdır, ancak diğerleri değildir. Örneğin, bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimini 0 olarak ölçeklendirmeye çalışır, ancak aynı denetimi sıfır olmayan bir değere ölçeklendirmeye çalışırsanız, denetimin boyutu 0 kalır. Daha fazla bilgi için bkz. [WindowsFormsHost öğesi Için düzen konuları](layout-considerations-for-the-windowsformshost-element.md).  
  
<a name="adapter"></a>   
## <a name="adapter"></a>Bağdaştırıcı  
 Gizli bir kapsayıcı içerdiğinden <xref:System.Windows.Forms.Integration.WindowsFormsHost> ve <xref:System.Windows.Forms.Integration.ElementHost> sınıfları çalışırken karışıklığa neden olabilir. <xref:System.Windows.Forms.Integration.WindowsFormsHost> ve <xref:System.Windows.Forms.Integration.ElementHost> sınıflarının her ikisi de, içerik barındırmak için kullandıkları *Bağdaştırıcı*olarak adlandırılan gizli bir kapsayıcıya sahiptir. <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi için, bağdaştırıcı <xref:System.Windows.Forms.ContainerControl?displayProperty=nameWithType> sınıfından türetilir. <xref:System.Windows.Forms.Integration.ElementHost> denetimi için, bağdaştırıcı <xref:System.Windows.Controls.DockPanel> öğesinden türetilir. Diğer birlikte çalışabilirlik konularında bağdaştırıcıya yönelik başvuruları gördüğünüzde, bu kapsayıcı ele alınmıştır.  
  
<a name="nesting"></a>   
## <a name="nesting"></a>İç içe geçirme  
 Bir <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesinin <xref:System.Windows.Forms.Integration.ElementHost> denetimi içinde iç içe geçirilmesi desteklenmez. <xref:System.Windows.Forms.Integration.WindowsFormsHost> bir öğe içinde <xref:System.Windows.Forms.Integration.ElementHost> denetiminin iç içe geçirilmesi de desteklenmez.  
  
<a name="focus"></a>   
## <a name="focus"></a>Odaklanma  
 Odak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]farklı çalışır ve bu da odak sorunlarının karma bir uygulamada gerçekleşebileceği anlamına gelir. Örneğin, bir <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesinin içine odaklandıysanız ve sayfayı en aza indirip geri yükledikten veya kalıcı iletişim kutusunu gösterdiğinizde, <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesinin içine odak kaybolabilir. <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi hala odağa sahiptir ancak içindeki denetim bu olmayabilir.  
  
 Veri doğrulama de odaklanarak etkilenir. Doğrulama bir <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesinde çalışır, ancak <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğenin dışına veya iki farklı <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi arasında sekme olarak çalışmaz.  
  
<a name="property_mapping"></a>   
## <a name="property-mapping"></a>Özellik Eşleme  
 Bazı özellik eşlemeleri, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] teknolojileri arasında benzer uygulamaları köprülemek için kapsamlı bir yorum gerektirir. Özellik eşlemeleri, kodunuzun yazı tiplerinde, renklerde ve diğer özelliklerde yapılan değişikliklere tepki vermesini sağlar. Genel olarak özellik eşlemeleri, *özellik*değişmiş olayları ya da*özellik*değişmiş çağrıları dinleyerek ve alt denetimde veya bağdaştırıcısında uygun özellikleri ayarlayarak çalışır. Daha fazla bilgi için bkz. [Windows Forms ve WPF özellik eşleme](windows-forms-and-wpf-property-mapping.md).  
  
<a name="layoutrelated_properties_on_hosted_content"></a>   
## <a name="layout-related-properties-on-hosted-content"></a>Barındırılan Içerikte düzenle ilgili özellikler  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A?displayProperty=nameWithType> veya <xref:System.Windows.Forms.Integration.ElementHost.Child%2A?displayProperty=nameWithType> özelliği atandığında, barındırılan içerikteki bazı düzenle ilgili özellikler otomatik olarak ayarlanır. Bu içerik özelliklerini değiştirmek beklenmeyen düzen davranışlarına neden olabilir.  
  
 Barındırılan içeriğiniz <xref:System.Windows.Forms.Integration.WindowsFormsHost> ve üst <xref:System.Windows.Forms.Integration.ElementHost> dolduracak şekilde yerleştirildi. Bu Fill davranışını etkinleştirmek için, alt özelliği ayarladığınızda birçok özellik ayarlanır. Aşağıdaki tabloda, hangi içerik özelliklerinin <xref:System.Windows.Forms.Integration.ElementHost> ve <xref:System.Windows.Forms.Integration.WindowsFormsHost> sınıfları tarafından ayarlandığı listelenmektedir.  
  
|Ana bilgisayar sınıfı|İçerik özellikleri|  
|----------------|------------------------|  
|<xref:System.Windows.Forms.Integration.ElementHost>|<xref:System.Windows.FrameworkElement.Height%2A><br /><br /> <xref:System.Windows.FrameworkElement.Width%2A><br /><br /> <xref:System.Windows.FrameworkElement.Margin%2A><br /><br /> <xref:System.Windows.FrameworkElement.VerticalAlignment%2A><br /><br /> <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>|  
|<xref:System.Windows.Forms.Integration.WindowsFormsHost>|<xref:System.Windows.Forms.Control.Margin%2A><br /><br /> <xref:System.Windows.Forms.Control.Dock%2A><br /><br /> <xref:System.Windows.Forms.Control.AutoSize%2A><br /><br /> <xref:System.Windows.Forms.Control.Location%2A><br /><br /> <xref:System.Windows.Forms.Control.MaximumSize%2A>|  
  
 Bu özellikleri doğrudan barındırılan içerikte ayarlamayın. Daha fazla bilgi için bkz. [WindowsFormsHost öğesi Için düzen konuları](layout-considerations-for-the-windowsformshost-element.md).  
  
<a name="navigation_applications"></a>   
## <a name="navigation-applications"></a>Gezinti uygulamaları  
 Gezinti uygulamaları Kullanıcı durumunu koruyamayabilir. <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi, bir gezinti uygulamasında kullanıldığında denetimlerini yeniden oluşturur. Kullanıcı <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesini barındıran sayfadan uzaklaştığında alt denetimleri yeniden oluşturmak oluşur ve sonra buna geri döner. Kullanıcı tarafından yazılan içerikler kaybedilir.  
  
<a name="message_loop_interoperation"></a>   
## <a name="message-loop-interoperation"></a>İleti döngüsü birlikte çalışma  
 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ileti döngülerinde çalışırken, iletiler beklendiği gibi işlenmeyebilir. <xref:System.Windows.Forms.Integration.WindowsFormsHost.EnableWindowsFormsInterop%2A> yöntemi <xref:System.Windows.Forms.Integration.WindowsFormsHost> Oluşturucusu tarafından çağrılır. Bu yöntem [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ileti döngüsüne bir ileti filtresi ekler. Bu filtre, bir <xref:System.Windows.Forms.Control?displayProperty=nameWithType> iletinin hedefi ise ve iletiyi çevirdiğinde/dağıtırsa <xref:System.Windows.Forms.Control.PreProcessMessage%2A?displayProperty=nameWithType> yöntemini çağırır.  
  
 <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType>ile [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ileti döngüsünde bir <xref:System.Windows.Window> gösterdiğinizde, <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A> yöntemini çağırmadığınız takdirde hiçbir şey belirtemezsiniz. <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A> yöntemi bir <xref:System.Windows.Window> alır ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mesajı döngüsüne anahtarla ilgili iletileri reroutes <xref:System.Windows.Forms.IMessageFilter?displayProperty=nameWithType>ekler. Daha fazla bilgi için bkz. [Windows Forms ve WPF birlikte çalışabilirlik giriş mimarisi](windows-forms-and-wpf-interoperability-input-architecture.md).  
  
<a name="opacity_and_layering"></a>   
## <a name="opacity-and-layering"></a>Opaklık ve katmanlama  
 <xref:System.Windows.Interop.HwndHost> sınıfı katmanlanın desteklemez. Bu, <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesindeki <xref:System.Windows.UIElement.Opacity%2A> özelliğinin ayarının hiçbir etkisi olmadığı ve <xref:System.Windows.Window.AllowsTransparency%2A> `true`olarak ayarlanmış diğer [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pencereleri ile hiçbir karıştırma gerçekleşmeyeceği anlamına gelir.  
  
<a name="dispose"></a>   
## <a name="dispose"></a>'U  
 Sınıfların elden atılırken kaynakları sızmasını sağlayabilirsiniz. Karma uygulamalarınızda <xref:System.Windows.Forms.Integration.WindowsFormsHost> ve <xref:System.Windows.Forms.Integration.ElementHost> sınıflarının atıldığından emin olun ya da kaynakları sızdırabilirsiniz. kalıcı olmayan <xref:System.Windows.Forms.Form> üst öğesi kapandığında [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Integration.ElementHost> denetimleri ortadan kaldırıyor. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], uygulamanız kapandığında <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğeleri ortadan kaldırır. Bir <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesini bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ileti döngüsünde <xref:System.Windows.Window> göstermek mümkündür. Bu durumda, kodunuz uygulamanızın kapanmakta olduğu bildirimini alamayabilir.  
  
<a name="enabling_visual_styles"></a>   
## <a name="enabling-visual-styles"></a>Görsel stilleri etkinleştirme  
 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimindeki Microsoft Windows XP görsel stilleri etkinleştirilmemiş olabilir. <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> yöntemi [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] bir uygulama için şablonunda çağırılır. Bu yöntem varsayılan olarak çağrılmasa da, bir proje oluşturmak için Visual Studio kullanıyorsanız, Comctl32. dll 6,0 sürümü varsa, denetimler için Microsoft Windows XP görsel stilleri alırsınız. İş parçacığında tanıtıcıların oluşturulabilmesi için <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> yöntemini çağırmanız gerekir. Daha fazla bilgi için bkz. [nasıl yapılır: karma uygulamada görsel stilleri etkinleştirme](how-to-enable-visual-styles-in-a-hybrid-application.md).  
  
<a name="licensed_controls"></a>   
## <a name="licensed-controls"></a>Lisanslı denetimler  
 Lisans bilgilerini kullanıcıya bir ileti kutusunda görüntüleyen lisanslı [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimleri, karma uygulama için beklenmeyen davranışlara neden olabilir. Bazı lisanslı denetimler, oluşturma tanıtıcısının yanıt olarak bir iletişim kutusu gösterir. Örneğin, lisanslı bir denetim kullanıcıya bir lisansın gerekli olduğunu veya kullanıcının bu denetimin üç deneme sürümünü kullandığını bildirebilir.  
  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi <xref:System.Windows.Interop.HwndHost> sınıfından türetilir ve alt denetimin tanıtıcısı <xref:System.Windows.Forms.Integration.WindowsFormsHost.BuildWindowCore%2A> yöntemi içinde oluşturulur. <xref:System.Windows.Interop.HwndHost> sınıfı iletilerin <xref:System.Windows.Forms.Integration.WindowsFormsHost.BuildWindowCore%2A> yönteminde işlenmesine izin vermez, ancak bir iletişim kutusunun görüntülenmesi iletilerin gönderilmesine neden olur. Bu lisans senaryosunu etkinleştirmek için, <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesinin alt öğesi olarak atamadan önce denetimdeki <xref:System.Windows.Forms.Control.CreateControl%2A?displayProperty=nameWithType> yöntemini çağırın.  
  
<a name="wpf_designer"></a>   
## <a name="wpf-designer"></a>WPF Tasarımcısı  
 Visual Studio için WPF Tasarımcısı 'nı kullanarak WPF içeriğinizi tasarlayabilirsiniz. Aşağıdaki bölümlerde, WPF Tasarımcısı ile karma uygulamalar yazarken oluşabilecek bazı yaygın sorunlar listelenmektedir.  
  
### <a name="backcolortransparent-is-ignored-at-design-time"></a>BackColorTransparent, tasarım zamanında yoksayılıyor  
 <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> özelliği tasarım zamanında beklendiği gibi çalışmayabilir.  
  
 WPF denetimi görünür bir üst öğede değilse, WPF çalışma zamanı <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> değerini yoksayar. <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> yok sayılabilir olmasının nedeni, <xref:System.Windows.Forms.Integration.ElementHost> nesnenin ayrı bir <xref:System.AppDomain>oluşturulması olabilir. Ancak, uygulamayı çalıştırdığınızda <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> beklendiği gibi çalışır.  
  
### <a name="design-time-error-list-appears-when-the-obj-folder-is-deleted"></a>Tasarım Zamanı Hata Listesi obj klasörü silindiğinde görüntülenir  
 Obj klasörü silinirse, Tasarım Zamanı Hata Listesi görüntülenir.  
  
 <xref:System.Windows.Forms.Integration.ElementHost>kullanarak tasarladığınızda Windows Form Tasarımcısı, projenin obj klasöründeki hata ayıklama veya yayınlama klasöründe oluşturulan dosyaları kullanır. Bu dosyaları silerseniz tasarım zamanı Hata Listesi görüntülenir. Bu sorunu gidermek için projenizi yeniden derleyin. Daha fazla bilgi için bkz. [Windows Form Tasarımcısı tasarım zamanı hataları](../../winforms/controls/design-time-errors-in-the-windows-forms-designer.md).  
  
<a name="elementhost_and_ime"></a>   
## <a name="elementhost-and-ime"></a>ElementHost ve IME  
 Şu anda <xref:System.Windows.Forms.Integration.ElementHost> barındırılan WPF denetimleri <xref:System.Windows.Forms.Control.ImeMode%2A> özelliğini desteklemiyor. <xref:System.Windows.Forms.Control.ImeMode%2A> yapılan değişiklikler barındırılan denetimler tarafından yok sayılacak.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [WPF Tasarımcısında birlikte çalışabilirlik](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb628658(v=vs.100))
- [Windows Forms ve WPF Birlikte Çalışabilirlik Giriş Mimarisi](windows-forms-and-wpf-interoperability-input-architecture.md)
- [Nasıl yapılır: Karma Uygulamada Görsel Stilleri Etkinleştirme](how-to-enable-visual-styles-in-a-hybrid-application.md)
- [WindowsFormsHost Öğesi için Düzen Konusunda Dikkat Edilmesi Gereken Noktalar](layout-considerations-for-the-windowsformshost-element.md)
- [Windows Forms ve WPF Özelliğini Eşleme](windows-forms-and-wpf-property-mapping.md)
- [Windows Forms Tasarımcısında Tasarım Zamanı Hataları](../../winforms/controls/design-time-errors-in-the-windows-forms-designer.md)
- [Geçiş ve Birlikte Çalışabilirlik](migration-and-interoperability.md)
