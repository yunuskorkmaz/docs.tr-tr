---
title: Veri Şablonu Oluşturmaya Genel Bakış
description: Windows Presentation Foundation (WPF) ' de verilerinizin sunumunu tanımlayan veri şablonu oluşturma modeli esnekliğini keşfedelim.
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
ms.openlocfilehash: 0226085a82cf97ea799a5a2d38e879b239d9b52a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619656"
---
# <a name="data-templating-overview"></a>Veri Şablonu Oluşturmaya Genel Bakış
WPF veri şablonu oluşturma modeli, verilerinizin sunumunu tanımlamak için size büyük bir esneklik sağlar. WPF denetimleri, veri sunumu özelleştirmeyi desteklemek için yerleşik işlevlere sahiptir. Bu konu, ilk olarak nasıl tanımlanacağını <xref:System.Windows.DataTemplate> ve daha sonra özel mantık ve hiyerarşik veri görüntüleme desteği gibi diğer veri şablonu oluşturma özelliklerinin nasıl tanıtıldiğini gösterir.

<a name="Prerequisites"></a>
## <a name="prerequisites"></a>Ön koşullar
 Bu konu, veri şablonu oluşturma özelliklerine odaklanmaktadır ve veri bağlama kavramlarının bir tanıtımı değildir. Temel veri bağlama kavramları hakkında daha fazla bilgi için bkz. [veri bağlamaya genel bakış](../../../desktop-wpf/data/data-binding-overview.md).

 <xref:System.Windows.DataTemplate>, verilerin sunumu ve WPF stili ve şablon oluşturma modeli tarafından sunulan birçok özellikten biridir. WPF stili ve şablon oluşturma modeli için bir giriş (örneğin, <xref:System.Windows.Style> denetimler üzerinde özellikleri ayarlamak için kullanma gibi) Için [Stil oluşturma ve şablon](../../../desktop-wpf/fundamentals/styles-templates-overview.md) oluşturma konusuna bakın.

 Buna ek olarak, `Resources` , ve gibi nesnelerin <xref:System.Windows.Style> yeniden kullanılabilir olmasını sağlayan, aslında anlaşılması önemlidir <xref:System.Windows.DataTemplate> . Kaynaklar hakkında daha fazla bilgi için bkz. [xaml kaynakları](../../../desktop-wpf/fundamentals/xaml-resources-define.md).

