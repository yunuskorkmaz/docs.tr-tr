---
title: Temel Öğelere Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- base elements [WPF]
ms.assetid: 2c997092-72c6-4767-bc84-74267f4eee72
ms.openlocfilehash: 823c81bf6b21b88d719503387a68ce6e7d643d61
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740916"
---
# <a name="base-elements-overview"></a>Temel Öğelere Genel Bakış
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] sınıfının yüksek yüzdesi, SDK belgelerinde genellikle temel öğe sınıfları olarak adlandırılan dört sınıftan türetilir. Bu sınıflar <xref:System.Windows.UIElement>, <xref:System.Windows.FrameworkElement>, <xref:System.Windows.ContentElement>ve <xref:System.Windows.FrameworkContentElement>. <xref:System.Windows.DependencyObject> sınıfı da ilişkili olduğundan, hem <xref:System.Windows.UIElement> hem de ortak bir temel sınıf olduğundan <xref:System.Windows.ContentElement>  

<a name="base_apis"></a>   
## <a name="base-element-apis-in-wpf-classes"></a>WPF sınıflarında temel öğe API 'Leri  
 <xref:System.Windows.UIElement> ve <xref:System.Windows.ContentElement> her ikisi de biraz farklı yol yollarla <xref:System.Windows.DependencyObject>türetilir. Bu düzeyin bölünmesi, bir <xref:System.Windows.UIElement> veya <xref:System.Windows.ContentElement> bir kullanıcı arabiriminde nasıl kullanıldığı ve bir uygulamada hangi amaçla kullanılacağı ile ilgilidir. <xref:System.Windows.UIElement> Ayrıca, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]temeldeki alt düzey grafik desteğini sunan bir sınıf olan sınıf hiyerarşisinde <xref:System.Windows.Media.Visual> sahiptir. <xref:System.Windows.Media.Visual> bağımsız dikdörtgen ekran bölgelerini tanımlayarak bir işleme çerçevesi sağlar. Pratikte, daha büyük bir nesne modelini destekleyecek öğeler için <xref:System.Windows.UIElement>, dikdörtgen ekran bölgesi olarak açıklanabilecek bölgelerin işlenmesine ve düzenine göre ve farklı kombinasyonlara izin vermek için içerik modelinin daha fazla açık olması için tasarlanmıştır öğe. <xref:System.Windows.ContentElement> <xref:System.Windows.Media.Visual>türetilmez; modeli, bir <xref:System.Windows.ContentElement> başka bir şey tarafından tüketilecektir. Bu, daha sonra öğelerin yorumlanması ve [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] kullanım için tüm <xref:System.Windows.Media.Visual> üretecektir. Belirli <xref:System.Windows.UIElement> sınıflarının içerik Konakları olması amaçlanmıştır: bir veya daha fazla <xref:System.Windows.ContentElement> sınıfı için barındırma ve işleme sağlar (<xref:System.Windows.Controls.DocumentViewer> böyle bir sınıfa bir örnektir). <xref:System.Windows.ContentElement>, biraz daha küçük nesne modelleriyle öğeler için temel sınıf olarak kullanılır ve bir <xref:System.Windows.UIElement>içinde barındırılabilecek metin, bilgi veya belge içeriğini daha fazla ele alabilir.  
  
### <a name="framework-level-and-core-level"></a>Çerçeve düzeyi ve çekirdek düzeyi  
 <xref:System.Windows.UIElement> <xref:System.Windows.FrameworkElement>için temel sınıf işlevi görür ve <xref:System.Windows.ContentElement> <xref:System.Windows.FrameworkContentElement>için temel sınıf olarak hizmet verir. Bu sonraki sınıf düzeyinin nedeni, bir WPF çerçeve düzeyinden ayrı bir WPF Core düzeyini destekliyoruz. Bu bölüm, aynı zamanda API 'Lerin PresentationCore ve PresentationFramework derlemeleri arasında nasıl bölüneceğini de var. WPF framework düzeyi, sununun düzen yöneticisinin uygulanması dahil olmak üzere temel uygulama gereksinimlerine yönelik daha kapsamlı bir çözüm sunar. WPF çekirdek düzeyi, ek derlemenin ek yükünü almadan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] çoğunu kullanmanın bir yolunu sunar. Bu düzeyler arasındaki ayrım, çoğu tipik uygulama geliştirme senaryosunda çok nadir olarak önemlidir ve genel olarak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] API 'Leri bir bütün olarak düşünmeniz ve WPF framework düzeyi ile WPF çekirdek düzeyi arasındaki fark ile ilgilenmemelisiniz. Uygulama tasarımınız, büyük miktarlarda WPF çerçevesi düzeyi işlevini değiştirmeyi seçerse, örneğin genel çözümünüz kendi [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] kompozisyonunun uygulamalarına zaten sahipse ve Düzenle.  
  
