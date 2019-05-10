---
title: Temel Öğelere Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- base elements [WPF]
ms.assetid: 2c997092-72c6-4767-bc84-74267f4eee72
ms.openlocfilehash: 6fc34c02ab1add0710b65da7d63f444e1628cbc6
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64657367"
---
# <a name="base-elements-overview"></a>Temel Öğelere Genel Bakış
Sınıflarda yüksek miktarda [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] sık başvurulan dört sınıflardan türetilmiş [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)] temel öğe sınıfları belgeler. Bu sınıflar <xref:System.Windows.UIElement>, <xref:System.Windows.FrameworkElement>, <xref:System.Windows.ContentElement>, ve <xref:System.Windows.FrameworkContentElement>. <xref:System.Windows.DependencyObject> Sınıfı da ilgili, çünkü bu iki genel bir temel sınıf <xref:System.Windows.UIElement> ve <xref:System.Windows.ContentElement>  

<a name="base_apis"></a>   
## <a name="base-element-apis-in-wpf-classes"></a>WPF sınıf içinde temel öğe API'leri  
 Her ikisi de <xref:System.Windows.UIElement> ve <xref:System.Windows.ContentElement> türetilmiştir <xref:System.Windows.DependencyObject>, biraz farklı yollarla. Bu düzeyde bölme ile nasıl ilgileneceğini bir <xref:System.Windows.UIElement> veya <xref:System.Windows.ContentElement> bir kullanıcı arabirimi ve bir uygulamada verdikleri ne amaçla kullanılır. <xref:System.Windows.UIElement> Ayrıca <xref:System.Windows.Media.Visual> kendi sınıf hiyerarşisinde olduğu alt düzey grafik temel destek gösteren bir sınıf [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. <xref:System.Windows.Media.Visual> bağımsız bir dikdörtgen ekran bölgeleri tanımlayarak bir işleme çerçevesi sağlar. Uygulamada, <xref:System.Windows.UIElement> daha büyük bir nesne modelini destekleyen öğeler için oluşturulacak amaçlayan ve dikdörtgen ekran bölgeleri olarak tanımlanabilen ve içerik modeli olduğu farklı izin vermek için kasıtlı olarak daha açık, bölgeleri öğeleri birleşimleri. <xref:System.Windows.ContentElement> türünden türemez <xref:System.Windows.Media.Visual>; kendi modelini olan bir <xref:System.Windows.ContentElement> okuyucu veya sonra öğeleri yorumlama ve tam üretmek Görüntüleyicisi gibi başka bir şey tarafından tüketilen <xref:System.Windows.Media.Visual> için [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] kullanmak için. Belirli <xref:System.Windows.UIElement> sınıfları, içerik ana bilgisayar olacak şekilde yöneliktir: barındırma ve işleme için bir veya daha fazla sağladıkları <xref:System.Windows.ContentElement> sınıfları (<xref:System.Windows.Controls.DocumentViewer> bu tür bir sınıfının bir örneğidir). <xref:System.Windows.ContentElement> içinde biraz daha küçük nesne modellerine sahip öğeleri için temel sınıf ve daha fazla bilgi, metin, adres veya belge içeriğini barındırılabilir olarak kullanılan bir <xref:System.Windows.UIElement>.  
  
### <a name="framework-level-and-core-level"></a>Framework ve çekirdek düzeyi  
 <xref:System.Windows.UIElement> için temel sınıf olarak hizmet veren <xref:System.Windows.FrameworkElement>, ve <xref:System.Windows.ContentElement> için taban sınıf görevi gören <xref:System.Windows.FrameworkContentElement>. Bu İleri düzey sınıflarının nedeni bu bölüm ayrıca de varolan bir WPF framework düzeyden ayrı olan bir WPF çekirdek düzeyi desteklemektir [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] PresentationCore ve PresentationFramework derlemeler arasında bölünür. WPF framework düzeyi sunu Düzen Yöneticisi uygulanması da dahil olmak üzere temel uygulama gereksinimleri için daha eksiksiz bir çözüm sunar. WPF çekirdek düzeyi çoğunu kullanmak için bir yol sağlar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ek derleme yükünden almadan. Bunlar arasında ayrım nadiren en sık karşılaşılan uygulama geliştirme senaryoları için önemli olan konuya düzeylerini ve genel olarak, almalısınız [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] bir bütün olarak ve kendiniz WPF çerçeve düzeyi arasındaki fark ile uğraşmak değil ve WPF çekirdek düzeyi. Uygulama tasarımınızı WPF framework düzeyi işlevi, önemli miktarda örneği için değiştirilecek seçerse düzey farklılıklar hakkında bilmeniz gerekebilir genel çözümünüzün kendi uygulamalarını varsa [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] oluşturma ve düzeni.  
  
<a name="subclassing_elements"></a>   
## <a name="choosing-which-element-to-derive-from"></a>Türetmek için hangi öğe seçme  
 Genişleten özel bir sınıf oluşturmak en kullanışlı yolu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] birinden türettikten olan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sınıfları, istenen işlevselliği varolan aracılığıyla mümkün olduğunca nereden sınıf hiyerarşisi. Bu bölümde, üç devralınacak hangi sınıfın karar vermenize yardımcı olması için en önemli öğe sınıfları ile birlikte gelen işlevleri listeler.  
  
 Bir denetimi uyguluyorsanız olduğu gerçekten türetmek için daha yaygın nedenlerinden biri bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sınıf, büyük olasılıkla istediğiniz pratik denetimi, bir denetim ailesi temel sınıfı olan bir sınıftan veya türetmek en az gelen <xref:System.Windows.Controls.Control> temel sınıfı. Bazı yönergeler ve uygulamalı örnekler için bkz. [denetim yazmaya genel bakış](../controls/control-authoring-overview.md).  
  
 Denetim oluşturmadığınızı ve hiyerarşide daha yüksek bir sınıf türetmek ihtiyacınız varsa, aşağıdaki bölümlerde hangi özellikleri için her temel öğe sınıfında tanımlanan bir kılavuz olarak tasarlanmıştır.  
  
 Türetilen bir sınıf oluşturursanız <xref:System.Windows.DependencyObject>, aşağıdaki işlevleri devralır:  
  
