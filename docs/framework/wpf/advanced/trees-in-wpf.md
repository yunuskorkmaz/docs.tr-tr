---
title: WPF İçinde Ağaçlar
ms.date: 03/30/2017
helpviewer_keywords:
- logical tree [WPF]
- element tree [WPF]
- visual tree [WPF]
ms.assetid: e83f25e5-d66b-4fc7-92d2-50130c9a6649
ms.openlocfilehash: 1b1763f2fcad60da757a3d6ff23dc289e7506ead
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966100"
---
# <a name="trees-in-wpf"></a>WPF İçinde Ağaçlar
Birçok teknolojilerde, öğeler ve bileşenler, geliştiricilerin bir uygulamanın işlenmesini veya davranışını etkilemek için ağaçta nesne düğümlerini doğrudan işleyebileceği bir ağaç yapısında düzenlenir. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]Ayrıca, program öğeleri arasındaki ilişkileri tanımlamak için çeşitli ağaç yapısı metaphörler kullanır. Çoğu bölüm WPF geliştiricisi, kod içinde bir uygulama oluşturabilir veya nesne ağacı metaphor hakkında kavramsal olarak düşünürken XAML 'de uygulamanın bölümlerini tanımlayabilir, ancak belirli bir API 'yi çağırarak veya belirli bir biçimlendirmeyi kullanarak, bazı genel XML DOM 'da kullanabileceğiniz gibi nesne ağacı işleme API 'SI. WPF, <xref:System.Windows.LogicalTreeHelper> ağaç benzetimini görünümü sağlayan iki yardımcı sınıfı sunar ve <xref:System.Windows.Media.VisualTreeHelper>. Şartlar görsel ağacı ve mantıksal ağaç, bazı temel WPF özelliklerinin davranışını anlamak için yararlı olduğundan, WPF belgelerinde de kullanılır. Bu konu, görsel ağaç ve mantıksal ağacın ne olduğunu tanımlar, bu ağaçların genel nesne ağacı kavramıyla ilişkisini açıklar ve tanıtır <xref:System.Windows.LogicalTreeHelper>. <xref:System.Windows.Media.VisualTreeHelper>  

<a name="element_tree"></a>   
## <a name="trees-in-wpf"></a>WPF İçinde Ağaçlar  
 ' Deki [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] en kapsamlı ağaç yapısı, nesne ağacıdır. ' De [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] bir uygulama sayfası tanımlayıp öğesini [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]yüklerseniz, ağaç yapısı, İşaretlemede öğelerin iç içe geçmiş ilişkilerine göre oluşturulur. Kod içinde uygulamanın bir uygulamasını veya bir bölümünü tanımlarsanız, ağaç yapısı, belirli bir nesne için içerik modelini uygulayan özellikler için özellik değerlerini nasıl atayacağınıza göre oluşturulur. ' [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]De, tüm nesne ağacının kavramsalsel olması ve genel API 'sine, mantıksal ağaç olarak ve görsel ağaç olarak raporlanabilmesi için iki yol vardır: Mantıksal ağaç ve görsel ağaç arasındaki farklılıklar her zaman önemli değildir, ancak bazen belirli [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] alt sistemler ile ilgili sorunlara neden olabilir ve biçimlendirme veya kod içinde yaptığınız seçimleri etkiler.  
  
 Mantıksal ağacı ya da görsel ağacı her zaman doğrudan işlemeseniz bile, ağaçların teknolojiyi bir teknoloji olarak anlamak için nasıl etkileşim kurabileceğine ilişkin kavramları anlayın. WPF 'nin bir ağaç benzetimini veya bir tür olarak düşünmek, özellik devralmanın ve olay yönlendirmenin [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]nasıl çalıştığını anlamak için de önemlidir.  
  
> [!NOTE]
> Nesne ağacı gerçek bir API 'nin bir kavramından daha fazla olduğundan, kavramı düşünmek için başka bir yöntem de bir nesne grafiği olarak belirlenir. Uygulamada, çalışma zamanında ağaç benzetimini 'ın parçalara kapbulunacağı nesneler arasında ilişkiler vardır. Bununla birlikte, özellikle xaml tanımlı kullanıcı arabirimi ile, ağaç benzetimini, bu genel kavrama başvururken en çok WPF belgelerinin nesne ağacını kullanması yeterli olacaktır.  
  
