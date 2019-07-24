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
ms.openlocfilehash: 556ce7b42f13d7c5ba7fba36b09277cda9bcae5d
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68400663"
---
# <a name="data-templating-overview"></a>Veri Şablonu Oluşturmaya Genel Bakış
WPF veri şablonu oluşturma modeli, verilerinizin sunumunu tanımlamak için size büyük bir esneklik sağlar. WPF denetimleri, veri sunumu özelleştirmeyi desteklemek için yerleşik işlevlere sahiptir. Bu konu, ilk olarak nasıl tanımlanacağını ve <xref:System.Windows.DataTemplate> daha sonra özel mantık ve hiyerarşik veri görüntüleme desteği gibi diğer veri şablonu oluşturma özelliklerinin nasıl tanıtıldiğini gösterir.  
  
<a name="Prerequisites"></a>   
## <a name="prerequisites"></a>Önkoşullar  
 Bu konu, veri şablonu oluşturma özelliklerine odaklanmaktadır ve veri bağlama kavramlarının bir tanıtımı değildir. Temel veri bağlama kavramları hakkında daha fazla bilgi için bkz. [veri bağlamaya genel bakış](data-binding-overview.md).  
  
 <xref:System.Windows.DataTemplate>, verilerin sunumu ve WPF stili ve şablon oluşturma modeli tarafından sunulan birçok özellikten biridir. WPF stili ve şablon oluşturma modeli için bir giriş (örneğin, denetimler üzerinde özellikleri ayarlamak için <xref:System.Windows.Style> kullanma gibi) için [Stil oluşturma ve şablon](../controls/styling-and-templating.md) oluşturma konusuna bakın.  
  
 Buna ek olarak,, ve gibi `Resources` <xref:System.Windows.Style> nesnelerin yeniden <xref:System.Windows.DataTemplate> kullanılabilir olmasını sağlayan, aslında anlaşılması önemlidir. Kaynaklar hakkında daha fazla bilgi için bkz. [xaml kaynakları](../advanced/xaml-resources.md).  
  
