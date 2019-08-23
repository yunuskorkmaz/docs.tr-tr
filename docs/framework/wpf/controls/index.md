---
title: Denetimler
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], about WPF controls
ms.assetid: 3f255a8a-35a8-4712-9065-472ff7d75599
ms.openlocfilehash: faa1fbad85acf5788c10de7750c6a7c32b535bf5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957032"
---
# <a name="controls"></a>Denetimler
<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)],,, ve <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.Menu> <xref:System.Windows.Controls.Label> gibi<xref:System.Windows.Controls.ListBox>neredeyse her Windows uygulamasında kullanılan birçok ortak kullanıcı arabirimi bileşeni ile birlikte gönderilir. Tarihsel olarak, bu nesneler denetimler olarak adlandırılmıştır. SDK, bir uygulamadaki görünür bir nesneyi temsil eden herhangi bir sınıfı gevşekme etmek için "Control" terimini kullanmaya devam ederken, bir sınıfın görünür bir varlığına sahip olacak şekilde <xref:System.Windows.Controls.Control> sınıftan devralması gerekmediğini unutmayın. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Control> Sınıfından kalıtımla alan sınıflar, bir denetimin tüketicisinin yeni bir alt sınıf oluşturmaya gerek kalmadan denetimin görünümünü bir şekilde değiştirmesine izin veren bir <xref:System.Windows.Controls.ControlTemplate>içerir.  Bu konuda, denetimlerin (her ikisi de <xref:System.Windows.Controls.Control> sınıfından ve olmayan) yaygın olarak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]kullanılan denetimlerin nasıl kullanıldığı açıklanmaktadır.  