<a name="logical_tree"></a>   
## <a name="the-logical-tree"></a>Mantıksal ağaç  
 İçinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], bu öğeleri geri alan nesnelerin özelliklerini ayarlayarak UI öğelerine içerik eklersiniz. Örneğin, <xref:System.Windows.Controls.ListBox> <xref:System.Windows.Controls.ItemsControl.Items%2A> özelliğini düzenleyerek öğeleri bir denetime eklersiniz. Bunu yaparak öğesi, <xref:System.Windows.Controls.ItemCollection> <xref:System.Windows.Controls.ItemsControl.Items%2A> Özellik değeri olan öğesine yerleştirirsiniz. Benzer şekilde, bir <xref:System.Windows.Controls.DockPanel>öğesine nesne eklemek için, <xref:System.Windows.Controls.Panel.Children%2A> özellik değerini işlersiniz. Burada, öğesine <xref:System.Windows.Controls.UIElementCollection>nesne ekliyoruz. Kod örneği için bkz [. nasıl yapılır: Dinamik olarak](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms752374(v=vs.100))bir öğe ekleyin.  
  
 ' [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]De, liste öğelerini <xref:System.Windows.Controls.ListBox> bir veya denetimlerine veya bir <xref:System.Windows.Controls.DockPanel>içindeki diğer Kullanıcı Arabirimi öğelerine yerleştirdiğinizde, aşağıdaki örnekte olduğu gibi açıkça <xref:System.Windows.Controls.ItemsControl.Items%2A> veya <xref:System.Windows.Controls.Panel.Children%2A> örtük olarak, ve özelliklerini de kullanabilirsiniz.  
  
 [!code-xaml[TreeOvwsSupport#AllCode](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeOvwsSupport/CS/page1.xaml#allcode)]  
  
 Bu XAML 'yi bir belge nesne modeli altında XML olarak işlemek olsaydıysanız ve öğeleri örtük olarak (yasal olacak şekilde) eklediyseniz, sonuçta elde edilen XML DOM ağacının öğesi ve diğer örtük öğeler için `<ListBox.Items>` dahil edilen öğeler vardır. Ancak XAML biçimlendirmeyi okurken ve nesnelere yazdığınızda bu şekilde işlem yapmaz, sonuçta elde edilen nesne grafiğinde tam olarak dahil `ListBox.Items`değildir. <xref:System.Windows.Controls.ListBox> `Items` Ancak ,<xref:System.Windows.Controls.ItemCollection> içeren adlı ve xamlişlendiğindebaşlatılmışancakboşolanadlıbirözelliğesahiptir.<xref:System.Windows.Controls.ListBox> <xref:System.Windows.Controls.ItemCollection> Ardından, için <xref:System.Windows.Controls.ListBox> içerik olarak var olan her bir alt nesne öğesi, ayrıştırıcının öğesine <xref:System.Windows.Controls.ItemCollection> `ItemCollection.Add`çağrıları tarafından eklenir. XAML 'yi bir nesne ağacına işlemenin bu örneği, oluşturulan nesne ağacının temel olarak mantıksal ağaç olduğu bir örnektir.  
  
 Ancak, mantıksal ağaç, çalışma zamanında uygulama kullanıcı arabirimi için mevcut olan nesne grafiğinin tamamı değildir ve XAML örtülü sözdizimi öğeleri de buna eşit değildir. Bunun ana nedeni görseller ve şablonlarıdır. Örneğin, öğesini değerlendirin <xref:System.Windows.Controls.Button>. Mantıksal ağaç, <xref:System.Windows.Controls.Button> nesnesini ve ayrıca dizesini `Content`raporlar. Ancak çalışma zamanı nesne ağacında bu düğmenin daha fazlası vardır. Özellikle, düğme yalnızca belirli <xref:System.Windows.Controls.Button> bir denetim şablonu uygulanmış olduğu için ekranda görüntülenir. Çalışma zamanı sırasında mantıksal ağaca bakıyor olsanız bile, uygulanan bir şablondan gelen görseller <xref:System.Windows.Controls.Border> (örneğin, görsel düğme etrafında koyu gri), mantıksal ağaçta bildirilmiyor (örneğin, bir giriş olayını işleme) görünür kullanıcı arabirimi ve ardından mantıksal ağacı okuma). Şablon görsellerini bulmak için, bunun yerine görsel ağacı incelemeniz gerekir.  
  
 Sözdiziminin oluşturulan nesne grafiğine nasıl [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] eşlendiği ve xaml 'de örtük sözdizimi hakkında daha fazla bilgi için bkz. ayrıntılı veya xaml ['de XAML sözdizimi](xaml-syntax-in-detail.md) [genel bakış (WPF)](xaml-overview-wpf.md).  
  
