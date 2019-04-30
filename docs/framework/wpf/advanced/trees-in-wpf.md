---
title: WPF İçinde Ağaçlar
ms.date: 03/30/2017
helpviewer_keywords:
- logical tree [WPF]
- element tree [WPF]
- visual tree [WPF]
ms.assetid: e83f25e5-d66b-4fc7-92d2-50130c9a6649
ms.openlocfilehash: f9b507c874dfe0ab3feca19e7fcf79df5af93e10
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775004"
---
# <a name="trees-in-wpf"></a>WPF İçinde Ağaçlar
Birçok teknolojileri burada geliştiriciler nesne düğümleri işleme veya uygulamanın davranışını etkilemek için ağacında doğrudan düzenlemezsiniz ağaç yapısında öğeleri ve bileşenleri düzenlenir. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Ayrıca birkaç ağaç yapısı metaphors program öğeler arasındaki ilişkileri tanımlamak için kullanır. Çoğunlukla WPF geliştiricilerinin kod içinde bir uygulama oluşturun veya nesne ağaç benzetimini düşünmek kavramsal olarak çalışırken XAML içinde uygulama bölümlerini tanımlayan ancak olacak belirli bir API'yi çağırıp ya da bunu yerine bazı genel yapmak için özel biçimlendirme kullanma Nesne ağacında işlemeyi API gibi XML DOM kullanabilir WPF sunan bir ağaç benzetimini görünümü sağlayan iki yardımcı sınıflar <xref:System.Windows.LogicalTreeHelper> ve <xref:System.Windows.Media.VisualTreeHelper>. Bu aynı ağaçları belirli anahtar WPF özellikleri davranışını anlamak için yararlı olduğundan koşulları görsel ağacı ve mantıksal ağaç WPF belgelerinde de kullanılır. Bu konu ne görsel ağacı ve mantıksal ağaç temsil tanımlar, böyle ağaçları için genel bir nesne ağacında kavramdır nasıl ilişkili olduğunu açıklar ve tanıtır <xref:System.Windows.LogicalTreeHelper> ve <xref:System.Windows.Media.VisualTreeHelper>s.  

