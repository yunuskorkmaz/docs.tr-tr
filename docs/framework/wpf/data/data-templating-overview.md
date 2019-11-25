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
ms.openlocfilehash: 40d5ac257fa412afeb81b324d99604c0c1f5e878
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73974887"
---
# <a name="data-templating-overview"></a>Veri Şablonu Oluşturmaya Genel Bakış
WPF veri şablonu oluşturma modeli, verilerinizin sunumunu tanımlamak için size büyük bir esneklik sağlar. WPF denetimleri, veri sunumu özelleştirmeyi desteklemek için yerleşik işlevlere sahiptir. Bu konu, ilk olarak bir <xref:System.Windows.DataTemplate> tanımlama ve ardından özel mantık ve hiyerarşik veri görüntüleme desteği gibi diğer veri şablonu oluşturma özelliklerinin nasıl tanıtıldiğini gösterir.

<a name="Prerequisites"></a>
## <a name="prerequisites"></a>Prerequisites
 Bu konu, veri şablonu oluşturma özelliklerine odaklanmaktadır ve veri bağlama kavramlarının bir tanıtımı değildir. Temel veri bağlama kavramları hakkında daha fazla bilgi için bkz. [veri bağlamaya genel bakış](../../../desktop-wpf/data/data-binding-overview.md).

 <xref:System.Windows.DataTemplate>, verilerin sunumu ve WPF stili ve şablon oluşturma modeli tarafından sunulan birçok özellikten biridir. WPF stili ve şablon oluşturma modeli için bir <xref:System.Windows.Style>, örneğin denetimlerin özelliklerini ayarlamak için kullanma gibi bir giriş için, bkz. [Stil ve şablon](../controls/styling-and-templating.md) oluşturma konusu.

 Buna ek olarak, <xref:System.Windows.Style> ve <xref:System.Windows.DataTemplate> gibi nesnelerin yeniden kullanılabilir olmasını sağlayan `Resources`anlaşılması önemlidir. Kaynaklar hakkında daha fazla bilgi için bkz. [xaml kaynakları](../advanced/xaml-resources.md).