<a name="tree_property_inheritance_event_routing"></a>   
### <a name="the-purpose-of-the-logical-tree"></a>Mantıksal ağacın amacı  
 Mantıksal ağaç, içerik modellerinin olası alt nesnelerinin üzerinde kolayca yineleme yapabilmesi ve böylece içerik modellerinin Genişletilebilir olması için vardır. Ayrıca, mantıksal ağaç, mantıksal ağaçtaki tüm nesneler yüklenirken olduğu gibi belirli bildirimler için bir çerçeve sağlar. Temel olarak, mantıksal ağaç, görselleri dışlayan, ancak kendi çalıştırma zamanı uygulamanızın kompozisyonundan çok sayıda sorgulama işlemi için yeterli olan bir çalışma zamanı nesne grafiğinin bir yaklaşık sıdır.  
  
 Bunlara ek olarak, hem statik hem de dinamik kaynak başvuruları, ilk istenen nesnedeki koleksiyonlar için <xref:System.Windows.FrameworkElement.Resources%2A> mantıksal ağaca giderek, ardından mantıksal ağacı ve her <xref:System.Windows.FrameworkElement> bir denetimi (veya <xref:System.Windows.FrameworkContentElement>) Bu anahtarı `Resources` içeren bir, içeren <xref:System.Windows.ResourceDictionary>başka bir değer için. Mantıksal ağaç, hem mantıksal ağaç hem de görsel ağaç varsa kaynak arama için kullanılır. Kaynak sözlükleri ve arama hakkında daha fazla bilgi için bkz. [xaml kaynakları](xaml-resources.md).  
  
<a name="composition"></a>   
### <a name="composition-of-the-logical-tree"></a>Mantıksal ağacın bileşimi  
 Mantıksal ağaç, WPF çerçeve düzeyinde tanımlanmıştır, bu da mantıksal ağaç işlemleri için en uygun WPF temel öğesinin <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement>olduğu anlamına gelir. Ancak, <xref:System.Windows.LogicalTreeHelper> API 'yi gerçekten kullanıp kullandıysanız, mantıksal ağaç bazen <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement>olmayan düğümleri içerir. Örneğin, mantıksal ağaç ' a bir <xref:System.Windows.Controls.TextBlock.Text%2A> <xref:System.Windows.Controls.TextBlock>dize olan değerini bildirir.  
  
<a name="override_logical_tree"></a>   
### <a name="overriding-the-logical-tree"></a>Mantıksal ağacı geçersiz kılma  
 Gelişmiş denetim yazarları, genel bir nesne veya içerik modelinin mantıksal ağaç içinde nesne ekleme veya kaldırma şeklini tanımlayan çeşitli API 'Leri geçersiz kılarak mantıksal ağacı geçersiz kılabilir. Mantıksal ağacı nasıl geçersiz kılabileceğiniz hakkında bir örnek için bkz. [mantıksal ağacı geçersiz kılma](how-to-override-the-logical-tree.md).  
  
<a name="pvi"></a>   
### <a name="property-value-inheritance"></a>Özellik Değeri Kalıtımı  
 Özellik değeri kalıtımı karma ağaç üzerinden çalışır. Özellik devralmayı sağlayan <xref:System.Windows.FrameworkPropertyMetadata.Inherits%2A> özelliği içeren gerçek meta veriler WPF framework düzeyi <xref:System.Windows.FrameworkPropertyMetadata> sınıfıdır. Bu nedenle, hem özgün değeri tutan hem de bu değeri devralan alt nesnenin her ikisi de olmalıdır <xref:System.Windows.FrameworkElement> <xref:System.Windows.FrameworkContentElement>ve her ikisi de bir mantıksal ağacın parçası olmalıdır. Ancak, özellik devralmayı destekleyen mevcut WPF özellikleri için, özellik değeri devralma, mantıksal ağaçta olmayan bir araya giren nesne aracılığıyla sürdürülebilir. Temel olarak bu, şablon öğelerinin sahip olduğu örnekte ya da daha yüksek sayfa düzeyi bileşim ve bu nedenle mantıksal ağaçta daha yüksek düzeylerde bulunan devralınan özellik değerlerini kullanması için geçerlidir. Özellik değeri kalıtımını bu tür bir sınır boyunca tutarlı bir şekilde çalışacak şekilde, devralan özellik iliştirilmiş bir özellik olarak kaydedilmelidir ve özelliği ile özel bir bağımlılık özelliği tanımlamak istiyorsanız bu düzeni izlemeniz gerekir devralma davranışı. Özellik devralımı için kullanılan tam ağaç, çalışma zamanında bile bir yardımcı sınıf yardımcı programı yöntemi tarafından tamamen tahmin edilemez. Daha fazla bilgi için bkz. [özellik değeri devralma](property-value-inheritance.md).  
  