<a name="element_tree"></a>   
## <a name="trees-in-wpf"></a>WPF İçinde Ağaçlar  
 En kapsamlı ağaç yapısında [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nesne ağacıdır. Bir uygulama sayfasındaki tanımlarsanız [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ve ardından Yük [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], ağaç yapısını biçimlendirmede öğelerinin iç içe geçme ilişkileri temel alınarak oluşturulur. Bir uygulamayı tanımlayan veya bir bölümü uygulama kodundaki ardından ağaç yapısını oluşturduysanız, belirli bir nesne için içerik modeli uygulayan özellikler için özellik değerlerini nasıl atamak temel. İçinde [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], tam nesne ağacının conceptualized ve kendi ortak API için bildirilen iki yolu vardır: mantıksal ağacı ve görsel ağaç olarak. Mantıksal ağaç ve görsel ağaç arasındaki farklılıklar her zaman olması önemli değildir, ancak bunlar zaman zaman sorunları ile belirli neden olabilir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] alt sistemlerin ve işaretleme veya kod içinde yaptığınız etkileyen seçenekleri.  
  
 Her zaman mantıksal ağaç veya görsel ağacı doğrudan düzenlemezsiniz değil olsa da, ağaçları etkileşimini kavramları anlama WPF bir teknoloji olarak anlamak için kullanışlıdır. Tür bir ağaç benzetimini de özellik devralma ve olay yönlendirmeyi nasıl çalıştığını anlamak için çok önemli olduğu gibi WPF düşünmek [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
> [!NOTE]
>  Nesne ağacının daha fazla gerçek bir API bir kavram kavramını düşünme başka bir yolu bir nesne grafiğinin olduğu. Uygulamada, çalışma zamanında ağaç benzetimini burada bölecektir nesneler arasındaki ilişkileri vardır. Bununla birlikte, özellikle XAML tanımlı UI ile ağaç benzetimini çoğu WPF belgeler terimi nesne ağacının bu genel kavram başvururken kullanacağınız kadar geçerlidir.  
  
<a name="logical_tree"></a>   
## <a name="the-logical-tree"></a>Mantıksal ağacı  
 İçinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], bu öğeleri geri nesnelerin özelliklerini ayarlayarak içerik için kullanıcı Arabirimi öğeleri ekleyin. Örneğin, öğeleri eklediğiniz bir <xref:System.Windows.Controls.ListBox> düzenleme denetimini kendi <xref:System.Windows.Controls.ItemsControl.Items%2A> özelliği. Bunu yaparak, öğeleri yerleştirdiğinizi <xref:System.Windows.Controls.ItemCollection> diğer bir deyişle <xref:System.Windows.Controls.ItemsControl.Items%2A> özellik değeri. Benzer şekilde, eklemek için nesneleri için bir <xref:System.Windows.Controls.DockPanel>, düzenleme, kendi <xref:System.Windows.Controls.Panel.Children%2A> özellik değeri. Burada, nesne eklemeyi <xref:System.Windows.Controls.UIElementCollection>. Kod örneği için bkz: [nasıl yapılır: Dinamik olarak bir öğe ekleme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms752374(v=vs.100)).  
  
 İçinde [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], liste öğelerini yerleştirdiğinizde bir <xref:System.Windows.Controls.ListBox> veya denetimleri veya diğer kullanıcı Arabirimi öğelerinde bir <xref:System.Windows.Controls.DockPanel>, ayrıca <xref:System.Windows.Controls.ItemsControl.Items%2A> ve <xref:System.Windows.Controls.Panel.Children%2A> özellikleri, açıkça veya dolaylı olarak, aşağıdaki örnekte olduğu gibi.  
  
 [!code-xaml[TreeOvwsSupport#AllCode](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeOvwsSupport/CS/page1.xaml#allcode)]  
  
 Bu XAML XML belge nesne modeli altında işlemek için olan ve açıklamalı etiketleri dahil, out örtük olarak (hangi yasal olabilirdi) durumunda elde edilen XML DOM ağacı öğeleri dahil `<ListBox.Items>` ve diğer örtük öğeleri. Ancak, XAML biçimlendirme okuma ve yazma nesneleri için bu şekilde işlemez, elde edilen Nesne grafiğini tam anlamıyla içermemesi `ListBox.Items`. Ancak sahip bir <xref:System.Windows.Controls.ListBox> adlı özellik `Items` içeren bir <xref:System.Windows.Controls.ItemCollection>ve <xref:System.Windows.Controls.ItemCollection> başlatılır ancak boş <xref:System.Windows.Controls.ListBox> XAML işlenir. Ardından, içeriği olarak var. her alt nesne öğesi <xref:System.Windows.Controls.ListBox> eklenir <xref:System.Windows.Controls.ItemCollection> yapılan çağrılar ayrıştırıcı tarafından `ItemCollection.Add`. Bu örnek, bir nesne ağacına XAML işleme kadar görünüşte oluşturulan nesne ağacının temel olarak mantıksal ağaç olduğu örneğidir.  
  
 Ancak, mantıksal ağaç bile XAML örtülü söz dizimi öğeleri ile çalışma zamanında kullanıcı Arabirimi kullanıma factored uygulamanız için var olan tüm nesne grafiğinin değil. Bu ana nedeni, görsel öğeler ve şablonlar olmasıdır. Örneğin, düşünün <xref:System.Windows.Controls.Button>. Mantıksal ağaç raporları <xref:System.Windows.Controls.Button> nesne ve ayrıca kendi dize `Content`. Ancak daha fazla çalışma süresi nesne ağacında düğmesi. Özellikle, yalnızca ekranda, çünkü olduğu gibi belirli bir düğmesinin <xref:System.Windows.Controls.Button> denetim şablonu uygulandı. Uygulanan bir şablondan gelen görselleri (şablon tarafından tanımlanan gibi <xref:System.Windows.Controls.Border> visual düğmenin etrafında koyu gri) çalışma zamanı sırasında mantıksal ağacını arıyor olsanız mantıksal ağaçta bildirilmedi (Giriş bir olay işleme gibi görünür kullanıcı Arabirimi ve ardından mantıksal ağaç okuma). Şablon görsellerin bulmak için bunun yerine inceleyin görsel ağacın gerekecektir.  
  
 Hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] oluşturulan nesne grafiği ve XAML, örtük sözdiziminde söz dizimi haritalar'a bkz [içinde XAML söz dizimi ayrıntı](xaml-syntax-in-detail.md) veya [XAML genel bakış (WPF)](xaml-overview-wpf.md).  
  
<a name="tree_property_inheritance_event_routing"></a>   
### <a name="the-purpose-of-the-logical-tree"></a>Mantıksal ağacı amacı  
 Mantıksal ağacı, böylece içerik modelleri, olası alt nesneler üzerinde kolayca yineleme yapmak ve böylece içerik modelleri Genişletilebilir bulunmaktadır. Ayrıca, mantıksal ağacı bir çerçeve gibi tüm nesnelerin mantıksal ağaçta ne zaman yüklendiği bildirimleri belirli sunar. Temelde, mantıksal bir çalışma süresi Nesne grafiği görselleri dahil değildir, ancak kendi çalışma zamanında uygulamanızın karşı birçok sorgulama işlemleri için yeterli framework düzeyinde yaklaşık ağacıdır.  
  
 Ayrıca, hem statik hem de dinamik kaynak başvuruları için mantıksal ağaç içinde yukarı bakarak çözümlenir <xref:System.Windows.FrameworkElement.Resources%2A> ilk isteyen nesnesi ve ardından mantıksal ağacı devam etmesini ve her koleksiyonları <xref:System.Windows.FrameworkElement> (veya <xref:System.Windows.FrameworkContentElement>) başka bir `Resources` içeren değer bir <xref:System.Windows.ResourceDictionary>, büyük olasılıkla bu anahtarı içeren. Mantıksal ağacı hem görsel ağacı mevcut olduğunda mantıksal ağaç kaynak araması için kullanılır. Kaynak sözlükleri ve arama hakkında daha fazla bilgi için bkz. [XAML kaynakları](xaml-resources.md).  
  
<a name="composition"></a>   
### <a name="composition-of-the-logical-tree"></a>Mantıksal ağacı oluşturma  
 Mantıksal ağacı WPF framework-yani mantıksal ağaç işlemleri için en uygun WPF temel öğe ya da etkin düzeyinde tanımlanan <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement>. Ancak, gördüğünüz gibi gerçekten kullanıyorsanız <xref:System.Windows.LogicalTreeHelper> API, mantıksal ağaç bazen ya da olmayan düğüm içeren <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement>. Örneğin, mantıksal ağaç raporları <xref:System.Windows.Controls.TextBlock.Text%2A> değerini bir <xref:System.Windows.Controls.TextBlock>, bir dize olduğu.  
  
<a name="override_logical_tree"></a>   
### <a name="overriding-the-logical-tree"></a>Mantıksal ağacı geçersiz kılma  
 Gelişmiş denetim yazarları, birkaç geçersiz kılarak mantıksal ağaç kılabilir [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] nasıl bir genel nesne veya içerik modeli ekler veya kaldırır mantıksal ağacı içindeki nesneleri tanımlayın. Mantıksal ağacı geçersiz kılma ilişkin bir örnek için bkz: [mantıksal ağacı geçersiz kılma](how-to-override-the-logical-tree.md).  
  
<a name="pvi"></a>   
### <a name="property-value-inheritance"></a>Özellik Değeri Kalıtımı  
 Özellik değeri kalıtımı karma ağacı ile çalışır. Gerçek meta veriler içeren <xref:System.Windows.FrameworkPropertyMetadata.Inherits%2A> özellik devralma sağlayan özelliktir çerçeve düzeyi WPF <xref:System.Windows.FrameworkPropertyMetadata> sınıfı. Hem özgün değeri tutan üst hem de bu değeri devralır alt nesne hem de bu nedenle, olmalıdır <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement>, ve bunların her ikisi de bazı mantıksal ağacının bir parçası olması gerekir. Ancak, özellik devralma destekleyen varolan WPF özellikler için özellik değeri kalıtımı mantıksal ağacı içinde değil, müdahalede bulunan bir nesne aracılığıyla aktarmak kullanabilirsiniz. Esas olarak şablon öğelerin herhangi devralınan özellik değerleri, şablonlu ya da örnek üzerinde olması veya sayfa düzeyi oluşturma, yine de daha yüksek düzeylerde ilgilidir ve bu nedenle daha yüksek mantıksal ağaçta budur. Böyle bir sınır arasında tutarlı bir şekilde çalışması özellik değeri kalıtımı sırasıyla devralan özelliği ekli özelliği kayıtlı olması gerekir ve özelliği ile özel bir bağımlılık özelliği tanımlamak istiyorsanız bu deseni izlemelidir Devralma davranışı. Özellik devralma için kullanılan tam ağaç tamamen yardımcı sınıf yardımcı yöntemi tarafından bile çalışma zamanında beklenen olamaz. Daha fazla bilgi için [özellik değeri kalıtımı](property-value-inheritance.md).  
  
<a name="two_trees"></a>   
## <a name="the-visual-tree"></a>Görsel ağaç  
 Mantıksal ağaç kavramı yanı sıra, ayrıca mevcuttur görsel ağaçta kavramını [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Tarafından temsil edilen görsel ağacı görsel nesneler yapısını açıklayan <xref:System.Windows.Media.Visual> temel sınıfı. Bir denetim için bir şablon yazdığınızda, tanımlama veya bu denetim için uygulanan görsel ağacı yeniden tanımlama. Görsel ağacı, alt düzey performans ve iyileştirme nedeniyle çizim denetime isteyen geliştiriciler için de ilgilendirir. Bir görsel ağacı geleneksel parçası olarak açığa [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama programlama, olay yollar yönlendirilmiş olay için çoğunlukla görsel ağacı mantıksal ağaç seyahat. Bir denetim yazarı olmadığı sürece bu subtlety yönlendirilmiş olay davranış hemen görünür olmayabilir. Görsel ağacı üzerinden olay yönlendirme oluşturma olayları işlemek veya olay ayarlayıcıları oluşturmak için görsel düzeydeki uygulayan denetimleri sağlar.  
  
<a name="trees_content"></a>   
## <a name="trees-content-elements-and-content-hosts"></a>İçerik ana ağaçları ve içerik öğeleri  
 İçerik öğeleri (türetilen sınıfları <xref:System.Windows.ContentElement>) görsel ağacın parçası değildir; seçeneğinden devralmamanızı <xref:System.Windows.Media.Visual> ve görsel bir temsili yok. Hiç bir kullanıcı arabiriminde görünmesi için bir <xref:System.Windows.ContentElement> hem de içerik bir ana barındırılan bir <xref:System.Windows.Media.Visual> ve mantıksal ağaç katılımcıdır. Genellikle bu tür bir nesnedir bir <xref:System.Windows.FrameworkElement>. İçerik ana bakıma "browser" için içeriktir ve denetimleri ekran bölge içinde bu içeriğin nasıl görüntüleneceğini seçer kavramsallaştırmak. İçerik barındırıldığında, içeriği görsel ağaçta normalde ilişkili bazı ağaç işlemleri bir katılımcı yapılabilir. Genellikle, <xref:System.Windows.FrameworkElement> ana sınıfı içeren ekler barındırılan herhangi bir uygulama kodu <xref:System.Windows.ContentElement> içerik mantıksal ağaç düğümlerini aracılığıyla olay rotaya olsa bile barındırılan içeriğin parçası değil gerçek görsel ağaç. Bunun gerekli olmasının böylece bir <xref:System.Windows.ContentElement> kendisinden başka herhangi bir öğeye yönlendiren gönderilmiş bir olay kaynağı.  
  
<a name="tree_traversal"></a>   
## <a name="tree-traversal"></a>Ağaç geçişi  
 <xref:System.Windows.LogicalTreeHelper> Sağlar sınıfını <xref:System.Windows.LogicalTreeHelper.GetChildren%2A>, <xref:System.Windows.LogicalTreeHelper.GetParent%2A>, ve <xref:System.Windows.LogicalTreeHelper.FindLogicalNode%2A> mantıksal ağacının çapraz geçişi için yöntemleri. Bu denetimler, mantıksal alt öğeleri neredeyse her zaman gibi koleksiyon erişimi destekleyen bir adanmış koleksiyon özelliği kullanıma sunun. çünkü çoğu durumda, mevcut denetimlerin mantıksal ağacı gezme oluşturmak zorunda değilsiniz `Add`, bir dizin oluşturucu ve benzeri. Ağaç geçişi çoğunlukla hedeflenen denetim modellerinden gibi türetilen değil seçen denetimi yazarları tarafından kullanılan bir senaryo olduğundan <xref:System.Windows.Controls.ItemsControl> veya <xref:System.Windows.Controls.Panel> koleksiyon özellikleri zaten tanımlandığı ve kimin kendi koleksiyon sağlamak istiyorsanız özellik desteği.  
  
 Görsel ağacı yardımcı bir sınıf görsel ağacı geçişi için de destekler. <xref:System.Windows.Media.VisualTreeHelper>. Görsel ağaç olarak bir kolayca denetime özgü özelikleri gösterilmez böylece <xref:System.Windows.Media.VisualTreeHelper> programlama senaryonuz için gerekliyse, görsel ağacı geçirmek için önerilen yöntem bir sınıftır. Daha fazla bilgi için [WPF Grafik işlemeye genel bakış](../graphics-multimedia/wpf-graphics-rendering-overview.md).  
  
> [!NOTE]
>  Bazen bir uygulanan şablon görsel ağacını incelemek gereklidir. Bu teknik kullanırken dikkatli olmanız gerekir. Şablon tanımladığınız bir denetim için bir görsel ağacı geçiş yapıyorsanız bile denetiminizin tüketicilerinin her zaman şablonu ayarlayarak değiştirebilirsiniz <xref:System.Windows.Controls.Control.Template%2A> örnekleri ve hatta son kullanıcı özelliği etkilemek uygulanan şablon değiştirerek Sistem teması.  
  
<a name="routes"></a>   
## <a name="routes-for-routed-events-as-a-tree"></a>"Ağacı" yönlendirilmiş olaylar için yollar  
 Daha önce belirtildiği gibi herhangi bir belirli yönlendirilmiş olay rotası hibrit bir görsel ve mantıksal ağaç gösterimleri, bir ağaç bir tek ve önceden belirlenen yolu izler. Aşağı yönde olmasına bağlı olarak ağacı içinde bir tünel veya tırmanma olay yönlendirilebilir veya yukarı ya da olay yolu izler. Olay yönlendirme kavramını "olay yolu aslında yönlendiren olay bildirmek bağımsız olarak yürütmek için" kullanılabilir doğrudan destekleyen bir yardımcı sınıfı yok. Rota temsil eden bir sınıf yok <xref:System.Windows.EventRoute>, ancak bu sınıftaki yöntemleri genellikle yalnızca dahili kullanım içindir.  
  
<a name="resourcesandtrees"></a>   
## <a name="resource-dictionaries-and-trees"></a>Kaynak sözlükleri ve ağaçları  
 Tüm kaynak sözlüğü arama `Resources` tanımlanan bir sayfa temel olarak mantıksal ağaç erişir. Mantıksal ağaçta olmayan nesneler anahtarlı kaynaklarına başvurabilir, ancak bu nesne için mantıksal ağaç nerede bağlı bir noktada kaynak arama sırası başlar. WPF içinde yalnızca mantıksal ağaç düğümleri olabilir bir `Resources` içeren özelliği bir <xref:System.Windows.ResourceDictionary>, bu nedenle anahtarlı kaynaklardan aranıyor görsel ağacının çapraz geçişi içinde hiçbir avantajı yoktur bir <xref:System.Windows.ResourceDictionary>.  
  
 Ancak, kaynak araması hemen mantıksal ağaç genişletebilirsiniz. Uygulama biçimlendirme için kaynak araması ardından ileriye doğru uygulama düzeyinde kaynak sözlükleri ve ardından statik özellikler veya anahtarlarının başvurulan tema desteği ve sistem değerleri devam edebilirsiniz. Kaynak başvurularını dinamik ise Temalar kendilerini tema mantıksal ağaç dışında sistem değerleri de başvurabilirsiniz. Kaynak sözlükleri ve arama mantığı hakkında daha fazla bilgi için bkz. [XAML kaynakları](xaml-resources.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Girişe Genel Bakış](input-overview.md)
- [WPF Grafik İşlemeye Genel Bakış](../graphics-multimedia/wpf-graphics-rendering-overview.md)
- [Yönlendirilmiş Olaylara Genel Bakış](routed-events-overview.md)
- [Nesne Ağacında Olmayan Nesne Öğelerini Başlatma](initialization-for-object-elements-not-in-an-object-tree.md)
- [WPF Mimarisi](wpf-architecture.md)
