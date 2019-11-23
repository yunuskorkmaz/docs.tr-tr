---
title: Denetimler
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], about WPF controls
ms.assetid: 3f255a8a-35a8-4712-9065-472ff7d75599
ms.openlocfilehash: 42596c8adf1b8b27f250fa7a3cf6cc173a63e2eb
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459453"
---
# <a name="controls"></a>Denetimler
<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], neredeyse her Windows uygulamasında kullanılan <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.TextBox>, <xref:System.Windows.Controls.Menu>ve <xref:System.Windows.Controls.ListBox>gibi birçok ortak kullanıcı arabirimi bileşeni ile birlikte gelir. Tarihsel olarak, bu nesneler denetimler olarak adlandırılmıştır. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] SDK, bir uygulamadaki görünür bir nesneyi temsil eden herhangi bir sınıfı gevşekme etmek için "Control" terimini kullanmaya devam ederken, bir sınıfın görünür bir varlığına sahip olmak için <xref:System.Windows.Controls.Control> sınıfından devralması gerekmediğini unutmayın. <xref:System.Windows.Controls.Control> sınıfından kalıtımla alan sınıflar, bir denetimin tüketicisinin yeni bir alt sınıf oluşturmaya gerek kalmadan denetimin görünümünü bir şekilde değiştirmesine izin veren bir <xref:System.Windows.Controls.ControlTemplate>içerir.  Bu konuda, denetimlerin (hem <xref:System.Windows.Controls.Control> sınıfından, hem de olmayanlar) [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]yaygın olarak kullanıldığı denetimlerin (her ikisi de) açıklanmaktadır.  

