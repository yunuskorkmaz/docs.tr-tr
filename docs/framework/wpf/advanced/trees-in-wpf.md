---
title: Ağaç
ms.date: 03/30/2017
helpviewer_keywords:
- logical tree [WPF]
- element tree [WPF]
- visual tree [WPF]
ms.assetid: e83f25e5-d66b-4fc7-92d2-50130c9a6649
ms.openlocfilehash: aed4350f1a7084b7894a70ac9d6d00cf25b39e34
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646195"
---
# <a name="trees-in-wpf"></a>WPF İçinde Ağaçlar
Birçok teknolojide, öğeler ve bileşenler, geliştiricilerin bir uygulamanın oluşturma veya davranışını etkilemek için ağaçtaki nesne düğümlerini doğrudan manipüle ettiği bir ağaç yapısında düzenlenir. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]ayrıca program öğeleri arasındaki ilişkileri tanımlamak için çeşitli ağaç yapısı metaforları kullanır. WPF geliştiricileri çoğunlukla, nesne ağacı metaforu hakkında kavramsal olarak düşünürken kod lu bir uygulama oluşturabilir veya XAML'de uygulamanın bölümlerini tanımlayabilir, ancak XML DOM'da kullanabileceğiniz bazı genel nesne ağacı işleme API'leri yerine belirli API'leri çağırabilir veya bunu yapmak için belirli biçimlendirmeyi kullanacaktır. WPF, <xref:System.Windows.LogicalTreeHelper> ağaç metaforu görünümü sağlayan iki <xref:System.Windows.Media.VisualTreeHelper>yardımcı sınıfı ortaya çıkarır ve . Bu aynı ağaçlar belirli anahtar WPF özelliklerinin davranışını anlamak için yararlı olduğundan, görsel ağaç ve mantıksal ağaç terimleri De WPF belgelerinde kullanılır. Bu konu görsel ağacın ve mantıksal ağacın neyi temsil etmesini tanımlar, bu tür ağaçların <xref:System.Windows.LogicalTreeHelper> genel <xref:System.Windows.Media.VisualTreeHelper>bir nesne ağacı kavramıyla nasıl ilişkili olduğunu tartışır ve tanıyıp s.  

