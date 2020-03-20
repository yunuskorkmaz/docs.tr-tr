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
ms.openlocfilehash: b85a607d2e44d6253359a81118f90e6ee05d2d3f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187321"
---
# <a name="troubleshooting-hybrid-applications"></a>Karma Uygulama Sorunlarını Giderme
<a name="introduction"></a>Bu konu, hem de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Windows Forms teknolojilerini kullanan karma uygulamaları yazarken oluşabilecek bazı sık karşılaşılan sorunları listeler.  

<a name="overlapping_controls"></a>
## <a name="overlapping-controls"></a>Çakışan Denetimler  
 Denetimler beklediğiniz gibi çakışmayabilir. Windows Forms, her denetim için ayrı bir HWND kullanır. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]bir sayfadaki tüm içerik ler için bir HWND kullanır. Bu uygulama farkı beklenmeyen çakışan davranışlara neden olur.  
  
 Barındırılan bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Windows Forms denetimi her [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zaman içeriğin üstünde görünür.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]denetimde <xref:System.Windows.Forms.Integration.ElementHost> barındırılan <xref:System.Windows.Forms.Integration.ElementHost> içerik, denetimin z-sırasında görünür. Denetimleri çakıştmak <xref:System.Windows.Forms.Integration.ElementHost> mümkündür, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ancak barındırılan içerik birleşmiyor veya etkileşimde yok.  
  
<a name="child_property"></a>
## <a name="child-property"></a>Çocuk Mülkiyeti  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> Ve <xref:System.Windows.Forms.Integration.ElementHost> sınıflar yalnızca tek bir alt denetim veya öğe barındırabilir. Birden fazla denetim veya öğe barındırmak için, alt içerik olarak bir kapsayıcı kullanmanız gerekir. Örneğin, windows forms düğmesi ve onay kutusu <xref:System.Windows.Forms.Panel?displayProperty=nameWithType> denetimlerini bir denetime ekleyebilir <xref:System.Windows.Forms.Integration.WindowsFormsHost> ve <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A> ardından paneli denetimin özelliğine atayabilirsiniz. Ancak, düğme ve onay kutusu denetimlerini aynı <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetime ayrı ayrı ekleyemezsiniz.  
  
<a name="scaling"></a>
## <a name="scaling"></a>Ölçeklendirme  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ve Windows Formlar farklı ölçekleme modelleri vardır. Bazı [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ölçekleme dönüşümleri Windows Forms denetimleri için anlamlıdır, ancak diğerleri anlamlı değildir. Örneğin, Windows Forms denetimini 0'a ölçeklendirme çalışması, ancak aynı denetimi sıfır olmayan bir değere geri ölçeklendirmeye çalışırsanız, denetimin boyutu 0 kalır. Daha fazla bilgi [için WindowsFormsHost Öğesi için Düzen Hususları'na](layout-considerations-for-the-windowsformshost-element.md)bakın.  
  
<a name="adapter"></a>
## <a name="adapter"></a>Bağdaştırıcı  
 Gizli bir kapsayıcı içerdikleri için, <xref:System.Windows.Forms.Integration.WindowsFormsHost> sınıfları ve <xref:System.Windows.Forms.Integration.ElementHost> çalışma yaparken karışıklık olabilir. Hem <xref:System.Windows.Forms.Integration.WindowsFormsHost> sınıflarda, <xref:System.Windows.Forms.Integration.ElementHost> içeriği barındırmak için kullandıkları *bağdaştırıcı*adı verilen gizli bir kapsayıcı vardır. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğe için bağdaştırıcı <xref:System.Windows.Forms.ContainerControl?displayProperty=nameWithType> sınıftan türetilmiştir. Denetim <xref:System.Windows.Forms.Integration.ElementHost> için bağdaştırıcı <xref:System.Windows.Controls.DockPanel> öğeden türetilmiştir. Diğer işlem leşme konularında bağdaştırıcıya yapılan başvuruları gördüğünüzde, bu kapsayıcı tartışılmaktadır.  
  
<a name="nesting"></a>
## <a name="nesting"></a>Iç içe  
 Bir <xref:System.Windows.Forms.Integration.WindowsFormsHost> <xref:System.Windows.Forms.Integration.ElementHost> öğenin denetimin içine yerleştirme desteklenmez. Bir <xref:System.Windows.Forms.Integration.ElementHost> <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğenin içinde bir denetim iç içe de desteklenmez.  
  
