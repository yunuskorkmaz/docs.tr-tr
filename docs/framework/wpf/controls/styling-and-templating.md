---
title: Stil ve Şablon Oluşturma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- triggers [WPF]
- styles [WPF], referencing
- event triggers [WPF]
- styles [WPF], prerequisites
- styles [WPF], declaring
- styles [WPF], overview
- styles [WPF], extending
- styles [WPF], triggers
- styles [WPF], event triggers
ms.assetid: 481765e5-5467-4a75-9f7b-e10e2ac410d9
ms.openlocfilehash: 3fae4993a13b02ad998668f644a80ba7c07196fa
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59132307"
---
# <a name="styling-and-templating"></a>Stil ve Şablon Oluşturma
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Stil ve şablon oluşturma özellikleri içeren bir paketi, geliştiricilerin ve tasarımcıların görsel açıdan ilgi çekici efektleri oluşturun ve kendi ürün için tutarlı bir görünüm oluşturmak için izin ver (stiller, şablonlar, tetikleyiciler ve görsel Taslaklar) bakın. Tasarımcılar ve geliştiriciler bir uygulama tarafından uygulama temelinde Java'da görünümünü özelleştirebilirsiniz olsa da, güçlü bir stil ve şablon oluşturma modeli Bakım ve görünümü içinde ve uygulamalar arasında paylaşılmasına izin vermek gereklidir. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Bu modeli sağlar.  
  
 Başka bir özelliği [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stil modelidir, sunu ve mantığının ayrımı. Yani yalnızca kullanarak tasarımcılar uygulama görünümünü üzerinde çalışabilir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] geliştiriciler programlama mantığını kullanarak çalışma aynı anda C# veya Visual Basic.  
  
 Bu genel bakışta, stil ve şablon oluşturma görünüşlerine uygulamanın odaklanır ve tüm veri bağlama kavramlarını ele almaz. Veri bağlama hakkında daha fazla bilgi için bkz: [Data Binding Overview](../data/data-binding-overview.md).  
  
 Ayrıca, hangi stilleri ve şablonları, yeniden kullanılabilmeleri için etkinleştirme olan kaynakları anlamak önemlidir. Kaynaklar hakkında daha fazla bilgi için bkz. [XAML kaynakları](../advanced/xaml-resources.md).

<a name="styling_and_templating_sample"></a>   
## <a name="styling-and-templating-sample"></a>Stil ve şablon oluşturma örneği  
 Bu genel bakışta kullanılan kod örnekleri aşağıdaki çizimde gösterilen bir basit fotoğraf örneğini temel alır:  
  
 ![ListView biçimlendirilmiş](./media/stylingintro-triggers.png "StylingIntro_triggers")  
  
 Bu basit fotoğraf örnek, görsel açıdan ilgi çekici bir kullanıcı deneyimi oluşturmak üzere stil ve şablon oluşturma kullanır. İki örnek içeren <xref:System.Windows.Controls.TextBlock> öğeleri ve <xref:System.Windows.Controls.ListBox> görüntülerin bir listeye bağlı denetim. Tam bir örnek için bkz. [stil ve şablon oluşturma örnek giriş](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).  
  
