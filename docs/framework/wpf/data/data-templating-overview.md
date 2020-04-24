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
ms.openlocfilehash: b9e55eac1c72cd3deec21754373da4364a7cfed2
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646456"
---
# <a name="data-templating-overview"></a>Veri Şablonu Oluşturmaya Genel Bakış
WPF veri baştan çıkarıcı modeli, verilerinizin sunumunu tanımlamak için size büyük esneklik sağlar. WPF denetimleri, veri sunusunun özelleştirilmesini desteklemek için yerleşik işlevsellik sağlar. Bu konu önce a'nın <xref:System.Windows.DataTemplate> nasıl tanımlandığını gösterir ve daha sonra özel mantığa dayalı şablon seçimi ve hiyerarşik verilerin görüntülenmesi için destek gibi diğer verileri baştan çıkarıcı özellikleri sunar.

<a name="Prerequisites"></a>
## <a name="prerequisites"></a>Ön koşullar
 Bu konu veri cazip özelliklere odaklanır ve veri bağlama kavramlarının bir giriş değildir. Temel veri bağlama kavramları hakkında bilgi için [Veri Bağlama Genel Bakış'a](../../../desktop-wpf/data/data-binding-overview.md)bakın.

 <xref:System.Windows.DataTemplate>verilerin sunumu hakkında dır ve WPF stil ve templating modeli tarafından sağlanan birçok özellikten biridir. WPF stilinin ve cazip modelinin tanıtımı için, örneğin <xref:System.Windows.Style> denetimlerde özellikleri ayarlamak için nasıl kullanılacağı gibi, [Stil ve Templating](../../../desktop-wpf/fundamentals/styles-templates-overview.md) konusuna bakın.

 Buna ek olarak, temelde `Resources`ne gibi <xref:System.Windows.Style> nesneleri etkinleştirmek ve <xref:System.Windows.DataTemplate> yeniden kullanılabilir olmak olduğunu anlamak önemlidir. Kaynaklar hakkında daha fazla bilgi için [Bkz. XAML Kaynakları.](../../../desktop-wpf/fundamentals/xaml-resources-define.md)

<a name="DataTemplating_Basic"></a>
## <a name="data-templating-basics"></a>Veri Templating Temelleri

 Neden <xref:System.Windows.DataTemplate> önemli olduğunu göstermek için, veri bağlama örneğini gözden geçirelim. Bu örnekte, <xref:System.Windows.Controls.ListBox> `Task` nesnelerin listesine bağlı bir var. Her `Task` nesnenin `TaskName` bir `Description` (dize), `Priority` a (dize), a `TaskType`(int) `Enum` ve `Home` `Work`bir tür özelliği vardır, hangi değerleri ile ve .

 [!code-xaml[DataTemplatingIntro_snip#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#resources)]
[!code-xaml[DataTemplatingIntro_snip#UI1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#ui1)]
[!code-xaml[DataTemplatingIntro_snip#UI2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#ui2)]

<a name="without_a_datatemplate"></a>
### <a name="without-a-datatemplate"></a>Veri Şablonu olmadan
 Olmadan <xref:System.Windows.DataTemplate>, <xref:System.Windows.Controls.ListBox> bizim şu anda bu gibi görünüyor:

 ![Veri cazip örnek ekran görüntüsü](./media/datatemplatingintro-fig1.png "DataTemplatingIntro_fig1")

 Olan şey, belirli bir yönerge <xref:System.Windows.Controls.ListBox> olmadan, `ToString` koleksiyondaki nesneleri görüntülemeye çalışırken varsayılan olarak çağrıların. Bu nedenle, `Task` nesne `ToString` yöntemi geçersiz kılarsa, alttaki koleksiyondaki her kaynak nesnenin dize gösterimini <xref:System.Windows.Controls.ListBox> görüntüler.

 Örneğin, `Task` sınıf `ToString` yöntemi bu şekilde geçersiz kılarsa, özelliğin `name` `TaskName` alanı nerededir:

 [!code-csharp[DataTemplatingIntro_snip#ToString](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Data.cs#tostring)]
 [!code-vb[DataTemplatingIntro_snip#ToString](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataTemplatingIntro_snip/visualbasic/data.vb#tostring)]

 Sonra <xref:System.Windows.Controls.ListBox> aşağıdaki gibi görünüyor:

 ![Veri cazip örnek ekran görüntüsü](./media/datatemplatingintro-fig2.png "DataTemplatingIntro_fig2")

 Ancak, bu sınırlayıcı ve esnek değildir. Ayrıca, XML verilerine bağlıysanız, geçersiz kılınamaz. `ToString`

<a name="defining_simple_datatemplate"></a>
### <a name="defining-a-simple-datatemplate"></a>Basit Bir Veri Şablonu Tanımlama
 Çözüm bir <xref:System.Windows.DataTemplate>. Bunu yapmanın bir yolu bir <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> <xref:System.Windows.Controls.ListBox> <xref:System.Windows.DataTemplate>. Sizin için belirttiğiniz <xref:System.Windows.DataTemplate> şey, veri nesnenizin görsel yapısı olur. Aşağıdaki <xref:System.Windows.DataTemplate> oldukça basittir. Her öğenin <xref:System.Windows.Controls.TextBlock> bir <xref:System.Windows.Controls.StackPanel>. Her <xref:System.Windows.Controls.TextBlock> öğe `Task` sınıfın bir özelliğine bağlıdır.

 [!code-xaml[DataTemplatingIntro_snip#Inline](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#inline)]

 Bu konudaki örneklerin altında yatan veriler CLR nesnelerinin bir koleksiyonudur. XML verilerine bağlıysanız, temel kavramlar aynıdır, ancak hafif bir sözdizimsiz fark vardır. Örneğin, sahip `Path=TaskName`olmak yerine, <xref:System.Windows.Data.Binding.XPath%2A> `@TaskName` (XML `TaskName` düğümünüzün bir özniteliği ise) ayarlayabilirsiniz.

 Şimdi <xref:System.Windows.Controls.ListBox> bizim aşağıdaki gibi görünüyor:

 ![Veri cazip örnek ekran görüntüsü](./media/datatemplatingintro-fig3.png "DataTemplatingIntro_fig3")

<a name="defining_datatemplate_as_a_resource"></a>
### <a name="creating-the-datatemplate-as-a-resource"></a>Kaynak Olarak Veri Şablonu Oluşturma
 Yukarıdaki örnekte, <xref:System.Windows.DataTemplate> satır satırını tanımladık. Aşağıdaki örnekte olduğu gibi yeniden kullanılabilir bir nesne olabilmesi için kaynaklar bölümünde tanımlamak daha yaygındır:

 [!code-xaml[DataTemplatingIntro_snip#R1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r1)]
[!code-xaml[DataTemplatingIntro_snip#AsResource](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#asresource)]
[!code-xaml[DataTemplatingIntro_snip#R2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r2)]

 Şimdi aşağıdaki `myTaskTemplate` örnekte olduğu gibi kaynak olarak kullanabilirsiniz:

 [!code-xaml[DataTemplatingIntro_snip#MyTaskTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#mytasktemplate)]

 Bir `myTaskTemplate` kaynak olduğundan, artık bir <xref:System.Windows.DataTemplate> tür alan bir özelliği olan diğer denetimlerde kullanabilirsiniz. Yukarıda gösterildiği gibi, nesneler <xref:System.Windows.Controls.ItemsControl> için, <xref:System.Windows.Controls.ListBox>gibi , <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> bu özelliktir. Nesneler <xref:System.Windows.Controls.ContentControl> için, bu <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> özelliktir.

<a name="Styling_DataType"></a>
### <a name="the-datatype-property"></a>DataType Özelliği
 Sınıfın <xref:System.Windows.DataTemplate> <xref:System.Windows.DataTemplate.DataType%2A> <xref:System.Windows.Style.TargetType%2A> özelliğine <xref:System.Windows.Style> çok benzeyen bir özelliği vardır. Bu nedenle, yukarıdaki `x:Key` <xref:System.Windows.DataTemplate> örnekte bir için bir belirtme yerine, aşağıdakileri yapabilirsiniz:

 [!code-xaml[DataTemplatingIntro_snip#DataType](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#datatype)]

 Bu, <xref:System.Windows.DataTemplate> tüm `Task` nesnelere otomatik olarak uygulanır. Bu durumda örtülü `x:Key` olarak ayarlanır unutmayın. <xref:System.Windows.DataTemplate> Bu nedenle, bu bir `x:Key` değer atarsanız, örtülü `x:Key` geçersiz <xref:System.Windows.DataTemplate> kılma ve otomatik olarak uygulanmaz.

 A'yı <xref:System.Windows.Controls.ContentControl> `Task` nesneler koleksiyonuna bağlıyorsanız, <xref:System.Windows.Controls.ContentControl> yukarıdakileri <xref:System.Windows.DataTemplate> otomatik olarak kullanmaz. Bunun nedeni, bir <xref:System.Windows.Controls.ContentControl> koleksiyonun tamamına mı yoksa tek tek nesnelere mi bağlanmak istediğinizi ayırt etmek için daha fazla bilgiye ihtiyaç dalmasıdır. Bir <xref:System.Windows.Controls.ContentControl> <xref:System.Windows.Controls.ItemsControl> türün seçimini takip ediyorsanız, geçerli <xref:System.Windows.Data.Binding.Path%2A> öğeyle <xref:System.Windows.Controls.ContentControl> ilgilendiğinizi belirtmek için bağlama özelliğini " "`/`olarak ayarlayabilirsiniz. Örneğin, [Seçime Dayalı Toplama ve Görüntü Bilgilerine Bağlama'ya bakın.](how-to-bind-to-a-collection-and-display-information-based-on-selection.md) Aksi takdirde, <xref:System.Windows.DataTemplate> <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> özelliği ayarlayarak açıkça belirtmeniz gerekir.

 Özellik, <xref:System.Windows.DataTemplate.DataType%2A> farklı türde veri <xref:System.Windows.Data.CompositeCollection> nesnelerine sahipseniz özellikle kullanışlıdır. Örneğin, [bkz.](how-to-implement-a-compositecollection.md)

<a name="adding_more_to_datatemplate"></a>
## <a name="adding-more-to-the-datatemplate"></a>Veri Şablonuna Daha Fazla Ekleme
 Şu anda veriler gerekli bilgilerle birlikte görünür, ancak kesinlikle iyileştirme için yer vardır. Görüntülenen verileri açıklayan bir <xref:System.Windows.Controls.Border>, a <xref:System.Windows.Controls.Grid>ve bazı <xref:System.Windows.Controls.TextBlock> öğeler ekleyerek sunuyu geliştirelim.

 [!code-xaml[DataTemplatingIntro#AddingMore](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore)]
[!code-xaml[DataTemplatingIntro#AddingMore2](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore2)]

 Aşağıdaki ekran görüntüsü <xref:System.Windows.Controls.ListBox> bu <xref:System.Windows.DataTemplate>değiştirilmiş ile gösterir:

 ![Veri cazip örnek ekran görüntüsü](./media/datatemplatingintro-fig4.png "DataTemplatingIntro_fig4")

 Öğelerin <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> genişliğinin <xref:System.Windows.Controls.ListBox> tüm alanı kapladığından emin olmak için aşağıdakileri ayarlayabiliriz: <xref:System.Windows.HorizontalAlignment.Stretch>

 [!code-xaml[DataTemplatingIntro_snip#Stretch](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#stretch)]

 <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> Özellik ayarlanmış ile <xref:System.Windows.HorizontalAlignment.Stretch>, <xref:System.Windows.Controls.ListBox> şimdi bu gibi görünüyor:

 ![Veri cazip örnek ekran görüntüsü](./media/datatemplatingintro-fig5.png "DataTemplatingIntro_fig5")

<a name="DataTrigger_to_Apply_Property_Values"></a>
### <a name="use-datatriggers-to-apply-property-values"></a>Özellik Değerlerini Uygulamak için DataTriggers'ı kullanma
 Geçerli sunu bize bir `Task` ev görevi mi yoksa ofis görevi mi olduğunu söylemez. Nesnenin `Task` `TaskType` `TaskType`değerlerle `Home` numaralandırma türü ne özelliği olduğunu unutmayın ve `Work`.

 Aşağıdaki <xref:System.Windows.DataTrigger> örnekte, <xref:System.Windows.Controls.Border.BorderBrush%2A> `border` `Yellow` `TaskType` özellik. `TaskType.Home`

 [!code-xaml[DataTemplatingIntro#DT](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#dt)]
[!code-xaml[DataTemplatingIntro#DataTrigger](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#datatrigger)]
[!code-xaml[DataTemplatingIntro#AddingMore2](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore2)]

 Uygulamamız şimdi aşağıdaki gibi görünüyor. Ev görevleri sarı kenarlıkla görünür ve ofis görevleri su sınırıyla görünür:

 ![Veri cazip örnek ekran görüntüsü](./media/datatemplatingintro-fig6.png "DataTemplatingIntro_fig6")

 Bu örnekte <xref:System.Windows.DataTrigger> bir <xref:System.Windows.Setter> özellik değeri ayarlamak için a kullanır. Tetikleyici sınıfları, <xref:System.Windows.TriggerBase.EnterActions%2A> animasyonlar gibi bir dizi eylem başlatmanızı sağlayan ve <xref:System.Windows.TriggerBase.ExitActions%2A> özelliklere de sahiptir. Buna ek olarak, <xref:System.Windows.MultiDataTrigger> birden çok veriye bağlı özellik değerlerini temel alan değişiklikleri uygulamanızı sağlayan bir sınıf da vardır.

 Aynı etkiyi elde etmek için alternatif <xref:System.Windows.Controls.Border.BorderBrush%2A> bir yol `TaskType` özelliği özelliği bağlamak ve `TaskType` değeri temel alan renk dönmek için bir değer dönüştürücü kullanmaktır. Bir dönüştürücü kullanarak yukarıdaki efekti oluşturmak performans açısından biraz daha etkilidir. Ayrıca, kendi konvertörünüzü oluşturmak size daha fazla esneklik sağlar, çünkü kendi mantığınızı sağlarsınız. Sonuç olarak, hangi tekniği seçeceğiniz senaryonuza ve tercihinize bağlıdır. Dönüştürücü nasıl yazılır hakkında bilgi <xref:System.Windows.Data.IValueConverter>için bkz.

<a name="what_belongs_in_datatemplate"></a>
### <a name="what-belongs-in-a-datatemplate"></a>Veri Şablonuna Ne Ait?

Önceki örnekte, tetikleyiciyi kullanma <xref:System.Windows.DataTemplate> <xref:System.Windows.DataTemplate.Triggers%2A?displayProperty=nameWithType> özelliğinin içine yerleştirdik. <xref:System.Windows.Setter> Tetikleyici, <xref:System.Windows.DataTemplate>bir öğenin <xref:System.Windows.Controls.Border> (öğe) içindeki değerini ayarlar. Ancak, ilgili olduğunuz `Setters` özellikler geçerli <xref:System.Windows.DataTemplate>öğelerin özellikleri değilse, <xref:System.Windows.Style> <xref:System.Windows.Controls.ListBoxItem> sınıf için olan özellikleri ayarlamak daha uygun olabilir (bağlandığınız denetim bir <xref:System.Windows.Controls.ListBox>denetim). Örneğin, fare bir <xref:System.Windows.Trigger> öğeyi işaret <xref:System.Windows.UIElement.Opacity%2A> ettiğinde öğenin değerini canlandırmanızı istiyorsanız, bir <xref:System.Windows.Controls.ListBoxItem> stil içinde tetikleyiciler tanımlarsınız. Örneğin, [Stil ve Templating Örnek Giriş](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)bakın.

 Genel olarak, oluşturulan <xref:System.Windows.DataTemplate> <xref:System.Windows.Controls.ListBoxItem> her birine uygulandığını unutmayın (gerçekte nasıl ve nerede uygulandığı hakkında daha <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> fazla bilgi için sayfaya bakın.) Sizin <xref:System.Windows.DataTemplate> veri nesnelerinin yalnızca sunumu ve görünümü ile ilgilidir. Çoğu durumda, bir öğeseçildiğinde nasıl göründüğü veya öğelerin nasıl <xref:System.Windows.Controls.ListBox> ortaya çıktığı gibi sununun diğer tüm yönleri bir <xref:System.Windows.DataTemplate>. Örneğin, [Bir Öğe Denetimi'ni Stillendirme ve Baştan Çıkarmak](#DataTemplating_ItemsControl) bölümüne bakın.

<a name="Styling_StyleSelection"></a>
## <a name="choosing-a-datatemplate-based-on-properties-of-the-data-object"></a>Veri Nesnesinin Özelliklerine Göre Veri Şablonu Seçme
 [DataType Özelliği](#Styling_DataType) bölümünde, farklı veri nesneleri için farklı veri şablonları tanımlayabileceğinizi tartıştık. Bu, özellikle farklı <xref:System.Windows.Data.CompositeCollection> türde öğeleriçeren farklı türde veya koleksiyonlara sahip olduğunuzda kullanışlıdır. Özellik [Değerlerini Uygulamak için DataTriggers'ı kullan](#DataTrigger_to_Apply_Property_Values) bölümünde, aynı tür veri nesnelerinden oluşan bir koleksiyonunuz varsa, her veri nesnesinin özellik değerlerini temel alan değişiklikleri uygulamak için bir oluşturup <xref:System.Windows.DataTemplate> ardından tetikleyiciler kullanabileceğinizi gösterdik. Ancak, tetikleyiciler özellik değerlerini uygulamanıza veya animasyonları başlatmanıza olanak sağlar, ancak size veri nesnelerinizin yapısını yeniden oluşturma esnekliği vermez. Bazı senaryolar, aynı türde <xref:System.Windows.DataTemplate> olan ancak farklı özelliklere sahip veri nesneleri için farklı bir tane oluşturmanızı gerektirebilir.

 Örneğin, bir `Task` nesnenin `Priority` `1`bir değeri varsa, kendiniz için bir uyarı olarak hizmet vermek için tamamen farklı bir görünüm vermek isteyebilirsiniz. Bu durumda, yüksek <xref:System.Windows.DataTemplate> öncelikli `Task` nesnelerin görüntülenmesi için bir oluşturursunuz. Kaynaklar bölümüne aşağıdakileri <xref:System.Windows.DataTemplate> ekleyelim:

 [!code-xaml[DataTemplatingIntro_snip#ImportantTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#importanttemplate)]

Bu örnekte [DataTemplate.Resources](xref:System.Windows.FrameworkTemplate.Resources%2A) özelliği kullanılır. Bu bölümde tanımlanan <xref:System.Windows.DataTemplate>kaynaklar, 'deki öğeler tarafından paylaşılır.

 Veri <xref:System.Windows.DataTemplate> nesnesinin `Priority` değerine göre hangisini kullanacağınızı seçmek için mantık <xref:System.Windows.Controls.DataTemplateSelector> sağlamak için, <xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A> yöntemin bir alt sınıfı oluşturun ve metodun geçersiz kılınmasını sağlar. Aşağıdaki örnekte, <xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A> yöntem `Priority` özelliğin değerini temel alan uygun şablonu döndürmek için mantık sağlar. Döndürülecek şablon, saran <xref:System.Windows.Window> öğenin kaynaklarında bulunur.

 [!code-csharp[DataTemplatingIntro_snip#DTSClass](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/TaskListDataTemplateSelector.cs#dtsclass)]
 [!code-vb[DataTemplatingIntro_snip#DTSClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataTemplatingIntro_snip/visualbasic/tasklistdatatemplateselector.vb#dtsclass)]

 Daha sonra kaynak `TaskListDataTemplateSelector` olarak bildirebiliriz:

 [!code-xaml[DataTemplatingIntro_snip#R1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r1)]
[!code-xaml[DataTemplatingIntro_snip#DTS](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#dts)]
[!code-xaml[DataTemplatingIntro_snip#R2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r2)]

 Şablon seçici kaynağını kullanmak için, <xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A> <xref:System.Windows.Controls.ListBox>'nin özelliğine atayın. Temel <xref:System.Windows.Controls.ListBox> koleksiyondaki öğelerin her biri <xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A> `TaskListDataTemplateSelector` için yöntem çağırır. Çağrı, öğe parametresi olarak veri nesnesini geçirir. <xref:System.Windows.DataTemplate> Yöntem tarafından döndürülen daha sonra bu veri nesnesine uygulanır.

 [!code-xaml[DataTemplatingIntro_snip#ItemTemplateSelector](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#itemtemplateselector)]

 Şablon seçici yerinde olduğu için, <xref:System.Windows.Controls.ListBox> şimdi aşağıdaki gibi görünür:

 ![Veri cazip örnek ekran görüntüsü](./media/datatemplatingintro-fig7.png "DataTemplatingIntro_fig7")

Bu, bu örnekle ilgili tartışmamızı sona erdiriyor. Tam örnek için [bkz.](https://github.com/Microsoft/WPF-Samples/tree/master/Data%20Binding/DataTemplatingIntro)

<a name="DataTemplating_ItemsControl"></a>
## <a name="styling-and-templating-an-itemscontrol"></a>Bir Öğeyi Şekillendirme ve TemplatingKontrolü
 Bir <xref:System.Windows.Controls.ItemsControl> <xref:System.Windows.DataTemplate> ile kullanabileceğiniz tek denetim türü olmasa da, bir <xref:System.Windows.Controls.ItemsControl> koleksiyona bağlamak için çok yaygın bir senaryodur. DataTemplate bölümünde [ki ait](#what_belongs_in_datatemplate) olan şey bölümünde, sizin <xref:System.Windows.DataTemplate> tanımınızın yalnızca verilerin sunumuyla ilgilenmesi gerektiğini tartıştık. Ne zaman kullanılmanın <xref:System.Windows.DataTemplate> uygun olmadığını bilmek için farklı stil ve şablon özelliklerini anlamak <xref:System.Windows.Controls.ItemsControl>önemlidir. Aşağıdaki örnek, bu özelliklerin her birinin işlevini göstermek için tasarlanmıştır. Bu <xref:System.Windows.Controls.ItemsControl> örnekte önceki örnekte `Tasks` olduğu gibi aynı koleksiyona bağlıdır. Gösterim amacıyla, bu örnekteki stillerin ve şablonların tümü satır içinde olarak bildirilir.

 [!code-xaml[DataTemplatingIntro_snip#ItemsControlProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#itemscontrolproperties)]

 Aşağıdaki, görüntülendiğinde örneğin bir ekran görüntüsüdür:

 ![ÖğelerKontrol örnek ekran görüntüsü](./media/databinding-itemscontrolproperties.png "DataBinding_ItemsControlProperties")

 Bunun yerine , <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>'yi <xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A>kullanabilirsiniz unutmayın. Bir örnek için önceki bölüme bakın. Benzer şekilde, kullanmak <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>yerine , <xref:System.Windows.Controls.ItemsControl.ItemContainerStyleSelector%2A>'yi kullanma seçeneğiniz var.

 Burada gösterilmeyen diğer iki <xref:System.Windows.Controls.ItemsControl> stil ile ilgili <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> <xref:System.Windows.Controls.ItemsControl.GroupStyleSelector%2A>özellikleri ve .

<a name="DataTemplating_HeirarchicalDataTemplate"></a>
## <a name="support-for-hierarchical-data"></a>Hiyerarşik Veriler için Destek
 Şimdiye kadar sadece bağlamak ve tek bir koleksiyon görüntülemek için nasıl baktım. Bazen diğer koleksiyonları içeren bir koleksiyon var. Sınıf, <xref:System.Windows.HierarchicalDataTemplate> bu tür verileri <xref:System.Windows.Controls.HeaderedItemsControl> görüntülemek için türleri ile kullanılmak üzere tasarlanmıştır. Aşağıdaki örnekte, `ListLeagueList` `League` nesnelerin bir listesidir. Her `League` nesnenin `Name` bir ve `Division` bir nesne koleksiyonu vardır. Her `Division` bir `Name` `Team` nesne koleksiyonu vardır ve `Team` her nesnenin bir `Name`.

 [!code-xaml[HierarchicalDataTemplateSnippet#HDT](~/samples/snippets/csharp/VS_Snippets_Wpf/HierarchicalDataTemplateSnippet/CS/window1.xaml#hdt)]

 Örnek, <xref:System.Windows.HierarchicalDataTemplate>kullanımıyla, diğer listeleri içeren liste verilerini kolayca görüntüleyebileceğinizi gösterir. Aşağıda, örneğin ekran görüntüsü verilmiştir.

 ![HiyerarşikDataTemplate örnek ekran görüntüsü](./media/databinding-hierarchicaldatatemplate.png "DataBinding_HierarchicalDataTemplate")

## <a name="see-also"></a>Ayrıca bkz.

- [Veri Bağlama](../advanced/optimizing-performance-data-binding.md)
- [DataTemplate tarafından oluşturulan öğeleri bulma](how-to-find-datatemplate-generated-elements.md)
- [Stil ve Şablon Oluşturma](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Veri Bağlama Genel Bakış](../../../desktop-wpf/data/data-binding-overview.md)
- [GridView Sütun Üst Bilgi Stil ve Şablonlarına Genel Bakış](../controls/gridview-column-header-styles-and-templates-overview.md)
