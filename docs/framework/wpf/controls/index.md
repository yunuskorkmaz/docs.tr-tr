---
title: Denetimler
description: Denetimler olarak adlandırılan, ancak Denetim sınıfından devralınabilir olabilecek ortak kullanıcı arabirimi bileşenleri Windows Presentation Foundation hakkında bilgi edinin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], about WPF controls
ms.assetid: 3f255a8a-35a8-4712-9065-472ff7d75599
ms.openlocfilehash: c3d9d3a38cf5f84e21df195e113e264e5a4ac025
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165845"
---
# <a name="controls"></a>Denetimler
<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)],,, ve gibi neredeyse her Windows uygulamasında kullanılan birçok ortak kullanıcı arabirimi bileşeni ile birlikte gönderilir <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.Label> <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.Menu> <xref:System.Windows.Controls.ListBox> . Tarihsel olarak, bu nesneler denetimler olarak adlandırılmıştır. SDK, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir uygulamadaki görünür bir nesneyi temsil eden herhangi bir sınıfı gevşekme etmek için "Control" terimini kullanmaya devam ederken, bir sınıfın <xref:System.Windows.Controls.Control> görünür bir varlığına sahip olacak şekilde sınıftan devralması gerekmediğini unutmayın. Sınıfından kalıtımla alan sınıflar <xref:System.Windows.Controls.Control> <xref:System.Windows.Controls.ControlTemplate> , bir denetimin tüketicisinin yeni bir alt sınıf oluşturmaya gerek kalmadan denetimin görünümünü bir şekilde değiştirmesine izin veren bir içerir.  Bu konuda, denetimlerin (her ikisi de <xref:System.Windows.Controls.Control> sınıfından ve olmayan) yaygın olarak kullanılan denetimlerin nasıl kullanıldığı açıklanmaktadır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] .  