- <xref:System.Windows.DependencyObject.GetValue%2A> ve <xref:System.Windows.DependencyObject.SetValue%2A> desteği ve genel özellik sistemi desteği.  
  
- Bağımlılık özellikleri bağımlılık özelliklerinin ve uygulanan ekli özelliklerini kullanma olanağı.  
  
 Türetilen bir sınıf oluşturursanız <xref:System.Windows.UIElement>, sağlanan ek olarak, aşağıdaki işlevleri devral <xref:System.Windows.DependencyObject>:  
  
- Animasyonlu özellik değerlerini temel desteği. Daha fazla bilgi için [animasyona genel bakış](../graphics-multimedia/animation-overview.md).  
  
- Temel giriş olayı desteği ve komut verme desteği. Daha fazla bilgi için [giriş genel bakış](input-overview.md) ve [komut vermeye genel genel bakış](commanding-overview.md).  
  
- Düzen sistemi bilgileri sağlamak için kılınabilen sanal yöntemler.  
  
 Türetilen bir sınıf oluşturursanız <xref:System.Windows.FrameworkElement>, sağlanan ek olarak, aşağıdaki işlevleri devral <xref:System.Windows.UIElement>:  
  
- Stil ve görsel taslak desteği. Daha fazla bilgi için <xref:System.Windows.Style> ve [görsel taslaklara genel bakış](../graphics-multimedia/storyboards-overview.md).  
  
- Veri bağlamayı destekler. Daha fazla bilgi için [Data Binding Overview](../data/data-binding-overview.md).  
  
- Dinamik kaynak başvuruları için destek. Daha fazla bilgi için [XAML kaynakları](xaml-resources.md).  
  
- Özellik değeri devralma desteği ve meta verilerindeki framework Hizmetleri veri bağlama, stil veya Düzen framework uygulamasını gibi özellikleri hakkında rapor koşullar yardımcı diğer bayraklar. Daha fazla bilgi için [çerçeve özelliği meta verileri](framework-property-metadata.md).  
  
- Mantıksal ağaç kavramı. Daha fazla bilgi için [WPF içinde ağaçlar](trees-in-wpf.md).  
  
- Düzen sistemi pratik WPF çerçeve düzeyi uygulanması için destek dahil olmak üzere bir <xref:System.Windows.FrameworkElement.OnPropertyChanged%2A> algılayabilir geçersiz kılma etkisi düzenini özelliklerini değiştirir.  
  
 Türetilen bir sınıf oluşturursanız <xref:System.Windows.ContentElement>, sağlanan ek olarak, aşağıdaki işlevleri devral <xref:System.Windows.DependencyObject>:  
  
- Animasyon için destek. Daha fazla bilgi için [animasyona genel bakış](../graphics-multimedia/animation-overview.md).  
  
- Temel giriş olayı desteği ve komut verme desteği. Daha fazla bilgi için [giriş genel bakış](input-overview.md) ve [komut vermeye genel genel bakış](commanding-overview.md).  
  
 Türetilen bir sınıf oluşturursanız <xref:System.Windows.FrameworkContentElement>, buna ek olarak, tarafından sağlanan şu işlevleri elde edersiniz <xref:System.Windows.ContentElement>:  
  
- Stil ve görsel taslak desteği. Daha fazla bilgi için <xref:System.Windows.Style> ve [animasyona genel bakış](../graphics-multimedia/animation-overview.md).  
  
- Veri bağlamayı destekler. Daha fazla bilgi için [Data Binding Overview](../data/data-binding-overview.md).  
  
- Dinamik kaynak başvuruları için destek. Daha fazla bilgi için [XAML kaynakları](xaml-resources.md).  
  
