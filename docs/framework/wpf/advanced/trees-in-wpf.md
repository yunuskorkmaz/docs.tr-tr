---
title: "WPF İçinde Ağaçlar"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- logical tree [WPF]
- element tree [WPF]
- visual tree [WPF]
ms.assetid: e83f25e5-d66b-4fc7-92d2-50130c9a6649
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 363d81ff0e4262ce0c8252ada3625bb9a157f5a1
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="trees-in-wpf"></a>WPF İçinde Ağaçlar
Birçok teknolojilerindeki, öğeleri ve bileşenleri, burada geliştiriciler işleme veya uygulamanın davranışını etkilemek için ağacında nesne düğümleri doğrudan düzenlersiniz ağaç yapısında düzenlenir. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]Ayrıca birkaç ağaç yapısı metaphors program öğeleri arasında ilişki tanımlamak için kullanır. Çoğunlukla WPF geliştiriciler uygulama kodu oluşturma veya nesne ağaç benzetimini kavramsal olarak düşünmek sırasında XAML'de uygulama bölümlerini tanımladığınız ancak olur belirli API'yi çağıran veya bunu yerine bazı genel yapmak için belirli biçimlendirme kullanma XML DOM nesnesi ağaç işleme API, gibi kullanabilir WPF kullanıma sunan bir ağaç benzetimini görünümü sağlayan iki yardımcı sınıfları <xref:System.Windows.LogicalTreeHelper> ve <xref:System.Windows.Media.VisualTreeHelper>. Bu aynı ağaçları belirli anahtar WPF özellikleri davranışını anlamak için yararlıdır çünkü koşulları görsel ağaç ve mantıksal ağacının WPF belgelerinde de kullanılır. Bu konu ne görsel ağaç ve mantıksal ağacının temsil eden tanımlar, ne tür ağaçları bir genel nesne ağaç kavram ilişkili açıklar ve tanıtır <xref:System.Windows.LogicalTreeHelper> ve <xref:System.Windows.Media.VisualTreeHelper>s.  
  

  
<a name="element_tree"></a>   
## <a name="trees-in-wpf"></a>WPF İçinde Ağaçlar  
 En eksiksiz ağaç yapısında [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nesne ağacıdır. ' Nda uygulama sayfası tanımlarsanız [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ve ardından Yük [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], ağaç yapısı, iç içe geçme ilişkileri biçimlendirme öğeleri temel alarak oluşturulur. Bir uygulamayı tanımlamak veya bir bölümü uygulama kodundaki sonra ağaç yapısını oluşturduysanız belirli nesne içerik modeli uygulamak özellikler için özellik değerlerini nasıl atamak temel. İçinde [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], tam nesne ağacına conceptualized ve ortak API'si için bildirilebilir. iki yolu vardır: mantıksal ağacının ve görsel ağaç olarak. Mantıksal ağacının ve görsel ağaç arasındaki farklılıklar her zaman mutlaka önemli değildir, ancak bunlar zaman zaman sorunlara belirli ile neden olabilir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] alt sistemleri ve işaretleme veya kod yaptığınız etkileyen seçenekleri.  
  
 Her zaman mantıksal ağacının veya görsel ağaç doğrudan değiştiremez olsa bile, ağaçlar nasıl etkileşim kavramlarını anlama WPF bir teknoloji olarak anlamak için kullanışlıdır. Tür bir ağaç benzetimini de özellik devralma ve olay yönlendirme nasıl çalıştığını anlamak için önemli olduğu gibi WPF düşünüyorum [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
> [!NOTE]
>  Nesne ağacına bir kavram gerçek bir API'den daha fazla olduğundan, kavramı düşünmek başka bir nesne grafiğinin yoludur. Uygulamada, ağaç benzetimini nerede bölecektir çalışma zamanında nesneler arasındaki ilişkileri vardır. Bununla birlikte, özellikle XAML tanımlanan UI ile ağaç benzetimini çoğu WPF belgelerine terim nesne ağacına genel bu kavramı başvururken kullanacağını yetecek kadar geçerlidir.  
  
<a name="logical_tree"></a>   
## <a name="the-logical-tree"></a>Mantıksal ağacının  
 İçinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], bu öğeleri geri nesnelerin özelliklerini ayarlayarak içerik için kullanıcı Arabirimi öğeleri ekleyebilirsiniz. Örneğin, öğe ekleme bir <xref:System.Windows.Controls.ListBox> düzenleme tarafından denetim kendi <xref:System.Windows.Controls.ItemsControl.Items%2A> özelliği. Bunu yaparak, öğeleri yerleştirdiğinizi <xref:System.Windows.Controls.ItemCollection> diğer bir deyişle <xref:System.Windows.Controls.ItemsControl.Items%2A> özellik değeri. Benzer şekilde, eklemek için nesneleri için bir <xref:System.Windows.Controls.DockPanel>, düzenlersiniz kendi <xref:System.Windows.Controls.Panel.Children%2A> özellik değeri. Burada, nesne eklemeyi <xref:System.Windows.Controls.UIElementCollection>. Kod örneği için bkz: [bir öğe dinamik olarak eklemek](http://msdn.microsoft.com/library/d00f258a-7973-4de7-bc54-a3fc1f638419).  
  
 İçinde [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], liste öğelerini yerleştirdiğinizde bir <xref:System.Windows.Controls.ListBox> veya denetimleri ya da diğer kullanıcı Arabirimi öğeleri bir <xref:System.Windows.Controls.DockPanel>, aynı zamanda <xref:System.Windows.Controls.ItemsControl.Items%2A> ve <xref:System.Windows.Controls.Panel.Children%2A> özellikleri, açık veya örtülü olarak, aşağıdaki örnekteki gibi.  
  
 [!code-xaml[TreeOvwsSupport#AllCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeOvwsSupport/CS/page1.xaml#allcode)]  
  
 Bu XAML belge nesne modeli altında XML olarak işlemek için olan ve yorum etiketleri dahil, çıkış olarak örtük (hangi yasal olabilirdi) varsa ortaya çıkan XML DOM ağacı için öğeleri dahil `<ListBox.Items>` ve bir örtük öğeleri. Ancak XAML işaretleme okuma ve yazma nesneleri için bu şekilde işlemez, sonuçta elde edilen Nesne grafiği tam anlamıyla içermemesi `ListBox.Items`. Ancak sahip bir <xref:System.Windows.Controls.ListBox> adlı özellik `Items` içeren bir <xref:System.Windows.Controls.ItemCollection>ve <xref:System.Windows.Controls.ItemCollection> başlatılır, ancak ne zaman boş <xref:System.Windows.Controls.ListBox> XAML işlenir. Ardından, içerik için bulunan her alt nesne öğesi <xref:System.Windows.Controls.ListBox> eklenen <xref:System.Windows.Controls.ItemCollection> ayrıştırıcı çağrıları tarafından `ItemCollection.Add`. Bu örnek bir nesne ağacına XAML işleme kadarki görünen oluşturulan nesne ağacına temel olarak mantıksal ağacının olduğu örneğidir.  
  
 Ancak, mantıksal ağacının çıkışı bile XAML örtük sözdizimi öğeleriyle çalışma zamanında kullanıcı Arabirimi oluşturmak, uygulamanız için mevcut tüm nesne grafiğinin değil. Bu ana nedeni, görselleri ve şablonları olmasıdır. Örneğin, göz önünde bulundurun <xref:System.Windows.Controls.Button>. Mantıksal ağacının raporları <xref:System.Windows.Controls.Button> nesne ve ayrıca, dize `Content`. Ancak daha fazla çalışma zamanı nesne ağacında düğmesi. Özellikle, yalnızca ekranda mevcut olduğundan şekilde belirli bir düğmesinin <xref:System.Windows.Controls.Button> denetim şablonu uygulandı. Uygulanan bir şablondan gelen görselleri (şablon tarafından tanımlanan gibi <xref:System.Windows.Controls.Border> visual düğmesi çevresinde koyu gri) çalışma zamanı sırasında mantıksal ağacını arıyorsanız bile mantıksal ağaçta raporlanmaz (Giriş bir olay işleme gibi görünür kullanıcı Arabirimi ve mantıksal ağacının okuma). Şablon görselleri bulmak için bunun yerine görsel ağaç incelemek gerekir.  
  
 Hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sözdizimi eşlemeleri oluşturulan nesne grafiği ve XAML örtük sözdiziminde bkz [içinde XAML sözdizimi ayrıntı](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md) veya [XAML genel bakış (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md).  
  
<a name="tree_property_inheritance_event_routing"></a>   
### <a name="the-purpose-of-the-logical-tree"></a>Mantıksal ağacının amacı  
 Mantıksal ağacının böylece içerik modelleri taşımalarına kendi olası alt nesneler üzerinde yineleyebilirsiniz ve böylece içerik modelleri Genişletilebilir bulunmaktadır. Ayrıca, mantıksal ağacının bir çerçeve mantıksal ağaç içindeki tüm nesneleri ne zaman yüklenen gibi bildirimler, belirli sağlar. Temel olarak mantıksal ağacının bir çalışma zamanı nesne grafiğinin görselleri dışlar, ancak kendi çalışma zamanında uygulamanın birleşim karşı birçok sorgulanırken işlemler için yeterli framework düzeyinde bir yaklaşık bir değeridir.  
  
 Ek olarak, her iki statik ve dinamik kaynak başvuruları için mantıksal ağacı aracılığıyla yukarı bakarak çözümlenir <xref:System.Windows.FrameworkElement.Resources%2A> ilk istekte bulunan nesne ve ardından mantıksal ağaca devam etmeden ve her denetimi koleksiyonları <xref:System.Windows.FrameworkElement> (veya <xref:System.Windows.FrameworkContentElement>) diğer `Resources` içeren değeri bir <xref:System.Windows.ResourceDictionary>, büyük olasılıkla bu anahtarı içeren. Mantıksal ağacının ve görsel ağaç olmadığında mantıksal ağacının kaynak arama için kullanılır. Kaynak sözlüklerindeki ve arama ile ilgili daha fazla bilgi için bkz: [XAML kaynakları](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
<a name="composition"></a>   
### <a name="composition-of-the-logical-tree"></a>Mantıksal ağacının oluşturma  
 Mantıksal ağacının WPF framework-mantıksal ağacının işlemleri için en uygun WPF base öğesi ya da olduğu anlamına gelir düzeyinde tanımlanan <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement>. Ancak, gördüğünüz gibi gerçekten kullanıyorsanız <xref:System.Windows.LogicalTreeHelper> API, mantıksal ağacının bazen ya da olmayan düğüm içeren <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement>. Örneğin, mantıksal ağacının raporları <xref:System.Windows.Controls.TextBlock.Text%2A> değerini bir <xref:System.Windows.Controls.TextBlock>, bir dize değil.  
  
<a name="override_logical_tree"></a>   
### <a name="overriding-the-logical-tree"></a>Mantıksal ağacının geçersiz kılma  
 Gelişmiş denetim yazarlarının birkaç kılarak mantıksal ağacının kılabilirsiniz [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] nasıl genel nesne veya içerik modeli ekler veya kaldırır mantıksal ağaçtaki nesneleri tanımlayın. Mantıksal ağacının geçersiz kılmak nasıl bir örnek için bkz: [mantıksal ağacı geçersiz kılma](../../../../docs/framework/wpf/advanced/how-to-override-the-logical-tree.md).  
  
<a name="pvi"></a>   
### <a name="property-value-inheritance"></a>Özellik Değeri Kalıtımı  
 Özellik değeri devralma karma ağacı ile çalışır. Gerçek meta verileri içeren <xref:System.Windows.FrameworkPropertyMetadata.Inherits%2A> özellik devralma sağlayan bir özelliktir WPF çerçeve düzeyi <xref:System.Windows.FrameworkPropertyMetadata> sınıfı. Bu nedenle, hem özgün değeri tutan üst değer devralan alt nesne hem de olmalıdır <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement>, ve bunların her ikisi de bazı mantıksal ağacının bir parçası olması gerekir. Ancak, özellik devralma desteği varolan WPF özellikler için özellik değeri devralma mantıksal ağaçta değil bir araya giren nesnesi aracılığıyla aktarmak kullanabilirsiniz. Çoğunlukla bu şablonlu olan ya da örneğinde ayarlayın tüm devralınan özellik değerlerini şablon öğelerin sahip veya sayfa düzeyinde birleşim hala yüksek düzeylerinde ilgili ve bu nedenle mantıksal ağacının daha yüksek değildir. Bu tür bir sınır arasında tutarlı bir şekilde çalışması özellik değeri devralma sırasıyla devralan özelliği iliştirilmiş bir özellik olarak kayıtlı olması gerekir ve özel bir bağımlılık özelliği özelliğiyle tanımlamak istiyorsanız, bu deseni izlemelidir Devralma davranışı. Özellik devralma için kullanılan tam ağaç tamamen yardımcı sınıf yardımcı yöntemi tarafından bile çalışma zamanında beklenen olamaz. Daha fazla bilgi için bkz: [özellik değeri devralma](../../../../docs/framework/wpf/advanced/property-value-inheritance.md).  
  
<a name="two_trees"></a>   
## <a name="the-visual-tree"></a>Görsel ağaç  
 Mantıksal ağacının kavramı ek olarak, ayrıca vardır görsel ağaçta kavramı [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Tarafından temsil edilen görsel ağaç görsel nesneler yapısını açıklayan <xref:System.Windows.Media.Visual> temel sınıfı. Bir denetim için bir şablon yazarken, tanımlama veya bu denetim için geçerlidir görsel ağaç yeniden tanımlama. Görsel ağaç de performans ve en iyi duruma getirme nedeniyle çizim üzerinde alt düzey denetim isteyen geliştiriciler için ilgilendirir. Görsel ağaç geleneksel parçası olarak bir riskini [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama programlama olan olay yollar yönlendirilmiş olay için çoğunlukla görsel ağaç mantıksal ağacının ilerler. Bir denetim yazarı olmadığı sürece bu subtlety yönlendirilmiş olay davranış hemen belirgin olmayabilir. Görsel ağaç aracılığıyla olaylarını yönlendirme olayları işlemek veya olay ayarlayıcıları oluşturmak için visual düzeyinde birleşim uygulamak denetimleri sağlar.  
  
<a name="trees_content"></a>   
## <a name="trees-content-elements-and-content-hosts"></a>Ağaçları, içerik öğeleri ve içerik ana bilgisayarlar  
 İçerik öğeleri (öğesinden türetilen sınıflar <xref:System.Windows.ContentElement>) görsel ağaç parçası olmayan; öğesinden devralmaz <xref:System.Windows.Media.Visual> ve görsel bir sahip değil. Hiç bir kullanıcı arabiriminde görünen için bir <xref:System.Windows.ContentElement> hem de bir içerik ana içinde barındırılan bir <xref:System.Windows.Media.Visual> ve mantıksal ağacının katılımcı. Böyle bir nesnenin genellikle olan bir <xref:System.Windows.FrameworkElement>. İçerik ana biraz "tarayıcı" gibi içeriği olan ve ana bilgisayar denetimleri ekran bölge içindeki o içeriği görüntülemek nasıl seçer kavramsallaştırabilirsiniz. İçerik barındırıldığında, içerik ile görsel ağaç normalde ilişkili olan bazı ağaç işlemleri Katılımcısı yapılabilir. Genellikle, <xref:System.Windows.FrameworkElement> ana sınıf içeren herhangi bir barındırılan ekler uygulama kodu <xref:System.Windows.ContentElement> içerik mantıksal ağacının alt düğümler üzerinden olay rotaya rağmen barındırılan içerik parçası değil doğru görsel ağaç. Bu işlem gereklidir böylece bir <xref:System.Windows.ContentElement> kendisinden başka herhangi bir öğeye yönlendirir yönlendirilmiş bir olay kaynağı.  
  
<a name="tree_traversal"></a>   
## <a name="tree-traversal"></a>Ağaç geçişi  
 <xref:System.Windows.LogicalTreeHelper> SAX <xref:System.Windows.LogicalTreeHelper.GetChildren%2A>, <xref:System.Windows.LogicalTreeHelper.GetParent%2A>, ve <xref:System.Windows.LogicalTreeHelper.FindLogicalNode%2A> mantıksal ağacının geçişi için yöntemleri. Bu denetimler, bunların mantıksal alt öğelerini neredeyse her zaman koleksiyon erişim gibi destekleyen bir adanmış koleksiyon özelliği kullanıma sunar. çünkü çoğu durumda, mevcut denetimleri mantıksal ağacının gezinmesine olmamalıdır `Add`, bir dizin oluşturucu ve benzeri. Ağaç geçişi olduğu çoğunlukla hedeflenen denetim modellerinden gibi türetilen değil seçen denetim yazarlar tarafından kullanılan bir senaryo <xref:System.Windows.Controls.ItemsControl> veya <xref:System.Windows.Controls.Panel> koleksiyon özellikleri zaten tanımlandığı ve kimlerin kendi koleksiyon sağlamak istiyorsanız özellik desteği.  
  
 Görsel ağaç bir yardımcı sınıfı görsel ağaç geçişi için de destekler. <xref:System.Windows.Media.VisualTreeHelper>. Görsel ağaç özel denetim özelliklerinden gibi rahat gösterilmeyen böylece <xref:System.Windows.Media.VisualTreeHelper> programlama senaryonuz için gerekliyse, görsel ağacı gezme için önerilen yöntem bir sınıftır. Daha fazla bilgi için bkz: [WPF Grafik işleme genel bakış](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md).  
  
> [!NOTE]
>  Bazen uygulanan şablon görsel ağaç incelemek gereklidir. Bu teknik kullanırken dikkatli olmanız gerekir. Şablon tanımladığınız bir denetim için görsel bir ağaç geçiş yapıyorsanız olsa bile, Tüketicileri denetiminizin her zaman şablon ayarlayarak değiştirebilirsiniz <xref:System.Windows.Controls.Control.Template%2A> örnekleri ve hatta son kullanıcı özelliği etkilediklerini uygulanan şablon değiştirerek Sistem teması.  
  
<a name="routes"></a>   
## <a name="routes-for-routed-events-as-a-tree"></a>"Ağaç" olarak yönlendirilmiş olaylar için yollar  
 Önceden belirtildiği gibi bir görsel ve mantıksal ağaç Beyanları karması olan bir ağacı tek ve önceden belirlenmiş yol boyunca herhangi bir belirli yönlendirilmiş olay rotası dolaşır. Olay yolu ya da yukarı ilerleyebilir veya onu olup olmamasına bağlı olarak ağaç içindeki yönergeleri aşağı tünel veya tırmanmasını yönlendirilmiş olay. Olay rota kavramını "yol gerçekte yönlendiren bir olayı tetiklenmeden bağımsız olarak olay yolu için" kullanılabilir doğrudan destekleyen bir yardımcı sınıfı yok. Rota temsil eden bir sınıf yok <xref:System.Windows.EventRoute>, ancak bu sınıfın yöntemleri genellikle yalnızca dahili kullanım içindir.  
  
<a name="resourcesandtrees"></a>   
## <a name="resource-dictionaries-and-trees"></a>Kaynak sözlüklerindeki ve ağaçları  
 Tüm kaynak sözlük arama `Resources` tanımlanan bir sayfa temel olarak mantıksal ağacının erişir. Mantıksal ağaçta olmayan nesneler anahtarlı kaynakları başvurabilir, ancak bu nesne için mantıksal ağacının bağlandığı noktada kaynak arama sırası başlar. WPF içinde yalnızca mantıksal ağaç düğümleri bulunabilir bir `Resources` içeren özelliği bir <xref:System.Windows.ResourceDictionary>, bu nedenle anahtarlı kaynaklardan arayan görsel ağaç çapraz geçiş yapan hiçbir avantajı yoktur bir <xref:System.Windows.ResourceDictionary>.  
  
 Bununla birlikte, kaynak arama hemen mantıksal ağacının genişletebilirsiniz. Uygulama biçimlendirme için kaynak arama sonra ileriye doğru uygulama düzeyi kaynak sözlükleri ve ardından statik özellikler veya anahtarları başvurulan tema destek ve sistem değerleri devam edebilirsiniz. Kaynak başvuruları dinamik ise Temalar kendileri de tema mantıksal ağacının dışında sistem değerler başvuruda bulunabilir. Kaynak sözlüklerindeki ve arama mantığı hakkında daha fazla bilgi için bkz: [XAML kaynakları](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Girişe Genel Bakış](../../../../docs/framework/wpf/advanced/input-overview.md)  
 [WPF Grafik İşlemeye Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)  
 [Yönlendirilmiş Olaylara Genel Bakış](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [Nesne Ağacında Olmayan Nesne Öğelerini Başlatma](../../../../docs/framework/wpf/advanced/initialization-for-object-elements-not-in-an-object-tree.md)  
 [WPF Mimarisi](../../../../docs/framework/wpf/advanced/wpf-architecture.md)