<a name="DataTemplating_Basic"></a>   
## <a name="data-templating-basics"></a>Veri şablonu oluşturma temelleri  
  
 Neden <xref:System.Windows.DataTemplate> önemli olduğunu göstermek için bir veri bağlama örneğinde dolaşalım. Bu örnekte, bir <xref:System.Windows.Controls.ListBox> `Task` nesne listesine bağladık. Her `Task` nesnenin bir `TaskName` (dize), bir `Description` (dize), bir `Priority` (int `Enum` ) ve türünde `TaskType`bir özelliği, ve `Work`değerleri `Home` ile olan bir özelliğine sahiptir.  
  
 [!code-xaml[DataTemplatingIntro_snip#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#resources)]  
[!code-xaml[DataTemplatingIntro_snip#UI1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#ui1)]  
[!code-xaml[DataTemplatingIntro_snip#UI2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#ui2)]  
  
<a name="without_a_datatemplate"></a>   
### <a name="without-a-datatemplate"></a>DataTemplate olmadan  
 <xref:System.Windows.DataTemplate> Bir<xref:System.Windows.Controls.ListBox> olmadan Şu anda şöyle görünür:  
  
 ![Veri şablonu oluşturma örnek ekran görüntüsü](./media/datatemplatingintro-fig1.png "DataTemplatingIntro_fig1")  
  
 Ne olur?, belirli yönergeler olmadan, <xref:System.Windows.Controls.ListBox> koleksiyondaki nesneleri görüntülemeye çalışırken varsayılan olarak çağırır. `ToString` Bu nedenle, `ToString` <xref:System.Windows.Controls.ListBox> nesne yöntemi geçersiz kıldığında, temel koleksiyondaki her kaynak nesnesinin dize gösterimini görüntüler. `Task`  
  
 Örneğin, `Task` sınıfı bu şekilde `ToString` yöntemi geçersiz kıldığında, burada `name` `TaskName` özelliğin alanıdır:  
  
 [!code-csharp[DataTemplatingIntro_snip#ToString](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Data.cs#tostring)]
 [!code-vb[DataTemplatingIntro_snip#ToString](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataTemplatingIntro_snip/visualbasic/data.vb#tostring)]  
  
 Ardından aşağıdaki gibi görünür: <xref:System.Windows.Controls.ListBox>  
  
 ![Veri şablonu oluşturma örnek ekran görüntüsü](./media/datatemplatingintro-fig2.png "DataTemplatingIntro_fig2")  
  
 Ancak, bu sınırlama ve esnek bir şekilde kullanılır. Ayrıca, [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] verilere bağlıyorsanız, geçersiz kılamazsınız `ToString`.  
  
<a name="defining_simple_datatemplate"></a>   
### <a name="defining-a-simple-datatemplate"></a>Basit bir DataTemplate tanımlama  
 Çözüm bir <xref:System.Windows.DataTemplate>tanımlar. Bunu yapmanın bir yolu, <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> <xref:System.Windows.Controls.ListBox> öğesinin özelliğini ' a <xref:System.Windows.DataTemplate>ayarlamaya yönelik bir yoldur. Uygulamanızda <xref:System.Windows.DataTemplate> belirttiğiniz özellikler, veri nesnenizin görsel yapısı haline gelir. Aşağıdakiler <xref:System.Windows.DataTemplate> oldukça basittir. Her öğenin bir <xref:System.Windows.Controls.TextBlock> <xref:System.Windows.Controls.StackPanel>içinde üç öğe olarak göründüğüne ilişkin yönergeler sunuyoruz. Her <xref:System.Windows.Controls.TextBlock> öğe, `Task` sınıfının bir özelliğine bağlanır.  
  
 [!code-xaml[DataTemplatingIntro_snip#Inline](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#inline)]  
  
 Bu konudaki örneklerin temel alınan verileri, CLR nesnelerinin bir koleksiyonudur. [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] Verilere bağlıyorsanız, temel kavramlar aynıdır, ancak hafif bir sözdizimi farkı vardır. Örneğin, `Path=TaskName`yerine, ( `@TaskName`düğümünüz <xref:System.Windows.Data.Binding.XPath%2A> bir[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] özniteliği ise) olarak ayarlanır. `TaskName`  
  
 Şimdi şu şekilde görünür: <xref:System.Windows.Controls.ListBox>  
  
 ![Veri şablonu oluşturma örnek ekran görüntüsü](./media/datatemplatingintro-fig3.png "DataTemplatingIntro_fig3")  
  
<a name="defining_datatemplate_as_a_resource"></a>   
### <a name="creating-the-datatemplate-as-a-resource"></a>DataTemplate 'i kaynak olarak oluşturma  
 Yukarıdaki örnekte, <xref:System.Windows.DataTemplate> satır içi tanımlandık. Aşağıdaki örnekte olduğu gibi yeniden kullanılabilir bir nesne olması için kaynaklar bölümünde tanımlanması daha yaygındır.  
  
 [!code-xaml[DataTemplatingIntro_snip#R1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r1)]  
[!code-xaml[DataTemplatingIntro_snip#AsResource](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#asresource)]  
[!code-xaml[DataTemplatingIntro_snip#R2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r2)]  
  
 Artık aşağıdaki örnekte olduğu `myTaskTemplate` gibi kaynak olarak kullanabilirsiniz:  
  
 [!code-xaml[DataTemplatingIntro_snip#MyTaskTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#mytasktemplate)]  
  
 Bir kaynak olduğundan, artık bunu <xref:System.Windows.DataTemplate> türü alan bir özelliği olan diğer denetimlerde kullanabilirsiniz. `myTaskTemplate` Yukarıda gösterildiği gibi nesneler <xref:System.Windows.Controls.ItemsControl> <xref:System.Windows.Controls.ListBox>için, <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> özelliği ise özelliğidir. Nesneler <xref:System.Windows.Controls.ContentControl> için, <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> özelliği olur.  
  
<a name="Styling_DataType"></a>   
### <a name="the-datatype-property"></a>DataType özelliği  
 Sınıfı, sınıfının<xref:System.Windows.Style> <xref:System.Windows.DataTemplate.DataType%2A> <xref:System.Windows.Style.TargetType%2A> özelliğine çok benzeyen bir özelliğe sahiptir. <xref:System.Windows.DataTemplate> Bu nedenle, yukarıdaki örnekte `x:Key` <xref:System.Windows.DataTemplate> için bir için belirtmek yerine şunları yapabilirsiniz:  
  
 [!code-xaml[DataTemplatingIntro_snip#DataType](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#datatype)]  
  
 Bu <xref:System.Windows.DataTemplate> , tüm `Task` nesnelere otomatik olarak uygulanır. Bu durumda, `x:Key` örtük olarak ayarlanır. <xref:System.Windows.DataTemplate> Bu nedenle, bu `x:Key` değeri atarsanız, örtük `x:Key` olarak <xref:System.Windows.DataTemplate> geçersiz kıldınız ve otomatik olarak uygulanmaz.  
  
 Bir <xref:System.Windows.Controls.ContentControl> nesne`Task` koleksiyonuna bağlıyorsanız, ' ı <xref:System.Windows.Controls.ContentControl> <xref:System.Windows.DataTemplate> otomatik olarak kullanmaz. Bunun nedeni, bir koleksiyonun tamamına veya <xref:System.Windows.Controls.ContentControl> tek tek nesnelere bağlamak isteyip istemediğinizi belirtmek için bir, ' deki bağlamanın daha fazla bilgiye ihtiyacı vardır. <xref:System.Windows.Controls.ContentControl> `/` <xref:System.Windows.Data.Binding.Path%2A> Bir <xref:System.Windows.Controls.ContentControl> türünseçiminiizleiyorsa,geçerliöğeileilgilendiğinizigöstermekiçinbağlamaözelliğini"<xref:System.Windows.Controls.ItemsControl> " olarak ayarlayabilirsiniz. Bir örnek için bkz. [bir koleksiyona bağlama ve seçime göre bilgi görüntüleme](how-to-bind-to-a-collection-and-display-information-based-on-selection.md). Aksi takdirde, <xref:System.Windows.DataTemplate> <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> özelliğini ayarlayarak açıkça belirtmeniz gerekir.  
  
 Özelliği <xref:System.Windows.DataTemplate.DataType%2A> , özellikle farklı türde veri <xref:System.Windows.Data.CompositeCollection> nesneleriniz olduğunda yararlıdır. Bir örnek için bkz. [CompositeCollection uygulama](how-to-implement-a-compositecollection.md).  
  
<a name="adding_more_to_datatemplate"></a>   
## <a name="adding-more-to-the-datatemplate"></a>DataTemplate 'e daha fazla ekleme  
 Şu anda veriler gerekli bilgilerle birlikte görüntülenir, ancak geliştirme için kesin bir oda vardır. Görüntülenen verileri betimleyen bir <xref:System.Windows.Controls.Border>, a <xref:System.Windows.Controls.Grid>ve bazı <xref:System.Windows.Controls.TextBlock> öğeler ekleyerek sunumu geliştirelim.  
  
 [!code-xaml[DataTemplatingIntro#AddingMore](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore)]  
[!code-xaml[DataTemplatingIntro#AddingMore2](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore2)]  
  
 Aşağıdaki ekran görüntüsünde, <xref:System.Windows.Controls.ListBox> bu değiştirilmekte <xref:System.Windows.DataTemplate>olan ile gösterilir:  
  
 ![Veri şablonu oluşturma örnek ekran görüntüsü](./media/datatemplatingintro-fig4.png "DataTemplatingIntro_fig4")  
  
 Öğelerin genişliğinin tüm <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> alana <xref:System.Windows.HorizontalAlignment.Stretch> sahip olduğundan <xref:System.Windows.Controls.ListBox> emin olmak için üzerinde olarak ayarlayabiliriz:  
  
 [!code-xaml[DataTemplatingIntro_snip#Stretch](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#stretch)]  
  
 Özelliği olarak <xref:System.Windows.HorizontalAlignment.Stretch>ayarlandığında ,<xref:System.Windows.Controls.ListBox> şimdi şöyle görünür: <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A>  
  
 ![Veri şablonu oluşturma örnek ekran görüntüsü](./media/datatemplatingintro-fig5.png "DataTemplatingIntro_fig5")  
  
<a name="DataTrigger_to_Apply_Property_Values"></a>   
### <a name="use-datatriggers-to-apply-property-values"></a>Özellik değerlerini uygulamak için veri tetikleyicilerini kullanın  
 Geçerli sunu, bir `Task` giriş görevi mi yoksa Office görevi mi olduğunu bize söylemez. `TaskType` Nesnesinin,değerlerine`Home` sahip bir numaralandırma olan türünde `TaskType`bir özelliği olduğunu unutmayın. `Work` `Task`  
  
 Aşağıdaki örnekte <xref:System.Windows.DataTrigger> , `border` <xref:System.Windows.Controls.Border.BorderBrush%2A> özelliği`TaskType` öğesiolarak`Yellow` adlandırılan öğesini olarak ayarlar .`TaskType.Home`  
  
 [!code-xaml[DataTemplatingIntro#DT](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#dt)]  
[!code-xaml[DataTemplatingIntro#DataTrigger](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#datatrigger)]  
[!code-xaml[DataTemplatingIntro#AddingMore2](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore2)]  
  
 Uygulamamız artık aşağıdaki gibi görünüyor. Giriş görevleri sarı bir kenarlıkla görünür ve Office görevleri deniz mavisi bir kenarlıkla görüntülenir:  
  
 ![Veri şablonu oluşturma örnek ekran görüntüsü](./media/datatemplatingintro-fig6.png "DataTemplatingIntro_fig6")  
  
 Bu örnekte, <xref:System.Windows.DataTrigger> bir özellik değeri <xref:System.Windows.Setter> ayarlamak için bir kullanır. Tetikleyici sınıfları, animasyonlar gibi bir <xref:System.Windows.TriggerBase.EnterActions%2A> dizi <xref:System.Windows.TriggerBase.ExitActions%2A> eyleme başlayabilmeniz için ve özelliklerini de sağlar. Ayrıca, birden çok veriye bağlı özellik <xref:System.Windows.MultiDataTrigger> değerine göre değişiklikler uygulamanıza olanak sağlayan bir sınıf de vardır.  
  
 Aynı etkiyi elde etmenin alternatif bir yolu, özelliği <xref:System.Windows.Controls.Border.BorderBrush%2A> `TaskType` özelliğine bağlamak ve değeri temel alarak `TaskType` rengi döndürmek için bir değer Dönüştürücüsü kullanmaktır. Bir dönüştürücüyü kullanarak yukarıdaki efektin oluşturulması, performans açısından biraz daha etkilidir. Ayrıca, kendi bir mantığınızı tedarik ettiğiniz için kendi dönüştürücüyü oluşturmanız daha fazla esneklik sağlar. Son olarak, seçtiğiniz teknik, senaryonuza ve tercihlerinize bağlıdır. Dönüştürücü yazma hakkında daha fazla bilgi için bkz <xref:System.Windows.Data.IValueConverter>.  
  
<a name="what_belongs_in_datatemplate"></a>   
### <a name="what-belongs-in-a-datatemplate"></a>DataTemplate 'e ait olanlar nelerdir?  

Önceki örnekte, tetikleyicisi <xref:System.Windows.DataTemplate> <xref:System.Windows.DataTemplate>kullanarak tetikleyiciyi yerleştirtik.<xref:System.Windows.DataTemplate.Triggers%2A> özelliði. Tetikleyicisinin içinde olan bir öğenin <xref:System.Windows.Controls.Border> (öğe <xref:System.Windows.DataTemplate>) özelliğinin değerini ayarlar. <xref:System.Windows.Setter> Bununla `Setters` birlikte, sizin için uygun olan özellikler geçerli <xref:System.Windows.DataTemplate>olan öğelerin özellikleri değilse, <xref:System.Windows.Controls.ListBoxItem> sınıfı için bir <xref:System.Windows.Style> olan öğesini kullanarak özellikleri ayarlamak daha uygun olabilir ( bağladığınız denetim bir <xref:System.Windows.Controls.ListBox>' dir. Örneğin, fare bir öğeye işaret ediyorsa <xref:System.Windows.Trigger> öğenin <xref:System.Windows.UIElement.Opacity%2A> değerine animasyon eklemek istiyorsanız, tetikleri bir <xref:System.Windows.Controls.ListBoxItem> stil içinde tanımlarsınız. Bir örnek için, [Stillendirme ve şablon oluşturma örneğine giriş](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)konusuna bakın.
  
 Genel olarak, oluşturulan <xref:System.Windows.DataTemplate> <xref:System.Windows.Controls.ListBoxItem> her birine uygulandığını aklınızda bulundurun ( <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> gerçekte nasıl ve nerede uygulandığı hakkında daha fazla bilgi için, sayfasına bakın.). <xref:System.Windows.DataTemplate> Yalnızca veri nesnelerinin sunumu ve görünümü ile ilgilenme amaçlıdır. Çoğu durumda, öğenin ne zaman seçildiği veya öğelerin nasıl oluşturulduğu <xref:System.Windows.Controls.ListBox> gibi göründüğü gibi sununun diğer tüm yönleri, ' <xref:System.Windows.DataTemplate>ın tanımına ait değildir. Bir örnek için bkz. [Stil oluşturma ve şablon oluşturma bir ıtemı denetimi](#DataTemplating_ItemsControl) bölümü.  
  
<a name="Styling_StyleSelection"></a>   
## <a name="choosing-a-datatemplate-based-on-properties-of-the-data-object"></a>Veri nesnesinin özelliklerine dayalı bir DataTemplate seçme  
 [DataType özelliği](#Styling_DataType) bölümünde, farklı veri nesneleri için farklı veri şablonları tanımlayacağınızı tartıştık. Bu, özellikle farklı türlerde öğeler içeren farklı <xref:System.Windows.Data.CompositeCollection> türlerde veya koleksiyonlarınız olduğunda faydalıdır. [Özellik değerlerini uygulamak için veri tetikleyicilerini kullan](#DataTrigger_to_Apply_Property_Values) bölümünde, oluşturabileceğiniz aynı türde veri nesneleri koleksiyonunuz varsa ve sonra her bir <xref:System.Windows.DataTemplate> veri nesnesinin özellik değerlerine göre değişiklikleri uygulamak için Tetikleyicileri kullanabilirsiniz. Ancak Tetikleyiciler, özellik değerlerini uygulamanıza veya animasyonları başlatmaya izin verir, ancak size veri nesnelerinizin yapısını yeniden oluşturmak için esneklik vermez. Bazı senaryolar, aynı türde ancak farklı özelliklere sahip <xref:System.Windows.DataTemplate> olan veri nesneleri için farklı bir oluşturmanız gerekebilir.  
  
 Örneğin, bir `Task` nesnenin `Priority` değeri `1`olduğunda, kendinize bir uyarı olarak sunmak için tamamen farklı bir görünüm vermek isteyebilirsiniz. Bu durumda, yüksek öncelikli <xref:System.Windows.DataTemplate> `Task` nesnelerin görüntülenmesi için bir oluşturursunuz. Kaynaklar bölümüne aşağıdakileri <xref:System.Windows.DataTemplate> ekleyelim:  
  
 [!code-xaml[DataTemplatingIntro_snip#ImportantTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#importanttemplate)]  
  
 Bu örneğin öğesini kullandığını <xref:System.Windows.DataTemplate>unutmayın.<xref:System.Windows.FrameworkTemplate.Resources%2A> özelliði. Bu bölümde tanımlanan kaynaklar, <xref:System.Windows.DataTemplate>içindeki öğeleri tarafından paylaşılır.  
  
 Veri nesnesinin `Priority` değerine göre kullanılacak mantığı <xref:System.Windows.DataTemplate> sağlamak için <xref:System.Windows.Controls.DataTemplateSelector> , bir <xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A> alt sınıfı oluşturun ve metodunu geçersiz kılın. Aşağıdaki örnekte, <xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A> yöntemi, `Priority` özelliğin değerine göre uygun şablonu döndürmek için mantık sağlar. Döndürülecek şablon enveloping <xref:System.Windows.Window> öğesinin kaynaklarında bulunur.  
  
 [!code-csharp[DataTemplatingIntro_snip#DTSClass](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/TaskListDataTemplateSelector.cs#dtsclass)]
 [!code-vb[DataTemplatingIntro_snip#DTSClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataTemplatingIntro_snip/visualbasic/tasklistdatatemplateselector.vb#dtsclass)]  
  
 Daha sonra bunu kaynak `TaskListDataTemplateSelector` olarak bildirebiliriz:  
  
 [!code-xaml[DataTemplatingIntro_snip#R1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r1)]  
[!code-xaml[DataTemplatingIntro_snip#DTS](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#dts)]  
[!code-xaml[DataTemplatingIntro_snip#R2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r2)]  
  
 Şablon Seçici kaynağını kullanmak için, <xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A> <xref:System.Windows.Controls.ListBox>öğesinin özelliğine atayın. , <xref:System.Windows.Controls.ListBox> Temel koleksiyondaki <xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A> öğelerin her biri `TaskListDataTemplateSelector` için yöntemini çağırır. Çağrı, veri nesnesini öğe parametresi olarak geçirir. Yöntemi tarafından döndürülen bu veri nesnesine uygulanır. <xref:System.Windows.DataTemplate>  
  
 [!code-xaml[DataTemplatingIntro_snip#ItemTemplateSelector](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#itemtemplateselector)]  
  
 Şablon seçiciyle <xref:System.Windows.Controls.ListBox> birlikte şu şekilde görünür:  
  
 ![Veri şablonu oluşturma örnek ekran görüntüsü](./media/datatemplatingintro-fig7.png "DataTemplatingIntro_fig7")  

Bu, bu örneğe ilişkin tartışmamızı yerine eriyor. Tüm örnek için bkz. [veri şablonu oluşturma örneğine giriş](https://github.com/Microsoft/WPF-Samples/tree/master/Data%20Binding/DataTemplatingIntro).

<a name="DataTemplating_ItemsControl"></a>   
## <a name="styling-and-templating-an-itemscontrol"></a>Itembir denetimin stillendirilmesini ve şablon oluşturma  
 İle kullanabileceğiniz tek denetim türü olmasa da, bir koleksiyona bağlamak <xref:System.Windows.Controls.ItemsControl> çok yaygın bir senaryodur. <xref:System.Windows.Controls.ItemsControl> <xref:System.Windows.DataTemplate> DataTemplate 'e [ait](#what_belongs_in_datatemplate) olan Özellikler bölümünde, ' ın tanımının <xref:System.Windows.DataTemplate> yalnızca veri sunumu ile ilgilenildiği açıklanmaktadır. Ne zaman kullanılması <xref:System.Windows.DataTemplate> uygun olmadığını bilmek için, <xref:System.Windows.Controls.ItemsControl>tarafından sunulan farklı stil ve şablon özelliklerini anlamak önemlidir. Aşağıdaki örnek, bu özelliklerin her birinin işlevini göstermek için tasarlanmıştır. Bu <xref:System.Windows.Controls.ItemsControl> örnekte, önceki örnekteki ile aynı `Tasks` koleksiyona bağlanır. Tanıtım amacıyla, bu örnekteki stillerin ve şablonların hepsi satır içi olarak bildirilmiştir.  
  
 [!code-xaml[DataTemplatingIntro_snip#ItemsControlProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#itemscontrolproperties)]  
  
 Aşağıda, örneği işlendiğinde örnek bir ekran görüntüsü verilmiştir:  
  
 ![Itemkıcontrol örnek ekran görüntüsü](./media/databinding-itemscontrolproperties.png "DataBinding_ItemsControlProperties")  
  
 Kullanmak yerine <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>, kullanabilirsiniz. <xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A> Bir örnek için önceki bölüme bakın. Benzer şekilde, <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>öğesini kullanmak yerine, <xref:System.Windows.Controls.ItemsControl.ItemContainerStyleSelector%2A>kullanma seçeneğiniz vardır.  
  
 Burada gösterilmemiş olan diğer iki stille ilgili <xref:System.Windows.Controls.ItemsControl> Özellikler ve ' <xref:System.Windows.Controls.ItemsControl.GroupStyleSelector%2A>dir <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> .  
  
<a name="DataTemplating_HeirarchicalDataTemplate"></a>   
## <a name="support-for-hierarchical-data"></a>Hiyerarşik veri desteği  
 Şimdiye kadar, yalnızca tek bir koleksiyon için bağlama ve görüntüleme hakkında baktık. Bazen diğer koleksiyonları içeren bir koleksiyonunuz vardır. Sınıfı, bu tür verileri göstermek için türlerle <xref:System.Windows.Controls.HeaderedItemsControl> birlikte kullanılmak üzere tasarlanmıştır. <xref:System.Windows.HierarchicalDataTemplate> Aşağıdaki örnekte, `ListLeagueList` `League` nesnelerinin bir listesidir. Her `League` nesne bir `Name` ve bir `Division` nesne koleksiyonuna sahiptir. Her `Division` birinin bir `Name` ve bir `Team` nesne koleksiyonu vardır ve her `Team` nesne bir `Name`içerir.  
  
 [!code-xaml[HierarchicalDataTemplateSnippet#HDT](~/samples/snippets/csharp/VS_Snippets_Wpf/HierarchicalDataTemplateSnippet/CS/window1.xaml#hdt)]  
  
 Örnek, öğesinin <xref:System.Windows.HierarchicalDataTemplate>kullanımını gösterir, diğer listeleri içeren liste verilerini kolayca görüntüleyebilirsiniz. Aşağıda, örneğin bir ekran görüntüsü verilmiştir.  
  
 ![HierarchicalDataTemplate örnek ekran görüntüsü](./media/databinding-hierarchicaldatatemplate.png "DataBinding_HierarchicalDataTemplate")  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Bağlama](../advanced/optimizing-performance-data-binding.md)
- [DataTemplate ile Oluşturulan Öğeleri Bulma](how-to-find-datatemplate-generated-elements.md)
- [Stil ve Şablon Oluşturma](../controls/styling-and-templating.md)
- [Veri Bağlamaya Genel Bakış](data-binding-overview.md)
- [GridView Sütun Üst Bilgi Stil ve Şablonlarına Genel Bakış](../controls/gridview-column-header-styles-and-templates-overview.md)