<a name="creating_an_instance_of_a_control"></a>
## <a name="creating-an-instance-of-a-control"></a>Bir denetimin örneğini oluşturma  
 Ya da kodunu kullanarak bir uygulamaya denetim ekleyebilirsiniz [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] .  Aşağıdaki örnek, kullanıcıdan ilk ve son adlarını soran basit bir uygulamanın nasıl oluşturulacağını gösterir.  Bu örnek altı denetim oluşturur: iki etiket, iki metin kutusu ve ' de iki düğme [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] . Tüm denetimler benzer şekilde oluşturulabilir.  
  
 [!code-xaml[ControlsOverview#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#1)]  
  
 Aşağıdaki örnek, kodda aynı uygulamayı oluşturur. Kısaltma için,, öğesinin oluşturulması <xref:System.Windows.Controls.Grid> `grid1` örnekten dışlandı. `grid1`, yukarıdaki örnekte gösterildiği gibi aynı sütun ve satır tanımlarına sahiptir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] .  
  
 [!code-csharp[ControlsOverview#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#2)]
 [!code-vb[ControlsOverview#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#2)]  
  
<a name="changing_the_appearance_of_a_control"></a>
## <a name="changing-the-appearance-of-a-control"></a>Bir denetimin görünümünü değiştirme  
 Bir denetimin görünümünü uygulamanızın görünümüne uyacak şekilde değiştirmek yaygındır. Bir denetimin görünüşünü, gerçekleştirmek istediğiniz seçeneğe bağlı olarak aşağıdakilerden birini yaparak değiştirebilirsiniz:  
  
- Denetimin bir özelliğinin değerini değiştirin.  
  
- <xref:System.Windows.Style>Denetim için oluşturun.  
  
- Denetim için yeni bir oluştur <xref:System.Windows.Controls.ControlTemplate> .  
  
### <a name="changing-a-controls-property-value"></a>Denetimin özellik değerini değiştirme  
 Birçok denetim, içindeki gibi denetimin nasıl göründüğünü değiştirmenize olanak tanıyan özelliklere sahiptir <xref:System.Windows.Controls.Control.Background%2A> <xref:System.Windows.Controls.Button> . Hem hem de kodunda değer özelliklerini ayarlayabilirsiniz [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] . Aşağıdaki örnek, <xref:System.Windows.Controls.Control.Background%2A> <xref:System.Windows.Controls.Control.FontSize%2A> <xref:System.Windows.Controls.Control.FontWeight%2A> içindeki içindeki, ve özelliklerini ayarlar <xref:System.Windows.Controls.Button> [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] .  
  
 [!code-xaml[ControlsOverview#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#3)]  
  
 Aşağıdaki örnek, kodda aynı özellikleri ayarlar.  
  
 [!code-csharp[ControlsOverview#4](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#4)]
 [!code-vb[ControlsOverview#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#4)]  
  
### <a name="creating-a-style-for-a-control"></a>Denetim için stil oluşturma  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], bir oluşturarak, uygulamadaki her bir örnekteki özellikleri ayarlamak yerine toplu olarak denetimlerin görünümünü belirtmenize olanak tanır <xref:System.Windows.Style> . Aşağıdaki örnek, <xref:System.Windows.Style> uygulamasında her birine uygulanan bir oluşturur <xref:System.Windows.Controls.Button> . <xref:System.Windows.Style>tanımlar, genellikle içinde ' ın özelliği gibi tanımlanır [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] <xref:System.Windows.ResourceDictionary> <xref:System.Windows.FrameworkElement.Resources%2A> <xref:System.Windows.FrameworkElement> .  
  
 [!code-xaml[ControlsOverview#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#5)]  
  
 Stile bir anahtar atayarak ve bu anahtarı denetiminizin özelliğinde belirterek belirli bir türün yalnızca belirli denetimlerine bir stil uygulayabilirsiniz `Style` .  Stiller hakkında daha fazla bilgi için bkz. [Stil oluşturma ve şablon](../../../desktop-wpf/fundamentals/styles-templates-overview.md)oluşturma.  
  
### <a name="creating-a-controltemplate"></a>ControlTemplate oluşturma  
 <xref:System.Windows.Style>, Tek seferde birden çok denetim üzerinde özellikler ayarlamanıza olanak tanır, ancak bazen bir oluşturarak, bir ' ı <xref:System.Windows.Controls.Control> oluşturarak yapabileceklerinizi daha fazla özelleştirmek isteyebilirsiniz <xref:System.Windows.Style> . Sınıfından kalıtımla alan sınıflar öğesine <xref:System.Windows.Controls.Control> sahiptir <xref:System.Windows.Controls.ControlTemplate> ve öğesinin yapısını ve görünümünü tanımlar <xref:System.Windows.Controls.Control> . <xref:System.Windows.Controls.Control.Template%2A>Öğesinin özelliği <xref:System.Windows.Controls.Control> geneldir, bu sayede, <xref:System.Windows.Controls.Control> <xref:System.Windows.Controls.ControlTemplate> varsayılandan farklı bir öğesine sahip olabilirsiniz. <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.Control> Görünümünü özelleştirmek için çoğunlukla bir denetimden devralma yerine bir için yeni bir belirleyebilirsiniz <xref:System.Windows.Controls.Control> .  
  
 En yaygın denetimi göz önünde bulundurun <xref:System.Windows.Controls.Button> .  Bir öğesinin birincil davranışı, bir <xref:System.Windows.Controls.Button> uygulamanın kullanıcı tıkladığı zaman bir eylem yapması için bir işlemdir.  Varsayılan olarak, <xref:System.Windows.Controls.Button> içinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir yükseltilmiş dikdörtgen olarak görünür.  Bir uygulama geliştirirken, bir, düğmenin tıklama olayını işleyerek, bir ' ın davranışından faydalanmak isteyebilirsiniz, <xref:System.Windows.Controls.Button> ancak düğmenin özelliklerini değiştirerek düğmenin görünümünü yapabileceklerinizi değiştirmiş olabilirsiniz.  Bu durumda, yeni bir oluşturabilirsiniz <xref:System.Windows.Controls.ControlTemplate> .  
  
 Aşağıdaki örnek <xref:System.Windows.Controls.ControlTemplate> bir için oluşturur <xref:System.Windows.Controls.Button> .  , <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.Button> Yuvarlatılmış köşeler ve gradyan arka planı oluşturur.  , <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.Border> <xref:System.Windows.Controls.Border.Background%2A> <xref:System.Windows.Media.LinearGradientBrush> İki nesnesi olan olan bir içerir <xref:System.Windows.Media.GradientStop> .  İlki <xref:System.Windows.Media.GradientStop> <xref:System.Windows.Media.GradientStop.Color%2A> , öğesinin özelliğini <xref:System.Windows.Media.GradientStop> düğmenin arka planının rengine bağlamak için veri bağlamayı kullanır.  <xref:System.Windows.Controls.Control.Background%2A>Öğesinin özelliğini ayarladığınızda <xref:System.Windows.Controls.Button> , bu değerin rengi ilk olarak kullanılacaktır <xref:System.Windows.Media.GradientStop> . Veri bağlama hakkında daha fazla bilgi için bkz. [veri bağlamaya genel bakış](../../../desktop-wpf/data/data-binding-overview.md). Örnek, öğesinin <xref:System.Windows.Trigger> ne olduğu, görünümünü değiştiren bir de oluşturur <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A> `true` .  
  
 [!code-xaml[ControlsOverview#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#6)]  
[!code-xaml[ControlsOverview#7](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#7)]  
  
> [!NOTE]
> <xref:System.Windows.Controls.Control.Background%2A> <xref:System.Windows.Controls.Button> Örneği düzgün şekilde çalışması için öğesinin özelliği bir olarak ayarlanmalıdır <xref:System.Windows.Media.SolidColorBrush> .  
  
<a name="subscribing_to_events"></a>
## <a name="subscribing-to-events"></a>Olaylara abone olma  
 Ya da kodunu kullanarak bir denetimin olayına abone olabilirsiniz [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , ancak kodda yalnızca bir olayı işleyebilirsiniz.  Aşağıdaki örnek, bir öğesinin olayına nasıl abone olunacağını göstermektedir `Click` <xref:System.Windows.Controls.Button> .  
  
 [!code-xaml[ControlsOverview#10](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#10)]  
  
 [!code-csharp[ControlsOverview#8](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#8)]
 [!code-vb[ControlsOverview#8](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#8)]  
  
 Aşağıdaki örnek, olayını işler `Click` <xref:System.Windows.Controls.Button> .  
  
 [!code-csharp[ControlsOverview#9](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#9)]
 [!code-vb[ControlsOverview#9](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#9)]  
  
<a name="rich_content_in_controls"></a>
## <a name="rich-content-in-controls"></a>Denetimlerde zengin Içerik  
 Sınıfından kalıtımla alan çoğu sınıfın <xref:System.Windows.Controls.Control> , zengin içerik içerme kapasitesi vardır. Örneğin, bir <xref:System.Windows.Controls.Label> dize,, veya gibi herhangi bir nesne içerebilir <xref:System.Windows.Controls.Image> <xref:System.Windows.Controls.Panel> .  Aşağıdaki sınıflar zengin içerik desteği sağlar ve içindeki denetimlerin çoğu için temel sınıf olarak davranır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] .  
  
- <xref:System.Windows.Controls.ContentControl>--Bu sınıftan kalıtımla alan sınıfların bazı örnekleri <xref:System.Windows.Controls.Label> , ve ' dir <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.ToolTip> .  
  
- <xref:System.Windows.Controls.ItemsControl>--Bu sınıftan kalıtımla alan sınıfların bazı örnekleri <xref:System.Windows.Controls.ListBox> , ve ' dir <xref:System.Windows.Controls.Menu> <xref:System.Windows.Controls.Primitives.StatusBar> .  
  
- <xref:System.Windows.Controls.HeaderedContentControl>--Bu sınıftan kalıtımla alan sınıfların bazı örnekleri <xref:System.Windows.Controls.TabItem> , ve ' dir <xref:System.Windows.Controls.GroupBox> <xref:System.Windows.Controls.Expander> .  
  
- <xref:System.Windows.Controls.HeaderedItemsControl>--Bu sınıftan kalıtımla alan sınıfların bazı örnekleri <xref:System.Windows.Controls.MenuItem> , ve ' dir <xref:System.Windows.Controls.TreeViewItem> <xref:System.Windows.Controls.ToolBar> .  

 Bu temel sınıflar hakkında daha fazla bilgi için bkz. [WPF Içerik modeli](wpf-content-model.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Stil ve Şablon Oluşturma](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Kategoriye Göre Denetimler](controls-by-category.md)
- [Denetim Kitaplığı](control-library.md)
- [Veri Şablonu Oluşturmaya Genel Bakış](../data/data-templating-overview.md)
- [Veri Bağlamaya Genel Bakış](../../../desktop-wpf/data/data-binding-overview.md)
- [Girdi](../advanced/input-wpf.md)
- [Komutu Etkinleştirme](../advanced/how-to-enable-a-command.md)
- [İzlenecek yollar: Özel Animasyonlu Düğme Oluşturma](walkthroughs-create-a-custom-animated-button.md)
- [Denetim Özelleştirme](control-customization.md)