<a name="element_tree"></a>
## <a name="trees-in-wpf"></a>WPF İçinde Ağaçlar  
 En eksiksiz ağaç [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yapısı nesne ağacıdır. Bir uygulama sayfasını tanımlar [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ve sonra [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]yüklerseniz, ağaç yapısı biçimlendirmedeki öğelerin iç içe geçme ilişkilerine göre oluşturulur. Bir uygulamayı veya uygulamanın bir bölümünü kodolarak tanımlarsanız, ağaç yapısı, belirli bir nesne için içerik modelini uygulayan özellikler için özellik değerlerini nasıl atadığınıza bağlı olarak oluşturulur. Burada, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]tam nesne ağacının kavramsallaştırılan ve genel API'sine bildirilebilen iki yol vardır: mantıksal ağaç ve görsel ağaç olarak. Mantıksal ağaç ve görsel ağaç arasındaki ayrımlar her zaman önemli olmayabilir, ancak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bazen belirli alt sistemlerle ilgili sorunlara neden olabilir ve biçimlendirme veya kodda yaptığınız seçimleri etkileyebilir.  
  
 Mantıksal ağacı veya görsel ağacı her zaman doğrudan manipüle etmeseniz de, ağaçların nasıl etkileşime girdiği kavramlarını anlamak WPF'yi bir teknoloji olarak anlamak için yararlıdır. WPF'nin bir tür ağaç metaforu olarak düşünülmesi, mülkiyet mirasının [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ve olay yönlendirmenin nasıl çalıştığını anlamak için de çok önemlidir.  
  
> [!NOTE]
> Nesne ağacı gerçek bir API'den çok bir kavram olduğundan, kavramı düşünmenin başka bir yolu nesne grafiğidir. Uygulamada, ağaç metaforunun bozulacağı çalışma zamanında nesneler arasında ilişkiler vardır. Bununla birlikte, özellikle XAML tanımlı UI ile, ağaç metaforu, bu genel kavrama atıfta bulunurken çoğu WPF dokümantasyonunun nesne ağacı terimini kullanacağı kadar alakalıdır.  
  
<a name="logical_tree"></a>
## <a name="the-logical-tree"></a>Mantıksal Ağaç  
 In, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]bu öğeleri destekleyen nesnelerin özelliklerini ayarlayarak Kullanıcı Birliğini öğelerine içerik eklersiniz. Örneğin, <xref:System.Windows.Controls.ItemsControl.Items%2A> özelliğini değiştirerek <xref:System.Windows.Controls.ListBox> denetime öğeler eklersiniz. Bunu yaparak, <xref:System.Windows.Controls.ItemCollection> <xref:System.Windows.Controls.ItemsControl.Items%2A> öğeleri özellik değeri olan içine yerleştirdiğiniz. Benzer şekilde, bir <xref:System.Windows.Controls.DockPanel>, onun <xref:System.Windows.Controls.Panel.Children%2A> özellik değerini işlemek nesneleri eklemek için. Burada, nesneleri <xref:System.Windows.Controls.UIElementCollection>ekliyoruz. Kod örneği için [bkz: Bir Öğeyi Dinamik olarak ekleyin.](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms752374(v=vs.100))  
  
 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]Liste <xref:System.Windows.Controls.ListBox> öğelerini bir veya denetime veya diğer UI <xref:System.Windows.Controls.DockPanel>öğelerine yerleştirdiğinizde, aşağıdaki örnekte olduğu gibi açık veya örtülü olarak <xref:System.Windows.Controls.ItemsControl.Items%2A> öğeleri ve <xref:System.Windows.Controls.Panel.Children%2A> özellikleri de kullanırsınız.  
  
 [!code-xaml[TreeOvwsSupport#AllCode](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeOvwsSupport/CS/page1.xaml#allcode)]  
  
 Bu XAML'yi bir belge nesnesi modeli altında XML olarak işlediyseniz ve örtülü olarak yorumlanan etiketleri (yasal olurdu) dahil ettiyseniz, ortaya çıkan XML DOM ağacı ve diğer örtük öğeler için `<ListBox.Items>` öğeler içerirdi. Ancak XAML, biçimlendirmeyi okuyup nesnelere yazdığınızda bu şekilde işlemez, ortaya `ListBox.Items`çıkan nesne grafiği tam anlamıyla içermez. Ancak, xaml `Items` işlendiğinde <xref:System.Windows.Controls.ItemCollection>bir , <xref:System.Windows.Controls.ItemCollection> ve başlatılan ancak <xref:System.Windows.Controls.ListBox> boş adlı bir <xref:System.Windows.Controls.ListBox> özelliği vardır. Daha sonra, içerik olarak var olan <xref:System.Windows.Controls.ListBox> her alt <xref:System.Windows.Controls.ItemCollection> nesne öğesi `ItemCollection.Add`için parser çağrıları tarafından eklenir. XAML'yi bir nesne ağacına işlemenin bu örneği, şimdiye kadar oluşturulmuş nesne ağacının temelde mantıksal ağaç olduğu bir örnektir.  
  
 Ancak, mantıksal ağaç, xaml örtülü sözdizimi öğeleri dışa vursa bile, çalışma zamanında uygulama kullanıcı arabirimi için var olan tüm nesne grafiği değildir. Bunun temel nedeni görseller ve şablonlardır. Örneğin, <xref:System.Windows.Controls.Button>göz önünde bulundurun. Mantıksal ağaç nesneyi <xref:System.Windows.Controls.Button> ve ayrıca `Content`dizesini bildirir. Ancak çalışma zamanı nesne ağacında bu düğmenin devamı vardır. Özellikle, belirli <xref:System.Windows.Controls.Button> bir denetim şablonu uygulandığından düğme yalnızca ekranda olduğu gibi görünür. Uygulamalı bir şablondan gelen görseller (görsel düğmenin etrafındaki koyu gri şablonu <xref:System.Windows.Controls.Border> gibi) çalışma süresi sırasında mantıksal ağaca bakıyor sanız (görünür UI'den bir giriş olayını işlemek ve ardından mantıksal ağacı okumak gibi) mantıksal ağaçta bildirilmez. Şablon görsellerini bulmak için, bunun yerine görsel ağacı incelemeniz gerekir.  
  
 Oluşturulan nesne grafiğine [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sözdizimi haritaları ve XAML'deki örtük sözdizimi hakkında daha [XAML Overview (WPF)](../../../desktop-wpf/fundamentals/xaml.md)fazla bilgi için [bkz.](xaml-syntax-in-detail.md)  
  
<a name="tree_property_inheritance_event_routing"></a>
### <a name="the-purpose-of-the-logical-tree"></a>Mantıksal Ağacın Amacı  
 Mantıksal ağaç, içerik modellerinin olası alt nesneleri üzerinde kolayca tekrarlanabilmesi ve içerik modellerinin genişletilebilmeleri için vardır. Ayrıca, mantıksal ağaç, mantıksal ağaçtaki tüm nesnelerin yüklenmesi gibi belirli bildirimler için bir çerçeve sağlar. Temel olarak, mantıksal ağaç, görselleri dışlayan, ancak kendi çalışma süresi uygulamanızın kompozisyonuna karşı birçok sorgu işlemi için yeterli olan çerçeve düzeyindeki bir çalışma zamanı nesnesi grafiğinin yaklaşık olarak algılanmasıdır.  
  
 Buna ek olarak, hem statik hem de dinamik kaynak başvuruları, <xref:System.Windows.FrameworkElement.Resources%2A> ilk isteyen nesnedeki koleksiyonlar için mantıksal ağaca yukarı bakarak <xref:System.Windows.FrameworkElement> ve <xref:System.Windows.FrameworkContentElement>ardından `Resources` mantıksal ağacı <xref:System.Windows.ResourceDictionary>(veya) muhtemelen bu anahtarı içeren başka bir değer için her biri (veya) denetleyerek çözülür. Mantıksal ağaç, hem mantıksal ağaç hem de görsel ağaç bulunduğunda kaynak araması için kullanılır. Kaynak sözlükleri ve arama hakkında daha fazla bilgi için [Bkz. XAML Kaynakları.](../../../desktop-wpf/fundamentals/xaml-resources-define.md)  
  
<a name="composition"></a>
### <a name="composition-of-the-logical-tree"></a>Mantıksal Ağacın Bileşimi  
 Mantıksal ağaç WPF çerçeve düzeyinde tanımlanır, bu da mantıksal ağaç işlemleri için en alakalı WPF <xref:System.Windows.FrameworkContentElement>temel öğesiya ya da <xref:System.Windows.FrameworkElement> . Ancak, API'yi gerçekten kullanıp kullanmadığınızı <xref:System.Windows.LogicalTreeHelper> görebileceğiniz gibi, mantıksal ağaç <xref:System.Windows.FrameworkElement> <xref:System.Windows.FrameworkContentElement>bazen olmayan düğümler veya . Örneğin, mantıksal ağaç bir <xref:System.Windows.Controls.TextBlock.Text%2A> dize <xref:System.Windows.Controls.TextBlock>olan bir , değerini bildirir.  
  
<a name="override_logical_tree"></a>
### <a name="overriding-the-logical-tree"></a>Mantıksal Ağacı Geçersiz Kılma  
 Gelişmiş denetim yazarları, genel bir nesnenin veya içerik modelinin mantıksal ağaç içindeki nesneleri nasıl eklediği veya kaldırdığını tanımlayan birkaç API'yi geçersiz kılarak mantıksal ağacı geçersiz kılabilir. Mantıksal ağacı nasıl geçersiz kılılabildiğini görmek için [bkz.](how-to-override-the-logical-tree.md)  
  
<a name="pvi"></a>
### <a name="property-value-inheritance"></a>Özellik Değeri Kalıtımı  
 Özellik değeri devralma melez bir ağaç üzerinden çalışır. Özellik devralma sağlayan <xref:System.Windows.FrameworkPropertyMetadata.Inherits%2A> özelliği içeren gerçek meta veri WPF çerçeve <xref:System.Windows.FrameworkPropertyMetadata> düzeyinde sınıftır. Bu nedenle, hem özgün değeri tutan üst öğe hem de bu <xref:System.Windows.FrameworkElement> <xref:System.Windows.FrameworkContentElement>değeri devralan alt nesne nin her ikisi de olması veya , her ikisi de bazı mantıksal ağacın bir parçası olmalıdır. Ancak, özellik devralma destekleyen varolan WPF özellikleri için, özellik değeri devralma mantıksal ağaç olmayan bir araya gelen bir nesne üzerinden sürdürmek mümkün. Esas olarak bu, şablon öğelerinin şablonlanan örnekte veya sayfa düzeyinde kompozisyonun hala daha yüksek düzeylerde ve bu nedenle mantıksal ağaçta daha yüksek olan bazı kalıtsal özellik değerlerini kullanması yla ilgilidir. Özellik değeri devralmasının böyle bir sınır boyunca tutarlı bir şekilde çalışabilmesi için, devralan özelliğin ekli bir özellik olarak kaydedilmesi gerekir ve özellik devralma davranışıyla özel bir bağımlılık özelliği tanımlamayı planlıyorsanız bu deseni izlemeniz gerekir. Özellik devralma için kullanılan tam ağaç, çalışma zamanında bile yardımcı sınıf yardımcı programı yöntemi yle tamamen beklenemez. Daha fazla bilgi için [Bkz. Özellik Değeri Devralma.](property-value-inheritance.md)  
  
<a name="two_trees"></a>
## <a name="the-visual-tree"></a>Görsel Ağaç  
 Mantıksal ağaç kavramına ek olarak, görsel ağaç kavramı da [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]vardır. Görsel ağaç, <xref:System.Windows.Media.Visual> temel sınıf tarafından temsil edildiği gibi görsel nesnelerin yapısını açıklar. Denetim için bir şablon yazdığınızda, bu denetim için geçerli olan görsel ağacı tanımlıyor veya yeniden tanımlıyorsunuz. Görsel ağaç, performans ve optimizasyon nedenleriyle çizim üzerinde alt düzey denetim isteyen geliştiricilerin de ilgisini çekmiştir. Geleneksel [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama programlamanın bir parçası olarak görsel ağacın bir pozlama, yönlendirilmiş bir olay için olay yolları çoğunlukla görsel ağaç değil, mantıksal ağaç boyunca seyahat olmasıdır. Yönlendirilen olay davranışının bu inceliği, bir denetim yazarı değilseniz hemen belirgin olmayabilir. Olayları görsel ağaç üzerinden yönlendirme, olayları işlemek veya olay ayarlayıcıları oluşturmak için görsel düzeyde kompozisyon uygulayan denetimleri sağlar.  
  
<a name="trees_content"></a>
## <a name="trees-content-elements-and-content-hosts"></a>Ağaçlar, İçerik Öğeleri ve İçerik Barındıran  
 İçerik öğeleri (türetilen <xref:System.Windows.ContentElement>sınıflar) görsel ağacın bir parçası değildir; onlar <xref:System.Windows.Media.Visual> miras yok ve görsel bir temsil iyyok. Kullanıcı Arabirimi'nde görünmesi için, <xref:System.Windows.ContentElement> hem bir <xref:System.Windows.Media.Visual> hem de mantıksal bir ağaç katılımcısı olan bir içerik ana bilgisayarda barındırılması gerekir. Genellikle böyle bir <xref:System.Windows.FrameworkElement>nesne bir . İçerik ana bilgisayar barındıran bir şekilde içerik için bir "tarayıcı" gibi olduğunu kavramsallaştırabilir ve bu içeriğin ana bilgisayar denetimleri için ekran bölgesinde nasıl görüntüleneceğini seçebilirsiniz. İçerik barındırıldığında, içerik normalde görsel ağaçla ilişkili belirli ağaç işlemlerinde katılımcı yapılabilir. Genellikle, <xref:System.Windows.FrameworkElement> barındırılan içerik gerçek görsel <xref:System.Windows.ContentElement> ağacın bir parçası olmasa da, ana bilgisayar sınıfı, içerik mantıksal ağacın alt düğümleri aracılığıyla olay rotasına barındırılan herhangi bir uygulama kodu içerir. Bu, bir yönlendirilmiş olay kendisi dışında herhangi bir <xref:System.Windows.ContentElement> öğeye yönlendirir kaynak böylece gereklidir.  
  
<a name="tree_traversal"></a>
## <a name="tree-traversal"></a>Ağaç Traversal  
 Sınıf, <xref:System.Windows.LogicalTreeHelper> mantıksal <xref:System.Windows.LogicalTreeHelper.GetParent%2A>ağaç <xref:System.Windows.LogicalTreeHelper.FindLogicalNode%2A> geçişi için , ve yöntemleri sağlar. <xref:System.Windows.LogicalTreeHelper.GetChildren%2A> Çoğu durumda, varolan denetimlerin mantıksal ağacında geçiş yapmak zorunda kalmamalısınız, çünkü bu denetimler mantıksal alt öğelerini, bir dizin oluşturma, dizini gibi `Add`koleksiyon erişimini destekleyen özel bir koleksiyon özelliği olarak hemen hemen her zaman ortaya çıkarır. Ağaç geçişi esas olarak, koleksiyon özelliklerinin zaten tanımlandığı <xref:System.Windows.Controls.ItemsControl> veya <xref:System.Windows.Controls.Panel> tanımlandığı gibi amaçlanan denetim desenlerinden türemeyi seçen ve kendi toplama özelliği desteğini sağlamayı amaçlayan denetim yazarları tarafından kullanılan bir senaryodur.  
  
 Görsel ağaç da görsel ağaç geçiş için bir <xref:System.Windows.Media.VisualTreeHelper>yardımcı sınıf destekler. Görsel ağaç denetime özgü özellikler aracılığıyla uygun şekilde <xref:System.Windows.Media.VisualTreeHelper> açıklanmaz, bu nedenle programlama senaryonuz için gerekliyse sınıf görsel ağacı geçmeniz için önerilen yoldur. Daha fazla bilgi için [WPF Grafik Oluşturma Genel Bakış'a](../graphics-multimedia/wpf-graphics-rendering-overview.md)bakın.  
  
> [!NOTE]
> Bazen uygulanan bir şablonun görsel ağacını incelemek gerekir. Bu tekniği kullanırken dikkatli olmalısınız. Şablonu tanımladığınız bir denetim için görsel bir ağaçta geçiş yapsanız bile, denetiminizin <xref:System.Windows.Controls.Control.Template%2A> tüketicileri özelliği örneklere göre ayarlayarak şablonu her zaman değiştirebilir ve hatta son kullanıcı bile sistem tesini değiştirerek uygulanan şablonu etkileyebilir.  
  
<a name="routes"></a>
## <a name="routes-for-routed-events-as-a-tree"></a>"Ağaç" Olarak Yönlendirilen Etkinlikler için Rotalar  
 Daha önce de belirtildiği gibi, herhangi bir yönlendirilmiş olayın rotası, görsel ve mantıksal ağaç gösterimlerinin bir melezi olan bir ağacın tek ve önceden belirlenmiş bir yolu boyunca ilerler. Olay rotası, bir tünel veya köpüren yönlendirilmiş olay olup olmadığına bağlı olarak ağaç içinde yukarı veya aşağı yönde seyahat edebilir. Olay rotası kavramı, olay rotasını gerçekten yönlendiren bir olayı yükseltmekten bağımsız olarak "yürümek" için kullanılabilecek doğrudan destekleyici bir yardımcı sınıfa sahip değildir. Rotayı temsil eden bir <xref:System.Windows.EventRoute>sınıf vardır, ancak bu sınıfın yöntemleri genellikle yalnızca iç kullanım içindir.  
  
<a name="resourcesandtrees"></a>
## <a name="resource-dictionaries-and-trees"></a>Kaynak Sözlükleri ve Ağaçlar  
 Bir sayfada tanımlanan `Resources` tüm kaynak sözlüğü aramatemelde mantıksal ağaç geçer. Mantıksal ağaçta olmayan nesneler anahtarlı kaynaklara başvurulabilir, ancak kaynak arama sırası, bu nesnenin mantıksal ağaca bağlı olduğu noktada başlar. WPF'de, yalnızca mantıksal ağaç düğümleri içeren `Resources` <xref:System.Windows.ResourceDictionary>bir özelliğe sahip olabilir, bu nedenle bir <xref:System.Windows.ResourceDictionary>anahtarlı kaynakları arayan görsel ağaç geçiş hiçbir yararı yoktur .  
  
 Ancak, kaynak arama da hemen mantıksal ağaç ötesine uzanabilir. Uygulama biçimlendirmesi için kaynak araması daha sonra uygulama düzeyindeki kaynak sözlüklerine ve ardından statik özellikler veya anahtarlar olarak başvurulan tema desteğine ve sistem değerlerine devam edebilir. Kaynak başvuruları dinamikse, temaların kendileri de tema mantıksal ağacının dışındaki sistem değerlerine başvurur. Kaynak sözlükleri ve arama mantığı hakkında daha fazla bilgi için [Bkz. XAML Kaynakları.](../../../desktop-wpf/fundamentals/xaml-resources-define.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Girişe Genel Bakış](input-overview.md)
- [WPF Grafik İşlemeye Genel Bakış](../graphics-multimedia/wpf-graphics-rendering-overview.md)
- [Gönderilmiş Olaylara Genel Bakış](routed-events-overview.md)
- [Nesne Ağacında Olmayan Nesne Öğelerini Başlatma](initialization-for-object-elements-not-in-an-object-tree.md)
- [WPF Mimarisi](wpf-architecture.md)