<a name="subclassing_elements"></a>   
## <a name="choosing-which-element-to-derive-from"></a>Hangi öğenin türetileceğini seçme  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] genişleten özel bir sınıf oluşturmanın en pratik yolu, mevcut sınıf hiyerarşisi aracılığıyla istediğiniz işlevselliklerinizin mümkün olduğunca büyük bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sınıftan türetiliyor. Bu bölümde, hangi sınıfa kalýtýmla karar vermenize yardımcı olmak için en önemli öğe sınıflarından üçüne sahip olan işlevler listelenmiştir.  
  
 Bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sınıfından Türetmenin daha yaygın nedenlerinden biri olan bir denetim uygulamadıysanız, muhtemelen pratik denetim, denetim ailesi temel sınıfı olan bir sınıftan veya en azından <xref:System.Windows.Controls.Control> temel sınıftan türetebilirsiniz. Bazı rehberlik ve pratik örnekler için bkz. [Denetim yazma genel bakış](../controls/control-authoring-overview.md).  
  
 Bir denetim oluşturmadıysanız ve hiyerarşide daha yüksek bir sınıftan türetmeniz gerekiyorsa, aşağıdaki bölümler her bir temel öğe sınıfında hangi özelliklerin tanımlandıklarından oluşan bir kılavuz olarak hazırlanmıştır.  
  
 <xref:System.Windows.DependencyObject>türetilen bir sınıf oluşturursanız, aşağıdaki işlevleri alırsınız:  
  
- <xref:System.Windows.DependencyObject.GetValue%2A> ve <xref:System.Windows.DependencyObject.SetValue%2A> desteği ve genel özellik sistemi desteği.  
  
- Bağımlılık özelliklerini ve bağımlılık özellikleri olarak uygulanan iliştirilmiş özellikleri kullanma özelliği.  
  
 <xref:System.Windows.UIElement>türetilen bir sınıf oluşturursanız, <xref:System.Windows.DependencyObject>tarafından sağlana ek olarak aşağıdaki işlevselliği de devralınmıştır:  
  
- Animasyonlu özellik değerleri için Temel destek. Daha fazla bilgi için bkz. [animasyon genel bakış](../graphics-multimedia/animation-overview.md).  
  
- Temel giriş olayı desteği ve komut verme desteği. Daha fazla bilgi için bkz. [girişe genel bakış](input-overview.md) ve [verme genel bakış](commanding-overview.md).  
  
- Bir düzen sistemine bilgi sağlamak için geçersiz kılınabilen sanal yöntemler.  
  
 <xref:System.Windows.FrameworkElement>türetilen bir sınıf oluşturursanız, <xref:System.Windows.UIElement>tarafından sağlana ek olarak aşağıdaki işlevselliği de devralınmıştır:  
  
- Stil ve film şeritleri için destek. Daha fazla bilgi için bkz. <xref:System.Windows.Style> ve görsel taslaklara [genel bakış](../graphics-multimedia/storyboards-overview.md).  
  
- Veri bağlama desteği. Daha fazla bilgi için bkz. [veri bağlamaya genel bakış](../data/data-binding-overview.md).  
  
- Dinamik kaynak başvuruları desteği. Daha fazla bilgi için bkz. [xaml kaynakları](../../../desktop-wpf/fundamentals/xaml-resources-define.md).  
  
- Özellik değeri devralma desteği ve meta verilerde bulunan ve veri bağlama, stiller ya da düzenin çerçeve uygulamasıyla ilgili özellikler hakkındaki koşullara rapor veren diğer bayraklar. Daha fazla bilgi için bkz. [Framework özelliği meta verileri](framework-property-metadata.md).  
  
- Mantıksal ağaç kavramı. Daha fazla bilgi için bkz. [WPF Içindeki ağaçlar](trees-in-wpf.md).  
  
- Düzeni etkileyen özelliklerde yapılan değişiklikleri algılayabilen <xref:System.Windows.FrameworkElement.OnPropertyChanged%2A> bir geçersiz kılma da dahil olmak üzere, düzen sisteminin pratik WPF framework düzeyi uygulamasına yönelik destek.  
  
 <xref:System.Windows.ContentElement>türetilen bir sınıf oluşturursanız, <xref:System.Windows.DependencyObject>tarafından sağlana ek olarak aşağıdaki işlevselliği de devralınmıştır:  
  
- Animasyonlar için destek. Daha fazla bilgi için bkz. [animasyon genel bakış](../graphics-multimedia/animation-overview.md).  
  
- Temel giriş olayı desteği ve komut verme desteği. Daha fazla bilgi için bkz. [girişe genel bakış](input-overview.md) ve [verme genel bakış](commanding-overview.md).  
  
 <xref:System.Windows.FrameworkContentElement>türetilen bir sınıf oluşturursanız, <xref:System.Windows.ContentElement>tarafından sağlana ek olarak aşağıdaki işlevselliği alırsınız:  
  
- Stil ve film şeritleri için destek. Daha fazla bilgi için bkz. <xref:System.Windows.Style> ve [animasyona genel bakış](../graphics-multimedia/animation-overview.md).  
  
- Veri bağlama desteği. Daha fazla bilgi için bkz. [veri bağlamaya genel bakış](../data/data-binding-overview.md).  
  
- Dinamik kaynak başvuruları desteği. Daha fazla bilgi için bkz. [xaml kaynakları](../../../desktop-wpf/fundamentals/xaml-resources-define.md).  
  