<a name="DataTemplating_Basic"></a>
## <a name="data-templating-basics"></a>Veri şablonu oluşturma temelleri

 <xref:System.Windows.DataTemplate> neden önemli olduğunu göstermek için bir veri bağlama örneğinde dolaşalım. Bu örnekte, bir `Task` nesneleri listesine bağlanan <xref:System.Windows.Controls.ListBox> vardır. Her `Task` nesnesi bir `TaskName` (dize), bir `Description` (dize), `Priority` (int) ve `TaskType`ve `Enum` değerleri olan `Home` türünde bir özelliktir.

 [!code-xaml[DataTemplatingIntro_snip#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#resources)]
[!code-xaml[DataTemplatingIntro_snip#UI1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#ui1)]
[!code-xaml[DataTemplatingIntro_snip#UI2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#ui2)]

<a name="without_a_datatemplate"></a>
### <a name="without-a-datatemplate"></a>DataTemplate olmadan
 <xref:System.Windows.DataTemplate>olmadan <xref:System.Windows.Controls.ListBox> Şu anda şöyle görünür:

 ![Veri şablonu oluşturma örnek ekran görüntüsü](./media/datatemplatingintro-fig1.png "DataTemplatingIntro_fig1")

 Ne olur? belirli yönergeler olmadan <xref:System.Windows.Controls.ListBox>, varsayılan olarak, koleksiyondaki nesneleri görüntülemeye çalışırken `ToString` çağırır. Bu nedenle, `Task` nesnesi `ToString` yöntemini geçersiz kılıyorsa, <xref:System.Windows.Controls.ListBox> temel koleksiyondaki her kaynak nesnenin dize gösterimini görüntüler.

 Örneğin, `Task` sınıfı bu şekilde `ToString` yöntemini geçersiz kılıyorsa, burada `name` `TaskName` özelliğinin alanıdır:

 [!code-csharp[DataTemplatingIntro_snip#ToString](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Data.cs#tostring)]
 [!code-vb[DataTemplatingIntro_snip#ToString](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataTemplatingIntro_snip/visualbasic/data.vb#tostring)]

 <xref:System.Windows.Controls.ListBox> aşağıdaki gibi görünür:

 ![Veri şablonu oluşturma örnek ekran görüntüsü](./media/datatemplatingintro-fig2.png "DataTemplatingIntro_fig2")

 Ancak, bu sınırlama ve esnek bir şekilde kullanılır. Ayrıca, XML verilerine bağlıyorsanız `ToString`geçersiz kılamazsınız.

<a name="defining_simple_datatemplate"></a>
### <a name="defining-a-simple-datatemplate"></a>Basit bir DataTemplate tanımlama
 Çözüm bir <xref:System.Windows.DataTemplate>tanımlamaktır. Bunu yapmanın bir yolu, <xref:System.Windows.Controls.ListBox> <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> özelliğini bir <xref:System.Windows.DataTemplate>olarak ayarlamanıza yönelik bir yoldur. <xref:System.Windows.DataTemplate> ne belirtdikleriniz, veri nesnenizin görsel yapısı haline gelir. Aşağıdaki <xref:System.Windows.DataTemplate> oldukça basittir. Her öğenin bir <xref:System.Windows.Controls.StackPanel>içinde üç <xref:System.Windows.Controls.TextBlock> öğe olarak göründüğüne ilişkin yönergeler sunuyoruz. Her <xref:System.Windows.Controls.TextBlock> öğesi `Task` sınıfının bir özelliğine bağlanır.

 [!code-xaml[DataTemplatingIntro_snip#Inline](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#inline)]

 Bu konudaki örneklerin temel alınan verileri, CLR nesnelerinin bir koleksiyonudur. XML verilerine bağlıyorsanız, temel kavramlar aynıdır, ancak hafif bir sözdizimi farkı vardır. Örneğin, `Path=TaskName`olması yerine <xref:System.Windows.Data.Binding.XPath%2A> `@TaskName` (`TaskName` XML düğümünüz bir özniteliği ise) olarak ayarlamanız gerekir.

 Şimdi <xref:System.Windows.Controls.ListBox> şu şekilde görünür:

 ![Veri şablonu oluşturma örnek ekran görüntüsü](./media/datatemplatingintro-fig3.png "DataTemplatingIntro_fig3")

<a name="defining_datatemplate_as_a_resource"></a>
### <a name="creating-the-datatemplate-as-a-resource"></a>DataTemplate 'i kaynak olarak oluşturma
 Yukarıdaki örnekte <xref:System.Windows.DataTemplate> satır içi olarak tanımlamış olduğumuz. Aşağıdaki örnekte olduğu gibi yeniden kullanılabilir bir nesne olması için kaynaklar bölümünde tanımlanması daha yaygındır.

 [!code-xaml[DataTemplatingIntro_snip#R1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r1)]
[!code-xaml[DataTemplatingIntro_snip#AsResource](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#asresource)]
[!code-xaml[DataTemplatingIntro_snip#R2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r2)]

 Artık, aşağıdaki örnekte olduğu gibi `myTaskTemplate` kaynak olarak kullanabilirsiniz:

 [!code-xaml[DataTemplatingIntro_snip#MyTaskTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#mytasktemplate)]

 `myTaskTemplate` bir kaynak olduğundan, artık bunu bir <xref:System.Windows.DataTemplate> türü alan özelliğe sahip diğer denetimlerde kullanabilirsiniz. Yukarıda gösterildiği gibi, <xref:System.Windows.Controls.ListBox>gibi <xref:System.Windows.Controls.ItemsControl> nesneler için <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> özelliğidir. <xref:System.Windows.Controls.ContentControl> nesneler için, <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> özelliktir.

<a name="Styling_DataType"></a>
### <a name="the-datatype-property"></a>DataType özelliği
 <xref:System.Windows.DataTemplate> sınıfı, <xref:System.Windows.Style> sınıfının <xref:System.Windows.Style.TargetType%2A> özelliğine çok benzeyen bir <xref:System.Windows.DataTemplate.DataType%2A> özelliğine sahiptir. Bu nedenle, yukarıdaki örnekteki <xref:System.Windows.DataTemplate> için bir `x:Key` belirtmek yerine şunları yapabilirsiniz:

 [!code-xaml[DataTemplatingIntro_snip#DataType](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#datatype)]

 Bu <xref:System.Windows.DataTemplate> tüm `Task` nesnelerine otomatik olarak uygulanır. Bu durumda `x:Key` örtük olarak ayarlanır. Bu nedenle, bu <xref:System.Windows.DataTemplate> bir `x:Key` değeri atarsanız, örtük `x:Key` geçersiz kıldınız ve <xref:System.Windows.DataTemplate> otomatik olarak uygulanmaz.

 Bir <xref:System.Windows.Controls.ContentControl> `Task` nesneleri koleksiyonuna bağlıyorsanız, <xref:System.Windows.Controls.ContentControl> yukarıdaki <xref:System.Windows.DataTemplate> otomatik olarak kullanmaz. Bunun nedeni, bir <xref:System.Windows.Controls.ContentControl> bağlamanın, bir koleksiyonun tamamına veya tek tek nesneleri bağlamak isteyip istemediğinizi belirtmek için daha fazla bilgi ihtiyacı vardır. <xref:System.Windows.Controls.ContentControl>, bir <xref:System.Windows.Controls.ItemsControl> türünün seçimini izleiyorsa, geçerli öğeyle ilgilendiğinizi göstermek için <xref:System.Windows.Controls.ContentControl> bağlamasının <xref:System.Windows.Data.Binding.Path%2A> özelliğini "`/`" olarak ayarlayabilirsiniz. Bir örnek için bkz. [bir koleksiyona bağlama ve seçime göre bilgi görüntüleme](how-to-bind-to-a-collection-and-display-information-based-on-selection.md). Aksi takdirde, <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> özelliğini ayarlayarak <xref:System.Windows.DataTemplate> açıkça belirtmeniz gerekir.

 <xref:System.Windows.DataTemplate.DataType%2A> özelliği, özellikle farklı türlerde veri nesneleri <xref:System.Windows.Data.CompositeCollection> olduğunda yararlıdır. Bir örnek için bkz. [CompositeCollection uygulama](how-to-implement-a-compositecollection.md).

<a name="adding_more_to_datatemplate"></a>
## <a name="adding-more-to-the-datatemplate"></a>DataTemplate 'e daha fazla ekleme
 Şu anda veriler gerekli bilgilerle birlikte görüntülenir, ancak geliştirme için kesin bir oda vardır. <xref:System.Windows.Controls.Border>, <xref:System.Windows.Controls.Grid>ve görüntülenmekte olan verileri tanımlayan bazı <xref:System.Windows.Controls.TextBlock> öğelerini ekleyerek sunumu geliştirelim.

 [!code-xaml[DataTemplatingIntro#AddingMore](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore)]
[!code-xaml[DataTemplatingIntro#AddingMore2](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore2)]

 Aşağıdaki ekran görüntüsünde, bu değiştirilen <xref:System.Windows.DataTemplate><xref:System.Windows.Controls.ListBox> gösterilmektedir:

 ![Veri şablonu oluşturma örnek ekran görüntüsü](./media/datatemplatingintro-fig4.png "DataTemplatingIntro_fig4")

 Öğelerin genişliğinin tüm alanı kaplakından emin olmak için <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> <xref:System.Windows.Controls.ListBox> <xref:System.Windows.HorizontalAlignment.Stretch> ayarlayabiliriz:

 [!code-xaml[DataTemplatingIntro_snip#Stretch](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#stretch)]

 <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> özelliği <xref:System.Windows.HorizontalAlignment.Stretch>olarak ayarlandığında <xref:System.Windows.Controls.ListBox> şu şekilde görünür:

 ![Veri şablonu oluşturma örnek ekran görüntüsü](./media/datatemplatingintro-fig5.png "DataTemplatingIntro_fig5")

<a name="DataTrigger_to_Apply_Property_Values"></a>
### <a name="use-datatriggers-to-apply-property-values"></a>Özellik değerlerini uygulamak için veri tetikleyicilerini kullanın
 Geçerli sunu, bir `Task` giriş görevi mi yoksa Office görevi mi olduğunu bize söylemez. `Task` nesnesinin, `Home` ve `Work`değerlerini içeren bir numaralandırma olan `TaskType`türünde bir `TaskType` özelliğine sahip olduğunu unutmayın.

 Aşağıdaki örnekte <xref:System.Windows.DataTrigger>, `TaskType` özelliği `TaskType.Home`ise, `border` adlı öğenin <xref:System.Windows.Controls.Border.BorderBrush%2A> `Yellow` olarak ayarlar.

 [!code-xaml[DataTemplatingIntro#DT](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#dt)]
[!code-xaml[DataTemplatingIntro#DataTrigger](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#datatrigger)]
[!code-xaml[DataTemplatingIntro#AddingMore2](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore2)]

 Uygulamamız artık aşağıdaki gibi görünüyor. Giriş görevleri sarı bir kenarlıkla görünür ve Office görevleri deniz mavisi bir kenarlıkla görüntülenir:

 ![Veri şablonu oluşturma örnek ekran görüntüsü](./media/datatemplatingintro-fig6.png "DataTemplatingIntro_fig6")

 Bu örnekte <xref:System.Windows.DataTrigger>, bir özellik değeri ayarlamak için bir <xref:System.Windows.Setter> kullanır. Tetikleyici sınıflarda Ayrıca, animasyonlar gibi bir dizi eylemi başlatmalarını sağlayan <xref:System.Windows.TriggerBase.EnterActions%2A> ve <xref:System.Windows.TriggerBase.ExitActions%2A> özellikleri de vardır. Ayrıca, birden çok veriye bağlı özellik değerine göre değişiklikler uygulamanıza olanak sağlayan bir <xref:System.Windows.MultiDataTrigger> sınıfı da vardır.

 Aynı etkiyi elde etmenin alternatif bir yolu, <xref:System.Windows.Controls.Border.BorderBrush%2A> özelliğini `TaskType` özelliğine bağlamak ve bir değer dönüştürücüsü kullanarak rengi `TaskType` değerine göre geri döndürmenin bir yoludur. Bir dönüştürücüyü kullanarak yukarıdaki efektin oluşturulması, performans açısından biraz daha etkilidir. Ayrıca, kendi bir mantığınızı tedarik ettiğiniz için kendi dönüştürücüyü oluşturmanız daha fazla esneklik sağlar. Son olarak, seçtiğiniz teknik, senaryonuza ve tercihlerinize bağlıdır. Dönüştürücü yazma hakkında daha fazla bilgi için bkz. <xref:System.Windows.Data.IValueConverter>.

<a name="what_belongs_in_datatemplate"></a>
### <a name="what-belongs-in-a-datatemplate"></a>DataTemplate 'e ait olanlar nelerdir?

Önceki örnekte, <xref:System.Windows.DataTemplate.Triggers%2A?displayProperty=nameWithType> özelliğini kullanarak tetikleyiciyi <xref:System.Windows.DataTemplate> yerleştirdik. Tetikleyicinin <xref:System.Windows.Setter>, <xref:System.Windows.DataTemplate>içindeki bir öğenin (<xref:System.Windows.Controls.Border> öğesi) bir özelliğinin değerini ayarlar. Ancak, `Setters` özellikler geçerli <xref:System.Windows.DataTemplate>içindeki öğelerin özellikleri değilse, özellikleri <xref:System.Windows.Controls.ListBoxItem> sınıfı için olan bir <xref:System.Windows.Style> kullanarak ayarlamak daha uygun olabilir (Eğer bağladığınız denetim bir ise <xref:System.Windows.Controls.ListBox>). Örneğin, bir fare bir öğeye işaret ediyorsa, <xref:System.Windows.Trigger> öğenin <xref:System.Windows.UIElement.Opacity%2A> değerine animasyon eklemek istiyorsanız, Tetikleyicileri bir <xref:System.Windows.Controls.ListBoxItem> stili içinde tanımlarsınız. Bir örnek için, [Stillendirme ve şablon oluşturma örneğine giriş](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)konusuna bakın.

 Genel olarak, <xref:System.Windows.DataTemplate> oluşturulan <xref:System.Windows.Controls.ListBoxItem> her birine uygulandığını göz önünde bulundurun (gerçekte nasıl ve nerede uygulandığı hakkında daha fazla bilgi için, bkz. <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> sayfası.). <xref:System.Windows.DataTemplate>, yalnızca veri nesnelerinin sunumu ve görünümüyle ilgilidir. Çoğu durumda, öğenin seçilme gibi göründüğü veya <xref:System.Windows.Controls.ListBox> öğeleri nasıl düzenlediklerinin bir <xref:System.Windows.DataTemplate>tanımına ait olmadığı gibi sununun diğer tüm yönleri. Bir örnek için bkz. [Stil oluşturma ve şablon oluşturma bir ıtemı denetimi](#DataTemplating_ItemsControl) bölümü.

<a name="Styling_StyleSelection"></a>
## <a name="choosing-a-datatemplate-based-on-properties-of-the-data-object"></a>Veri nesnesinin özelliklerine dayalı bir DataTemplate seçme
 [DataType özelliği](#Styling_DataType) bölümünde, farklı veri nesneleri için farklı veri şablonları tanımlayacağınızı tartıştık. Bu, özellikle farklı türlerde öğeler içeren farklı türlerde veya koleksiyonlardan <xref:System.Windows.Data.CompositeCollection> olduğunda faydalıdır. [Özellik değerlerini uygulamak için veri tetikleyicilerini kullan](#DataTrigger_to_Apply_Property_Values) bölümünde, aynı türde veri nesneleri koleksiyonunuz varsa <xref:System.Windows.DataTemplate> oluşturup her bir veri nesnesinin özellik değerlerine göre değişiklikleri uygulamak için Tetikleyicileri kullanabilirsiniz. Ancak Tetikleyiciler, özellik değerlerini uygulamanıza veya animasyonları başlatmaya izin verir, ancak size veri nesnelerinizin yapısını yeniden oluşturmak için esneklik vermez. Bazı senaryolar, aynı türde ancak farklı özelliklere sahip olan veri nesneleri için farklı bir <xref:System.Windows.DataTemplate> oluşturmanızı gerektirebilir.

 Örneğin, bir `Task` nesnesi `1``Priority` değerine sahip olduğunda, kendinize uyarı olarak sunmak için tamamen farklı bir görünüm vermek isteyebilirsiniz. Bu durumda, yüksek öncelikli `Task` nesnelerinin görüntülenmesi için bir <xref:System.Windows.DataTemplate> oluşturursunuz. Kaynaklar bölümüne aşağıdaki <xref:System.Windows.DataTemplate> ekleyelim:

 [!code-xaml[DataTemplatingIntro_snip#ImportantTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#importanttemplate)]

Bu örnek, [DataTemplate. resources](xref:System.Windows.FrameworkTemplate.Resources%2A) özelliğini kullanır. Bu bölümde tanımlanan kaynaklar <xref:System.Windows.DataTemplate>içindeki öğeler tarafından paylaşılır.

 Veri nesnesinin `Priority` değerine göre hangi <xref:System.Windows.DataTemplate> kullanacağınızı seçme mantığını sağlamak için, <xref:System.Windows.Controls.DataTemplateSelector> bir alt sınıfı oluşturun ve <xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A> yöntemini geçersiz kılın. Aşağıdaki örnekte <xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A> yöntemi, `Priority` özelliğinin değerine göre uygun şablonu döndürmek için mantık sağlar. Döndürülecek şablon, enveloping <xref:System.Windows.Window> öğesinin kaynaklarında bulunur.

 [!code-csharp[DataTemplatingIntro_snip#DTSClass](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/TaskListDataTemplateSelector.cs#dtsclass)]
 [!code-vb[DataTemplatingIntro_snip#DTSClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataTemplatingIntro_snip/visualbasic/tasklistdatatemplateselector.vb#dtsclass)]

 Daha sonra `TaskListDataTemplateSelector` kaynak olarak bildirebiliriz:

 [!code-xaml[DataTemplatingIntro_snip#R1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r1)]
[!code-xaml[DataTemplatingIntro_snip#DTS](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#dts)]
[!code-xaml[DataTemplatingIntro_snip#R2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r2)]

 Şablon Seçici kaynağını kullanmak için, <xref:System.Windows.Controls.ListBox><xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A> özelliğine atayın. <xref:System.Windows.Controls.ListBox>, temel koleksiyondaki öğelerin her biri için `TaskListDataTemplateSelector` <xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A> yöntemini çağırır. Çağrı, veri nesnesini öğe parametresi olarak geçirir. Yöntemi tarafından döndürülen <xref:System.Windows.DataTemplate> bu veri nesnesine uygulanır.

 [!code-xaml[DataTemplatingIntro_snip#ItemTemplateSelector](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#itemtemplateselector)]

 Şablon seçiciyle birlikte <xref:System.Windows.Controls.ListBox> artık aşağıdaki gibi görünür:

 ![Veri şablonu oluşturma örnek ekran görüntüsü](./media/datatemplatingintro-fig7.png "DataTemplatingIntro_fig7")

Bu, bu örneğe ilişkin tartışmamızı yerine eriyor. Tüm örnek için bkz. [veri şablonu oluşturma örneğine giriş](https://github.com/Microsoft/WPF-Samples/tree/master/Data%20Binding/DataTemplatingIntro).

<a name="DataTemplating_ItemsControl"></a>
## <a name="styling-and-templating-an-itemscontrol"></a>Itembir denetimin stillendirilmesini ve şablon oluşturma
 <xref:System.Windows.Controls.ItemsControl>, ile <xref:System.Windows.DataTemplate> kullanabileceğiniz tek denetim türü olmasa da, bir <xref:System.Windows.Controls.ItemsControl> koleksiyona bağlamak çok yaygın bir senaryodur. DataTemplate 'e [ait](#what_belongs_in_datatemplate) olan Özellikler bölümünde, <xref:System.Windows.DataTemplate> tanımının yalnızca veri sunumu ile ilgilenildiği açıklanmaktadır. <xref:System.Windows.DataTemplate> kullanmaya uygun olmadığını bilmek için, <xref:System.Windows.Controls.ItemsControl>tarafından sunulan farklı stil ve şablon özelliklerini anlamak önemlidir. Aşağıdaki örnek, bu özelliklerin her birinin işlevini göstermek için tasarlanmıştır. Bu örnekteki <xref:System.Windows.Controls.ItemsControl>, önceki örnekteki gibi aynı `Tasks` koleksiyonuna bağlanır. Tanıtım amacıyla, bu örnekteki stillerin ve şablonların hepsi satır içi olarak bildirilmiştir.

 [!code-xaml[DataTemplatingIntro_snip#ItemsControlProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#itemscontrolproperties)]

 Aşağıda, örneği işlendiğinde örnek bir ekran görüntüsü verilmiştir:

 ![Itemkıcontrol örnek ekran görüntüsü](./media/databinding-itemscontrolproperties.png "DataBinding_ItemsControlProperties")

 <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>kullanmak yerine <xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A>kullanabileceğinizi unutmayın. Bir örnek için önceki bölüme bakın. Benzer şekilde, <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>kullanmak yerine <xref:System.Windows.Controls.ItemsControl.ItemContainerStyleSelector%2A>kullanma seçeneğiniz vardır.

 Burada görünmeyen <xref:System.Windows.Controls.ItemsControl> stil ile ilgili diğer iki özelliği <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> ve <xref:System.Windows.Controls.ItemsControl.GroupStyleSelector%2A>.

<a name="DataTemplating_HeirarchicalDataTemplate"></a>
## <a name="support-for-hierarchical-data"></a>Hiyerarşik veri desteği
 Şimdiye kadar, yalnızca tek bir koleksiyon için bağlama ve görüntüleme hakkında baktık. Bazen diğer koleksiyonları içeren bir koleksiyonunuz vardır. <xref:System.Windows.HierarchicalDataTemplate> sınıfı, bu tür verileri göstermek için <xref:System.Windows.Controls.HeaderedItemsControl> türleriyle kullanılmak üzere tasarlanmıştır. Aşağıdaki örnekte, `ListLeagueList` `League` nesnelerinin bir listesidir. Her `League` nesnesi bir `Name` ve `Division` nesneleri koleksiyonu içerir. Her `Division` bir `Name` ve bir `Team` nesneleri koleksiyonu vardır ve her `Team` nesnesi bir `Name`içerir.

 [!code-xaml[HierarchicalDataTemplateSnippet#HDT](~/samples/snippets/csharp/VS_Snippets_Wpf/HierarchicalDataTemplateSnippet/CS/window1.xaml#hdt)]

 Örnek, <xref:System.Windows.HierarchicalDataTemplate>kullanımı ile diğer listeleri içeren liste verilerini kolayca görüntülemenizi gösterir. Aşağıda, örneğin bir ekran görüntüsü verilmiştir.

 ![HierarchicalDataTemplate örnek ekran görüntüsü](./media/databinding-hierarchicaldatatemplate.png "DataBinding_HierarchicalDataTemplate")

## <a name="see-also"></a>Ayrıca bkz.

- [Veri Bağlama](../advanced/optimizing-performance-data-binding.md)
- [DataTemplate ile Oluşturulan Öğeleri Bulma](how-to-find-datatemplate-generated-elements.md)
- [Stil ve Şablon Oluşturma](../controls/styling-and-templating.md)
- [Veri Bağlamaya Genel Bakış](../../../desktop-wpf/data/data-binding-overview.md)
- [GridView Sütun Üst Bilgi Stil ve Şablonlarına Genel Bakış](../controls/gridview-column-header-styles-and-templates-overview.md)