<a name="creating_an_instance_of_a_control"></a>   
## <a name="creating-an-instance-of-a-control"></a>Bir denetimin örneğini oluşturma  
 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] veya kodu kullanarak uygulamaya bir denetim ekleyebilirsiniz.  Aşağıdaki örnek, kullanıcıdan ilk ve son adlarını soran basit bir uygulamanın nasıl oluşturulacağını gösterir.  Bu örnek altı denetim oluşturur: iki etiket, iki metin kutusu ve iki düğme, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Tüm denetimler benzer şekilde oluşturulabilir.  
  
 [!code-xaml[ControlsOverview#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#1)]  
  
 Aşağıdaki örnek, kodda aynı uygulamayı oluşturur. Kısaltma için, <xref:System.Windows.Controls.Grid>`grid1`oluşturma, örnekten dışlandı. `grid1`, önceki [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] örneğinde gösterildiği gibi aynı sütun ve satır tanımlarına sahiptir.  
  
 [!code-csharp[ControlsOverview#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#2)]
 [!code-vb[ControlsOverview#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#2)]  
  
<a name="changing_the_appearance_of_a_control"></a>   
## <a name="changing-the-appearance-of-a-control"></a>Bir denetimin görünümünü değiştirme  
 Bir denetimin görünümünü uygulamanızın görünümüne uyacak şekilde değiştirmek yaygındır. Bir denetimin görünüşünü, gerçekleştirmek istediğiniz seçeneğe bağlı olarak aşağıdakilerden birini yaparak değiştirebilirsiniz:  
  
- Denetimin bir özelliğinin değerini değiştirin.  
  
- Denetim için bir <xref:System.Windows.Style> oluşturun.  
  
- Denetim için yeni bir <xref:System.Windows.Controls.ControlTemplate> oluşturun.  
  
### <a name="changing-a-controls-property-value"></a>Denetimin özellik değerini değiştirme  
 Birçok denetimin, bir <xref:System.Windows.Controls.Button><xref:System.Windows.Controls.Control.Background%2A> gibi, denetimin görünümünü değiştirmenize olanak tanıyan özellikler vardır. Değer özelliklerini hem [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] hem de kodda ayarlayabilirsiniz. Aşağıdaki örnek, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]bir <xref:System.Windows.Controls.Button> üzerinde <xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.FontSize%2A>ve <xref:System.Windows.Controls.Control.FontWeight%2A> özelliklerini ayarlar.  
  
 [!code-xaml[ControlsOverview#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#3)]  
  
 Aşağıdaki örnek, kodda aynı özellikleri ayarlar.  
  
 [!code-csharp[ControlsOverview#4](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#4)]
 [!code-vb[ControlsOverview#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#4)]  
  
### <a name="creating-a-style-for-a-control"></a>Denetim için stil oluşturma  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], bir <xref:System.Windows.Style>oluşturarak uygulamadaki her bir örnekteki özellikleri ayarlamak yerine, denetimlerin toptan görünümünü belirtme olanağı sağlar. Aşağıdaki örnek, uygulamadaki her bir <xref:System.Windows.Controls.Button> uygulanan bir <xref:System.Windows.Style> oluşturur. <xref:System.Windows.Style> tanımları, genellikle <xref:System.Windows.FrameworkElement><xref:System.Windows.FrameworkElement.Resources%2A> özelliği gibi bir <xref:System.Windows.ResourceDictionary>[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] tanımlanmıştır.  
  
 [!code-xaml[ControlsOverview#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#5)]  
  
 Ayrıca, stile bir anahtar atayarak ve bu anahtarı denetiminizin `Style` özelliğinde belirterek belirli bir türün yalnızca belirli denetimlerine bir stil uygulayabilirsiniz.  Stiller hakkında daha fazla bilgi için bkz. [Stil oluşturma ve şablon](styling-and-templating.md)oluşturma.  
  
### <a name="creating-a-controltemplate"></a>ControlTemplate oluşturarak  
 <xref:System.Windows.Style>, tek seferde birden çok denetim üzerinde özellikler ayarlamanıza olanak tanır, ancak bazen bir <xref:System.Windows.Style>oluşturarak yapabileceklerinizin ötesinde bir <xref:System.Windows.Controls.Control> görünümünü özelleştirmek isteyebilirsiniz. <xref:System.Windows.Controls.Control> sınıfından kalıtımla alan sınıfların bir <xref:System.Windows.Controls.Control>yapısını ve görünümünü tanımlayan bir <xref:System.Windows.Controls.ControlTemplate>vardır. Bir <xref:System.Windows.Controls.Control> <xref:System.Windows.Controls.Control.Template%2A> özelliği geneldir, bu sayede varsayılandan farklı bir <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.Control> sağlayabilirsiniz. Bir <xref:System.Windows.Controls.Control>görünümünü özelleştirmek için bir denetimden devralma yerine, genellikle bir <xref:System.Windows.Controls.Control> için yeni bir <xref:System.Windows.Controls.ControlTemplate> belirtebilirsiniz.  
  
 <xref:System.Windows.Controls.Button>en yaygın denetimi göz önünde bulundurun.  Bir <xref:System.Windows.Controls.Button> birincil davranışı, bir uygulamanın kullanıcı tıkladığı zaman bir eylem yapması olanaklı hale gelir.  Varsayılan olarak, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Button> yükseltilmiş dikdörtgen olarak görünür.  Bir uygulama geliştirirken, düğmenin tıklama olayını işleyerek bir <xref:System.Windows.Controls.Button>davranışından faydalanmak isteyebilirsiniz, ancak düğmenin özelliklerini değiştirerek düğmenin görünümünü yapabileceklerinizi aşabilirsiniz. bu işlemi yapabilirsiniz.  Bu durumda, yeni bir <xref:System.Windows.Controls.ControlTemplate>oluşturabilirsiniz.  
  
 Aşağıdaki örnek bir <xref:System.Windows.Controls.Button>için <xref:System.Windows.Controls.ControlTemplate> oluşturur.  <xref:System.Windows.Controls.ControlTemplate>, yuvarlatılmış köşeler ve gradyan arka planına sahip bir <xref:System.Windows.Controls.Button> oluşturur.  <xref:System.Windows.Controls.ControlTemplate>, <xref:System.Windows.Controls.Border.Background%2A> iki <xref:System.Windows.Media.GradientStop> nesnesine sahip <xref:System.Windows.Media.LinearGradientBrush> olan bir <xref:System.Windows.Controls.Border> içerir.  İlk <xref:System.Windows.Media.GradientStop>, <xref:System.Windows.Media.GradientStop> <xref:System.Windows.Media.GradientStop.Color%2A> özelliğini düğmenin arka planının rengine bağlamak için veri bağlamayı kullanır.  <xref:System.Windows.Controls.Button><xref:System.Windows.Controls.Control.Background%2A> özelliğini ayarladığınızda, bu değerin rengi ilk <xref:System.Windows.Media.GradientStop>olarak kullanılacaktır. Veri bağlama hakkında daha fazla bilgi için bkz. [veri bağlamaya genel bakış](../../../desktop-wpf/data/data-binding-overview.md). Örnek ayrıca <xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A> `true`olduğunda <xref:System.Windows.Controls.Button> görünümünü değiştiren bir <xref:System.Windows.Trigger> oluşturur.  
  
 [!code-xaml[ControlsOverview#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#6)]  
[!code-xaml[ControlsOverview#7](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#7)]  
  
> [!NOTE]
> Örneğin düzgün çalışması için <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.Control.Background%2A> özelliği bir <xref:System.Windows.Media.SolidColorBrush> olarak ayarlanmalıdır.  
  
<a name="subscribing_to_events"></a>   
## <a name="subscribing-to-events"></a>Olaylara abone olma  
 Bir denetimin olayına [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] veya kodu kullanarak abone olabilirsiniz, ancak kodda yalnızca bir olayı işleyebilirsiniz.  Aşağıdaki örnekte, bir <xref:System.Windows.Controls.Button>`Click` olayına nasıl abone olunacağı gösterilmektedir.  
  
 [!code-xaml[ControlsOverview#10](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#10)]  
  
 [!code-csharp[ControlsOverview#8](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#8)]
 [!code-vb[ControlsOverview#8](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#8)]  
  
 Aşağıdaki örnek, bir <xref:System.Windows.Controls.Button>`Click` olayını işler.  
  
 [!code-csharp[ControlsOverview#9](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#9)]
 [!code-vb[ControlsOverview#9](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#9)]  
  
<a name="rich_content_in_controls"></a>   
## <a name="rich-content-in-controls"></a>Denetimlerde zengin Içerik  
 <xref:System.Windows.Controls.Control> sınıfından kalıtımla alan çoğu sınıfın, zengin içerik içerme kapasitesi vardır. Örneğin, bir <xref:System.Windows.Controls.Label> dize, <xref:System.Windows.Controls.Image>veya <xref:System.Windows.Controls.Panel>gibi herhangi bir nesne içerebilir.  Aşağıdaki sınıflar zengin içerik desteği sağlar ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]içindeki denetimlerin çoğu için temel sınıf olarak davranır.  
  
- <xref:System.Windows.Controls.ContentControl>--bu sınıftan kalıtımla alan sınıfların bazı örnekleri <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Button>ve <xref:System.Windows.Controls.ToolTip>.  
  
- <xref:System.Windows.Controls.ItemsControl>--bu sınıftan kalıtımla alan sınıfların bazı örnekleri <xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.Menu>ve <xref:System.Windows.Controls.Primitives.StatusBar>.  
  
- <xref:System.Windows.Controls.HeaderedContentControl>--bu sınıftan kalıtımla alan sınıfların bazı örnekleri <xref:System.Windows.Controls.TabItem>, <xref:System.Windows.Controls.GroupBox>ve <xref:System.Windows.Controls.Expander>.  
  
- <xref:System.Windows.Controls.HeaderedItemsControl>--bu sınıftan kalıtımla alan sınıfların bazı örnekleri <xref:System.Windows.Controls.MenuItem>, <xref:System.Windows.Controls.TreeViewItem>ve <xref:System.Windows.Controls.ToolBar>.  

 Bu temel sınıflar hakkında daha fazla bilgi için bkz. [WPF Içerik modeli](wpf-content-model.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Stil ve Şablon Oluşturma](styling-and-templating.md)
- [Kategoriye Göre Denetimler](controls-by-category.md)
- [Denetim Kitaplığı](control-library.md)
- [Veri Şablonu Oluşturmaya Genel Bakış](../data/data-templating-overview.md)
- [Veri Bağlamaya Genel Bakış](../../../desktop-wpf/data/data-binding-overview.md)
- [Girdi](../advanced/input-wpf.md)
- [Komutu Etkinleştirme](../advanced/how-to-enable-a-command.md)
- [İzlenecek yollar: Özel Animasyonlu Düğme Oluşturma](walkthroughs-create-a-custom-animated-button.md)
- [Denetim Özelleştirme](control-customization.md)