<a name="creating_an_instance_of_a_control"></a>   
## <a name="creating-an-instance-of-a-control"></a>Bir denetimin örneğini oluşturma  
 Ya da [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] kodunu kullanarak bir uygulamaya denetim ekleyebilirsiniz.  Aşağıdaki örnek, kullanıcıdan ilk ve son adlarını soran basit bir uygulamanın nasıl oluşturulacağını gösterir.  Bu örnek altı denetim oluşturur: iki etiket, iki metin kutusu ve ' de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]iki düğme. Tüm denetimler benzer şekilde oluşturulabilir.  
  
 [!code-xaml[ControlsOverview#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#1)]  
  
 Aşağıdaki örnek, kodda aynı uygulamayı oluşturur. Kısaltma için,, öğesinin <xref:System.Windows.Controls.Grid> `grid1`oluşturulması örnekten dışlandı. `grid1`, yukarıdaki [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] örnekte gösterildiği gibi aynı sütun ve satır tanımlarına sahiptir.  
  
 [!code-csharp[ControlsOverview#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#2)]
 [!code-vb[ControlsOverview#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#2)]  
  
<a name="changing_the_appearance_of_a_control"></a>   
## <a name="changing-the-appearance-of-a-control"></a>Bir denetimin görünümünü değiştirme  
 Bir denetimin görünümünü uygulamanızın görünümüne uyacak şekilde değiştirmek yaygındır. Bir denetimin görünüşünü, gerçekleştirmek istediğiniz seçeneğe bağlı olarak aşağıdakilerden birini yaparak değiştirebilirsiniz:  
  
- Denetimin bir özelliğinin değerini değiştirin.  
  
- <xref:System.Windows.Style> Denetim için oluşturun.  
  
- Denetim için yeni <xref:System.Windows.Controls.ControlTemplate> bir oluştur.  
  
### <a name="changing-a-controls-property-value"></a>Denetimin özellik değerini değiştirme  
 Birçok denetim, <xref:System.Windows.Controls.Control.Background%2A> <xref:System.Windows.Controls.Button>içindeki gibi denetimin nasıl göründüğünü değiştirmenize olanak tanıyan özelliklere sahiptir. Hem [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] hem de kodunda değer özelliklerini ayarlayabilirsiniz. <xref:System.Windows.Controls.Control.Background%2A>Aşağıdaki örnek, <xref:System.Windows.Controls.Button> içindeki <xref:System.Windows.Controls.Control.FontWeight%2A> içindeki <xref:System.Windows.Controls.Control.FontSize%2A>,veözelliklerini Ayarlar[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 [!code-xaml[ControlsOverview#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#3)]  
  
 Aşağıdaki örnek, kodda aynı özellikleri ayarlar.  
  
 [!code-csharp[ControlsOverview#4](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#4)]
 [!code-vb[ControlsOverview#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#4)]  
  
### <a name="creating-a-style-for-a-control"></a>Denetim için stil oluşturma  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], bir oluşturarak, uygulamadaki her bir <xref:System.Windows.Style>örnekteki özellikleri ayarlamak yerine toplu olarak denetimlerin görünümünü belirtmenize olanak tanır. Aşağıdaki örnek, uygulamasında her <xref:System.Windows.Style> birine <xref:System.Windows.Controls.Button> uygulanan bir oluşturur. <xref:System.Windows.Style>tanımlar, genellikle içinde ' [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ın <xref:System.Windows.FrameworkElement.Resources%2A> özelliği <xref:System.Windows.ResourceDictionary> <xref:System.Windows.FrameworkElement>gibi tanımlanır.  
  
 [!code-xaml[ControlsOverview#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#5)]  
  
 Stile bir anahtar atayarak ve bu anahtarı `Style` denetiminizin özelliğinde belirterek belirli bir türün yalnızca belirli denetimlerine bir stil uygulayabilirsiniz.  Stiller hakkında daha fazla bilgi için bkz. [Stil oluşturma ve şablon](styling-and-templating.md)oluşturma.  
  
### <a name="creating-a-controltemplate"></a>ControlTemplate oluşturarak  
 , Tek seferde birden çok denetim üzerinde özellikler ayarlamanıza <xref:System.Windows.Controls.Control> <xref:System.Windows.Style> olanaktanır,ancakbazenbiroluşturarak,bir'ıoluşturarakyapabileceklerinizidaha<xref:System.Windows.Style> fazla özelleştirmek isteyebilirsiniz. <xref:System.Windows.Controls.Control> Sınıfından kalıtımla alan sınıflar öğesine <xref:System.Windows.Controls.ControlTemplate>sahiptir ve öğesinin <xref:System.Windows.Controls.Control>yapısını ve görünümünü tanımlar. Öğesinin özelliği geneldir <xref:System.Windows.Controls.Control> , Bu<xref:System.Windows.Controls.ControlTemplate> sayede, varsayılandan farklı bir öğesine sahip olabilirsiniz. <xref:System.Windows.Controls.Control.Template%2A> <xref:System.Windows.Controls.Control> Görünümünü <xref:System.Windows.Controls.ControlTemplate> özelleştirmekiçin<xref:System.Windows.Controls.Control> çoğunlukla bir denetimden devralma yerine bir için yeni bir belirleyebilirsiniz. <xref:System.Windows.Controls.Control>  
  
 En yaygın denetimi <xref:System.Windows.Controls.Button>göz önünde bulundurun.  Bir <xref:System.Windows.Controls.Button> öğesinin birincil davranışı, bir uygulamanın kullanıcı tıkladığı zaman bir eylem yapması için bir işlemdir.  Varsayılan <xref:System.Windows.Controls.Button> olarak, içinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir yükseltilmiş dikdörtgen olarak görünür.  Bir uygulama geliştirirken, bir, düğmenin tıklama olayını işleyerek, bir <xref:System.Windows.Controls.Button>' ın davranışından faydalanmak isteyebilirsiniz, ancak düğmenin özelliklerini değiştirerek düğmenin görünümünü yapabileceklerinizi değiştirmiş olabilirsiniz.  Bu durumda, yeni <xref:System.Windows.Controls.ControlTemplate>bir oluşturabilirsiniz.  
  
 Aşağıdaki örnek bir <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.Button>için oluşturur.  , <xref:System.Windows.Controls.ControlTemplate> Yuvarlatılmış köşeler <xref:System.Windows.Controls.Button> ve gradyan arka planı oluşturur.  , <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.Border.Background%2A> <xref:System.Windows.Controls.Border> İki<xref:System.Windows.Media.LinearGradientBrush> nesnesi olan olan biriçerir.<xref:System.Windows.Media.GradientStop>  İlki <xref:System.Windows.Media.GradientStop> <xref:System.Windows.Media.GradientStop.Color%2A> , öğesinin<xref:System.Windows.Media.GradientStop> özelliğini düğmenin arka planının rengine bağlamak için veri bağlamayı kullanır.  <xref:System.Windows.Controls.Control.Background%2A> Öğesinin özelliğini ayarladığınızda <xref:System.Windows.Media.GradientStop>, bu değerin rengi ilk olarak kullanılacaktır. <xref:System.Windows.Controls.Button> Veri bağlama hakkında daha fazla bilgi için bkz. [veri bağlamaya genel bakış](../data/data-binding-overview.md). Örnek <xref:System.Windows.Trigger> , öğesinin <xref:System.Windows.Controls.Button> ne <xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A> olduğu ,görünümünüdeğiştirenbirdeoluşturur.`true`  
  
 [!code-xaml[ControlsOverview#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#6)]  
[!code-xaml[ControlsOverview#7](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#7)]  
  
> [!NOTE]
> Örneği düzgün şekilde çalışması <xref:System.Windows.Controls.Button> için öğesinin <xref:System.Windows.Media.SolidColorBrush> özelliğibirolarakayarlanmalıdır.<xref:System.Windows.Controls.Control.Background%2A>  
  
<a name="subscribing_to_events"></a>   
## <a name="subscribing-to-events"></a>Olaylara abone olma  
 Ya da [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kodunu kullanarak bir denetimin olayına abone olabilirsiniz, ancak kodda yalnızca bir olayı işleyebilirsiniz.  Aşağıdaki örnek, bir `Click` <xref:System.Windows.Controls.Button>öğesinin olayına nasıl abone olunacağını göstermektedir.  
  
 [!code-xaml[ControlsOverview#10](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#10)]  
  
 [!code-csharp[ControlsOverview#8](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#8)]
 [!code-vb[ControlsOverview#8](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#8)]  
  
 Aşağıdaki örnek, `Click` olayını <xref:System.Windows.Controls.Button>işler.  
  
 [!code-csharp[ControlsOverview#9](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#9)]
 [!code-vb[ControlsOverview#9](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#9)]  
  
<a name="rich_content_in_controls"></a>   
## <a name="rich-content-in-controls"></a>Denetimlerde zengin Içerik  
 <xref:System.Windows.Controls.Control> Sınıfından kalıtımla alan çoğu sınıfın, zengin içerik içerme kapasitesi vardır. Örneğin, bir <xref:System.Windows.Controls.Label> dize <xref:System.Windows.Controls.Image>,, veya <xref:System.Windows.Controls.Panel>gibi herhangi bir nesne içerebilir.  Aşağıdaki sınıflar zengin içerik desteği sağlar ve içindeki [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]denetimlerin çoğu için temel sınıf olarak davranır.  
  
- <xref:System.Windows.Controls.ContentControl>--Bu sınıftan kalıtımla alan sınıfların bazı örnekleri, <xref:System.Windows.Controls.Label> <xref:System.Windows.Controls.Button>ve <xref:System.Windows.Controls.ToolTip>' dir.  
  
- <xref:System.Windows.Controls.ItemsControl>--Bu sınıftan kalıtımla alan sınıfların bazı örnekleri, <xref:System.Windows.Controls.ListBox> <xref:System.Windows.Controls.Menu>ve <xref:System.Windows.Controls.Primitives.StatusBar>' dir.  
  
- <xref:System.Windows.Controls.HeaderedContentControl>--Bu sınıftan kalıtımla alan sınıfların bazı örnekleri, <xref:System.Windows.Controls.TabItem> <xref:System.Windows.Controls.GroupBox>ve <xref:System.Windows.Controls.Expander>' dir.  
  
- <xref:System.Windows.Controls.HeaderedItemsControl>--Bu sınıftan kalıtımla alan sınıfların bazı örnekleri, <xref:System.Windows.Controls.MenuItem> <xref:System.Windows.Controls.TreeViewItem>ve <xref:System.Windows.Controls.ToolBar>' dir.  

 Bu temel sınıflar hakkında daha fazla bilgi için bkz. [WPF Içerik modeli](wpf-content-model.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Stil ve Şablon Oluşturma](styling-and-templating.md)
- [Kategoriye Göre Denetimler](controls-by-category.md)
- [Denetim Kitaplığı](control-library.md)
- [Veri Şablonu Oluşturmaya Genel Bakış](../data/data-templating-overview.md)
- [Veri Bağlamaya Genel Bakış](../data/data-binding-overview.md)
- [Giriş](../advanced/input-wpf.md)
- [Komutu Etkinleştirme](../advanced/how-to-enable-a-command.md)
- [İzlenecek yollar: Özel bir animasyonlu düğme oluşturma](walkthroughs-create-a-custom-animated-button.md)
- [Denetim Özelleştirme](control-customization.md)
