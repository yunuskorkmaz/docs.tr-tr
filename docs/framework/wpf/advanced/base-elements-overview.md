---
title: Temel Öğelere Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- base elements [WPF]
ms.assetid: 2c997092-72c6-4767-bc84-74267f4eee72
ms.openlocfilehash: f6519675ebf3624152e1077e7582f04e38b1dce9
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81644048"
---
# <a name="base-elements-overview"></a>Temel Öğelere Genel Bakış
Yüksek orandaki [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] sınıflar, SDK belgelerinde temel öğe sınıfları olarak yaygın olarak adlandırılan dört sınıftan türetilir. Bu sınıflar <xref:System.Windows.UIElement> <xref:System.Windows.FrameworkElement>, <xref:System.Windows.ContentElement>, <xref:System.Windows.FrameworkContentElement>, ve . Sınıf <xref:System.Windows.DependencyObject> da ilişkilidir, çünkü her ikisinin ve <xref:System.Windows.UIElement><xref:System.Windows.ContentElement>  

<a name="base_apis"></a>
## <a name="base-element-apis-in-wpf-classes"></a>WPF Sınıflarında Temel Eleman API'leri  
 Her <xref:System.Windows.UIElement> <xref:System.Windows.ContentElement> ikisi de <xref:System.Windows.DependencyObject>ve türetilmiştir , biraz farklı yollar aracılığıyla. Bu düzeydeki bölme, bir <xref:System.Windows.UIElement> <xref:System.Windows.ContentElement> kullanıcı arabiriminde nasıl kullanıldığı ve bir uygulamada hangi amaca hizmet ettikleri ile ilgilidir. <xref:System.Windows.UIElement>ayrıca, <xref:System.Windows.Media.Visual> alt düzey grafik desteğini ortaya çıkaran bir sınıf olan sınıf [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]hiyerarşisinde de vardır. <xref:System.Windows.Media.Visual>bağımsız dikdörtgen ekran bölgeleri tanımlayarak bir render çerçevesi sağlar. Uygulamada, <xref:System.Windows.UIElement> daha büyük bir nesne modelini destekleyecek öğeler içindir, dikdörtgen ekran bölgeleri olarak tanımlanabilecek ve içerik modelinin farklı öğe kombinasyonlarına izin vermek için kasıtlı olarak daha açık olduğu bölgelere işlemek ve düzenler. <xref:System.Windows.ContentElement><xref:System.Windows.Media.Visual>türetilemiyor; onun modeli, <xref:System.Windows.ContentElement> bir başka bir şey tarafından tüketilen olacağını, daha sonra öğeleri yorumlamak <xref:System.Windows.Media.Visual> [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] ve tüketmek için tam üretmek bir okuyucu veya görüntüleyici gibi. Belirli <xref:System.Windows.UIElement> sınıflar içerik ana bilgisayarları olarak tasarlanmıştır: bir veya <xref:System.Windows.ContentElement> daha<xref:System.Windows.Controls.DocumentViewer> fazla sınıf için barındırma ve işleme sağlar (böyle bir sınıfın bir örneğidir). <xref:System.Windows.ContentElement>biraz daha küçük nesne modellerine sahip öğeler için taban sınıf olarak kullanılır ve bir <xref:System.Windows.UIElement>.  
  
