---
title: Temel Öğelere Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- base elements [WPF]
ms.assetid: 2c997092-72c6-4767-bc84-74267f4eee72
ms.openlocfilehash: bcfcb87d0ddf5181a47d459e821bacd9b9f6b61c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="base-elements-overview"></a>Temel Öğelere Genel Bakış
Sınıflarda yüksek miktarda [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] sık başvurulan farklı dört sınıfından türetilen [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)] temel öğe sınıfları belgelemek. Bu sınıflar <xref:System.Windows.UIElement>, <xref:System.Windows.FrameworkElement>, <xref:System.Windows.ContentElement>, ve <xref:System.Windows.FrameworkContentElement>. <xref:System.Windows.DependencyObject> Sınıfı ayrıca ile ilgili, ortak bir taban sınıfı hem olduğundan <xref:System.Windows.UIElement> ve <xref:System.Windows.ContentElement>  
 
  
<a name="base_apis"></a>   
## <a name="base-element-apis-in-wpf-classes"></a>WPF sınıfları içinde temel öğe API'leri  
 Her ikisi de <xref:System.Windows.UIElement> ve <xref:System.Windows.ContentElement> türetilmiş <xref:System.Windows.DependencyObject>, biraz farklı yollarla. Bu düzeyde bölme ile nasıl ilgileneceğini bir <xref:System.Windows.UIElement> veya <xref:System.Windows.ContentElement> bir kullanıcı arabirimi ve bir uygulamada verdikleri ne amaçla kullanılır. <xref:System.Windows.UIElement> Ayrıca <xref:System.Windows.Media.Visual> kendi sınıf hiyerarşisinde olduğu alt düzey grafik temel destek gösteren bir sınıf [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. <xref:System.Windows.Media.Visual> bağımsız dikdörtgen ekran bölgeleri tanımlayarak işleme çerçevesi sağlar. Uygulamada, <xref:System.Windows.UIElement> daha büyük bir nesne modelini destekleyen öğeler için işlemek için amaçlanan ve düzeni dikdörtgen ekran bölgeleri olarak tanımlanabilen ve içerik modeli olduğu farklı izin vermek için kasıtlı olarak daha açık bölgeleri öğelerin birleşimlerine. <xref:System.Windows.ContentElement> türünden türemez <xref:System.Windows.Media.Visual>; kendi modelini olan bir <xref:System.Windows.ContentElement> bir okuyucu veya sonra öğeleri değerlendiren ve tam üretmek Görüntüleyicisi gibi başka bir şey tarafından tüketilen <xref:System.Windows.Media.Visual> için [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] kullanmak için. Belirli <xref:System.Windows.UIElement> sınıfları içerik konağı olacak şekilde yöneliktir: barındırmayı ve işlemeyi bir veya daha fazla sağladıkları <xref:System.Windows.ContentElement> sınıfları (<xref:System.Windows.Controls.DocumentViewer> gibi bir sınıf örneği gösterilmiştir). <xref:System.Windows.ContentElement> biraz daha küçük nesne modelleri ile öğeleri için temel sınıf ve daha fazla bilgi, metin adres veya belge içerik içinde barındırılabilir olarak kullanılan bir <xref:System.Windows.UIElement>.  
  
### <a name="framework-level-and-core-level"></a>Framework ve çekirdek düzeyi  
 <xref:System.Windows.UIElement> için temel sınıf görevi gören <xref:System.Windows.FrameworkElement>, ve <xref:System.Windows.ContentElement> için temel sınıf görevi gören <xref:System.Windows.FrameworkContentElement>. Bu sınıfların sonraki düzeyinin ayrıca de varolan bu bölme ile bir WPF framework düzeyden ayrı bir WPF çekirdek düzeyi desteklemek için nedeni [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] PresentationCore ve PresentationFramework derlemeleri arasında bölünür. WPF çerçeve düzeyi sunu için Düzen Yöneticisi uygulaması da dahil olmak üzere, basit uygulama gereksinimlerinde için daha eksiksiz bir çözüm sunar. WPF çekirdek düzeyi çoğunu kullanmak için bir yol sağlar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ek derleme yükünden alma olmadan. Bunlar arasında ayrım nadiren en tipik uygulama geliştirme senaryoları için önemlidir düzeyleri ve genel olarak düşünmelisiniz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] bir bütün olarak ve kendiniz WPF çerçeve düzeyi arasındaki farkı içeren endişe ve WPF çekirdek düzeyi. WPF framework düzeyi işlevselliği, önemli miktarda örneği için değiştirmek, Uygulama tasarımınız seçerse, düzey farklılıklarını bilmeniz gerekebilir, kendi uygulamalarını çözümünüzün genel zaten varsa, [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] birleşim ve düzeni.  
  
