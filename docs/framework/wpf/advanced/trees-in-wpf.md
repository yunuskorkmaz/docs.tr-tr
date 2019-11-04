---
title: WPF İçinde Ağaçlar
ms.date: 03/30/2017
helpviewer_keywords:
- logical tree [WPF]
- element tree [WPF]
- visual tree [WPF]
ms.assetid: e83f25e5-d66b-4fc7-92d2-50130c9a6649
ms.openlocfilehash: 0dfae3a601a07c68b2dfe029f061dcf838e98af7
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459505"
---
# <a name="trees-in-wpf"></a>WPF İçinde Ağaçlar
Birçok teknolojilerde, öğeler ve bileşenler, geliştiricilerin bir uygulamanın işlenmesini veya davranışını etkilemek için ağaçta nesne düğümlerini doğrudan işleyebileceği bir ağaç yapısında düzenlenir. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Ayrıca, program öğeleri arasındaki ilişkileri tanımlamak için çeşitli ağaç yapısı metaphiler kullanır. Çoğu bölüm WPF geliştiricisi, kod içinde bir uygulama oluşturabilir veya nesne ağacı metaphor hakkında kavramsal olarak düşünürken XAML 'de uygulamanın bölümlerini tanımlayabilir, ancak belirli bir API 'yi çağırarak veya belirli bir biçimlendirmeyi kullanarak, bazı genel XML DOM 'da kullanabileceğiniz gibi nesne ağacı işleme API 'SI. WPF, ağaç benzetimini görünüm, <xref:System.Windows.LogicalTreeHelper> ve <xref:System.Windows.Media.VisualTreeHelper>sağlayan iki yardımcı sınıf sunar. Şartlar görsel ağacı ve mantıksal ağaç, bazı temel WPF özelliklerinin davranışını anlamak için yararlı olduğundan, WPF belgelerinde de kullanılır. Bu konu, görsel ağaç ve mantıksal ağacın ne olduğunu tanımlar, bu ağaçların genel nesne ağacı kavramıyla ilişkisini açıklar ve <xref:System.Windows.LogicalTreeHelper> ve <xref:System.Windows.Media.VisualTreeHelper>açıklar.  

<a name="element_tree"></a>   
## <a name="trees-in-wpf"></a>WPF İçinde Ağaçlar  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ' deki en kapsamlı ağaç yapısı, nesne ağacıdır. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ' de bir uygulama sayfası tanımlayıp [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]yüklerseniz, ağaç yapısı, İşaretlemede öğelerin iç içe geçmiş ilişkilerine göre oluşturulur. Kod içinde uygulamanın bir uygulamasını veya bir bölümünü tanımlarsanız, ağaç yapısı, belirli bir nesne için içerik modelini uygulayan özellikler için özellik değerlerini nasıl atayacağınıza göre oluşturulur. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], tüm nesne ağacının kavramsalsel hale getirilmiş ve genel API 'sine, mantıksal ağaç ve görsel ağaç olarak raporlandığı iki yol vardır: Mantıksal ağaç ve görsel ağaç arasındaki farklılıklar her zaman önemli değildir, ancak bazen belirli [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] alt sistemler ile sorunlara neden olabilir ve biçimlendirme veya kod içinde yaptığınız seçimleri etkileyebilir.  
  
 Mantıksal ağacı ya da görsel ağacı her zaman doğrudan işlemeseniz bile, ağaçların teknolojiyi bir teknoloji olarak anlamak için nasıl etkileşim kurabileceğine ilişkin kavramları anlayın. WPF 'nin bir ağaç benzetimini veya bir tür olarak düşünmek, özellik devralmanın ve olay yönlendirmenin [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]nasıl çalıştığını anlamak için de önemlidir.  
  
> [!NOTE]
> Nesne ağacı gerçek bir API 'nin bir kavramından daha fazla olduğundan, kavramı düşünmek için başka bir yöntem de bir nesne grafiği olarak belirlenir. Uygulamada, çalışma zamanında ağaç benzetimini 'ın parçalara kapbulunacağı nesneler arasında ilişkiler vardır. Bununla birlikte, özellikle xaml tanımlı kullanıcı arabirimi ile, ağaç benzetimini, bu genel kavrama başvururken en çok WPF belgelerinin nesne ağacını kullanması yeterli olacaktır.  
  