- Özellik değeri devralma desteği ve meta verilerde bulunan ve veri bağlama, stiller ya da düzenin çerçeve uygulamasıyla ilgili özellikler hakkındaki koşullara rapor veren diğer bayraklar. Daha fazla bilgi için bkz. [Framework özelliği meta verileri](framework-property-metadata.md).  
  
- Düzen sistemi değişikliklerine erişimi (örneğin, <xref:System.Windows.FrameworkElement.ArrangeOverride%2A>) devralma. Düzen sistem uygulamaları yalnızca <xref:System.Windows.FrameworkElement>kullanılabilir. Ancak, düzeni etkileyen özelliklerde yapılan değişiklikleri algılayabilen ve bunları herhangi bir içerik konağına rapor eden bir <xref:System.Windows.FrameworkElement.OnPropertyChanged%2A> geçersiz kılmayı kalılarsınız.  
  
 İçerik modelleri çeşitli sınıflar için belgelenmiştir. Bir sınıf için içerik modeli, ' den türetmeye uygun bir sınıf bulmak istiyorsanız göz önünde bulundurmanız gereken tek bir faktördür. Daha fazla bilgi için bkz. [WPF Içerik modeli](../controls/wpf-content-model.md).  
  
<a name="other_base_classes"></a>   
## <a name="other-base-classes"></a>Diğer temel sınıflar  
  
### <a name="dispatcherobject"></a>DispatcherObject  
 <xref:System.Windows.Threading.DispatcherObject>, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] iş parçacığı modeli için destek sağlar ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalar için oluşturulan tüm nesnelerin bir <xref:System.Windows.Threading.Dispatcher>ile ilişkilendirilmesini sağlar. <xref:System.Windows.UIElement>, <xref:System.Windows.DependencyObject>veya <xref:System.Windows.Media.Visual>türetmeseniz bile, bu iş parçacığı modeli desteğini almak için <xref:System.Windows.Threading.DispatcherObject> türetmeye göz önünde bulundurmanız gerekir. Daha fazla bilgi için bkz. [Iş parçacığı modeli](threading-model.md).  
  
### <a name="visual"></a>Görsel  
 <xref:System.Windows.Media.Visual>, genellikle kabaca dikdörtgen bir bölgede görsel sunumu gerektiren bir 2B nesne kavramını uygular. <xref:System.Windows.Media.Visual> gerçek işleme diğer sınıflarda gerçekleşir (kendi kendine dahil değildir), ancak <xref:System.Windows.Media.Visual> sınıfı, işlemleri çeşitli düzeylerde işlerken kullanılan bilinen bir tür sağlar. <xref:System.Windows.Media.Visual> isabet testi uygular, ancak isabet testi pozitiflerini (bunlar <xref:System.Windows.UIElement>) rapor eden olayları açığa çıkarır. Daha fazla bilgi için bkz. [Görsel Katman Programlama](../graphics-multimedia/visual-layer-programming.md).  
  
### <a name="freezable"></a>Freezable  
 <xref:System.Windows.Freezable>, sabit bir nesne gerektiğinde veya performans nedenleriyle istenen nesnenin kopyalarını oluşturmak için bir değer sunarak kesilebilir bir nesnede dengesssliği taklit eder. <xref:System.Windows.Freezable> türü, geometriler ve fırçalar gibi belirli grafik öğelerine ve animasyonların yanı sıra animasyon ve fırçalar gibi ortak bir temel sağlar. Özellikle, bir <xref:System.Windows.Freezable> <xref:System.Windows.Media.Visual>değildir; <xref:System.Windows.Freezable> başka bir nesnenin özellik değerini dolduracak şekilde uygulandığında alt özellikler haline gelen özellikleri tutabilir ve bu alt özellikler işlemeyi etkileyebilir. Daha fazla bilgi için bkz. [Freezable nesnelerine genel bakış](freezable-objects-overview.md).  
  
 <xref:System.Windows.Media.Animation.Animatable>  
  
 <xref:System.Windows.Media.Animation.Animatable>, Animasyon denetim katmanını ve bazı yardımcı üyelerini, şu anda animasyon uygulanmış özelliklerden ayırt edilebilir olacak şekilde özel olarak ekleyen bir <xref:System.Windows.Freezable> türetilmiş sınıftır.  
  
### <a name="control"></a>Denetim  
 <xref:System.Windows.Controls.Control>, teknolojiden bağlı olarak bir denetim veya bileşen variously olan nesne türü için amaçlanan temel sınıftır. Genel olarak, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetim sınıfları doğrudan bir UI denetimini temsil eden veya denetim kompozisyonunu yakından katılan sınıflardır. <xref:System.Windows.Controls.Control> izin veren birincil işlevsellik, denetim şablonu oluşturma ' dır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.Control>
- [Bağımlılık Özelliklerine Genel Bakış](dependency-properties-overview.md)
- [Denetim Yazımına Genel Bakış](../controls/control-authoring-overview.md)
- [WPF Mimarisi](wpf-architecture.md)