<a name="subclassing_elements"></a>   
## <a name="choosing-which-element-to-derive-from"></a>Öğesinden türetilen için hangi öğe seçme  
 Genişletir özel bir sınıf oluşturmak için en kullanışlı yol [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] birinden türettikten olan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] varolan aracılığıyla, istenen işlevselliği mümkün olduğunca nereden sınıfları sınıf hiyerarşisi. Bu bölümde devralmak için hangi sınıfın karar vermenize yardımcı olacak en önemli öğe sınıfları üçünü birlikte işlevselliği listeler.  
  
 Bir denetim uyguluyorsanız olduğu gerçekten türetme daha yaygın nedenlerinden biri bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sınıfı, büyük olasılıkla istediğiniz pratik bir denetimdir, bir denetim ailesi temel sınıfı, bir sınıftan veya türetilen gelen en az <xref:System.Windows.Controls.Control> temel sınıfı. Bazı yönergeler ve pratik örnekler için bkz: [denetimine genel bakış yazma](../../../../docs/framework/wpf/controls/control-authoring-overview.md).  
  
 Bir denetim oluşturmuyor ve hiyerarşide daha yüksek bir sınıf türetin gerekiyorsa, aşağıdaki bölümlerde hangi özellikleri her temel öğe sınıfında tanımlanan için bir kılavuz olarak tasarlanmıştır.  
  
 Öğesinden türeyen bir sınıf oluşturursanız <xref:System.Windows.DependencyObject>, aşağıdaki işlevleri devral:  
  
-   <xref:System.Windows.DependencyObject.GetValue%2A> ve <xref:System.Windows.DependencyObject.SetValue%2A> desteği ve genel özellik sistemi desteği.  
  
-   Bağımlılık özellikleri ve uygulanan ekli özellikler bağımlılık özellikleri olarak kullanma olanağı.  
  
 Öğesinden türeyen bir sınıf oluşturursanız <xref:System.Windows.UIElement>, tarafından sağlanana ek olarak aşağıdaki işlevselliği devral <xref:System.Windows.DependencyObject>:  
  
