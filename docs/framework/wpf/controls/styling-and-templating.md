---
title: "Stil ve Şablon Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "34"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c33739d0e753146ffdc8b825d88c6ca7ba63fa1a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="styling-and-templating"></a>Stil ve Şablon Oluşturma
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]Stil ve şablon suite geliştiricilerin ve tasarımcıların görsel olarak ilgi çekici efektler oluşturmak ve kendi ürün için tutarlı bir görünüm oluşturmak için izin özellikleri (stiller, şablonlar, tetikleyiciler ve film şeritleri) bakın. Geliştiriciler ve/veya tasarımcıları bir uygulama tarafından uygulama temelinde yaygın görünümünü özelleştirebilirsiniz rağmen güçlü bir stil ve şablon modeli Bakım ve görünümü içinde ve uygulamalar arasında paylaşılmasını izin vermek gereklidir. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]Bu modeli sağlar.  
  
 Başka bir özelliği olan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stil modeldir sunu ve mantığı ayrılması. Bu yalnızca kullanarak tasarımcıları uygulamanın görünümünü çalışabilirsiniz anlamına gelir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] aynı anda geliştiriciler C# veya Visual Basic kullanarak programlama mantığa göre çalışır.  
  
 Bu genel bakışta uygulama stil ve şablon yönlerini üzerinde odaklanır ve tüm veri bağlama kavramlarını ele alınmaz. Veri bağlama hakkında daha fazla bilgi için bkz: [veri bağlama genel bakış](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
 Ayrıca, hangi stilleri ve şablonları yeniden etkinleştirin kaynakları anlamak önemlidir. Kaynaklar hakkında daha fazla bilgi için bkz: [XAML kaynakları](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
 
  
<a name="styling_and_templating_sample"></a>   
## <a name="styling-and-templating-sample"></a>Stil ve şablon örneği  
 Bu genel bakışta kullanılan kod örnekleri aşağıdaki çizimde gösterilen bir basit fotoğraf örnek dayanır:  
  
 ![ListView stilde](../../../../docs/framework/wpf/controls/media/stylingintro-triggers.png "StylingIntro_triggers")  
  
 Bu basit fotoğraf örnek, bir görsel olarak ilgi çekici kullanıcı deneyimi oluşturmak için stil ve şablon kullanır. İki örnek sahip <xref:System.Windows.Controls.TextBlock> öğeleri ve <xref:System.Windows.Controls.ListBox> görüntüleri bir listeye bağlı denetim. Tam bir örnek için bkz: [stil ve şablon örnek giriş](http://go.microsoft.com/fwlink/?LinkID=160010).  
  
<a name="styling_basics"></a>   
## <a name="style-basics"></a>Stil temelleri  
 Düşünebilirsiniz bir <xref:System.Windows.Style> özellik değerleri kümesi birden fazla öğeye uygulamak için kolay bir yol olarak. Örneğin, aşağıdakileri göz önünde bulundurun <xref:System.Windows.Controls.TextBlock> öğelerini ve varsayılan görünümleri:  
  
 [!code-xaml[StylingIntroSample_snippet#TextBlocks](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSample_snippet/CSharp/Window1.xaml#textblocks)]  
  
 ![Stil örnek ekran görüntüsü](../../../../docs/framework/wpf/controls/media/stylingintro-textblocksbefore.PNG "StylingIntro_TextBlocksBefore")  
  
 Varsayılan görünüm özelliklerini ayarlayarak değiştirebilirsiniz <xref:System.Windows.Controls.Control.FontSize%2A> ve <xref:System.Windows.Controls.Control.FontFamily%2A>, her <xref:System.Windows.Controls.TextBlock> doğrudan öğesi. Ancak, isterseniz, <xref:System.Windows.Controls.TextBlock> bazı özellikleri paylaşır öğeleri oluşturabileceğiniz bir <xref:System.Windows.Style> içinde `Resources` bölümünü, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] aşağıda gösterildiği gibi dosya:  
  
 [!code-xaml[StylingIntroSnippet#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources)]  
[!code-xaml[StylingIntroSnippet#tb1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#tb1)]  
[!code-xaml[StylingIntroSnippet#Resources2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources2)]  
  
 Ayarladığınızda <xref:System.Windows.Style.TargetType%2A> stilinize, <xref:System.Windows.Controls.TextBlock> türü, stil tümüne uygulanır <xref:System.Windows.Controls.TextBlock> pencere öğeleri.  
  
 Şimdi <xref:System.Windows.Controls.TextBlock> öğeleri aşağıdaki gibi görünür:  
  
 ![Stil örnek ekran görüntüsü](../../../../docs/framework/wpf/controls/media/stylingintro-textblocksbasestyle.PNG "StylingIntro_TextBlocksBaseStyle")  
  
### <a name="extending-styles"></a>Stilleri genişletme  
 İki belki de istediğiniz <xref:System.Windows.Controls.TextBlock> bazı özellik değerleri gibi paylaşmak için öğeleri <xref:System.Windows.Controls.Control.FontFamily%2A> ve ortalanmış <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, ancak "Bazı ek özellikler sağlamak için resimler" metin da isteyebilirsiniz. Aşağıda gösterildiği gibi ilk stilini dayalı yeni bir stil oluşturarak yapabilirsiniz:  
  
 [!code-xaml[StylingIntroSnippet#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources)]  
[!code-xaml[StylingIntroSnippet#tb2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#tb2)]  
[!code-xaml[StylingIntroSnippet#Resources2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources2)]  
  
 Önceki stili verilen bildirimi bir `x:Key`. Stil uygulamak için ayarladığınız <xref:System.Windows.FrameworkElement.Style%2A> özelliği, <xref:System.Windows.Controls.TextBlock> için `x:Key` aşağıda gösterildiği gibi değer:  
  
 [!code-xaml[StylingIntroSnippet#UIText](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#uitext)]  
  
 Bu <xref:System.Windows.Controls.TextBlock> şimdi stilde bir <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> değerini <xref:System.Windows.HorizontalAlignment.Center>, <xref:System.Windows.Controls.TextBlock.FontFamily%2A> değerini `Comic Sans MS`, <xref:System.Windows.Controls.TextBlock.FontSize%2A> 26, değeri ve bir <xref:System.Windows.Controls.TextBlock.Foreground%2A> değerine <xref:System.Windows.Media.LinearGradientBrush> örnekte gösterildiği. Bu geçersiz kılmaları bildirimi <xref:System.Windows.Controls.Control.FontSize%2A> temel stil değeri. Varsa birden fazla <xref:System.Windows.Setter> aynı özelliğini ayarlarken bir <xref:System.Windows.Style>, <xref:System.Windows.Setter> diğer bir deyişle bildirilen son önceliğe.  
  
 Aşağıdaki ne gösterir <xref:System.Windows.Controls.TextBlock> öğeleri şimdi Ara gibi:  
  
 ![TextBlock'lar stilde](../../../../docs/framework/wpf/controls/media/stylingintro-textblocks.png "StylingIntro_TextBlocks")  
  
 Bu `TitleText` stili için oluşturulan stil genişletir <xref:System.Windows.Controls.TextBlock> türü. Ayrıca sahip bir stil genişletebilirsiniz bir `x:Key` kullanarak `x:Key` değeri. Bir örnek için için sağlanan bkz <xref:System.Windows.Style.BasedOn%2A> özelliği.  
  
### <a name="relationship-of-the-targettype-property-and-the-xkey-attribute"></a>İlişki TargetType özelliği ve x: Key özniteliği  
 İlk örnekte gösterildiği gibi ayarı <xref:System.Windows.Style.TargetType%2A> özelliğine `TextBlock` stili atama olmadan bir `x:Key` tümüne uygulanacak stili neden <xref:System.Windows.Controls.TextBlock> öğeleri. Bu durumda, `x:Key` örtük olarak ayarlandığında `{x:Type TextBlock}`. Açık olarak ayarlarsanız, bunun anlamı `x:Key` için herhangi bir şey dışında değer `{x:Type TextBlock}`, <xref:System.Windows.Style> tümüne uygulanmıyor <xref:System.Windows.Controls.TextBlock> öğeler otomatik olarak. Bunun yerine, stil uygulamanız gerekir (kullanarak `x:Key` değeri) için <xref:System.Windows.Controls.TextBlock> öğeleri açıkça. Stil kodunuzu kaynakları bölümdür ve ayarlanmamış <xref:System.Windows.Style.TargetType%2A> stilinize olduktan sonra özellikte sağlamalıdır bir `x:Key`.  
  
 İçin varsayılan bir değer sağlama yanı sıra `x:Key`, <xref:System.Windows.Style.TargetType%2A> özellik ayarlayıcı özelliklerini uygulandığı türünü belirtir. Belirtmezseniz, bir <xref:System.Windows.Style.TargetType%2A>, özelliklerinde nitelemeniz gerekir, <xref:System.Windows.Setter> sözdizimini kullanarak bir sınıf adı nesneleriyle `Property="ClassName.Property"`. Örneğin, ayar yerine `Property="FontSize"`, ayarlamalısınız <xref:System.Windows.Setter.Property%2A> için `"TextBlock.FontSize"` veya `"Control.FontSize"`.  
  
 Ayrıca unutmayın bu kadar sayıda [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimleri diğer birleşiminden oluşur [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrol eder. Bir türdeki tüm denetimler için geçerli bir stil oluşturursanız, beklenmedik sonuçlar alabilirsiniz. Hedefleyen bir stil oluşturursanız, örneğin, <xref:System.Windows.Controls.TextBlock> yazın bir <xref:System.Windows.Window>, stil tümüne uygulanır <xref:System.Windows.Controls.TextBlock> denetimleri penceresinde olsa bile <xref:System.Windows.Controls.TextBlock> başka bir denetim, parçası olduğu gibi bir <xref:System.Windows.Controls.ListBox>.  
  
### <a name="styles-and-resources"></a>Stilleri ve kaynakları  
 Türetilen herhangi bir öğe üzerinde bir stil kullanın <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement>. Stil bildirmek için en yaygın bir kaynak olarak yoludur `Resources` bölümüne bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] önceki örneklerde gösterildiği gibi dosya. Stilleri kaynaklar olduğundan, bunlar tüm kaynaklara uygulamak aynı Ölçüm kuralları uyma; Burada bir stil stili uygulanabileceği etkiler bildirin. Örneğin, uygulama tanımının kök öğesinin stilde bildirirseniz [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosya, stil uygulamanızda herhangi bir kullanılabilir. Gezinti uygulaması oluşturup, uygulamanın birinde stili bildirme [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosyaları, stil yalnızca, kullanılabilir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosya. Kaynaklar için kuralları kapsamı hakkında daha fazla bilgi için bkz: [XAML kaynakları](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
 Ayrıca, stil ve kaynakları hakkında daha fazla bilgi bulabilirsiniz [paylaşılan kaynakları ve Temalar](#styling_themes) daha sonra bu genel bakış.  
  
### <a name="setting-styles-programmatically"></a>Stilleri programlı olarak ayarlama  
 Adlandırılmış bir stil program aracılığıyla bir öğe olarak atamak için kaynakları koleksiyondan stili alın ve öğenin atamak <xref:System.Windows.FrameworkElement.Style%2A> özelliği. Bir kaynak koleksiyondaki öğelerin türü olduğunu unutmayın <xref:System.Object>. Bu nedenle, alınan stiline dönüştürün bir <xref:System.Windows.Style> atanarak önce <xref:System.Windows.FrameworkElement.Style%2A> özelliği. Örneğin, tanımlı ayarlamak için `TitleText` üzerinde stil bir <xref:System.Windows.Controls.TextBlock> adlı `textblock1`, aşağıdakileri yapın:  
  
 [!code-csharp[StylingIntroSample_snippet#Code](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSample_snippet/CSharp/Window1.xaml.cs#code)]
 [!code-vb[StylingIntroSample_snippet#Code](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StylingIntroSample_snippet/visualbasic/window1.xaml.vb#code)]  
  
 Stil uygulandıktan sonra korumalı ve değiştirilemez unutmayın. Dinamik olarak zaten uygulanmış bir tarzını değiştirme istiyorsanız, var olan bir değiştirmek için yeni bir stil oluşturmanız gerekir. Daha fazla bilgi için bkz: <xref:System.Windows.Style.IsSealed%2A> özelliği.  
  
 Temel alınarak özel mantığını uygulamak için bir stil seçtiği bir nesne oluşturabilirsiniz. Bir örnek için için sağlanan bkz <xref:System.Windows.Controls.StyleSelector> sınıfı.  
  
<a name="styling_binding_dynamicresource"></a>   
### <a name="bindings-dynamic-resources-and-event-handlers"></a>Bağlamaları, dinamik kaynaklar ve olay işleyicileri  
 Kullanabileceğiniz Not `Setter.Value` özelliği belirtmek için bir [biçimlendirme uzantısı bağlama](../../../../docs/framework/wpf/advanced/binding-markup-extension.md) veya [DynamicResource Biçimlendirme Uzantısı](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md). Daha fazla bilgi için için sağlanan örnekleri görmek <xref:System.Windows.Setter.Value%2A?displayProperty=nameWithType> özelliği.  
  
 Şu ana kadar bu genel bakışta, yalnızca özellik değerini ayarlamak için ayarlayıcılar kullanımı anlatılmaktadır. Olay işleyicileri stilde de belirtebilirsiniz. Daha fazla bilgi için bkz. <xref:System.Windows.EventSetter>.  
  
<a name="styling_datatemplates"></a>   
## <a name="data-templates"></a>Veri şablonları  
 Bu örnek uygulamasında var olan bir <xref:System.Windows.Controls.ListBox> fotoğraf bir listeye bağlı denetimi:  
  
 [!code-xaml[StylingIntroSnippet#UIListBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#uilistbox)]  
  
 Bu <xref:System.Windows.Controls.ListBox> şu anda aşağıdaki gibi görünür:  
  
 ![Şablon uygulanmadan önce ListBox](../../../../docs/framework/wpf/controls/media/stylingintro-listboxbefore.png "StylingIntro_ListBoxBefore")  
  
 Çoğu denetim bazı içerik türüne sahip ve içeriği genellikle bağlama verilerden gelir. Bu örnekte, veri fotoğraf listelenmiştir. İçinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], kullandığınız bir <xref:System.Windows.DataTemplate> görsel veri tanımlamak için. Temel olarak, ne yerleştirdiğiniz içine bir <xref:System.Windows.DataTemplate> verileri nasıl işlenmiş uygulamada göründüğünü belirler.  
  
 Bizim örnek uygulamasında, her özel `Photo` nesnesi bir `Source` özellik türü dizenin resim dosya yolunu belirtir. Şu anda, fotoğraf nesneler dosya yolları görüntülenir.  
  
 Oluşturduğunuz fotoğraf görüntü olarak görünmesi bir <xref:System.Windows.DataTemplate> bir kaynak olarak:  
  
 [!code-xaml[StylingIntroSnippet#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources)]  
[!code-xaml[StylingIntroSnippet#DataTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#datatemplate)]  
[!code-xaml[StylingIntroSnippet#Resources2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources2)]  
  
 Dikkat <xref:System.Windows.DataTemplate.DataType%2A> özelliği için çok benzer <xref:System.Windows.Style.TargetType%2A> özelliği <xref:System.Windows.Style>. Varsa, <xref:System.Windows.DataTemplate> belirttiğiniz zaman kaynakları bölümünde olduğu <xref:System.Windows.DataTemplate.DataType%2A> türü özelliğine ve ata değil bir `x:Key`, <xref:System.Windows.DataTemplate> her türü görüntülendiğinde uygulanır. Her zaman atama seçeneğiniz vardır <xref:System.Windows.DataTemplate> ile bir `x:Key` ve olarak ayarlanmış bir `StaticResource` ele özellikleri için <xref:System.Windows.DataTemplate> türleri, aşağıdaki gibi <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> özelliği veya <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> özelliği.  
  
 Esas olarak, <xref:System.Windows.DataTemplate> olduğunda yukarıdaki örnekte tanımlayan bir `Photo` nesne olarak görünmelidir bir <xref:System.Windows.Controls.Image> içinde bir <xref:System.Windows.Controls.Border>. Bu <xref:System.Windows.DataTemplate>, uygulamamız şimdi şöyle görünür:  
  
 ![Fotoğraf görüntü](../../../../docs/framework/wpf/controls/media/stylingintro-photosasimages.png "StylingIntro_PhotosAsImages")  
  
 Veri şablon modeli diğer özellikleri sağlar. Örneğin, kullanarak diğer koleksiyonları içeren koleksiyon verileri görüntülüyorsanız bir <xref:System.Windows.Controls.HeaderedItemsControl> gibi yazın bir <xref:System.Windows.Controls.Menu> veya <xref:System.Windows.Controls.TreeView>, var. <xref:System.Windows.HierarchicalDataTemplate>. Başka bir veri şablon özelliği <xref:System.Windows.Controls.DataTemplateSelector>, seçmenize olanak sağlayan bir <xref:System.Windows.DataTemplate> dayalı olarak özel mantık kullanılacak. Daha fazla bilgi için bkz: [veri şablonu özeti](../../../../docs/framework/wpf/data/data-templating-overview.md), farklı veri şablon özelliklerin daha ayrıntılı bir tartışma sağlar.  
  
<a name="styling_controltemplates"></a>   
## <a name="control-templates"></a>Denetim şablonları  
 İçinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], <xref:System.Windows.Controls.ControlTemplate> bir denetimin denetiminin görünümünü tanımlar. Yeni bir tanımlayarak yapısı ve denetiminin görünümünü değiştirebilirsiniz <xref:System.Windows.Controls.ControlTemplate> denetimi için. Böylece, kendi özel denetimler yazma gerekmez çoğu durumda bu, yeterli esnekliği sağlar. Daha fazla bilgi için bkz: [ControlTemplate oluşturarak varolan denetiminin görünümünü özelleştirme](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
<a name="styling_triggers"></a>   
## <a name="triggers"></a>Tetikleyiciler  
 Tetikleyici özellikleri ayarlar veya özellik değeri değiştiğinde veya bir olay oluşturulduğunda bir animasyon gibi eylemleri başlatır. <xref:System.Windows.Style>, <xref:System.Windows.Controls.ControlTemplate>, ve <xref:System.Windows.DataTemplate> tümüne sahip bir `Triggers` Tetikleyicileri kümesi içerebilir özelliği. Çeşitli türlerde Tetikleyicileri vardır.  
  
### <a name="property-triggers"></a>Özellik tetikleyicileri  
 A <xref:System.Windows.Trigger> kümeleri özelliği değerleri veya bir özellik değeri temel alınarak Eylemler başladığı özellik tetikleyici adı verilir.  
  
 Özellik tetikleyicileri kullanmayı göstermek için her yapabilirsiniz <xref:System.Windows.Controls.ListBoxItem> seçili sürece kısmen saydam. Aşağıdaki ayarlar stil <xref:System.Windows.UIElement.Opacity%2A> değerini bir <xref:System.Windows.Controls.ListBoxItem> için `0.5`. Zaman <xref:System.Windows.Controls.ListBoxItem.IsSelected%2A> özelliği `true`, ancak <xref:System.Windows.UIElement.Opacity%2A> ayarlanır `1.0`:  
  
 [!code-xaml[StylingIntroSample_snippet#Triggers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSample_snippet/CSharp/Window1.xaml#triggers)]  
[!code-xaml[StylingIntroSample_snippet#EndTriggers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSample_snippet/CSharp/Window1.xaml#endtriggers)]  
  
 Bu örnekte bir <xref:System.Windows.Trigger> bir özellik değeri ayarlanmasına, ancak unutmayın <xref:System.Windows.Trigger> sınıfı da sahiptir <xref:System.Windows.TriggerBase.EnterActions%2A> ve <xref:System.Windows.TriggerBase.ExitActions%2A> eylemleri gerçekleştirmek bir tetikleyici etkinleştirmek özellikleri.  
  
 Dikkat <xref:System.Windows.FrameworkElement.MaxHeight%2A> özelliği <xref:System.Windows.Controls.ListBoxItem> ayarlanır `75`. Aşağıdaki çizimde üçüncü seçili öğe öğesidir:  
  
 ![ListView stilde](../../../../docs/framework/wpf/controls/media/stylingintro-triggers.png "StylingIntro_triggers")  
  
### <a name="eventtriggers-and-storyboards"></a>EventTriggers ve film şeritleri  
 Tetikleyici başka bir türde <xref:System.Windows.EventTrigger>, bir dizi olay tekrarlamasını üzerinde temel eylemleri başlatır. Örneğin, aşağıdaki <xref:System.Windows.EventTrigger> nesneleri belirtin, fare işaretçisini girdiğinde <xref:System.Windows.Controls.ListBoxItem>, <xref:System.Windows.FrameworkElement.MaxHeight%2A> özelliği için bir değer canlandırır `90` üzerinden bir `0.2` ikinci süresi. Fare öğesi uzağa doğru hareket ettiğinde özelliği özgün değeri bir süre içinde döndürür. `1` ikinci. Nasıl belirtmek için gerekli olmadığını unutmayın bir <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> değerini <xref:System.Windows.ContentElement.MouseLeave> animasyon. Animasyonun özgün değeri izlemek mümkün olduğundan bu değildir.  
  
 [!code-xaml[StylingIntroSample_snippet#EventTriggers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSample_snippet/CSharp/Window1.xaml#eventtriggers)]  
  
 Daha fazla bilgi için bkz: [film şeritleri genel bakış](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).  
  
 Aşağıdaki çizimde, fare üçüncü öğesine işaret ettiğinden:  
  
 ![Stil örnek ekran görüntüsü](../../../../docs/framework/wpf/controls/media/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")  
  
### <a name="multitriggers-datatriggers-and-multidatatriggers"></a>MultiTriggers, DataTriggers ve MultiDataTriggers  
 Ek olarak <xref:System.Windows.Trigger> ve <xref:System.Windows.EventTrigger>, diğer tür tetikleyici sunucusu vardır. <xref:System.Windows.MultiTrigger>birden çok koşullara göre özellik değerlerini ayarlamanıza olanak sağlar. Kullandığınız <xref:System.Windows.DataTrigger> ve <xref:System.Windows.MultiDataTrigger> koşulunuz özelliği verilere bağlı olduğunda.  
  
<a name="styling_themes"></a>   
## <a name="shared-resources-and-themes"></a>Paylaşılan kaynaklar ve Temalar  
 Tipik bir [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] uygulama uygulama genelinde uygulanan birden çok kullanıcı arabirimi (UI) kaynaklara sahip olabilir. Toplu olarak, bu kaynakları kümesi tema uygulama için kabul edilebilir. [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)]paketleme kullanıcı arabirimi (UI) kaynakların bir tema olarak olarak kapsüllenmiş bir kaynak sözlüğü kullanarak destek sağlar <xref:System.Windows.ResourceDictionary> sınıfı.  
  
 [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)]Temalar, stil ve şablon mekanizma kullanılarak tanımlanır, [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] herhangi bir öğeyi görsel özelleştirmek için kullanıma sunar.  
  
 [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)]Tema Kaynakları katıştırılmış kaynak sözlükte depolanır. Bu kaynak sözlüklerindeki içinde imzalı bir derleme gömülü gerekir ve ya da aynı bütünleştirilmiş kod veya yan yana derleme katıştırılabilir. PresentationFramework.dll, içeren derleme durumunda [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] denetimleri tema kaynaklardır yan yana derlemeler bir dizi.  
  
 Tema, bir öğenin stili ararken aramak için son yer haline gelir. Genellikle, arama uygun bir kaynak için arama öğe ağacı adım adım ilerlemenizi sağlayarak başlamak sonra uygulama kaynak koleksiyonunda görüneceğini ve son olarak sistem sorgu. Bu uygulama geliştiricileri ağaç veya uygulama düzeyinde herhangi bir nesne için stil tema erişmeden önce yeniden tanımlamanız olanağı verir.  
  
 Bir tema birden çok uygulama arasında yeniden kullanmanıza olanak sağlayan tek tek dosyalar olarak kaynak sözlüklerindeki tanımlayabilirsiniz. Kaynakların ancak farklı değerlerle aynı türlerini sağlayan birden çok kaynak sözlüklerindeki tanımlayarak swappable Temalar da oluşturabilirsiniz. Bu stiller veya diğer kaynakları uygulama düzeyinde tanımlayarak, bir uygulama kaplama için önerilen yaklaşımdır.  
  
 Bir dizi uygulamalar arasında stilleri ve şablonlar gibi kaynakları paylaşmak için oluşturabileceğiniz bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosya ve tanımlayan bir <xref:System.Windows.ResourceDictionary>. Örneğin, bir bölümünü gösteren aşağıdaki çizimde göz atın [ControlTemplates örneği ile stil oluşturma](http://go.microsoft.com/fwlink/?LinkID=160041):  
  
 ![Denetim şablonu örnekleri](../../../../docs/framework/wpf/controls/media/stylingintro-controltemplateexamples.png "StylingIntro_ControlTemplateExamples")  
  
 Bakarsanız [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosyaları örnekteki tüm dosyaları aşağıdaki olduğunu görürsünüz:  
  
 [!code-xaml[ControlTemplateExamples#MergedDictionaries](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/button.xaml#mergeddictionaries)]  
  
 Paylaşılmasını olan `shared.xaml`, tanımlayan bir <xref:System.Windows.ResourceDictionary> tutarlı bir görünüm için örnek denetimlerinde sağlar bir tarzını ve fırça kaynak kümesi içerir.  
  
 Daha fazla bilgi için bkz: [birleştirilmiş kaynak sözlükleri](../../../../docs/framework/wpf/advanced/merged-resource-dictionaries.md).  
  
 Sizin için bir tema özel denetim oluşturuyorsanız, dış denetim kitaplığı bölümüne bakın [denetimine genel bakış yazma](../../../../docs/framework/wpf/controls/control-authoring-overview.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WPF İçinde URI'leri Paketleme](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)  
 [Nasıl yapılır: ControlTemplate ile Oluşturulan Öğeleri Bulma](../../../../docs/framework/wpf/controls/how-to-find-controltemplate-generated-elements.md)  
 [DataTemplate ile Oluşturulan Öğeleri Bulma](../../../../docs/framework/wpf/data/how-to-find-datatemplate-generated-elements.md)