<a name="focus"></a>
## <a name="focus"></a>Odak  
 Odak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] farklı çalışır ve Windows Formlar, bu da odak sorunları karma bir uygulamada oluşabilir anlamına gelir. Örneğin, bir <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğenin içinde odağınız varsa ve sayfayı en aza indirip geri yüklediyseniz veya bir modal iletişim kutusu gösteriyorsanız, öğenin <xref:System.Windows.Forms.Integration.WindowsFormsHost> içindeki odak kaybolabilir. Öğe <xref:System.Windows.Forms.Integration.WindowsFormsHost> hala odak vardır, ancak içindeki denetim olmayabilir.  
  
 Veri doğrulama da odak etkilenir. Doğrulama bir <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğede çalışır, ancak <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğenin dışına sekme olarak veya <xref:System.Windows.Forms.Integration.WindowsFormsHost> iki farklı öğe arasında çalışmaz.  
  
<a name="property_mapping"></a>
## <a name="property-mapping"></a>Özellik Eşlemesi  
 Bazı özellik eşlemeleri, windows formları [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] teknolojileri arasındaki farklı uygulamaları köprülemek için kapsamlı yorum gerektirir. Özellik eşlemeleri, kodunuzun yazı tiplerinde, renklerdeki ve diğer özelliklerdeki değişikliklere tepki göstermesini sağlar. Genel olarak, özellik eşlemeleri *Özellik*Değiştirilen olayları dinleyerek veya*Özellik*Değiştirildi çağrıları üzerinde dinleyerek ve çocuk denetimi veya bağdaştırıcısı üzerinde uygun özellikleri ayarlayarak çalışır. Daha fazla bilgi için [Windows Formları ve WPF Özellik Eşleme'ye](windows-forms-and-wpf-property-mapping.md)bakın.  
  
<a name="layoutrelated_properties_on_hosted_content"></a>
## <a name="layout-related-properties-on-hosted-content"></a>Barındırılan İçerikte Düzenle İlgili Özellikler  
 Özellik <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A?displayProperty=nameWithType> <xref:System.Windows.Forms.Integration.ElementHost.Child%2A?displayProperty=nameWithType> atandığında, barındırılan içerikteki düzenle ilgili birkaç özellik otomatik olarak ayarlanır. Bu içerik özelliklerini değiştirmek beklenmeyen düzen davranışlarına neden olabilir.  
  
 Barındırılan içeriğiniz, üst <xref:System.Windows.Forms.Integration.WindowsFormsHost> <xref:System.Windows.Forms.Integration.ElementHost> öğeyi ve ebeveyni doldurmak için sabitlenir. Bu dolgu davranışını etkinleştirmek için, alt özelliği ayarladığınızda birkaç özellik ayarlanır. Aşağıdaki tabloda içerik özelliklerinin <xref:System.Windows.Forms.Integration.ElementHost> sınıflar <xref:System.Windows.Forms.Integration.WindowsFormsHost> ve sınıflar tarafından ayarlandığı listelenir.  
  
|Host Sınıf|İçerik Özellikleri|  
|----------------|------------------------|  
|<xref:System.Windows.Forms.Integration.ElementHost>|<xref:System.Windows.FrameworkElement.Height%2A><br /><br /> <xref:System.Windows.FrameworkElement.Width%2A><br /><br /> <xref:System.Windows.FrameworkElement.Margin%2A><br /><br /> <xref:System.Windows.FrameworkElement.VerticalAlignment%2A><br /><br /> <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>|  
|<xref:System.Windows.Forms.Integration.WindowsFormsHost>|<xref:System.Windows.Forms.Control.Margin%2A><br /><br /> <xref:System.Windows.Forms.Control.Dock%2A><br /><br /> <xref:System.Windows.Forms.Control.AutoSize%2A><br /><br /> <xref:System.Windows.Forms.Control.Location%2A><br /><br /> <xref:System.Windows.Forms.Control.MaximumSize%2A>|  
  
 Bu özellikleri doğrudan barındırılan içeriğe ayarlamayın. Daha fazla bilgi [için WindowsFormsHost Öğesi için Düzen Hususları'na](layout-considerations-for-the-windowsformshost-element.md)bakın.  
  
<a name="navigation_applications"></a>
## <a name="navigation-applications"></a>Navigasyon Uygulamaları  
 Gezinme uygulamaları kullanıcı durumunu koruyamaz. Öğe, <xref:System.Windows.Forms.Integration.WindowsFormsHost> bir gezinti uygulamasında kullanıldığında denetimlerini yeniden oluşturur. Alt denetimleri yeniden oluşturma, kullanıcı <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğeyi barındıran sayfadan uzağa gittiğinde ve sonra bu öğeye geri döndüğünde oluşur. Kullanıcı tarafından yazılan tüm içerik kaybolur.  
  
<a name="message_loop_interoperation"></a>
## <a name="message-loop-interoperation"></a>İleti Döngüsü İnİşleyişi  
 Windows Forms ileti döngüleri ile çalışırken, iletiler beklendiği gibi işlenmeyebilir. Yöntem <xref:System.Windows.Forms.Integration.WindowsFormsHost.EnableWindowsFormsInterop%2A> <xref:System.Windows.Forms.Integration.WindowsFormsHost> yapıcı tarafından çağrılır. Bu yöntem ileti döngüsüne [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir ileti filtresi ekler. Bu filtre, <xref:System.Windows.Forms.Control.PreProcessMessage%2A?displayProperty=nameWithType> iletinin <xref:System.Windows.Forms.Control?displayProperty=nameWithType> hedefi a ise yöntemi çağırır ve iletiyi çevirir/gönderir.  
  
 Windows Forms <xref:System.Windows.Window> ileti döngüsünde bir <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType>ileti döngüsü gösterirseniz, <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A> yöntemi aramadığınız sürece hiçbir şey yazamazsınız. Yöntem <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A> a <xref:System.Windows.Window> alır ve <xref:System.Windows.Forms.IMessageFilter?displayProperty=nameWithType>anahtarla ilgili iletileri [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ileti döngüsüne yeniden yönlendirir bir , ekler. Daha fazla bilgi için [Windows Formları ve WPF Birlikte Çalışabilirlik Giriş Mimarisi'ne](windows-forms-and-wpf-interoperability-input-architecture.md)bakın.  
  
<a name="opacity_and_layering"></a>
## <a name="opacity-and-layering"></a>Opaklık ve Katmanlama  
 Sınıf <xref:System.Windows.Interop.HwndHost> katmanlamayı desteklemez. Bu, öğe <xref:System.Windows.UIElement.Opacity%2A> üzerindeki özelliği <xref:System.Windows.Forms.Integration.WindowsFormsHost> ayarlamanın hiçbir etkisi olmadığı ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Window.AllowsTransparency%2A> `true`'de ayarlanan diğer pencerelerle karıştırma olmayacağı anlamına gelir.  
  
<a name="dispose"></a>
## <a name="dispose"></a>Dispose  
 Sınıfları düzgün bir şekilde atmamakaynakları sızdırabilir. Karma uygulamalarınızda, <xref:System.Windows.Forms.Integration.WindowsFormsHost> <xref:System.Windows.Forms.Integration.ElementHost> sınıfların elden çıkarıladığından veya kaynak sızdırdığından emin olun. Windows Forms, <xref:System.Windows.Forms.Integration.ElementHost> modal <xref:System.Windows.Forms.Form> olmayan üst öğesi kapandığında denetimleri ortadan kalar. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]uygulamanız <xref:System.Windows.Forms.Integration.WindowsFormsHost> kapandığında öğeleri ortadan katabilir. Windows Forms ileti <xref:System.Windows.Forms.Integration.WindowsFormsHost> döngüsündeki <xref:System.Windows.Window> bir öğeyi göstermek mümkündür. Bu durumda, kodunuz uygulamanızın kapatılıyor bildirimi almayabilir.  
  
<a name="enabling_visual_styles"></a>
## <a name="enabling-visual-styles"></a>Görsel Stilleri Etkinleştirme  
 Windows Forms denetimindeki Microsoft Windows XP görsel stilleri etkinleştirilemeyebilir. Yöntem, <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> Windows Forms uygulaması için şablonda çağrılır. Bu yöntem varsayılan olarak çağrılmasa da, bir proje oluşturmak için Visual Studio'yu kullanıyorsanız, Comctl32.dll sürümü 6.0 varsa denetimler için Microsoft Windows XP görsel stilleri alırsınız. İş parçacığı <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> üzerinde tutamaçları oluşturulmadan önce yöntemi aramanız gerekir. Daha fazla bilgi için [bkz: Karma Uygulamada Görsel Stilleri Etkinleştir.](how-to-enable-visual-styles-in-a-hybrid-application.md)  
  
<a name="licensed_controls"></a>
## <a name="licensed-controls"></a>Lisanslı Kontroller  
 Lisanslı Windows Forms, kullanıcıya ileti kutusunda lisans bilgilerini görüntüleyen denetimleri karma bir uygulama için beklenmeyen davranışlara neden olabilir. Bazı lisanslı denetimler, oluşturma yı işlemek için yanıt olarak bir iletişim kutusu gösterir. Örneğin, lisanslı denetim kullanıcıya bir lisansın gerekli olduğunu veya kullanıcının denetimin kalan üç deneme sürümü ne olduğunu bildirebilir.  
  
 Öğe <xref:System.Windows.Forms.Integration.WindowsFormsHost> <xref:System.Windows.Interop.HwndHost> sınıftan türetilir ve alt denetimin tutamacı <xref:System.Windows.Forms.Integration.WindowsFormsHost.BuildWindowCore%2A> yöntemin içinde oluşturulur. Sınıf <xref:System.Windows.Interop.HwndHost> iletilerin <xref:System.Windows.Forms.Integration.WindowsFormsHost.BuildWindowCore%2A> yöntemde işlenmesine izin vermez, ancak iletişim kutusu nun görüntülenmesi iletilerin gönderilmesine neden olur. Bu lisans senaryosunu etkinleştirmek <xref:System.Windows.Forms.Control.CreateControl%2A?displayProperty=nameWithType> için, <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğenin alt öğesi olarak atamadan önce denetim yöntemini arayın.  
  
<a name="wpf_designer"></a>
## <a name="wpf-designer"></a>WPF Tasarımcısı  
 WPF içeriğinizi Visual Studio için WPF Designer'ı kullanarak tasarlayabilirsiniz. Aşağıdaki bölümlerde WPF Tasarımcısı ile karma uygulamalar yazarken oluşabilecek bazı sık karşılaşılan sorunlar listelenerilmiştir.  
  
### <a name="backcolortransparent-is-ignored-at-design-time"></a>BackColorTransparent tasarım zamanda göz ardı edilir  
 Özellik <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> tasarım zamanında beklendiği gibi çalışmayabilir.  
  
 WPF denetimi görünür bir üst öğede değilse, WPF <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> çalışma zamanı değeri yoksa. Göz ardı <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> edilebilir nedeni <xref:System.Windows.Forms.Integration.ElementHost> nesne ayrı <xref:System.AppDomain>bir . Ancak, uygulamayı çalıştırdığınızda, <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> beklendiği gibi çalışır.  
  
### <a name="design-time-error-list-appears-when-the-obj-folder-is-deleted"></a>Obj klasörü silindiğinde tasarım zamanı Hata Listesi görüntülenir  
 OBJ klasörü silinirse, Tasarım zamanı Hata Listesi görüntülenir.  
  
 Windows Forms <xref:System.Windows.Forms.Integration.ElementHost>Designer kullanarak tasarım yaparken, Projenizin obj klasöründe Hata Ayıklama veya Sürüm klasöründe oluşturulan dosyaları kullanır. Bu dosyaları silerseniz, Tasarım zamanı Hata Listesi görüntülenir. Bu sorunu gidermek için projenizi yeniden oluşturun. Daha fazla bilgi için [Windows Forms Designer'daki Tasarım-Zaman Hataları bölümüne](../../winforms/controls/design-time-errors-in-the-windows-forms-designer.md)bakın.  
  
<a name="elementhost_and_ime"></a>
## <a name="elementhost-and-ime"></a>ElementHost ve IME  
 <xref:System.Windows.Forms.Integration.ElementHost> WPF denetimleri şu anda <xref:System.Windows.Forms.Control.ImeMode%2A> özelliği desteklemiyor. <xref:System.Windows.Forms.Control.ImeMode%2A> Değişiklikler barındırılan denetimler tarafından yoksayılır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [WPF Tasarımcısı'nda birlikte çalışabilirlik](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb628658(v=vs.100))
- [Windows Forms ve WPF Birlikte Çalışabilirlik Giriş Mimarisi](windows-forms-and-wpf-interoperability-input-architecture.md)
- [Nasıl yapılır: Karma Uygulamada Görsel Stilleri Etkinleştirme](how-to-enable-visual-styles-in-a-hybrid-application.md)
- [WindowsFormsHost Öğesi için Düzen Konusunda Dikkat Edilmesi Gereken Noktalar](layout-considerations-for-the-windowsformshost-element.md)
- [Windows Forms ve WPF Özelliğini Eşleme](windows-forms-and-wpf-property-mapping.md)
- [Windows Formları Tasarımcısında Tasarım Zamanı Hataları](../../winforms/controls/design-time-errors-in-the-windows-forms-designer.md)
- [Geçiş ve Birlikte Çalışabilirlik](migration-and-interoperability.md)