<a name="styling_basics"></a>   
## <a name="style-basics"></a>Stil temelleri  
 Kadar aklınıza gelebilecek bir <xref:System.Windows.Style> özellik değerlerini bir dizi birden fazla öğeye uygulamak için kullanışlı bir yol olarak. Örneğin, aşağıdakileri dikkate alın <xref:System.Windows.Controls.TextBlock> öğelerini ve varsayılan görünümleri:  
  
 [!code-xaml[StylingIntroSample_snippet#TextBlocks](~/samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSample_snippet/CSharp/Window1.xaml#textblocks)]  
  
 ![Stil örnek ekran](./media/stylingintro-textblocksbefore.PNG "StylingIntro_TextBlocksBefore")  
  
 Özelliklerini ayarlayarak varsayılan görünümünü değiştirebilirsiniz <xref:System.Windows.Controls.Control.FontSize%2A> ve <xref:System.Windows.Controls.Control.FontFamily%2A>, her <xref:System.Windows.Controls.TextBlock> doğrudan öğesi. Ancak isterseniz, <xref:System.Windows.Controls.TextBlock> bazı özellikler paylaşmak için öğeleri oluşturabileceğiniz bir <xref:System.Windows.Style> içinde `Resources` bölümünü, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] burada gösterildiği gibi dosya:  
  
 [!code-xaml[StylingIntroSnippet#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources)]  
[!code-xaml[StylingIntroSnippet#tb1](~/samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#tb1)]  
[!code-xaml[StylingIntroSnippet#Resources2](~/samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources2)]  
  
 Ayarladığınızda <xref:System.Windows.Style.TargetType%2A> stilinize, <xref:System.Windows.Controls.TextBlock> türü, stilini tümüne uygulanır <xref:System.Windows.Controls.TextBlock> pencere öğeleri.  
  
 Artık <xref:System.Windows.Controls.TextBlock> öğeleri şu şekilde görünür:  
  
 ![Stil örnek ekran](./media/stylingintro-textblocksbasestyle.PNG "StylingIntro_TextBlocksBaseStyle")  
  
### <a name="extending-styles"></a>Stilleri genişletme  
 Belki de iki istediğiniz <xref:System.Windows.Controls.TextBlock> bazı özellik değerleri gibi paylaşmak için öğeleri <xref:System.Windows.Controls.Control.FontFamily%2A> ve ortalanmış <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, ancak ayrıca bazı ek özellikler sağlamak için "My resimleri" metin istediğiniz. Burada gösterildiği gibi ilk stiline göre yeni bir stil oluşturarak bunu yapabilirsiniz:  
  
 [!code-xaml[StylingIntroSnippet#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources)]  
[!code-xaml[StylingIntroSnippet#tb2](~/samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#tb2)]  
[!code-xaml[StylingIntroSnippet#Resources2](~/samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources2)]  
  
 Önceki stil verilen bildirimi bir `x:Key`. Stil uygulamak için ayarladığınız <xref:System.Windows.FrameworkElement.Style%2A> özelliği, <xref:System.Windows.Controls.TextBlock> için `x:Key` burada gösterildiği gibi değer:  
  
 [!code-xaml[StylingIntroSnippet#UIText](~/samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#uitext)]  
  
 Bu <xref:System.Windows.Controls.TextBlock> artık stilde bir <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> değerini <xref:System.Windows.HorizontalAlignment.Center>, <xref:System.Windows.Controls.TextBlock.FontFamily%2A> değerini `Comic Sans MS`, <xref:System.Windows.Controls.TextBlock.FontSize%2A> 26, değeri ve <xref:System.Windows.Controls.TextBlock.Foreground%2A> değerine <xref:System.Windows.Media.LinearGradientBrush> örnekte gösterilen. Onu geçersiz kılar bildirimi <xref:System.Windows.Controls.Control.FontSize%2A> temel stil değeri. Varsa birden fazla <xref:System.Windows.Setter> aynı özellik ayarı bir <xref:System.Windows.Style>, <xref:System.Windows.Setter> diğer bir deyişle bildirilen son önceliğe.  
  
 Aşağıdaki ne gösterir <xref:System.Windows.Controls.TextBlock> öğeleri artık aramak gibi:  
  
 ![TextBlock'lar biçimlendirilmiş](./media/stylingintro-textblocks.png "StylingIntro_TextBlocks")  
  
 Bu `TitleText` stili için oluşturulan stili genişletir <xref:System.Windows.Controls.TextBlock> türü. Ayrıca sahip stil genişletebilirsiniz bir `x:Key` kullanarak `x:Key` değeri. Örneğin, için sağlanan örneği görmek <xref:System.Windows.Style.BasedOn%2A> özelliği.  
  
### <a name="relationship-of-the-targettype-property-and-the-xkey-attribute"></a>İlişki TargetType özellik ve x: Key özniteliği  
 İlk örnekte gösterildiği gibi ayarı <xref:System.Windows.Style.TargetType%2A> özelliğini `TextBlock` stili atama olmadan bir `x:Key` tümüne uygulanacak stili neden <xref:System.Windows.Controls.TextBlock> öğeleri. Bu durumda, `x:Key` örtük olarak ayarlandığında `{x:Type TextBlock}`. Bunun anlamı açıkça `x:Key` dışında hiçbir şeye değer `{x:Type TextBlock}`, <xref:System.Windows.Style> tümüne uygulanmaz <xref:System.Windows.Controls.TextBlock> öğeleri otomatik olarak. Bunun yerine, Stili Uygula (kullanarak `x:Key` değeri) için <xref:System.Windows.Controls.TextBlock> öğeleri açıkça. Stiliniz kaynakları bölümdür ve ayarlamayın <xref:System.Windows.Style.TargetType%2A> stiliniz olduktan sonra özelliği sağlamalıdır bir `x:Key`.  
  
 İçin varsayılan bir değer sağlamaya ek olarak `x:Key`, <xref:System.Windows.Style.TargetType%2A> özellik ayarlayıcı özelliklerinin uygulandığı türünü belirtir. Belirtmezseniz, bir <xref:System.Windows.Style.TargetType%2A>, özelliklerinde nitelemelidir, <xref:System.Windows.Setter> sözdizimini kullanarak bir sınıf adı nesneleriyle `Property="ClassName.Property"`. Örneğin, ayar yerine `Property="FontSize"`, ayarlamalısınız <xref:System.Windows.Setter.Property%2A> için `"TextBlock.FontSize"` veya `"Control.FontSize"`.  
  
 Ayrıca unutmayın, birçok [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimleri, diğer bileşiminden oluşur [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimleri. Bir türdeki tüm denetimlere uygulanan stil oluşturma, beklenmeyen sonuçlar alabilirsiniz. Örneğin hedefleyen bir stil oluşturma, <xref:System.Windows.Controls.TextBlock> yazın bir <xref:System.Windows.Window>, tümüne uygulanan stil <xref:System.Windows.Controls.TextBlock> penceresinde denetimleri bile <xref:System.Windows.Controls.TextBlock> başka bir denetimde bir parçası olduğu gibi bir <xref:System.Windows.Controls.ListBox>.  
  
### <a name="styles-and-resources"></a>Stiller ve kaynakları  
 Öğesinden türetilen herhangi bir öğede bir stili kullanabilirsiniz <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement>. Bir kaynak olarak bir stil bildirmek için en yaygın yolu olan `Resources` konusundaki bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] önceki örneklerde gösterildiği gibi dosya. Stilleri kaynaklar olduğundan, bunlar tüm kaynaklarına uygulayan aynı kapsam kuralları uyma; Burada bir stil stili uygulanabileceği etkiler bildirin. Örneğin, kök öğe, uygulama tanımının stili bildirirseniz [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosya, uygulamanızda herhangi bir stil kullanılabilir. Gezinti uygulaması oluşturur ve uygulamanın stilinde bildirmek [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] yalnızca, Stil dosyaları kullanılabilir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosya. Kaynaklar için kuralları kapsamı hakkında daha fazla bilgi için bkz. [XAML kaynakları](../advanced/xaml-resources.md).  
  
 Ayrıca, stil ve kaynakları hakkında daha fazla bilgi bulabilirsiniz [paylaşılan kaynaklar ve Temalar](#styling_themes) daha sonra bu genel bakış.  
  
### <a name="setting-styles-programmatically"></a>Stilleri programlı olarak ayarlama  
 Adlandırılmış bir stil programlı olarak öğe atamak için stil kaynakları koleksiyondan alın ve öğenin atayın <xref:System.Windows.FrameworkElement.Style%2A> özelliği. Bir kaynak koleksiyondaki öğelerin türü olduğunu unutmayın <xref:System.Object>. Bu nedenle, alınan stiline dönüştürün bir <xref:System.Windows.Style> giderek önce <xref:System.Windows.FrameworkElement.Style%2A> özelliği. Örneğin, tanımlanan ayarlamak için `TitleText` üzerinde stili bir <xref:System.Windows.Controls.TextBlock> adlı `textblock1`, aşağıdakileri yapın:  
  
 [!code-csharp[StylingIntroSample_snippet#Code](~/samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSample_snippet/CSharp/Window1.xaml.cs#code)]
 [!code-vb[StylingIntroSample_snippet#Code](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StylingIntroSample_snippet/visualbasic/window1.xaml.vb#code)]  
  
 Bir stil uygulandıktan sonra korumalı ve değiştirilemez unutmayın. Dinamik olarak zaten uygulanmış stili değiştirmek istiyorsanız, var olan dosyayla yeni bir stil oluşturmanız gerekir. Daha fazla bilgi için <xref:System.Windows.Style.IsSealed%2A> özelliği.  
  
 Bağlı olarak özel mantığı uygulamak için bir stil seçtiği bir nesne oluşturabilirsiniz. Örneğin, için sağlanan örneği görmek <xref:System.Windows.Controls.StyleSelector> sınıfı.  
  
<a name="styling_binding_dynamicresource"></a>   
### <a name="bindings-dynamic-resources-and-event-handlers"></a>Bağlamaları, dinamik kaynakları ve olay işleyicileri  
 Kullanabileceğiniz Not `Setter.Value` özelliği belirtmek için bir [biçimlendirme uzantısı bağlama](../advanced/binding-markup-extension.md) veya [DynamicResource işaretleme uzantısı](../advanced/dynamicresource-markup-extension.md). Daha fazla bilgi için için sağlanan örneklere bakın <xref:System.Windows.Setter.Value%2A?displayProperty=nameWithType> özelliği.  
  
 Şu ana kadar bu genel bakış yalnızca özellik değerini ayarlamak için ayarlayıcılar kullanımını açıklar. Bir style'nın olay işleyicileri de belirtebilirsiniz. Daha fazla bilgi için bkz. <xref:System.Windows.EventSetter>.  
  
<a name="styling_datatemplates"></a>   
## <a name="data-templates"></a>Veri Şablonları  
 Bu örnek uygulamasında var. bir <xref:System.Windows.Controls.ListBox> fotoğraf listesine bağlı denetimi:  
  
 [!code-xaml[StylingIntroSnippet#UIListBox](~/samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#uilistbox)]  
  
 Bu <xref:System.Windows.Controls.ListBox> şu anda aşağıdaki gibi görünür:  
  
 ![Şablon uygulanmadan önce ListBox](./media/stylingintro-listboxbefore.png "StylingIntro_ListBoxBefore")  
  
 Çoğu denetim herhangi bir türde içeriğe sahip ve içeriği genellikle bağlama, verilerden gelir. Bu örnekte, veri fotoğraf listesidir. İçinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], kullandığınız bir <xref:System.Windows.DataTemplate> veri görsel temsilini tanımlamak için. Temelde, eklediğiniz içine bir <xref:System.Windows.DataTemplate> veri işlenen uygulamanın nasıl göründüğünü belirler.  
  
 Bizim örnek uygulamada, her özel `Photo` nesnesinin bir `Source` görüntü dosya yolunu belirten türü dize özelliği. Şu anda, fotoğraf nesneler dosya yolları görüntülenir.  
  
 Fotoğraflar resim olarak görüntülenecek oluşturduğunuz bir <xref:System.Windows.DataTemplate> bir kaynak olarak:  
  
 [!code-xaml[StylingIntroSnippet#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources)]  
[!code-xaml[StylingIntroSnippet#DataTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#datatemplate)]  
[!code-xaml[StylingIntroSnippet#Resources2](~/samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources2)]  
  
 Dikkat <xref:System.Windows.DataTemplate.DataType%2A> özelliği çok benzer <xref:System.Windows.Style.TargetType%2A> özelliği <xref:System.Windows.Style>. Varsa, <xref:System.Windows.DataTemplate> belirttiğinizde kaynaklar bölümüne olan <xref:System.Windows.DataTemplate.DataType%2A> türü özelliğini ve atama değil bir `x:Key`, <xref:System.Windows.DataTemplate> türü görünür olduğunda uygulanır. Atama seçeneğini her zaman sahip <xref:System.Windows.DataTemplate> ile bir `x:Key` ve olarak ayarlamak bir `StaticResource` alan özellikleri için <xref:System.Windows.DataTemplate> gibi türleri <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> özelliği veya <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> özelliği.  
  
 Aslında, <xref:System.Windows.DataTemplate> olduğunda yukarıdaki örnekte tanımlayan bir `Photo` nesnesi olarak görünmelidir bir <xref:System.Windows.Controls.Image> içinde bir <xref:System.Windows.Controls.Border>. Bu <xref:System.Windows.DataTemplate>, uygulamamız artık şöyle görünür:  
  
 ![Fotoğraf resmini](./media/stylingintro-photosasimages.png "StylingIntro_PhotosAsImages")  
  
 Şablon oluşturma isteyebileceğimiz diğer özellikleri sağlar. Kullanarak diğer koleksiyonları içeren bir koleksiyon verisi görüntülüyorsunuz. Örneğin, bir <xref:System.Windows.Controls.HeaderedItemsControl> türünün bir <xref:System.Windows.Controls.Menu> veya <xref:System.Windows.Controls.TreeView>, yoktur <xref:System.Windows.HierarchicalDataTemplate>. Başka bir veri şablonu oluşturma özelliği <xref:System.Windows.Controls.DataTemplateSelector>, seçmenize olanak tanıyan bir <xref:System.Windows.DataTemplate> göre özel mantığı kullanılacak. Daha fazla bilgi için [veri şablonu oluşturmaya genel bakış](../data/data-templating-overview.md), farklı veri şablonu oluşturmaya özelliklerin daha ayrıntılı bir tartışma sağlar.  
  
<a name="styling_controltemplates"></a>   
## <a name="control-templates"></a>Denetim Şablonları  
 İçinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], <xref:System.Windows.Controls.ControlTemplate> bir denetimin denetimin görünümünü tanımlar. Yeni bir tanımlayarak yapısı ve denetiminin görünümünü değiştirebilirsiniz <xref:System.Windows.Controls.ControlTemplate> denetimi. Kendi Özek denetimlerinizi yazmanız gerekmez, çoğu durumda bu, yeterli esneklik sağlar. Daha fazla bilgi için [ControlTemplate oluşturarak varolan denetimin görünümünü özelleştirme](customizing-the-appearance-of-an-existing-control.md).  
  
<a name="styling_triggers"></a>   
## <a name="triggers"></a>Tetikleyiciler  
 Tetikleyici özelliklerini ayarlar veya özellik değeri değiştiğinde veya bir olay oluştuğunda animasyon gibi eylemler başlar. <xref:System.Windows.Style>, <xref:System.Windows.Controls.ControlTemplate>, ve <xref:System.Windows.DataTemplate> tüm bir `Triggers` Tetikleyiciler bir dizi içerebilir özelliği. Çeşitli türde Tetikleyiciler vardır.  
  
### <a name="property-triggers"></a>Özellik tetikleyicileri  
 A <xref:System.Windows.Trigger> kümeleri özelliği değerleri veya özellik değerine göre Eylemler başlar bir özellik tetikleyicisi adı verilir.  
  
 Özellik tetikleyicileri kullanma işlemini göstermek için her yapabilirsiniz <xref:System.Windows.Controls.ListBoxItem> seçili sürece kısmen saydam. Aşağıdaki ayarlar stil <xref:System.Windows.UIElement.Opacity%2A> değerini bir <xref:System.Windows.Controls.ListBoxItem> için `0.5`. Zaman <xref:System.Windows.Controls.ListBoxItem.IsSelected%2A> özelliği `true`, ancak <xref:System.Windows.UIElement.Opacity%2A> ayarlanır `1.0`:  
  
 [!code-xaml[StylingIntroSample_snippet#Triggers](~/samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSample_snippet/CSharp/Window1.xaml#triggers)]  
[!code-xaml[StylingIntroSample_snippet#EndTriggers](~/samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSample_snippet/CSharp/Window1.xaml#endtriggers)]  
  
 Bu örnekte bir <xref:System.Windows.Trigger> bir özellik değerini ayarlamak, ancak unutmayın <xref:System.Windows.Trigger> ayrıca sınıfında <xref:System.Windows.TriggerBase.EnterActions%2A> ve <xref:System.Windows.TriggerBase.ExitActions%2A> eylemleri gerçekleştirmek bir tetikleyici sağlayan özellikleri.  
  
 Dikkat <xref:System.Windows.FrameworkElement.MaxHeight%2A> özelliği <xref:System.Windows.Controls.ListBoxItem> ayarlanır `75`. Aşağıdaki çizimde, üçüncü öğe seçili öğesidir:  
  
 ![ListView biçimlendirilmiş](./media/stylingintro-triggers.png "StylingIntro_triggers")  
  
### <a name="eventtriggers-and-storyboards"></a>EventTriggers ve görsel Taslaklar  
 Başka bir tetikleyici türüdür <xref:System.Windows.EventTrigger>, bir dizi eylemi bir olayın oluşması göre başlar. Örneğin, aşağıdaki <xref:System.Windows.EventTrigger> nesneleri belirtin, fare işaretçisini girdiğinde <xref:System.Windows.Controls.ListBoxItem>, <xref:System.Windows.FrameworkElement.MaxHeight%2A> özellik değerine canlandırır `90` üzerinden bir `0.2` ikinci dönem. Uzağa öğe fareyi hareket ettirdiğinde özelliği bir dönem boyunca özgün değerine döndürür. `1` ikinci. Nasıl belirtmek gerekli olmadığını unutmayın bir <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> değerini <xref:System.Windows.ContentElement.MouseLeave> animasyon. Animasyon özgün değer takip mümkün olmasıdır.  
  
 [!code-xaml[StylingIntroSample_snippet#EventTriggers](~/samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSample_snippet/CSharp/Window1.xaml#eventtriggers)]  
  
 Daha fazla bilgi için [görsel taslaklara genel bakış](../graphics-multimedia/storyboards-overview.md).  
  
 Aşağıdaki çizimde, fare üçüncü öğesine işaret ediyor:  
  
 ![Stil örnek ekran](./media/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")  
  
### <a name="multitriggers-datatriggers-and-multidatatriggers"></a>MultiTriggers DataTriggers ve MultiDataTriggers  
 Ek olarak <xref:System.Windows.Trigger> ve <xref:System.Windows.EventTrigger>, diğer türde Tetikleyiciler vardır. <xref:System.Windows.MultiTrigger> birden çok koşullara göre özellik değerlerini ayarlamanıza olanak tanır. Kullandığınız <xref:System.Windows.DataTrigger> ve <xref:System.Windows.MultiDataTrigger> koşulunuzu özelliğini verilere bağlı olduğunda.  
  
<a name="styling_themes"></a>   
## <a name="shared-resources-and-themes"></a>Paylaşılan kaynaklar ve Temalar  
 Tipik bir Windows Presentation Foundation (WPF) uygulaması uygulama genelinde uygulanan birden çok kullanıcı arabirimi (UI) kaynaklarını olabilir. Toplu olarak, bu kaynak kümesi temayı uygulama için kabul edilebilir. Windows Presentation Foundation (WPF) desteği sağlar için paketleme kullanıcı arabirimi (UI) kaynaklarını bir tema olarak olarak kapsüllenmiş olan bir kaynak sözlüğünü kullanarak <xref:System.Windows.ResourceDictionary> sınıfı.  
  
 Windows Presentation Foundation (WPF) Temalar stil ve şablon oluşturma mekanizması, Windows Presentation Foundation (WPF) kullanıma sunar herhangi bir öğenin görselleri özelleştirmek için kullanılarak tanımlanmış.  
  
 Windows Presentation Foundation (WPF) Tema Kaynakları, katıştırılmış kaynak sözlükleri depolanır. Bu kaynak sözlükleri imzalı bir derleme gömülü olması gerekir ve ya da aynı bütünleştirilmiş kodu veya bir yan yana derleme eklenebilir. Windows Presentation Foundation (WPF) denetimleri içeren derleme PresentationFramework.dll söz konusu olduğunda tema yan yana derlemeler bir dizi kaynaklardır.  
  
 Tema öğesinin stilini ararken aramak için en son yeri haline gelir. Genellikle, arama uygun bir kaynak için arama öğesi ağacı walking tarafından başlamak sonra uygulama kaynak koleksiyonda görüneceğini ve son olarak sistem sorgu. Bu, uygulama geliştiricilerin temayı ulaşmadan önce herhangi bir nesne ağaç veya uygulama düzeyinde stil tanımlanacak bir fırsat sağlar.  
  
 Kaynak sözlükleri bir temayı birden çok uygulamada yeniden kullanmanıza olanak sağlayan tek tek dosyaları olarak tanımlayabilirsiniz. Ayrıca, aynı türlerini kaynakların ancak farklı değerlerle sağlayan birden çok kaynak sözlükleri tanımlayarak değiştirilebilir Temalar da oluşturabilirsiniz. Bu stiller veya diğer kaynakları uygulama düzeyinde tanımlayarak uygulamanın skinning için önerilen yaklaşımdır.  
  
 Uygulamalar arasında stiller ve şablonlar gibi kaynakları kümesi paylaşmak için oluşturabileceğiniz bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] tanımlayın ve dosya bir <xref:System.Windows.ResourceDictionary>. Örneğin, bir parçası gösteren aşağıdaki çizimde göz atın [ControlTemplates örneği ile stillendirme](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating):

![Denetim şablonu örnekleri](./media/stylingintro-controltemplateexamples.png "StylingIntro_ControlTemplateExamples")  
  
 Bakarsanız [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] örnek dosyaları, tüm dosyaları aşağıdaki olduğunu görürsünüz:  
  
 [!code-xaml[ControlTemplateExamples#MergedDictionaries](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/button.xaml#mergeddictionaries)]  
  
 Paylaşımını olan `shared.xaml`, tanımlayan bir <xref:System.Windows.ResourceDictionary> tutarlı bir görünüm sağlamak için örnek denetimler sağlayan bir stil ve fırça kaynakları kümesi içerir.  
  
 Daha fazla bilgi için [birleştirilmiş kaynak sözlükleri](../advanced/merged-resource-dictionaries.md).  
  
 Sizin için bir tema özel denetim oluşturuyorsanız, dış denetim kitaplığı bölümüne bakın. [denetim yazmaya genel bakış](control-authoring-overview.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WPF İçinde URI'leri Paketleme](../app-development/pack-uris-in-wpf.md)
- [Nasıl yapılır: ControlTemplate ile Oluşturulan Öğeleri Bulma](how-to-find-controltemplate-generated-elements.md)
- [DataTemplate ile Oluşturulan Öğeleri Bulma](../data/how-to-find-datatemplate-generated-elements.md)