### <a name="framework-level-and-core-level"></a>Çerçeve Düzeyi ve Çekirdek Düzeyi  
 <xref:System.Windows.UIElement>için taban sınıf <xref:System.Windows.FrameworkElement>olarak <xref:System.Windows.ContentElement> hizmet vermektedir ve <xref:System.Windows.FrameworkContentElement>temel sınıf olarak hizmet vermektedir. Bu sonraki sınıf düzeyinin nedeni, WPF çerçeve düzeyinden ayrı bir WPF çekirdek düzeyini desteklemektir ve bu bölüm ApI'lerin PresentationCore ve PresentationFramework derlemeleri arasında nasıl bölündüğü konusunda da mevcuttur. WPF çerçeve düzeyi, sunum için düzen yöneticisinin uygulanması da dahil olmak üzere temel uygulama gereksinimleri için daha eksiksiz bir çözüm sunar. WPF çekirdek düzeyi, ek derlemenin [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ek yükü almadan çoğunu kullanmanın bir yolunu sağlar. Bu düzeyler arasındaki ayrım çok nadiren en tipik uygulama geliştirme senaryoları [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] için önemlidir ve genel olarak bir bütün olarak API'ler düşünmek ve WPF çerçeve düzeyi ve WPF çekirdek düzeyi arasındaki fark ile kendinizi endişe olmamalıdır. Uygulama tasarımınız önemli miktarda WPF çerçeve düzeyi işlevini değiştirmeyi seçiyorsa,örneğin genel çözümünüz zaten [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] kendi kompozisyon ve düzen uygulamalarına sahipse, düzey ayrımları hakkında bilmeniz gerekebilir.  
  
<a name="subclassing_elements"></a>
## <a name="choosing-which-element-to-derive-from"></a>Hangi Öğeden Türene'yi Seç  
 Genişleyen özel bir sınıf oluşturmanın [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] en pratik yolu, varolan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sınıf hiyerarşisi aracılığıyla istediğiniz işlevselliği mümkün olduğunca elde ettiğiniz sınıflardan birinden elde etmektir. Bu bölümde, hangi sınıftan devralacağına karar vermenize yardımcı olacak en önemli öğe sınıflarından üçüyle birlikte gelen işlevsellik listelenmiştir.  
  
 Bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sınıftan türemiş olmak için gerçekten daha yaygın nedenlerden biri olan bir denetim uyguluyorsanız, büyük olasılıkla pratik bir denetim, bir denetim aile <xref:System.Windows.Controls.Control> taban sınıfı veya en azından taban sınıftan bir sınıf türetmek istiyorum. Bazı kılavuz ve pratik örnekler için [bkz.](../controls/control-authoring-overview.md)  
  
 Denetim oluşturmuyorsanız ve hiyerarşide daha yüksek bir sınıftan türemeniz gerekiyorsa, aşağıdaki bölümler her temel öğe sınıfında hangi özelliklerin tanımlandığına yönelik bir kılavuz olarak tasarlanmıştır.  
  
 Bu sınıftan <xref:System.Windows.DependencyObject>türeyen bir sınıf oluşturursanız, aşağıdaki işlevleri devralırsınız:  
  
- <xref:System.Windows.DependencyObject.GetValue%2A>ve <xref:System.Windows.DependencyObject.SetValue%2A> destek ve genel mülkiyet sistemi desteği.  
  
- Bağımlılık özellikleri olarak uygulanan bağımlılık özelliklerini ve ekli özellikleri kullanma yeteneği.  
  
 Bu türleyen bir sınıf <xref:System.Windows.UIElement>oluşturursanız, aşağıdaki işlevleri aşağıdaki lere <xref:System.Windows.DependencyObject>ek olarak devralırsınız:  
  