<a name="two_trees"></a>   
## <a name="the-visual-tree"></a>Görsel ağaç  
 Mantıksal ağaç kavramının yanı sıra, içinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]görsel ağaç kavramı de vardır. Görsel ağaç, <xref:System.Windows.Media.Visual> temel sınıf tarafından temsil edildiği gibi görsel nesnelerin yapısını açıklar. Bir denetim için şablon yazdığınızda, bu denetim için geçerli olan görsel ağacı tanımlar veya yeniden tanımlamanız gerekir. Görsel ağaç Ayrıca, performans ve iyileştirme nedenleriyle çizim üzerinde daha düşük düzeyde denetim isteyen geliştiricilere de ilgi çekici. Visual Tree 'nin geleneksel [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama programlama kapsamında bir parçası olarak, yönlendirilmiş bir olay için olay yollarının, büyük bir şekilde mantıksal ağaca değil görsel ağaç boyunca seyahat etmesidir. Bu, bir denetim yazarı olmadığınız takdirde, yönlendirilmiş olay davranışının bu alt ttisi hemen görünür olmayabilir. Olayları görsel ağaç aracılığıyla yönlendirme, olayları işlemek veya olay ayarlayıcıları oluşturmak için görsel düzeyde kompozisyon uygulayan denetimleri sağlar.  
  
<a name="trees_content"></a>   
## <a name="trees-content-elements-and-content-hosts"></a>Ağaçlar, Içerik öğeleri ve Içerik Konakları  
 İçerik öğeleri (öğesinden <xref:System.Windows.ContentElement>türetilen sınıflar) görsel ağacın bir parçası değildir; öğesinden <xref:System.Windows.Media.Visual> devralınmaz ve görsel temsiline sahip değildir. Her seferinde bir kullanıcı arabiriminde görünmesi için, bir <xref:System.Windows.ContentElement> , hem a <xref:System.Windows.Media.Visual> hem de mantıksal ağaç katılımcısı olan bir içerik konağında barındırılmalıdır. Genellikle böyle bir <xref:System.Windows.FrameworkElement>nesnesi olur. İçerik konağının içerik için bir "tarayıcı" gibi biraz benzediğini ve bu içeriğin ana bilgisayarın denetlediği ekran bölgesi içinde nasıl görüntüleneceğini tercih etmenizi sağlayabilirsiniz. İçerik barındırıldığı zaman, içerik, normal şekilde görsel ağaç ile ilişkili belirli ağaç işlemlerinde katılımcı hale getirilebilir. Genellikle konak sınıfı, barındırılan içerik doğru görsel ağacın bir parçası olmasa <xref:System.Windows.ContentElement> bile, içerik mantıksal ağacının alt düğümleri aracılığıyla olay rotasında barındırılan uygulama kodunu içerir. <xref:System.Windows.FrameworkElement> Bu, bir <xref:System.Windows.ContentElement> ' ın kendisi dışında herhangi bir öğeye yönlendiren yönlendirilmiş bir olay kaynağı kullanabilmesi için gereklidir.  
  