<a name="logical_tree"></a>   
## <a name="the-logical-tree"></a>Mantıksal ağaç  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], bu öğeleri geri alan nesnelerin özelliklerini ayarlayarak UI öğelerine içerik eklersiniz. Örneğin, <xref:System.Windows.Controls.ItemsControl.Items%2A> özelliğini düzenleyerek <xref:System.Windows.Controls.ListBox> denetimine öğe eklersiniz. Bunu yaparak, <xref:System.Windows.Controls.ItemsControl.Items%2A> Özellik değeri olan <xref:System.Windows.Controls.ItemCollection> öğeleri yerleştirirsiniz. Benzer şekilde, bir <xref:System.Windows.Controls.DockPanel>nesneleri eklemek için, <xref:System.Windows.Controls.Panel.Children%2A> özellik değerini işlersiniz. Burada, <xref:System.Windows.Controls.UIElementCollection>nesne ekliyoruz. Kod örneği için bkz. [nasıl yapılır: bir öğeyi dinamik olarak ekleme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms752374(v=vs.100)).  
  
 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], liste öğelerini bir <xref:System.Windows.Controls.DockPanel><xref:System.Windows.Controls.ListBox> veya denetimlere veya diğer Kullanıcı Arabirimi öğelerine yerleştirdiğinizde, aşağıdaki örnekte olduğu gibi açıkça veya örtük olarak <xref:System.Windows.Controls.ItemsControl.Items%2A> ve <xref:System.Windows.Controls.Panel.Children%2A> özelliklerini de kullanırsınız.  
  
 [!code-xaml[TreeOvwsSupport#AllCode](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeOvwsSupport/CS/page1.xaml#allcode)]  
  
 Bu XAML 'yi bir belge nesne modeli altında XML olarak işlemek olsaydıysanız ve öğeleri örtük olarak (yasal olacak şekilde) eklediyseniz, sonuçta elde edilen XML DOM ağacının `<ListBox.Items>` ve diğer örtük öğeler için öğeleri dahil edebilirsiniz. Ancak XAML biçimlendirmeyi okurken ve nesnelere yazdığınızda bu şekilde işlem yapmaz, sonuçta elde edilen nesne grafı `ListBox.Items`içermez. Ancak, <xref:System.Windows.Controls.ItemCollection>içeren `Items` adında bir <xref:System.Windows.Controls.ListBox> özelliğine sahiptir ve <xref:System.Windows.Controls.ListBox> XAML işlendiğinde <xref:System.Windows.Controls.ItemCollection> başlatılır ancak boştur. Daha sonra, <xref:System.Windows.Controls.ListBox> içerik olarak bulunan her bir alt nesne öğesi, `ItemCollection.Add`için ayrıştırıcı çağrıları tarafından <xref:System.Windows.Controls.ItemCollection> eklenir. XAML 'yi bir nesne ağacına işlemenin bu örneği, oluşturulan nesne ağacının temel olarak mantıksal ağaç olduğu bir örnektir.  
  
 Ancak, mantıksal ağaç, çalışma zamanında uygulama kullanıcı arabirimi için mevcut olan nesne grafiğinin tamamı değildir ve XAML örtülü sözdizimi öğeleri de buna eşit değildir. Bunun ana nedeni görseller ve şablonlarıdır. Örneğin, <xref:System.Windows.Controls.Button>göz önünde bulundurun. Mantıksal ağaç <xref:System.Windows.Controls.Button> nesnesini ve ayrıca dize `Content`bildirir. Ancak çalışma zamanı nesne ağacında bu düğmenin daha fazlası vardır. Özellikle, düğme yalnızca belirli bir <xref:System.Windows.Controls.Button> denetim şablonu uygulandığından ekranda görüntülenir. Uygulanan bir şablondan (görsel düğme etrafında koyu gri <xref:System.Windows.Controls.Border>) gelen görseller, çalışma zamanı sırasında mantıksal ağaca bakıyor olsanız bile mantıksal ağaçta bildirilmemiştir (örneğin, bir giriş olayını işleme görünür kullanıcı arabirimi ve ardından mantıksal ağacı okuma). Şablon görsellerini bulmak için, bunun yerine görsel ağacı incelemeniz gerekir.  
  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sözdiziminin oluşturulan nesne grafiğine nasıl eşlendiği ve XAML 'de örtük sözdizimi hakkında daha fazla bilgi için, bkz. [XAML sözdizimi ayrıntılı](xaml-syntax-in-detail.md) veya xaml 'de [genel bakış (WPF)](xaml-overview-wpf.md).  
  
<a name="tree_property_inheritance_event_routing"></a>   
### <a name="the-purpose-of-the-logical-tree"></a>Mantıksal ağacın amacı  
 Mantıksal ağaç, içerik modellerinin olası alt nesnelerinin üzerinde kolayca yineleme yapabilmesi ve böylece içerik modellerinin Genişletilebilir olması için vardır. Ayrıca, mantıksal ağaç, mantıksal ağaçtaki tüm nesneler yüklenirken olduğu gibi belirli bildirimler için bir çerçeve sağlar. Temel olarak, mantıksal ağaç, görselleri dışlayan, ancak kendi çalıştırma zamanı uygulamanızın kompozisyonundan çok sayıda sorgulama işlemi için yeterli olan bir çalışma zamanı nesne grafiğinin bir yaklaşık sıdır.  
  
 Bunlara ek olarak, hem statik hem de dinamik kaynak başvuruları, ilk istenen nesnedeki <xref:System.Windows.FrameworkElement.Resources%2A> koleksiyonları için yukarı doğru bakarak ve ardından mantıksal ağacı devam ettirerek her bir <xref:System.Windows.FrameworkElement> (veya <xref:System.Windows.FrameworkContentElement>) kontrol ederek çözümlenir. büyük olasılıkla bu anahtarı içeren bir <xref:System.Windows.ResourceDictionary>içeren başka bir `Resources` değeri. Mantıksal ağaç, hem mantıksal ağaç hem de görsel ağaç varsa kaynak arama için kullanılır. Kaynak sözlükleri ve arama hakkında daha fazla bilgi için bkz. [xaml kaynakları](../../../desktop-wpf/fundamentals/xaml-resources-define.md).  
  
<a name="composition"></a>   
### <a name="composition-of-the-logical-tree"></a>Mantıksal ağacın bileşimi  
 Mantıksal ağaç, WPF çerçeve düzeyinde tanımlanmıştır, bu da mantıksal ağaç işlemleri için en uygun WPF temel öğesinin <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement>olduğu anlamına gelir. Ancak, <xref:System.Windows.LogicalTreeHelper> API 'sini gerçekten kullanıp kullansanız da, mantıksal ağaç bazen <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement>olmayan düğümleri içerir. Örneğin, mantıksal ağaç bir dize olan bir <xref:System.Windows.Controls.TextBlock><xref:System.Windows.Controls.TextBlock.Text%2A> değerini raporlar.  
  
<a name="override_logical_tree"></a>   
### <a name="overriding-the-logical-tree"></a>Mantıksal ağacı geçersiz kılma  
 Gelişmiş denetim yazarları, genel bir nesne veya içerik modelinin mantıksal ağaç içinde nesne ekleme veya kaldırma şeklini tanımlayan çeşitli API 'Leri geçersiz kılarak mantıksal ağacı geçersiz kılabilir. Mantıksal ağacı nasıl geçersiz kılabileceğiniz hakkında bir örnek için bkz. [mantıksal ağacı geçersiz kılma](how-to-override-the-logical-tree.md).  
  
<a name="pvi"></a>   
### <a name="property-value-inheritance"></a>Özellik Değeri Kalıtımı  
 Özellik değeri kalıtımı karma ağaç üzerinden çalışır. Özellik devralmayı sağlayan <xref:System.Windows.FrameworkPropertyMetadata.Inherits%2A> özelliğini içeren gerçek meta veriler WPF framework düzeyi <xref:System.Windows.FrameworkPropertyMetadata> sınıfıdır. Bu nedenle, özgün değeri tutan üst öğenin ve bu değeri devralan alt nesnenin her ikisi de <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement>olmalıdır ve her ikisi de bazı mantıksal ağacın bir parçası olmalıdır. Ancak, özellik devralmayı destekleyen mevcut WPF özellikleri için, özellik değeri devralma, mantıksal ağaçta olmayan bir araya giren nesne aracılığıyla sürdürülebilir. Temel olarak bu, şablon öğelerinin sahip olduğu örnekte ya da daha yüksek sayfa düzeyi bileşim ve bu nedenle mantıksal ağaçta daha yüksek düzeylerde bulunan devralınan özellik değerlerini kullanması için geçerlidir. Özellik değeri kalıtımını bu tür bir sınır boyunca tutarlı bir şekilde çalışacak şekilde, devralan özellik iliştirilmiş bir özellik olarak kaydedilmelidir ve özelliği ile özel bir bağımlılık özelliği tanımlamak istiyorsanız bu düzeni izlemeniz gerekir devralma davranışı. Özellik devralımı için kullanılan tam ağaç, çalışma zamanında bile bir yardımcı sınıf yardımcı programı yöntemi tarafından tamamen tahmin edilemez. Daha fazla bilgi için bkz. [özellik değeri devralma](property-value-inheritance.md).  
  
<a name="two_trees"></a>   
## <a name="the-visual-tree"></a>Görsel ağaç  
 Mantıksal ağaç kavramının yanı sıra, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]görsel ağaç kavramı de vardır. Görsel ağaç, <xref:System.Windows.Media.Visual> temel sınıfı tarafından temsil edildiği gibi görsel nesnelerin yapısını açıklar. Bir denetim için şablon yazdığınızda, bu denetim için geçerli olan görsel ağacı tanımlar veya yeniden tanımlamanız gerekir. Görsel ağaç Ayrıca, performans ve iyileştirme nedenleriyle çizim üzerinde daha düşük düzeyde denetim isteyen geliştiricilere de ilgi çekici. Geleneksel [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama programlama kapsamında görsel ağacın bir parçası olarak, yönlendirilmiş bir olay için olay yollarının, büyük bir şekilde mantıksal ağacı değil, görsel ağaç boyunca seyahat etmesidir. Bu, bir denetim yazarı olmadığınız takdirde, yönlendirilmiş olay davranışının bu alt ttisi hemen görünür olmayabilir. Olayları görsel ağaç aracılığıyla yönlendirme, olayları işlemek veya olay ayarlayıcıları oluşturmak için görsel düzeyde kompozisyon uygulayan denetimleri sağlar.  
  
<a name="trees_content"></a>   
## <a name="trees-content-elements-and-content-hosts"></a>Ağaçlar, Içerik öğeleri ve Içerik Konakları  
 İçerik öğeleri (<xref:System.Windows.ContentElement>türetilen sınıflar) görsel ağacın bir parçası değildir; <xref:System.Windows.Media.Visual> devralma ve görsel temsili yok. Her seferinde bir kullanıcı arabiriminde görünmesi için, bir <xref:System.Windows.ContentElement> hem <xref:System.Windows.Media.Visual> hem de mantıksal ağaç katılımcısı olan bir içerik konağında barındırılmalıdır. Genellikle böyle bir nesne <xref:System.Windows.FrameworkElement>. İçerik konağının içerik için bir "tarayıcı" gibi biraz benzediğini ve bu içeriğin ana bilgisayarın denetlediği ekran bölgesi içinde nasıl görüntüleneceğini tercih etmenizi sağlayabilirsiniz. İçerik barındırıldığı zaman, içerik, normal şekilde görsel ağaç ile ilişkili belirli ağaç işlemlerinde katılımcı hale getirilebilir. Genellikle, <xref:System.Windows.FrameworkElement> Host sınıfı, barındırılan içerik doğru görsel ağacın bir parçası olmasa bile, içerik mantıksal ağacının alt düğümleri aracılığıyla, barındırılan <xref:System.Windows.ContentElement> olay yoluna ekleyen uygulama kodunu içerir. Bu, bir <xref:System.Windows.ContentElement> kendi dışında herhangi bir öğeye yönlendiren bir yönlendirilmiş olayı kaynak olarak yönlendirebilmesi için gereklidir.  
  
<a name="tree_traversal"></a>   
## <a name="tree-traversal"></a>Ağaç geçişi  
 <xref:System.Windows.LogicalTreeHelper> sınıfı, mantıksal ağaç geçişi için <xref:System.Windows.LogicalTreeHelper.GetChildren%2A>, <xref:System.Windows.LogicalTreeHelper.GetParent%2A>ve <xref:System.Windows.LogicalTreeHelper.FindLogicalNode%2A> yöntemleri sağlar. Çoğu durumda, bu denetimler, mantıksal alt öğelerini `Add`, Dizin Oluşturucu vb. gibi koleksiyon erişimini destekleyen ayrılmış bir koleksiyon özelliği olarak neredeyse her zaman kullanıma sunduğundan, varolan denetimlerin mantıksal ağacını gezmek zorunda değilsiniz. . Ağaç geçişi temel olarak, koleksiyon özelliklerinin zaten tanımlandığı ve kendi koleksiyon özelliğini sağlamak isteyen <xref:System.Windows.Controls.ItemsControl> veya <xref:System.Windows.Controls.Panel> gibi amaçlanan denetim desenlerinden türetilmeyen denetim yazarları tarafından kullanılan bir senaryodur. support.  
  
 Görsel ağaç Ayrıca, <xref:System.Windows.Media.VisualTreeHelper>görsel ağaç geçişi için yardımcı bir sınıf destekler. Görsel ağaç denetimine özgü özelliklerle rahat bir şekilde gösterilmez, bu nedenle <xref:System.Windows.Media.VisualTreeHelper> sınıfı, programlama senaryonuz için gerekliyse görsel ağaca geçiş yapmak için önerilen yoldur. Daha fazla bilgi için bkz. [WPF Grafik Işlemeye genel bakış](../graphics-multimedia/wpf-graphics-rendering-overview.md).  
  
> [!NOTE]
> Bazen uygulanan bir şablonun görsel ağacını incelemek gereklidir. Bu tekniği kullanırken dikkatli olmanız gerekir. Şablonu tanımladığınız bir denetim için görsel bir ağaçta geçiş yapsanız bile, denetiminizin tüketicileri örnekleri üzerinde <xref:System.Windows.Controls.Control.Template%2A> özelliğini ayarlayarak şablonu değiştirebilir ve hatta son kullanıcı sistemi değiştirerek uygulanan şablonu etkileyebilir Tema.  
  
<a name="routes"></a>   
## <a name="routes-for-routed-events-as-a-tree"></a>Yönlendirilmiş olaylar için "ağaç" olarak yollar  
 Daha önce belirtildiği gibi, belirli bir yönlendirilmiş olay rotası, görsel ve mantıksal ağaç temsillerinin karması olan bir ağacın tek ve önceden belirlenmiş bir yolu üzerinde dolaşır. Olay yolu, bir tünel oluşturma veya kabarcıklanma yönlendirilmiş olay olmasına bağlı olarak ağaç içindeki yukarı veya aşağı yönde hareket edebilir. Olay yolu kavramı, gerçekten yönlendiren bir olayı yükseltmeden bağımsız olarak, olay yolunu "göstermek" için kullanılabilecek doğrudan destekleyici yardımcı sınıfına sahip değildir. <xref:System.Windows.EventRoute>yolunu temsil eden bir sınıf vardır, ancak bu sınıfın yöntemleri genellikle yalnızca iç kullanım içindir.  
  
<a name="resourcesandtrees"></a>   
## <a name="resource-dictionaries-and-trees"></a>Kaynak sözlükleri ve ağaçları  
 Bir sayfada tanımlanan tüm `Resources` kaynak sözlüğü araması, temel olarak mantıksal ağaca geçer. Mantıksal ağaçta olmayan nesneler, anahtarlı kaynaklara başvurabilir, ancak kaynak arama sırası nesnenin mantıksal ağaca bağlı olduğu noktada başlar. WPF 'de, yalnızca mantıksal ağaç düğümlerinin bir <xref:System.Windows.ResourceDictionary>içeren `Resources` bir özelliği olabilir. bu nedenle, bir <xref:System.Windows.ResourceDictionary>anahtarlı kaynakları arayan görsel ağaç üzerinde geçiş yapma avantajı yoktur.  
  
 Ancak, kaynak arama, anlık mantıksal ağacın ötesine da genişletebilir. Uygulama biçimlendirmesi için, kaynak arama daha sonra uygulama düzeyi kaynak sözlüklerine ve sonra statik özellikler veya anahtarlar olarak başvurulan Tema desteği ve sistem değerleri ile devam edebilir. Ayrıca, kaynak başvuruları dinamik ise Temalar mantıksal ağacının dışındaki sistem değerlerine de başvurabilir. Kaynak sözlükleri ve arama mantığı hakkında daha fazla bilgi için bkz. [xaml kaynakları](../../../desktop-wpf/fundamentals/xaml-resources-define.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Girişe Genel Bakış](input-overview.md)
- [WPF Grafik İşlemeye Genel Bakış](../graphics-multimedia/wpf-graphics-rendering-overview.md)
- [Yönlendirilmiş Olaylara Genel Bakış](routed-events-overview.md)
- [Nesne Ağacında Olmayan Nesne Öğelerini Başlatma](initialization-for-object-elements-not-in-an-object-tree.md)
- [WPF Mimarisi](wpf-architecture.md)