- Animasyonlu özellik değerleri için temel destek. Daha fazla bilgi için [Animasyona Genel Bakış'a](../graphics-multimedia/animation-overview.md)bakın.  
  
- Temel giriş olay desteği ve komuta desteği. Daha fazla bilgi için [Girişe Genel Bakış](input-overview.md) ve [Komuta Genel Bakışı'na](commanding-overview.md)bakın.  
  
- Bir düzen sistemine bilgi sağlamak için geçersiz kılınabilen sanal yöntemler.  
  
 Bu türleyen bir sınıf <xref:System.Windows.FrameworkElement>oluşturursanız, aşağıdaki işlevleri aşağıdaki lere <xref:System.Windows.UIElement>ek olarak devralırsınız:  
  
- Stil ve film panoları için destek. Daha fazla bilgi <xref:System.Windows.Style> için bkz ve [Storyboards Genel Bakış.](../graphics-multimedia/storyboards-overview.md)  
  
- Veri bağlama desteği. Daha fazla bilgi için bkz: [Veri Bağlama Genel Bakışı.](../../../desktop-wpf/data/data-binding-overview.md)  
  
- Dinamik kaynak başvuruları için destek. Daha fazla bilgi için [Bkz. XAML Kaynakları.](../../../desktop-wpf/fundamentals/xaml-resources-define.md)  
  
- Özellik değeri devralma desteği ve meta verilerdeki diğer bayraklar, özelliklerle ilgili koşulları veri bağlama, stilleri veya düzenin çerçeve uygulaması gibi çerçeve hizmetlerine bildirmeye yardımcı olur. Daha fazla bilgi için [Çerçeve Özelliği Meta verileri'ne](framework-property-metadata.md)bakın.  
  
- Mantıksal ağaç kavramı. Daha fazla bilgi için [WPF'deki Ağaçlar'a](trees-in-wpf.md)bakın.  
  
- Düzeni etkileyen özelliklerdeki değişiklikleri algılayabilen bir <xref:System.Windows.FrameworkElement.OnPropertyChanged%2A> geçersiz kılma da dahil olmak üzere, düzen sisteminin pratik WPF çerçeve düzeyinde uygulanması için destek.  
  
 Bu türleyen bir sınıf <xref:System.Windows.ContentElement>oluşturursanız, aşağıdaki işlevleri aşağıdaki lere <xref:System.Windows.DependencyObject>ek olarak devralırsınız:  
  
- Animasyonlar için destek. Daha fazla bilgi için [Animasyona Genel Bakış'a](../graphics-multimedia/animation-overview.md)bakın.  
  
- Temel giriş olay desteği ve komuta desteği. Daha fazla bilgi için [Girişe Genel Bakış](input-overview.md) ve [Komuta Genel Bakışı'na](commanding-overview.md)bakın.  
  
 Bu türleyen bir sınıf <xref:System.Windows.FrameworkContentElement>oluşturursanız, aşağıdaki işlevleri aşağıdaki tarafından sağlanan <xref:System.Windows.ContentElement>ek olarak alırsınız:  
  
- Stil ve film panoları için destek. Daha fazla bilgi <xref:System.Windows.Style> için bkz ve [Animasyona Genel Bakış.](../graphics-multimedia/animation-overview.md)  
  
- Veri bağlama desteği. Daha fazla bilgi için bkz: [Veri Bağlama Genel Bakışı.](../../../desktop-wpf/data/data-binding-overview.md)  
  
- Dinamik kaynak başvuruları için destek. Daha fazla bilgi için [Bkz. XAML Kaynakları.](../../../desktop-wpf/fundamentals/xaml-resources-define.md)  
  
- Özellik değeri devralma desteği ve meta verilerdeki diğer bayraklar, özelliklerle ilgili koşulları veri bağlama, stilleri veya düzenin çerçeve uygulaması gibi çerçeve hizmetlerine bildirmeye yardımcı olur. Daha fazla bilgi için [Çerçeve Özelliği Meta verileri'ne](framework-property-metadata.md)bakın.  
  
- Düzen sistemi değişikliklerine (örneğin) <xref:System.Windows.FrameworkElement.ArrangeOverride%2A>erişim devralmazsınız. Düzen sistemi uygulamaları yalnızca <xref:System.Windows.FrameworkElement>. Ancak, düzeni <xref:System.Windows.FrameworkElement.OnPropertyChanged%2A> etkileyen özelliklerdeki değişiklikleri algılayabilen ve bunları herhangi bir içerik ana bilgisayara bildirebilen bir geçersiz kılma devralırsınız.  
  
 İçerik modelleri çeşitli sınıflar için belgelenmiştir. Bir sınıfın içerik modeli, türeecek uygun bir sınıf bulmak istiyorsanız göz önünde bulundurmanız gereken olası bir faktördür. Daha fazla bilgi için [WPF İçerik Modeli'ne](../controls/wpf-content-model.md)bakın.  
  
<a name="other_base_classes"></a>
## <a name="other-base-classes"></a>Diğer Taban Sınıfları  
  
### <a name="dispatcherobject"></a>Dispatcherobject  
 <xref:System.Windows.Threading.DispatcherObject>[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] iş parçacığı modeli için destek sağlar ve uygulamalar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] için oluşturulan tüm <xref:System.Windows.Threading.Dispatcher>nesnelerin bir . Bu iş parçacığı modeli <xref:System.Windows.UIElement>desteği <xref:System.Windows.DependencyObject>almak <xref:System.Windows.Media.Visual>için türeterek düşünmelisiniz , veya , türetme <xref:System.Windows.Threading.DispatcherObject> olmasa bile. Daha fazla bilgi için [İş Parçacığı Modeli'ne](threading-model.md)bakın.  
  
### <a name="visual"></a>Görsel  
 <xref:System.Windows.Media.Visual>genellikle kabaca dikdörtgen bir bölgede görsel sunum gerektiren bir 2B nesne kavramını uygular. Bir gerçek <xref:System.Windows.Media.Visual> işleme diğer sınıflarda olur (kendi kendine yeten <xref:System.Windows.Media.Visual> değildir), ancak sınıf çeşitli düzeylerde süreçleri işleme tarafından kullanılan bilinen bir tür sağlar. <xref:System.Windows.Media.Visual>isabet testi uygular, ancak isabet testi pozitif rapor olayları ortaya çıkarmaz (bu bulunmaktadır). <xref:System.Windows.UIElement> Daha fazla bilgi için [Visual Layer Programming'e](../graphics-multimedia/visual-layer-programming.md)bakın.  
  
### <a name="freezable"></a>Freezable  
 <xref:System.Windows.Freezable>değişmez bir nesne gerektiğinde veya performans nedenleriyle istendiğinde nesnenin kopyalarını oluşturmak için araçlar sağlayarak mutable nesnesi içinde değişmezlik simüle eder. Tür, <xref:System.Windows.Freezable> geometriler ve fırçalar gibi belirli grafik öğelerinin yanı sıra animasyonlar için ortak bir temel sağlar. Özellikle, bir <xref:System.Windows.Freezable> değildir; <xref:System.Windows.Media.Visual> başka bir nesnenin <xref:System.Windows.Freezable> özellik değerini doldurmak için uygulandığında alt özellik haline gelen özellikleri tutabilir ve bu alt özellikler işlemeyi etkileyebilir. Daha fazla bilgi için [Freezable Objects Genel Bakış'a](freezable-objects-overview.md)bakın.  
  
 <xref:System.Windows.Media.Animation.Animatable>  
  
 <xref:System.Windows.Media.Animation.Animatable>animasyonlu <xref:System.Windows.Freezable> özelliklerianimasyonolmayan özelliklerden ayırt edilebilmek için özellikle animasyon denetim katmanı ve bazı yardımcı program üyeleri ekleyen türetilmiş bir sınıftır.  
  
### <a name="control"></a>Denetim  
 <xref:System.Windows.Controls.Control>teknolojiye bağlı olarak, çeşitli bir denetim veya bileşen olarak adlandırılan nesne türü için amaçlanan taban sınıftır. Genel olarak, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetim sınıfları doğrudan bir UI denetimini temsil eden veya denetim kompozisyonuna yakından katılan sınıflardır. Etkinleştiren <xref:System.Windows.Controls.Control> birincil işlevsellik, baştan çıkarıcı denetimi denetlemektir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.Control>
- [Bağımlılık Özelliklerine Genel Bakış](dependency-properties-overview.md)
- [Denetim Yazımına Genel Bakış](../controls/control-authoring-overview.md)
- [WPF Mimarisi](wpf-architecture.md)