<a name="tree_traversal"></a>   
## <a name="tree-traversal"></a>Ağaç geçişi  
 Sınıfı, mantıksal ağaç geçişi <xref:System.Windows.LogicalTreeHelper.GetParent%2A>için, <xref:System.Windows.LogicalTreeHelper.FindLogicalNode%2A> ve yöntemlerini sağlar. <xref:System.Windows.LogicalTreeHelper.GetChildren%2A> <xref:System.Windows.LogicalTreeHelper> Çoğu durumda, var olan denetimlerin mantıksal ağacına geçiş yapmanız gerekmez, çünkü bu denetimler, mantıksal alt öğelerini neredeyse her zaman bir dizin oluşturucu gibi koleksiyon erişimini `Add`destekleyen ayrılmış bir koleksiyon özelliği olarak kullanıma sunar. vb. Ağaç geçişi temel olarak, gibi <xref:System.Windows.Controls.ItemsControl> amaçlanan denetim desenlerinden türetmeyen veya <xref:System.Windows.Controls.Panel> koleksiyon özelliklerinin zaten tanımlandığı ve kendi koleksiyonunu sağlamaya çalışan denetim yazarları tarafından kullanılan bir senaryodur. özellik desteği.  
  
 Görsel ağaç Ayrıca görsel ağaç geçişi <xref:System.Windows.Media.VisualTreeHelper>için yardımcı bir sınıf destekler. Görsel ağaç denetimine özgü özelliklerle rahat bir şekilde gösterilmez. bu nedenle <xref:System.Windows.Media.VisualTreeHelper> , programlama senaryonuz için gerekliyse, görsel ağaca geçiş yapmak için önerilen yoldur. Daha fazla bilgi için bkz. [WPF Grafik Işlemeye genel bakış](../graphics-multimedia/wpf-graphics-rendering-overview.md).  
  
> [!NOTE]
> Bazen uygulanan bir şablonun görsel ağacını incelemek gereklidir. Bu tekniği kullanırken dikkatli olmanız gerekir. Şablonu tanımladığınız bir denetim için görsel bir ağaçta geçiş yapsanız bile, denetiminizin tüketicileri, her zaman örnekleri üzerinde <xref:System.Windows.Controls.Control.Template%2A> özelliği ayarlayarak şablonu değiştirebilir ve hatta Son Kullanıcı, sistem teması.  
  
<a name="routes"></a>   
## <a name="routes-for-routed-events-as-a-tree"></a>Yönlendirilmiş olaylar için "ağaç" olarak yollar  
 Daha önce belirtildiği gibi, belirli bir yönlendirilmiş olay rotası, görsel ve mantıksal ağaç temsillerinin karması olan bir ağacın tek ve önceden belirlenmiş bir yolu üzerinde dolaşır. Olay yolu, bir tünel oluşturma veya kabarcıklanma yönlendirilmiş olay olmasına bağlı olarak ağaç içindeki yukarı veya aşağı yönde hareket edebilir. Olay yolu kavramı, gerçekten yönlendiren bir olayı yükseltmeden bağımsız olarak, olay yolunu "göstermek" için kullanılabilecek doğrudan destekleyici yardımcı sınıfına sahip değildir. Yolu <xref:System.Windows.EventRoute>temsil eden bir sınıf vardır, ancak bu sınıfın yöntemleri genellikle yalnızca iç kullanım içindir.  
  
<a name="resourcesandtrees"></a>   
## <a name="resource-dictionaries-and-trees"></a>Kaynak sözlükleri ve ağaçları  
 Bir sayfada tanımlanmış tüm `Resources` kaynak sözlüğü araması, temel olarak mantıksal ağaca geçer. Mantıksal ağaçta olmayan nesneler, anahtarlı kaynaklara başvurabilir, ancak kaynak arama sırası nesnenin mantıksal ağaca bağlı olduğu noktada başlar. WPF 'de, yalnızca mantıksal ağaç düğümlerinin `Resources` , <xref:System.Windows.ResourceDictionary>içeren bir özelliği olabilir, bu nedenle bir <xref:System.Windows.ResourceDictionary>' dan anahtarlı kaynakları arayan görsel ağaç üzerinde geçiş yapma avantajı yoktur.  
  
 Ancak, kaynak arama, anlık mantıksal ağacın ötesine da genişletebilir. Uygulama biçimlendirmesi için, kaynak arama daha sonra uygulama düzeyi kaynak sözlüklerine ve sonra statik özellikler veya anahtarlar olarak başvurulan Tema desteği ve sistem değerleri ile devam edebilir. Ayrıca, kaynak başvuruları dinamik ise Temalar mantıksal ağacının dışındaki sistem değerlerine de başvurabilir. Kaynak sözlükleri ve arama mantığı hakkında daha fazla bilgi için bkz. [xaml kaynakları](xaml-resources.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Girişe Genel Bakış](input-overview.md)
- [WPF Grafik İşlemeye Genel Bakış](../graphics-multimedia/wpf-graphics-rendering-overview.md)
- [Yönlendirilmiş Olaylara Genel Bakış](routed-events-overview.md)
- [Nesne Ağacında Olmayan Nesne Öğelerini Başlatma](initialization-for-object-elements-not-in-an-object-tree.md)
- [WPF Mimarisi](wpf-architecture.md)