-   Animasyonlu özellik değerleri için temel destek. Daha fazla bilgi için bkz: [animasyon genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
-   Temel giriş olayı desteği ve komut verme desteği. Daha fazla bilgi için bkz: [giriş genel bakış](../../../../docs/framework/wpf/advanced/input-overview.md) ve [kumanda genel bakış](../../../../docs/framework/wpf/advanced/commanding-overview.md).  
  
-   Düzen sistemine bilgi sağlamak için geçersiz kılınabilir sanal yöntemler.  
  
 Öğesinden türeyen bir sınıf oluşturursanız <xref:System.Windows.FrameworkElement>, tarafından sağlanana ek olarak aşağıdaki işlevselliği devral <xref:System.Windows.UIElement>:  
  
-   Stil ve film şeritleri için destek. Daha fazla bilgi için bkz: <xref:System.Windows.Style> ve [film şeritleri genel bakış](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).  
  
-   Veri bağlama için destek. Daha fazla bilgi için bkz: [veri bağlama genel bakış](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
-   Dinamik kaynak başvuruları için destek. Daha fazla bilgi için bkz: [XAML kaynakları](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
-   Özellik değeri devralma desteği ve veri bağlama, stiller veya düzen çerçevesi uygulamaları gibi çerçeve hizmetlerine özellikler hakkında rapor durumların yardımcı meta verilerindeki diğer bayraklar. Daha fazla bilgi için bkz: [Framework özellik meta verileri](../../../../docs/framework/wpf/advanced/framework-property-metadata.md).  
  
-   Mantıksal ağacının kavramı. Daha fazla bilgi için bkz: [WPF ağaçlarında](../../../../docs/framework/wpf/advanced/trees-in-wpf.md).  
  
-   Düzen sistemi pratik WPF çerçeve düzeyi uygulanması için destek dahil olmak üzere bir <xref:System.Windows.FrameworkElement.OnPropertyChanged%2A> algılayabilir geçersiz kılma etkisi düzenini özelliklerini değiştirir.  
  
 Öğesinden türeyen bir sınıf oluşturursanız <xref:System.Windows.ContentElement>, tarafından sağlanana ek olarak aşağıdaki işlevselliği devral <xref:System.Windows.DependencyObject>:  
  
-   Animasyon desteği. Daha fazla bilgi için bkz: [animasyon genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
-   Temel giriş olayı desteği ve komut verme desteği. Daha fazla bilgi için bkz: [giriş genel bakış](../../../../docs/framework/wpf/advanced/input-overview.md) ve [kumanda genel bakış](../../../../docs/framework/wpf/advanced/commanding-overview.md).  
  
 Öğesinden türeyen bir sınıf oluşturursanız <xref:System.Windows.FrameworkContentElement>, tarafından sağlanana ek olarak aşağıdaki işlevselliği elde <xref:System.Windows.ContentElement>:  
  
-   Stil ve film şeritleri için destek. Daha fazla bilgi için bkz: <xref:System.Windows.Style> ve [animasyon genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
-   Veri bağlama için destek. Daha fazla bilgi için bkz: [veri bağlama genel bakış](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
-   Dinamik kaynak başvuruları için destek. Daha fazla bilgi için bkz: [XAML kaynakları](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
-   Özellik değeri devralma desteği ve veri bağlama, stiller veya düzen çerçevesi uygulamaları gibi çerçeve hizmetlerine özellikler hakkında rapor durumların yardımcı meta verilerindeki diğer bayraklar. Daha fazla bilgi için bkz: [Framework özellik meta verileri](../../../../docs/framework/wpf/advanced/framework-property-metadata.md).  
  
-   Düzen sistemi değişikliklerine erişimi devralmayan (gibi <xref:System.Windows.FrameworkElement.ArrangeOverride%2A>). Düzen sistem uygulamaları kullanılabilir yalnızca <xref:System.Windows.FrameworkElement>. Ancak, bir <xref:System.Windows.FrameworkElement.OnPropertyChanged%2A> etkilemek düzeni ve bunları herhangi içerik konağına bildiren özelliklerine yapılan değişiklikler algılayabilir geçersiz kılma.  
  
 İçerik modelleri çeşitli sınıflar için belgelenmiştir. İçerik modeli için bir sınıf türetin için uygun sınıf bulmak istediğinizde düşünmelisiniz bir olası faktördür. Daha fazla bilgi için bkz: [WPF içerik modeli](../../../../docs/framework/wpf/controls/wpf-content-model.md).  
  
<a name="other_base_classes"></a>   
## <a name="other-base-classes"></a>Diğer temel sınıflar  
  
### <a name="dispatcherobject"></a>DispatcherObject  
 <xref:System.Windows.Threading.DispatcherObject> için destek sağlar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] iş parçacığı modeli ve tüm nesneleri için oluşturulan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ile ilişkili uygulamalar bir <xref:System.Windows.Threading.Dispatcher>. Öğesinden türetilen değil olsa bile <xref:System.Windows.UIElement>, <xref:System.Windows.DependencyObject>, veya <xref:System.Windows.Media.Visual>, türetme düşünmelisiniz <xref:System.Windows.Threading.DispatcherObject> bu iş parçacığı modeli desteğini alabilmek için. Daha fazla bilgi için bkz: [iş parçacığı modeline](../../../../docs/framework/wpf/advanced/threading-model.md).  
  
### <a name="visual"></a>Görsel  
 <xref:System.Windows.Media.Visual> Genellikle, kabaca dikdörtgen bir bölgede görsel sunumu gerektiren 2B nesne kavramını uygular. Gerçek işlemeyi bir <xref:System.Windows.Media.Visual> (bunu kendi içinde değil) diğer sınıflarda olur ancak <xref:System.Windows.Media.Visual> sınıfı, farklı düzeylerde işleme işlemler tarafından kullanılan bilinen bir türe sağlar. <xref:System.Windows.Media.Visual> isabet sınaması uygular, ancak isabet testi pozitif sonuç raporu olayları sunmaz (bunlar bulunan <xref:System.Windows.UIElement>). Daha fazla bilgi için bkz: [görsel katman programlama](../../../../docs/framework/wpf/graphics-multimedia/visual-layer-programming.md).  
  
### <a name="freezable"></a>Freezable  
 <xref:System.Windows.Freezable> değişebilir bir nesne girişi değişmez nesne gerektiğinde veya performans nedenleriyle istendiğinde nesnenin kopyasını oluşturmak için yol sağlayarak benzetimini yapar. <xref:System.Windows.Freezable> Tür sağlayan ortak bir temel belirli animasyonları yanı sıra geometri ve fırçalar gibi grafik öğeleri. Özellikle, bir <xref:System.Windows.Freezable> değil bir <xref:System.Windows.Media.Visual>; özellikler tutabilir zaman <xref:System.Windows.Freezable> başka bir nesnenin özellik değerini doldurmak için uygulanır ve bu alt özellikler işlemeyi etkileyebilir. Daha fazla bilgi için bkz: [Freezable nesnelere genel bakış](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
 <xref:System.Windows.Media.Animation.Animatable>  
  
 <xref:System.Windows.Media.Animation.Animatable> olan bir <xref:System.Windows.Freezable> türetilen özellikle animasyon denetim katmanı ve bazı yardımcı program üyeleri hareketlendirilmemiş özelliklerinden ekler ve böylece geçerli animasyon özelliklerinin ayırt sınıfı.  
  
### <a name="control"></a>Denetim  
 <xref:System.Windows.Controls.Control> teknolojiye denetimi veya bileşeni teknolojisi bağlı olarak ifade edilen nesnenin türü için amaçlanan temel sınıftır. Genel olarak, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetim sınıfları, doğrudan UI denetimi temsil eder ya da Denetim oluşumuna yakından katılan sınıflardır. Birincil işlevi, <xref:System.Windows.Controls.Control> denetlemedir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Controls.Control>  
 [Bağımlılık Özelliklerine Genel Bakış](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [Denetim Yazımına Genel Bakış](../../../../docs/framework/wpf/controls/control-authoring-overview.md)  
 [WPF Mimarisi](../../../../docs/framework/wpf/advanced/wpf-architecture.md)