<a name="DataTemplating_Basic"></a>
## <a name="data-templating-basics"></a>Veri şablonu oluşturma temelleri

 Neden <xref:System.Windows.DataTemplate> önemli olduğunu göstermek için bir veri bağlama örneğinde dolaşalım. Bu örnekte, bir <xref:System.Windows.Controls.ListBox> nesne listesine bağladık `Task` . Her `Task` nesnenin bir `TaskName` (dize), bir `Description` (dize), bir `Priority` (int) ve türünde bir özelliği, `TaskType` `Enum` ve değerleri ile `Home` `Work` olan bir özelliğine sahiptir.

 [!code-xaml[DataTemplatingIntro_snip#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#resources)]
[!code-xaml[DataTemplatingIntro_snip#UI1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#ui1)]
[!code-xaml[DataTemplatingIntro_snip#UI2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#ui2)]

<a name="without_a_datatemplate"></a>
### <a name="without-a-datatemplate"></a>DataTemplate olmadan
 Bir olmadan <xref:System.Windows.DataTemplate> <xref:System.Windows.Controls.ListBox> Şu anda şöyle görünür:

 ![Veri şablonu oluşturma örnek ekran görüntüsü](./media/datatemplatingintro-fig1.png "DataTemplatingIntro_fig1")

 Ne olur?, belirli yönergeler olmadan, <xref:System.Windows.Controls.ListBox> `ToString` koleksiyondaki nesneleri görüntülemeye çalışırken varsayılan olarak çağırır. Bu nedenle, `Task` nesne yöntemi geçersiz kıldığında, `ToString` <xref:System.Windows.Controls.ListBox> temel koleksiyondaki her kaynak nesnesinin dize gösterimini görüntüler.

 Örneğin, `Task` sınıfı `ToString` Bu şekilde yöntemi geçersiz kıldığında, burada `name` `TaskName` özelliğin alanıdır:

 [!code-csharp[DataTemplatingIntro_snip#ToString](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Data.cs#tostring)]
 [!code-vb[DataTemplatingIntro_snip#ToString](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataTemplatingIntro_snip/visualbasic/data.vb#tostring)]

 Ardından <xref:System.Windows.Controls.ListBox> aşağıdaki gibi görünür:

 ![Veri şablonu oluşturma örnek ekran görüntüsü](./media/datatemplatingintro-fig2.png "DataTemplatingIntro_fig2")

 Ancak, bu sınırlama ve esnek bir şekilde kullanılır. Ayrıca, XML verilerine bağlıyorsanız, geçersiz kılamazsınız `ToString` .

<a name="defining_simple_datatemplate"></a>
### <a name="defining-a-simple-datatemplate"></a>Basit bir DataTemplate tanımlama
 Çözüm bir tanımlar <xref:System.Windows.DataTemplate> . Bunu yapmanın bir yolu, öğesinin özelliğini ' a ayarlamaya yönelik bir yoldur <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> <xref:System.Windows.Controls.ListBox> <xref:System.Windows.DataTemplate> . Uygulamanızda belirttiğiniz Özellikler <xref:System.Windows.DataTemplate> , veri nesnenizin görsel yapısı haline gelir. Aşağıdakiler <xref:System.Windows.DataTemplate> oldukça basittir. Her öğenin bir içinde üç öğe olarak göründüğüne ilişkin yönergeler sunuyoruz <xref:System.Windows.Controls.TextBlock> <xref:System.Windows.Controls.StackPanel> . Her <xref:System.Windows.Controls.TextBlock> öğe, sınıfının bir özelliğine bağlanır `Task` .

 [!code-xaml[DataTemplatingIntro_snip#Inline](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#inline)]

 Bu konudaki örneklerin temel alınan verileri, CLR nesnelerinin bir koleksiyonudur. XML verilerine bağlıyorsanız, temel kavramlar aynıdır, ancak hafif bir sözdizimi farkı vardır. Örneğin, yerine, `Path=TaskName` <xref:System.Windows.Data.Binding.XPath%2A> `@TaskName` ( `TaskName` XML düğümünüz bir özniteliği ise) olarak ayarlanır.

 Şimdi <xref:System.Windows.Controls.ListBox> Şu şekilde görünür:

 ![Veri şablonu oluşturma örnek ekran görüntüsü](./media/datatemplatingintro-fig3.png "DataTemplatingIntro_fig3")

<a name="defining_datatemplate_as_a_resource"></a>
### <a name="creating-the-datatemplate-as-a-resource"></a>DataTemplate 'i kaynak olarak oluşturma
 Yukarıdaki örnekte, <xref:System.Windows.DataTemplate> satır içi tanımlandık. Aşağıdaki örnekte olduğu gibi yeniden kullanılabilir bir nesne olması için kaynaklar bölümünde tanımlanması daha yaygındır.

 [!code-xaml[DataTemplatingIntro_snip#R1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r1)]
[!code-xaml[DataTemplatingIntro_snip#AsResource](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#asresource)]
[!code-xaml[DataTemplatingIntro_snip#R2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r2)]

 Artık `myTaskTemplate` Aşağıdaki örnekte olduğu gibi kaynak olarak kullanabilirsiniz:

 [!code-xaml[DataTemplatingIntro_snip#MyTaskTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#mytasktemplate)]

 `myTaskTemplate`Bir kaynak olduğundan, artık bunu türü alan bir özelliği olan diğer denetimlerde kullanabilirsiniz <xref:System.Windows.DataTemplate> . Yukarıda gösterildiği gibi nesneler için, <xref:System.Windows.Controls.ItemsControl> <xref:System.Windows.Controls.ListBox> <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> özelliği ise özelliğidir. <xref:System.Windows.Controls.ContentControl>Nesneler için, <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> özelliği olur.

<a name="Styling_DataType"></a>
### <a name="the-datatype-property"></a>DataType özelliği
 <xref:System.Windows.DataTemplate>Sınıfı, <xref:System.Windows.DataTemplate.DataType%2A> sınıfının özelliğine çok benzeyen bir özelliğe sahiptir <xref:System.Windows.Style.TargetType%2A> <xref:System.Windows.Style> . Bu nedenle, `x:Key` Yukarıdaki örnekte için bir için belirtmek yerine <xref:System.Windows.DataTemplate> şunları yapabilirsiniz:

 [!code-xaml[DataTemplatingIntro_snip#DataType](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#datatype)]

 Bu, <xref:System.Windows.DataTemplate> tüm nesnelere otomatik olarak uygulanır `Task` . Bu durumda, `x:Key` örtük olarak ayarlanır. Bu nedenle, bu değeri atarsanız <xref:System.Windows.DataTemplate> `x:Key` , örtük `x:Key` olarak geçersiz <xref:System.Windows.DataTemplate> kıldınız ve otomatik olarak uygulanmaz.

 Bir nesne koleksiyonuna bağlıyorsanız, <xref:System.Windows.Controls.ContentControl> `Task` ' ı <xref:System.Windows.Controls.ContentControl> <xref:System.Windows.DataTemplate> otomatik olarak kullanmaz. Bunun nedeni, bir <xref:System.Windows.Controls.ContentControl> koleksiyonun tamamına veya tek tek nesnelere bağlamak isteyip istemediğinizi belirtmek için bir, ' deki bağlamanın daha fazla bilgiye ihtiyacı vardır. <xref:System.Windows.Controls.ContentControl>Bir türün seçimini izleiyorsa <xref:System.Windows.Controls.ItemsControl> , <xref:System.Windows.Data.Binding.Path%2A> <xref:System.Windows.Controls.ContentControl> `/` geçerli öğe ile ilgilendiğinizi göstermek için bağlama özelliğini "" olarak ayarlayabilirsiniz. Bir örnek için bkz. [bir koleksiyona bağlama ve seçime göre bilgi görüntüleme](how-to-bind-to-a-collection-and-display-information-based-on-selection.md). Aksi takdirde, <xref:System.Windows.DataTemplate> özelliğini ayarlayarak açıkça belirtmeniz gerekir <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> .

 <xref:System.Windows.DataTemplate.DataType%2A>Özelliği, özellikle <xref:System.Windows.Data.CompositeCollection> farklı türde veri nesneleriniz olduğunda yararlıdır. Bir örnek için bkz. [CompositeCollection uygulama](how-to-implement-a-compositecollection.md).

<a name="adding_more_to_datatemplate"></a>
## <a name="adding-more-to-the-datatemplate"></a>DataTemplate 'e daha fazla ekleme
 Şu anda veriler gerekli bilgilerle birlikte görüntülenir, ancak geliştirme için kesin bir oda vardır. <xref:System.Windows.Controls.Border> <xref:System.Windows.Controls.Grid> Görüntülenen verileri betimleyen bir, a ve bazı öğeler ekleyerek sunumu geliştirelim <xref:System.Windows.Controls.TextBlock> .

 [!code-xaml[DataTemplatingIntro#AddingMore](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore)]
[!code-xaml[DataTemplatingIntro#AddingMore2](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore2)]

 Aşağıdaki ekran görüntüsünde, <xref:System.Windows.Controls.ListBox> Bu değiştirilmekte olan ile gösterilir <xref:System.Windows.DataTemplate> :

 ![Veri şablonu oluşturma örnek ekran görüntüsü](./media/datatemplatingintro-fig4.png "DataTemplatingIntro_fig4")

 <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> <xref:System.Windows.HorizontalAlignment.Stretch> <xref:System.Windows.Controls.ListBox> Öğelerin genişliğinin tüm alana sahip olduğundan emin olmak için üzerinde olarak ayarlayabiliriz:

 [!code-xaml[DataTemplatingIntro_snip#Stretch](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#stretch)]

 <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A>Özelliği olarak ayarlandığında <xref:System.Windows.HorizontalAlignment.Stretch> , <xref:System.Windows.Controls.ListBox> Şimdi şöyle görünür:

 ![Veri şablonu oluşturma örnek ekran görüntüsü](./media/datatemplatingintro-fig5.png "DataTemplatingIntro_fig5")

<a name="DataTrigger_to_Apply_Property_Values"></a>
### <a name="use-datatriggers-to-apply-property-values"></a>Özellik değerlerini uygulamak için veri tetikleyicilerini kullanın
 Geçerli sunu, bir `Task` giriş görevi mi yoksa Office görevi mi olduğunu bize söylemez. `Task`Nesnesinin `TaskType` , değerlerine sahip bir numaralandırma olan türünde bir özelliği olduğunu unutmayın `TaskType` `Home` `Work` .

 Aşağıdaki örnekte, <xref:System.Windows.DataTrigger> <xref:System.Windows.Controls.Border.BorderBrush%2A> özelliği öğesi olarak adlandırılan öğesini `border` olarak ayarlar `Yellow` `TaskType` `TaskType.Home` .

 [!code-xaml[DataTemplatingIntro#DT](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#dt)]
[!code-xaml[DataTemplatingIntro#DataTrigger](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#datatrigger)]
[!code-xaml[DataTemplatingIntro#AddingMore2](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore2)]

 Uygulamamız artık aşağıdaki gibi görünüyor. Giriş görevleri sarı bir kenarlıkla görünür ve Office görevleri deniz mavisi bir kenarlıkla görüntülenir:

 ![Veri şablonu oluşturma örnek ekran görüntüsü](./media/datatemplatingintro-fig6.png "DataTemplatingIntro_fig6")

 Bu örnekte, <xref:System.Windows.DataTrigger> bir <xref:System.Windows.Setter> özellik değeri ayarlamak için bir kullanır. Tetikleyici sınıfları, <xref:System.Windows.TriggerBase.EnterActions%2A> <xref:System.Windows.TriggerBase.ExitActions%2A> animasyonlar gibi bir dizi eyleme başlayabilmeniz için ve özelliklerini de sağlar. Ayrıca, <xref:System.Windows.MultiDataTrigger> birden çok veriye bağlı özellik değerine göre değişiklikler uygulamanıza olanak sağlayan bir sınıf de vardır.

 Aynı etkiyi elde etmenin alternatif bir yolu, özelliği <xref:System.Windows.Controls.Border.BorderBrush%2A> `TaskType` özelliğine bağlamak ve değeri temel alarak rengi döndürmek için bir değer Dönüştürücüsü kullanmaktır `TaskType` . Bir dönüştürücüyü kullanarak yukarıdaki efektin oluşturulması, performans açısından biraz daha etkilidir. Ayrıca, kendi bir mantığınızı tedarik ettiğiniz için kendi dönüştürücüyü oluşturmanız daha fazla esneklik sağlar. Son olarak, seçtiğiniz teknik, senaryonuza ve tercihlerinize bağlıdır. Dönüştürücü yazma hakkında daha fazla bilgi için bkz <xref:System.Windows.Data.IValueConverter> ..

<a name="what_belongs_in_datatemplate"></a>
### <a name="what-belongs-in-a-datatemplate"></a>DataTemplate 'e ait olanlar nelerdir?

Önceki örnekte, özelliğini kullanarak tetikleyiciyi içine yerleştirdik <xref:System.Windows.DataTemplate> <xref:System.Windows.DataTemplate.Triggers%2A?displayProperty=nameWithType> . <xref:System.Windows.Setter>Tetikleyicisinin içinde olan bir öğenin (öğe) özelliğinin değerini ayarlar <xref:System.Windows.Controls.Border> <xref:System.Windows.DataTemplate> . Ancak, sizin için uygun olan Özellikler `Setters` geçerli olan öğelerin özellikleri değilse <xref:System.Windows.DataTemplate> , <xref:System.Windows.Style> sınıfı için olan <xref:System.Windows.Controls.ListBoxItem> (Eğer bağladığınız denetim bir ise) özellikleri ayarlamak daha uygun olabilir <xref:System.Windows.Controls.ListBox> . Örneğin, <xref:System.Windows.Trigger> <xref:System.Windows.UIElement.Opacity%2A> fare bir öğeye işaret ediyorsa öğenin değerine animasyon eklemek istiyorsanız, tetikleri bir stil içinde tanımlarsınız <xref:System.Windows.Controls.ListBoxItem> . Bir örnek için, [Stillendirme ve şablon oluşturma örneğine giriş](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)konusuna bakın.

 Genel olarak, <xref:System.Windows.DataTemplate> oluşturulan her birine uygulandığını aklınızda bulundurun <xref:System.Windows.Controls.ListBoxItem> (gerçekte nasıl ve nerede uygulandığı hakkında daha fazla bilgi için, <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> sayfasına bakın.). <xref:System.Windows.DataTemplate>Yalnızca veri nesnelerinin sunumu ve görünümü ile ilgilenme amaçlıdır. Çoğu durumda, öğenin ne zaman seçildiği veya öğelerin nasıl oluşturulduğu gibi göründüğü gibi sununun diğer tüm yönleri, ' <xref:System.Windows.Controls.ListBox> ın tanımına ait değildir <xref:System.Windows.DataTemplate> . Bir örnek için bkz. [Stil oluşturma ve şablon oluşturma bir ıtemı denetimi](#DataTemplating_ItemsControl) bölümü.

<a name="Styling_StyleSelection"></a>
## <a name="choosing-a-datatemplate-based-on-properties-of-the-data-object"></a>Veri nesnesinin özelliklerine dayalı bir DataTemplate seçme
 [DataType özelliği](#Styling_DataType) bölümünde, farklı veri nesneleri için farklı veri şablonları tanımlayacağınızı tartıştık. Bu, özellikle <xref:System.Windows.Data.CompositeCollection> farklı türlerde öğeler içeren farklı türlerde veya koleksiyonlarınız olduğunda faydalıdır. [Özellik değerlerini uygulamak için veri tetikleyicilerini kullan](#DataTrigger_to_Apply_Property_Values) bölümünde, oluşturabileceğiniz aynı türde veri nesneleri koleksiyonunuz varsa <xref:System.Windows.DataTemplate> ve sonra her bir veri nesnesinin özellik değerlerine göre değişiklikleri uygulamak için Tetikleyicileri kullanabilirsiniz. Ancak Tetikleyiciler, özellik değerlerini uygulamanıza veya animasyonları başlatmaya izin verir, ancak size veri nesnelerinizin yapısını yeniden oluşturmak için esneklik vermez. Bazı senaryolar, <xref:System.Windows.DataTemplate> aynı türde ancak farklı özelliklere sahip olan veri nesneleri için farklı bir oluşturmanız gerekebilir.

 Örneğin, bir `Task` nesnenin `Priority` değeri olduğunda `1` , kendinize bir uyarı olarak sunmak için tamamen farklı bir görünüm vermek isteyebilirsiniz. Bu durumda, <xref:System.Windows.DataTemplate> yüksek öncelikli nesnelerin görüntülenmesi için bir oluşturursunuz `Task` . Kaynaklar bölümüne aşağıdakileri ekleyelim <xref:System.Windows.DataTemplate> :

 [!code-xaml[DataTemplatingIntro_snip#ImportantTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#importanttemplate)]

Bu örnek, [DataTemplate. resources](xref:System.Windows.FrameworkTemplate.Resources%2A) özelliğini kullanır. Bu bölümde tanımlanan kaynaklar, içindeki öğeleri tarafından paylaşılır <xref:System.Windows.DataTemplate> .

 <xref:System.Windows.DataTemplate>Veri nesnesinin değerine göre kullanılacak mantığı sağlamak için `Priority` , bir alt sınıfı oluşturun <xref:System.Windows.Controls.DataTemplateSelector> ve metodunu geçersiz kılın <xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A> . Aşağıdaki örnekte, <xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A> yöntemi, özelliğin değerine göre uygun şablonu döndürmek için mantık sağlar `Priority` . Döndürülecek şablon enveloping öğesinin kaynaklarında bulunur <xref:System.Windows.Window> .

 [!code-csharp[DataTemplatingIntro_snip#DTSClass](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/TaskListDataTemplateSelector.cs#dtsclass)]
 [!code-vb[DataTemplatingIntro_snip#DTSClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataTemplatingIntro_snip/visualbasic/tasklistdatatemplateselector.vb#dtsclass)]

 Daha sonra bunu `TaskListDataTemplateSelector` kaynak olarak bildirebiliriz:

 [!code-xaml[DataTemplatingIntro_snip#R1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r1)]
[!code-xaml[DataTemplatingIntro_snip#DTS](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#dts)]
[!code-xaml[DataTemplatingIntro_snip#R2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r2)]

 Şablon Seçici kaynağını kullanmak için, <xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A> öğesinin özelliğine atayın <xref:System.Windows.Controls.ListBox> . , <xref:System.Windows.Controls.ListBox> <xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A> `TaskListDataTemplateSelector` Temel koleksiyondaki öğelerin her biri için yöntemini çağırır. Çağrı, veri nesnesini öğe parametresi olarak geçirir. <xref:System.Windows.DataTemplate>Yöntemi tarafından döndürülen bu veri nesnesine uygulanır.

 [!code-xaml[DataTemplatingIntro_snip#ItemTemplateSelector](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#itemtemplateselector)]

 Şablon seçiciyle birlikte <xref:System.Windows.Controls.ListBox> Şu şekilde görünür:

 ![Veri şablonu oluşturma örnek ekran görüntüsü](./media/datatemplatingintro-fig7.png "DataTemplatingIntro_fig7")

Bu, bu örneğe ilişkin tartışmamızı yerine eriyor. Tüm örnek için bkz. [veri şablonu oluşturma örneğine giriş](https://github.com/Microsoft/WPF-Samples/tree/master/Data%20Binding/DataTemplatingIntro).

<a name="DataTemplating_ItemsControl"></a>
## <a name="styling-and-templating-an-itemscontrol"></a>Itembir denetimin stillendirilmesini ve şablon oluşturma
 <xref:System.Windows.Controls.ItemsControl>İle kullanabileceğiniz tek denetim türü olmasa da, bir <xref:System.Windows.DataTemplate> koleksiyona bağlamak çok yaygın bir senaryodur <xref:System.Windows.Controls.ItemsControl> . DataTemplate 'e [ait](#what_belongs_in_datatemplate) olan Özellikler bölümünde, ' ın tanımının <xref:System.Windows.DataTemplate> yalnızca veri sunumu ile ilgilenildiği açıklanmaktadır. Ne zaman kullanılması uygun olmadığını bilmek için <xref:System.Windows.DataTemplate> , tarafından sunulan farklı stil ve şablon özelliklerini anlamak önemlidir <xref:System.Windows.Controls.ItemsControl> . Aşağıdaki örnek, bu özelliklerin her birinin işlevini göstermek için tasarlanmıştır. <xref:System.Windows.Controls.ItemsControl>Bu örnekte, `Tasks` önceki örnekteki ile aynı koleksiyona bağlanır. Tanıtım amacıyla, bu örnekteki stillerin ve şablonların hepsi satır içi olarak bildirilmiştir.

 [!code-xaml[DataTemplatingIntro_snip#ItemsControlProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#itemscontrolproperties)]

 Aşağıda, örneği işlendiğinde örnek bir ekran görüntüsü verilmiştir:

 ![Itemkıcontrol örnek ekran görüntüsü](./media/databinding-itemscontrolproperties.png "DataBinding_ItemsControlProperties")

 Kullanmak yerine, <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> kullanabilirsiniz <xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A> . Bir örnek için önceki bölüme bakın. Benzer şekilde, öğesini kullanmak yerine, <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> kullanma seçeneğiniz vardır <xref:System.Windows.Controls.ItemsControl.ItemContainerStyleSelector%2A> .

 Burada gösterilmemiş olan diğer iki stille ilgili Özellikler <xref:System.Windows.Controls.ItemsControl> <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> ve ' dir <xref:System.Windows.Controls.ItemsControl.GroupStyleSelector%2A> .

<a name="DataTemplating_HeirarchicalDataTemplate"></a>
## <a name="support-for-hierarchical-data"></a>Hiyerarşik veri desteği
 Şimdiye kadar, yalnızca tek bir koleksiyon için bağlama ve görüntüleme hakkında baktık. Bazen diğer koleksiyonları içeren bir koleksiyonunuz vardır. <xref:System.Windows.HierarchicalDataTemplate>Sınıfı, <xref:System.Windows.Controls.HeaderedItemsControl> Bu tür verileri göstermek için türlerle birlikte kullanılmak üzere tasarlanmıştır. Aşağıdaki örnekte, `ListLeagueList` nesnelerinin bir listesidir `League` . Her `League` nesne bir `Name` ve bir nesne koleksiyonuna sahiptir `Division` . Her birinin `Division` bir `Name` ve bir nesne koleksiyonu vardır `Team` ve her `Team` nesne bir içerir `Name` .

 [!code-xaml[HierarchicalDataTemplateSnippet#HDT](~/samples/snippets/csharp/VS_Snippets_Wpf/HierarchicalDataTemplateSnippet/CS/window1.xaml#hdt)]

 Örnek, öğesinin kullanımını gösterir <xref:System.Windows.HierarchicalDataTemplate> , diğer listeleri içeren liste verilerini kolayca görüntüleyebilirsiniz. Aşağıda, örneğin bir ekran görüntüsü verilmiştir.

 ![HierarchicalDataTemplate örnek ekran görüntüsü](./media/databinding-hierarchicaldatatemplate.png "DataBinding_HierarchicalDataTemplate")

## <a name="see-also"></a>Ayrıca bkz.

- [Veri Bağlama](../advanced/optimizing-performance-data-binding.md)
- [DataTemplate tarafından oluşturulan öğeleri bulma](how-to-find-datatemplate-generated-elements.md)
- [Stil ve Şablon Oluşturma](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Veri Bağlamaya Genel Bakış](../../../desktop-wpf/data/data-binding-overview.md)
- [GridView Sütun Üstbilgi Stil ve Şablonlarına Genel Bakış](../controls/gridview-column-header-styles-and-templates-overview.md)
