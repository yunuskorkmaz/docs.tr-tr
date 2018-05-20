---
title: Veri Şablonu Oluşturmaya Genel Bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], templates
- binding data [WPF], templates
- templates [WPF], data
- data templates [WPF]
ms.assetid: 0f4d9f8c-0230-4013-bd7b-e8e7fed01b4a
ms.openlocfilehash: 7aed418fe5e2c7d8a217f3016655f39c99300d53
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2018
---
# <a name="data-templating-overview"></a>Veri Şablonu Oluşturmaya Genel Bakış
WPF veri şablon modeli, verilerinizin sunumu tanımlamak için büyük esneklik sağlar. WPF denetimleri veri sunumu özelleştirme desteklemek için yerleşik işlevselliğe sahiptir. Bu konuda ilk nasıl tanımlanacağı gösterilmektedir bir <xref:System.Windows.DataTemplate> ve Özel mantık ve hiyerarşik veri görüntüsünü desteği göre şablonları seçimi gibi diğer veri şablon özellikleri sunar.  
  
<a name="Prerequisites"></a>   
## <a name="prerequisites"></a>Önkoşullar  
 Bu konuda veri şablon özellikleri odaklanır ve veri bağlama kavramlarını bir giriş değil. Temel veri bağlama kavramları hakkında daha fazla bilgi için bkz: [veri bağlama genel bakış](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
 <xref:System.Windows.DataTemplate> Veri sunu hakkında ve WPF stil ve şablon modeli tarafından sağlanan birçok özelliklerinden biridir. WPF stil ve şablon modelinin nasıl kullanılacağını gibi bir giriş için bir <xref:System.Windows.Style> denetimlerin özelliklerini ayarlamak için bkz: [stil ve şablon](../../../../docs/framework/wpf/controls/styling-and-templating.md) konu.  
  
 Ayrıca, anlaşılması önemlidir `Resources`, olan temelde ne gibi nesneleri etkinleştirmek <xref:System.Windows.Style> ve <xref:System.Windows.DataTemplate> yeniden kullanılabilir olması için. Kaynaklar hakkında daha fazla bilgi için bkz: [XAML kaynakları](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
<a name="DataTemplating_Basic"></a>   
## <a name="data-templating-basics"></a>Veri şablonu oluşturma temelleri  
  
 Neden göstermek için <xref:System.Windows.DataTemplate> şimdi, veri bağlama örneği yol önemlidir. Bu örnekte, sahibiz bir <xref:System.Windows.Controls.ListBox> listesine bağlı `Task` nesneleri. Her `Task` nesnesi bir `TaskName` (dize), bir `Description` (dize), bir `Priority` (int) ve türünde bir özellik `TaskType`, olduğu bir `Enum` değerlerle `Home` ve `Work`.  
  
 [!code-xaml[DataTemplatingIntro_snip#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#resources)]  
[!code-xaml[DataTemplatingIntro_snip#UI1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#ui1)]  
[!code-xaml[DataTemplatingIntro_snip#UI2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#ui2)]  
  
<a name="without_a_datatemplate"></a>   
### <a name="without-a-datatemplate"></a>DataTemplate  
 Olmadan bir <xref:System.Windows.DataTemplate>, bizim <xref:System.Windows.Controls.ListBox> şu anda şöyle görünür:  
  
 ![Veri şablon örnek ekran görüntüsü](../../../../docs/framework/wpf/data/media/datatemplatingintro-fig1.png "DataTemplatingIntro_fig1")  
  
 Tüm özel yönergeler olduğu olanlar <xref:System.Windows.Controls.ListBox> varsayılan çağrıları tarafından `ToString` koleksiyonda nesneleri görüntülemeye çalışırken. Bu nedenle, varsa `Task` Nesne geçersiz kılmaları `ToString` yöntemi, sonra <xref:System.Windows.Controls.ListBox> temel koleksiyonda her kaynak nesnenin dize gösterimini görüntüler.  
  
 Örneğin, varsa `Task` geçersiz kılmaları sınıf `ToString` yöntemi bu şekilde, burada `name` alanı `TaskName` özelliği:  
  
 [!code-csharp[DataTemplatingIntro_snip#ToString](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Data.cs#tostring)]
 [!code-vb[DataTemplatingIntro_snip#ToString](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataTemplatingIntro_snip/visualbasic/data.vb#tostring)]  
  
 Ardından <xref:System.Windows.Controls.ListBox> aşağıdaki gibi görünür:  
  
 ![Veri şablon örnek ekran görüntüsü](../../../../docs/framework/wpf/data/media/datatemplatingintro-fig2.png "DataTemplatingIntro_fig2")  
  
 Ancak, sınırlama ve esnek olmayan olmasıdır. Ayrıca, için bağlıyorsanız [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] verileri, olmayacaktır devre dışı `ToString`.  
  
<a name="defining_simple_datatemplate"></a>   
### <a name="defining-a-simple-datatemplate"></a>Basit bir DataTemplate tanımlama  
 Çözüm tanımlamaktır bir <xref:System.Windows.DataTemplate>. Bunu yapmanın bir yolu olan ayarlamak için <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> özelliği <xref:System.Windows.Controls.ListBox> için bir <xref:System.Windows.DataTemplate>. İçinde belirttiğiniz, <xref:System.Windows.DataTemplate> veri nesnesi görsel yapısı olur. Aşağıdaki <xref:System.Windows.DataTemplate> oldukça basittir. Her öğe üç görünür yönergeleri vermiş olursunuz <xref:System.Windows.Controls.TextBlock> içinde öğelerin bir <xref:System.Windows.Controls.StackPanel>. Her <xref:System.Windows.Controls.TextBlock> öğesi bir özelliğine bağlı `Task` sınıfı.  
  
 [!code-xaml[DataTemplatingIntro_snip#Inline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#inline)]  
  
 Bu konudaki örnekler için temel verilerin bir koleksiyonudur [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] nesneleri. İçin bağlıyorsanız [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] veri, temel kavramlar aynıdır, ancak küçük bir söz dizim fark yoktur. Örneğin, sahip olmak yerine `Path=TaskName`, ayarlamanız gerekir <xref:System.Windows.Data.Binding.XPath%2A> için `@TaskName` (varsa `TaskName` bir özniteliği olan, [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] düğüm).  
  
 Şimdi bizim <xref:System.Windows.Controls.ListBox> aşağıdaki gibi görünür:  
  
 ![Veri şablon örnek ekran görüntüsü](../../../../docs/framework/wpf/data/media/datatemplatingintro-fig3.png "DataTemplatingIntro_fig3")  
  
<a name="defining_datatemplate_as_a_resource"></a>   
### <a name="creating-the-datatemplate-as-a-resource"></a>Bir kaynak olarak DataTemplate oluşturma  
 Yukarıdaki örnekte, biz tanımlanan <xref:System.Windows.DataTemplate> satır içi. Aşağıdaki örnekte olduğu gibi yeniden kullanılabilir bir nesne olabilir kaynaklar bölümünde tanımlamak için daha yaygın kullanılır:  
  
 [!code-xaml[DataTemplatingIntro_snip#R1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r1)]  
[!code-xaml[DataTemplatingIntro_snip#AsResource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#asresource)]  
[!code-xaml[DataTemplatingIntro_snip#R2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r2)]  
  
 Kullanabileceğiniz artık `myTaskTemplate` aşağıdaki örnekteki gibi bir kaynak olarak:  
  
 [!code-xaml[DataTemplatingIntro_snip#MyTaskTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#mytasktemplate)]  
  
 Çünkü `myTaskTemplate` bir kaynaktır artık bu alan bir özelliği olan diğer denetimleri kullanabilirsiniz bir <xref:System.Windows.DataTemplate> türü. İçin yukarıdaki olarak gösterilen <xref:System.Windows.Controls.ItemsControl> gibi nesneleri <xref:System.Windows.Controls.ListBox>, bu <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> özelliği. İçin <xref:System.Windows.Controls.ContentControl> nesneler, bu <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> özelliği.  
  
<a name="Styling_DataType"></a>   
### <a name="the-datatype-property"></a>Öğesinin DataType özelliği  
 <xref:System.Windows.DataTemplate> Sınıfına sahip bir <xref:System.Windows.DataTemplate.DataType%2A> çok benzer özelliği <xref:System.Windows.Style.TargetType%2A> özelliği <xref:System.Windows.Style> sınıfı. Bu nedenle, belirtme yerine bir `x:Key` için <xref:System.Windows.DataTemplate> yukarıdaki örnekte, aşağıdakileri yapabilirsiniz:  
  
 [!code-xaml[DataTemplatingIntro_snip#DataType](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#datatype)]  
  
 Bu <xref:System.Windows.DataTemplate> tümüne otomatik olarak uygulanan `Task` nesneleri. Bu durumda unutmayın `x:Key` örtük olarak ayarlanır. Bu nedenle, bu atarsanız <xref:System.Windows.DataTemplate> bir `x:Key` değeri, örtük geçersiz kılma `x:Key` ve <xref:System.Windows.DataTemplate> otomatik olarak uygulanacak değil.  
  
 Bağlıyorsanız bir <xref:System.Windows.Controls.ContentControl> koleksiyonuna `Task` nesneleri <xref:System.Windows.Controls.ContentControl> yukarıdaki kullanmaz <xref:System.Windows.DataTemplate> otomatik olarak. Bunun nedeni, bağlamada bir <xref:System.Windows.Controls.ContentControl> koleksiyonunun tamamını veya ayrı nesneleri bağlamak istediğinizi ayırt etmek için daha fazla bilgi gerekiyor. Varsa, <xref:System.Windows.Controls.ContentControl> seçimini izleme bir <xref:System.Windows.Controls.ItemsControl> ayarlayabileceğiniz türü, <xref:System.Windows.Data.Binding.Path%2A> özelliği <xref:System.Windows.Controls.ContentControl> bağlama "`/`" geçerli öğedeki ilgilenen belirtmek için. Bir örnek için bkz: [toplama ve görüntüleme bilgileri seçimi temel bağlamak](../../../../docs/framework/wpf/data/how-to-bind-to-a-collection-and-display-information-based-on-selection.md). Aksi takdirde belirtmeniz gerekir <xref:System.Windows.DataTemplate> ayarlayarak açıkça <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> özelliği.  
  
 <xref:System.Windows.DataTemplate.DataType%2A> Varsa özelliği özellikle yararlı bir <xref:System.Windows.Data.CompositeCollection> veri nesneleri farklı türde. Bir örnek için bkz: [CompositeCollection uygulama](../../../../docs/framework/wpf/data/how-to-implement-a-compositecollection.md).  
  
<a name="adding_more_to_datatemplate"></a>   
## <a name="adding-more-to-the-datatemplate"></a>Daha fazla DataTemplate ekleme  
 Veriler gerekli olan bilgileri şu anda görünür ancak kesinlikle geliştirme için yer yok. Şimdi ekleyerek sunu geliştirin bir <xref:System.Windows.Controls.Border>, <xref:System.Windows.Controls.Grid>ve bazı <xref:System.Windows.Controls.TextBlock> görüntülenen verileri tanımlayan öğeleri.  
  
 [!code-xaml[DataTemplatingIntro#AddingMore](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore)]  
[!code-xaml[DataTemplatingIntro#AddingMore2](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore2)]  
  
 Aşağıdaki ekran görüntüsü gösterildiği <xref:System.Windows.Controls.ListBox> bu değişiklik <xref:System.Windows.DataTemplate>:  
  
 ![Veri şablon örnek ekran görüntüsü](../../../../docs/framework/wpf/data/media/datatemplatingintro-fig4.png "DataTemplatingIntro_fig4")  
  
 Biz ayarlayabilirsiniz <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> için <xref:System.Windows.HorizontalAlignment.Stretch> üzerinde <xref:System.Windows.Controls.ListBox> öğelerin genişliğini tüm yer alan emin olmak için:  
  
 [!code-xaml[DataTemplatingIntro_snip#Stretch](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#stretch)]  
  
 İle <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> özelliğini <xref:System.Windows.HorizontalAlignment.Stretch>, <xref:System.Windows.Controls.ListBox> şimdi şöyle görünür:  
  
 ![Veri şablon örnek ekran görüntüsü](../../../../docs/framework/wpf/data/media/datatemplatingintro-fig5.png "DataTemplatingIntro_fig5")  
  
<a name="DataTrigger_to_Apply_Property_Values"></a>   
### <a name="use-datatriggers-to-apply-property-values"></a>Özellik değerlerini uygulamak için DataTriggers kullanın  
 Geçerli sunu olup bize olmayan bir `Task` ev görev veya bir office görevi. Unutmayın `Task` nesnesi bir `TaskType` türündeki özelliği `TaskType`, numaralandırma değerlere sahip olduğu `Home` ve `Work`.  
  
 Aşağıdaki örnekte, <xref:System.Windows.DataTrigger> ayarlar <xref:System.Windows.Controls.Border.BorderBrush%2A> adlı öğesinin `border` için `Yellow` varsa `TaskType` özelliği `TaskType.Home`.  
  
 [!code-xaml[DataTemplatingIntro#DT](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#dt)]  
[!code-xaml[DataTemplatingIntro#DataTrigger](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#datatrigger)]  
[!code-xaml[DataTemplatingIntro#AddingMore2](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore2)]  
  
 Şimdi uygulamamız aşağıdaki gibi görünür. Giriş görevleri sarı bir sınır ile görünür ve office görevler bir açık mavi sınır ile görünür:  
  
 ![Veri şablon örnek ekran görüntüsü](../../../../docs/framework/wpf/data/media/datatemplatingintro-fig6.png "DataTemplatingIntro_fig6")  
  
 Bu örnekte <xref:System.Windows.DataTrigger> kullanan bir <xref:System.Windows.Setter> bir özellik değeri ayarlanamadı. Tetikleyici sınıfları de <xref:System.Windows.TriggerBase.EnterActions%2A> ve <xref:System.Windows.TriggerBase.ExitActions%2A> başlangıç animasyonları gibi eylemleri kümesi olanak tanıyan özellikler. Ayrıca, ayrıca vardır bir <xref:System.Windows.MultiDataTrigger> değişiklikleri uygulamak sağlayan sınıfı bağlı birden çok veri bağlama özellik değerlerini.  
  
 Bağlamak için aynı sonucu elde etmek için alternatif bir yoludur <xref:System.Windows.Controls.Border.BorderBrush%2A> özelliğine `TaskType` özelliği ve rengi döndürmek için bir değer dönüştürücüsü temel kullanım `TaskType` değeri. Bir dönüştürücü kullanarak yukarıdaki etkisi oluşturmak, performans açısından biraz daha verimlidir. Kendi mantığınızı sağladığını çünkü ek olarak, kendi dönüştürücü oluşturulması, daha fazla esneklik sunar. Sonuç olarak, seçtiğiniz yöntemden senaryonuza ve tercihinize bağlıdır. Bir dönüştürücü yazma hakkında daha fazla bilgi için bkz: <xref:System.Windows.Data.IValueConverter>.  
  
<a name="what_belongs_in_datatemplate"></a>   
### <a name="what-belongs-in-a-datatemplate"></a>Ne bir DataTemplate ait?  

Önceki örnekte, biz tetikleyici içinde yerleştirilen <xref:System.Windows.DataTemplate> kullanarak <xref:System.Windows.DataTemplate>.<xref:System.Windows.DataTemplate.Triggers%2A> özellik. <xref:System.Windows.Setter> Tetikleyicisi bir öğenin bir özelliğin değerini ayarlar ( <xref:System.Windows.Controls.Border> öğesi) içinde olduğunu <xref:System.Windows.DataTemplate>. Ancak, özellikleri, `Setters` ile ilgili bir kaygınız içinde geçerli olan öğeler özelliklerinin <xref:System.Windows.DataTemplate>, kullanarak özelliklerini ayarlamak daha uygun olabilir bir <xref:System.Windows.Style> olan için <xref:System.Windows.Controls.ListBoxItem> sınıfı (varsa bağlama denetimi bir <xref:System.Windows.Controls.ListBox>). İstiyorsanız, örneğin, <xref:System.Windows.Trigger> animasyon için <xref:System.Windows.UIElement.Opacity%2A> değeri öğenin fare bir öğeye üzerindeyken içinde tetikleyicilerini tanımlayın bir <xref:System.Windows.Controls.ListBoxItem> stili. Bir örnek için bkz: [stil ve şablon örnek giriş](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).
  
 Genel olarak, aklınızda <xref:System.Windows.DataTemplate> her oluşturulan uygulanan <xref:System.Windows.Controls.ListBoxItem> (gerçekte nasıl ve nerede uygulandığı hakkında daha fazla bilgi için bkz: <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> sayfası.). <xref:System.Windows.DataTemplate> Yalnızca sunu ve veri nesneleri görünümünü endişelidir. Çoğu durumda, tüm diğer yönlerini sunu hangi öğe gibi görünüyor gibi seçildiğinde veya nasıl <xref:System.Windows.Controls.ListBox> yerleştirir öğeleri ait olmayan tanımında bir <xref:System.Windows.DataTemplate>. Bir örnek için bkz: [stil ve şablon bir ItemsControl](#DataTemplating_ItemsControl) bölümü.  
  
<a name="Styling_StyleSelection"></a>   
## <a name="choosing-a-datatemplate-based-on-properties-of-the-data-object"></a>Veri nesnesi özelliğe göre bir DataTemplate seçme  
 İçinde [DataType özelliği](#Styling_DataType) bölümünde, biz ele alınan farklı veri nesneler için farklı veri şablonları tanımlayabilirsiniz. Varsa özellikle yararlı olan bir <xref:System.Windows.Data.CompositeCollection> farklı türlerin veya farklı türdeki öğeleri koleksiyonlarla. İçinde [kullanmak DataTriggers geçerli özellik değerlerini](#DataTrigger_to_Apply_Property_Values) bölümünde, biz göstermiştir aynı türde veri nesneleri koleksiyonu varsa oluşturabileceğiniz bir <xref:System.Windows.DataTemplate> ve özellik değerlerine göre değişiklikleri uygulamak için Tetikleyicileri kullanın Her veri nesnesi. Ancak, Tetikleyiciler, özellik değerlerini uygulamak veya animasyonları başlatmak izin ancak bunlar veri nesnelerinizi yapısını yeniden oluşturmak için esneklik vermeyin. Farklı bir oluşturmak bazı senaryolar gerektirebilecek <xref:System.Windows.DataTemplate> veriler için aynı olan nesneler yazın, ancak farklı özelliklere sahip.  
  
 Örneğin, bir `Task` nesnesi bir `Priority` değerini `1`, kendiniz için bir uyarı hizmet verecek tamamen farklı bir görünüm vermek isteyebilirsiniz. Bu durumda, oluşturduğunuz bir <xref:System.Windows.DataTemplate> yüksek öncelikli görüntülenmesi için `Task` nesneleri. Aşağıdaki ekleyelim <xref:System.Windows.DataTemplate> kaynaklar bölümüne:  
  
 [!code-xaml[DataTemplatingIntro_snip#ImportantTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#importanttemplate)]  
  
 Bu örnekte fark <xref:System.Windows.DataTemplate>.<xref:System.Windows.FrameworkTemplate.Resources%2A> özellik. Bölüm paylaşıldığı, içinde öğelerin tarafından tanımlanan kaynaklara <xref:System.Windows.DataTemplate>.  
  
 Hangi seçmek için mantığı sağlamak için <xref:System.Windows.DataTemplate> kullanmak için temel `Priority` değeri öğesinin bir alt veri nesnesinin oluşturma <xref:System.Windows.Controls.DataTemplateSelector> ve geçersiz kılma <xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A> yöntemi. Aşağıdaki örnekte, <xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A> yöntemi sağlar değerine göre uygun şablon döndürmek için mantığı `Priority` özelliği. Döndürmek için şablon işlevleri, kaynaklarında bulunan <xref:System.Windows.Window> öğesi.  
  
 [!code-csharp[DataTemplatingIntro_snip#DTSClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/TaskListDataTemplateSelector.cs#dtsclass)]
 [!code-vb[DataTemplatingIntro_snip#DTSClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataTemplatingIntro_snip/visualbasic/tasklistdatatemplateselector.vb#dtsclass)]  
  
 Biz sonra bildirebilir `TaskListDataTemplateSelector` bir kaynak olarak:  
  
 [!code-xaml[DataTemplatingIntro_snip#R1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r1)]  
[!code-xaml[DataTemplatingIntro_snip#DTS](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#dts)]  
[!code-xaml[DataTemplatingIntro_snip#R2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r2)]  
  
 Şablon seçici kaynağı kullanmak için kendisine atayın <xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A> özelliği <xref:System.Windows.Controls.ListBox>. <xref:System.Windows.Controls.ListBox> Çağrıları <xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A> yöntemi `TaskListDataTemplateSelector` temel koleksiyondaki öğelerin her biri için. Çağrı veri nesnesi öğesi parametre olarak geçirir. <xref:System.Windows.DataTemplate> Tarafından döndürülen yöntemi ardından bu veri nesnesine uygulanır.  
  
 [!code-xaml[DataTemplatingIntro_snip#ItemTemplateSelector](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#itemtemplateselector)]  
  
 Şablon seçici, yerinde ile <xref:System.Windows.Controls.ListBox> şimdi aşağıdaki gibi görünür:  
  
 ![Veri şablon örnek ekran görüntüsü](../../../../docs/framework/wpf/data/media/datatemplatingintro-fig7.png "DataTemplatingIntro_fig7")  

Bu örnekte bizim tartışma sonlanır. Tam bir örnek için bkz: [veri şablon örneği giriş](https://github.com/Microsoft/WPF-Samples/tree/master/Data%20Binding/DataTemplatingIntro).

<a name="DataTemplating_ItemsControl"></a>   
## <a name="styling-and-templating-an-itemscontrol"></a>Stil ve şablon bir ItemsControl  
 Olsa bile <xref:System.Windows.Controls.ItemsControl> kullanabileceğiniz yalnızca denetim türü değil bir <xref:System.Windows.DataTemplate> bağlamak için çok yaygın bir senaryo alttadır, bir <xref:System.Windows.Controls.ItemsControl> bir koleksiyon. İçinde [ne ait bir DataTemplate içinde](#what_belongs_in_datatemplate) biz ele bölümü tanımı, <xref:System.Windows.DataTemplate> yalnızca veri sunumu ilgilenen olmalıdır. Ne zaman kullanmak uygun değil bilmek için bir <xref:System.Windows.DataTemplate> tarafından sağlanan farklı stil ve şablon özelliklerini anlamak önemlidir <xref:System.Windows.Controls.ItemsControl>. Aşağıdaki örnek, bu özelliklerin her biri işlevini göstermek için tasarlanmıştır. <xref:System.Windows.Controls.ItemsControl> Bu örnekte, aynı bağlı `Tasks` önceki örnekte olduğu gibi koleksiyonu. Tanıtım için bildirilen tüm satır içi amacıyla, stilleri ve şablonları Bu örnekte sahip.  
  
 [!code-xaml[DataTemplatingIntro_snip#ItemsControlProperties](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#itemscontrolproperties)]  
  
 İşlendiğinde bir ekran görüntüsünü örnek verilmiştir:  
  
 ![ItemsControl örnek ekran](../../../../docs/framework/wpf/data/media/databinding-itemscontrolproperties.png "DataBinding_ItemsControlProperties")  
  
 Kullanmak yerine unutmayın <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>, kullanabileceğiniz <xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A>. Bir örnek için önceki bölüme bakın. Benzer şekilde, kullanmak yerine <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>, kullanılacak seçeneğiniz <xref:System.Windows.Controls.ItemsControl.ItemContainerStyleSelector%2A>.  
  
 İki diğer stil ilgili özelliklerini <xref:System.Windows.Controls.ItemsControl> , gösterilmiyor burada <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> ve <xref:System.Windows.Controls.ItemsControl.GroupStyleSelector%2A>.  
  
<a name="DataTemplating_HeirarchicalDataTemplate"></a>   
## <a name="support-for-hierarchical-data"></a>Hiyerarşik veri desteği  
 Şu ana kadar biz ne bağlamak ve tek bir koleksiyon görüntülemek yalnızca attıktan. Bazen diğer koleksiyonları içeren bir koleksiyon var. <xref:System.Windows.HierarchicalDataTemplate> Sınıfı ile kullanılmak üzere tasarlanmıştır <xref:System.Windows.Controls.HeaderedItemsControl> türleri tür verileri görüntülemek için. Aşağıdaki örnekte, `ListLeagueList` listesidir `League` nesneleri. Her `League` nesnesi bir `Name` ve koleksiyonu `Division` nesneleri. Her `Division` sahip bir `Name` ve koleksiyonu `Team` nesneleri ve her `Team` nesnesi bir `Name`.  
  
 [!code-xaml[HierarchicalDataTemplateSnippet#HDT](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HierarchicalDataTemplateSnippet/CS/window1.xaml#hdt)]  
  
 Örnek kullanımı ile gösterir <xref:System.Windows.HierarchicalDataTemplate>, diğer listeleri içeren liste verileri kolayca görüntüleyebilirsiniz. Örneğin bir ekran görüntüsü verilmiştir.  
  
 ![HierarchicalDataTemplate örnek ekran görüntüsü](../../../../docs/framework/wpf/data/media/databinding-hierarchicaldatatemplate.png "DataBinding_HierarchicalDataTemplate")  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri Bağlama](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)  
 [DataTemplate ile Oluşturulan Öğeleri Bulma](../../../../docs/framework/wpf/data/how-to-find-datatemplate-generated-elements.md)  
 [Stil ve Şablon Oluşturma](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Veri Bağlamaya Genel Bakış](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [GridView Sütun Üst Bilgi Stil ve Şablonlarına Genel Bakış](../../../../docs/framework/wpf/controls/gridview-column-header-styles-and-templates-overview.md)