- Özellik değeri devralma desteği ve framework Hizmetleri özellikleri hakkında rapor koşullar yardımcı olan diğer bayraklar meta veri bağlama, stil veya Düzen framework uygulamasını ister. Daha fazla bilgi için [çerçeve özelliği meta verileri](framework-property-metadata.md).  
  
- Düzen sistemi değişikliklerine erişim devralmamanızı (gibi <xref:System.Windows.FrameworkElement.ArrangeOverride%2A>). Düzen sistemi uygulamaları kullanılabilir yalnızca <xref:System.Windows.FrameworkElement>. Ancak, bir <xref:System.Windows.FrameworkElement.OnPropertyChanged%2A> etkilemek düzen ve içeriği tüm konakları Bu rapor özellikleri değişiklikleri algılayabilir geçersiz kılma.  
  
 İçerik modelleri, sınıfları çeşitli için belirtilmiştir. İçerik modeli için bir sınıf türetmek için uygun bir sınıf bulmak istiyorsanız dikkate almanız gereken bir olası faktördür. Daha fazla bilgi için [WPF içerik modeli](../controls/wpf-content-model.md).  
  
<a name="other_base_classes"></a>   
## <a name="other-base-classes"></a>Diğer temel sınıflar  
  
### <a name="dispatcherobject"></a>DispatcherObject  
 <xref:System.Windows.Threading.DispatcherObject> için destek sağlar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] iş parçacığı modeli ve tüm nesneleri için oluşturulan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamaları ile ilişkilendirilecek bir <xref:System.Windows.Threading.Dispatcher>. Öğesinden türetilen değil olsa bile <xref:System.Windows.UIElement>, <xref:System.Windows.DependencyObject>, veya <xref:System.Windows.Media.Visual>, türetilen dikkate almanız gereken <xref:System.Windows.Threading.DispatcherObject> bu iş parçacığı modeline destek almak için. Daha fazla bilgi için [iş parçacığı modeli](threading-model.md).  
  
### <a name="visual"></a>Görsel  
 <xref:System.Windows.Media.Visual> genellikle yaklaşık dikdörtgen bir bölgede görsel sunumunu gerektiren bir 2B nesnenin kavramını uygular. Gerçek işlenmesi bir <xref:System.Windows.Media.Visual> (değildir müstakil) diğer sınıflarda olur ancak <xref:System.Windows.Media.Visual> sınıf çeşitli düzeylerde işleme işlemler tarafından kullanılan bilinen bir türünü sağlar. <xref:System.Windows.Media.Visual> isabet sınaması uygular, ancak isabet sınaması hatalı pozitif sonuçlar rapor olayları kullanıma sunmuyor (bunlar bulunan <xref:System.Windows.UIElement>). Daha fazla bilgi için [görsel katman programlama](../graphics-multimedia/visual-layer-programming.md).  
  
### <a name="freezable"></a>Freezable  
 <xref:System.Windows.Freezable> değişebilir bir nesne içinde değiştirilemezlik değişmez bir nesne gerekli veya performansla ilgili nedenlerden dolayı nesnenin bir kopyasını oluşturmak için Araçlar sağlayarak benzetimini yapar. <xref:System.Windows.Freezable> Türü sağlayan ortak bir temeli belirli geometriler ve Fırçalar yanı sıra, animasyonları gibi grafik öğeleri. Özellikle, bir <xref:System.Windows.Freezable> değil bir <xref:System.Windows.Media.Visual>; özellikler içerebileceği olduğunda <xref:System.Windows.Freezable> başka bir nesnenin bir özellik değeri doldurmak için uygulanır ve bu alt işleme etkileyebilir. Daha fazla bilgi için [Freezable nesnelerine genel bakış](freezable-objects-overview.md).  
  
 <xref:System.Windows.Media.Animation.Animatable>  
  
 <xref:System.Windows.Media.Animation.Animatable> olan bir <xref:System.Windows.Freezable> türetilmiş sınıf hareketlendirilmemiş özelliklerinden animasyon denetimi katmanı ve bazı yardımcı programı üyeleri özel olarak ekler ve böylece şu anda animasyonlu özellikleri ayırt edilebilir.  
  
### <a name="control"></a>Denetim  
 <xref:System.Windows.Controls.Control> teknolojiye bir denetim veya bileşen teknolojisi bağlı olarak ifade edilen nesne türü için hedeflenen temel sınıftır. Genel olarak, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetim sınıfları, doğrudan bir UI denetimini temsil eden veya yakından denetim bileşiminin katılan sınıflardır. Birincil işlevselliği, <xref:System.Windows.Controls.Control> olan denetim şablonu oluşturma etkinleştirir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.Control>
- [Bağımlılık Özelliklerine Genel Bakış](dependency-properties-overview.md)
- [Denetim Yazımına Genel Bakış](../controls/control-authoring-overview.md)
- [WPF Mimarisi](wpf-architecture.md)
