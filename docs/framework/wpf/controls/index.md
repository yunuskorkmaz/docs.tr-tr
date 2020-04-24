---
title: Denetimler
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], about WPF controls
ms.assetid: 3f255a8a-35a8-4712-9065-472ff7d75599
ms.openlocfilehash: 2aab0fc8adaf17a8e9820a6269a740ef09540cda
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646480"
---
# <a name="controls"></a>Denetimler
<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]gibi hemen hemen her Windows uygulamasında kullanılan ortak Kullanıcı Arabirimi <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.Label>bileşenlerinin çoğuile gemiler, , <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.Menu>, , ve <xref:System.Windows.Controls.ListBox>. Tarihsel olarak, bu nesnelere denetimler olarak adlandırılır. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] SDK, bir uygulamada görünür bir nesneyi temsil eden herhangi bir sınıfı gevşek bir şekilde ifade etmek için "denetim" terimini <xref:System.Windows.Controls.Control> kullanmaya devam ederken, bir sınıfın görünür bir varlığa sahip olması için sınıftan devralmasına gerek olmadığını belirtmek önemlidir. <xref:System.Windows.Controls.Control> Sınıftan devralan sınıflar, <xref:System.Windows.Controls.ControlTemplate>bir denetimin tüketicisinin yeni bir alt sınıf oluşturmak zorunda kalmadan denetimin görünümünü kökten değiştirmesine olanak tanıyan bir sınıf içerir.  Bu konu, denetimlerin <xref:System.Windows.Controls.Control> (hem sınıftan devralanlar hem de devralınmayanlar) [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]'da nasıl kullanıldığını) açıklar.  

<a name="creating_an_instance_of_a_control"></a>
## <a name="creating-an-instance-of-a-control"></a>Denetim Örneği Oluşturma  
 Bir uygulama için bir denetim [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ya da kod kullanarak ekleyebilirsiniz.  Aşağıdaki örnek, kullanıcıdan ad ve soyadlarını soran basit bir uygulamanın nasıl oluşturulacağını gösterir.  Bu örnekte altı denetim oluşturulur: iki etiket, iki metin [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]kutusu ve iki düğme. Tüm denetimler benzer şekilde oluşturulabilir.  
  
 [!code-xaml[ControlsOverview#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#1)]  
  
 Aşağıdaki örnekkod aynı uygulamayı oluşturur. Kısaltma için, <xref:System.Windows.Controls.Grid>, , `grid1`oluşturulması , örnek dışında tutulmuştür. `grid1`önceki [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] örnekte gösterildiği gibi aynı sütun ve satır tanımları vardır.  
  
 [!code-csharp[ControlsOverview#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#2)]
 [!code-vb[ControlsOverview#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#2)]  
  
<a name="changing_the_appearance_of_a_control"></a>
## <a name="changing-the-appearance-of-a-control"></a>Denetimin Görünümünü Değiştirme  
 Uygulamanızın görünümüne ve hissine uyacak şekilde bir denetimin görünümünü değiştirmek yaygındır. Gerçekleştirmek istediğiniz şeye bağlı olarak aşağıdakilerden birini yaparak denetimin görünümünü değiştirebilirsiniz:  
  
- Denetimin özelliğinin değerini değiştirin.  
  
- Denetim <xref:System.Windows.Style> için bir oluştur.  
  
- Denetim için <xref:System.Windows.Controls.ControlTemplate> yeni bir oluştur.  
  
### <a name="changing-a-controls-property-value"></a>Denetimin Özellik Değerini Değiştirme  
 Birçok denetim, denetimin nasıl göründüğünü değiştirmenize olanak tanıyan <xref:System.Windows.Controls.Control.Background%2A> özelliklere <xref:System.Windows.Controls.Button>sahiptir ( Hem de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] koddaki değer özelliklerini ayarlayabilirsiniz. Aşağıdaki örnekte <xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.FontSize%2A>ve <xref:System.Windows.Controls.Control.FontWeight%2A> özellikleri <xref:System.Windows.Controls.Button> bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]in'de ayarlar.  
  
 [!code-xaml[ControlsOverview#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#3)]  
  
 Aşağıdaki örnekkodaynı özellikleri ayarlar.  
  
 [!code-csharp[ControlsOverview#4](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#4)]
 [!code-vb[ControlsOverview#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#4)]  
  
### <a name="creating-a-style-for-a-control"></a>Denetim için Stil Oluşturma  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]bir <xref:System.Windows.Style>. oluşturarak, uygulamadaki her örnekte özellikleri ayarlamak yerine denetimlerin görünümünü toptan belirtme olanağı sağlar. Aşağıdaki örnek, uygulamadaki her <xref:System.Windows.Style> <xref:System.Windows.Controls.Button> birine uygulanan bir örnek oluşturur. <xref:System.Windows.Style>[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] tanımlar genellikle <xref:System.Windows.ResourceDictionary>bir , örneğin <xref:System.Windows.FrameworkElement.Resources%2A> bir tanımlanır . <xref:System.Windows.FrameworkElement>  
  
 [!code-xaml[ControlsOverview#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#5)]  
  
 Ayrıca, stiliçin bir anahtar atayarak ve denetiminizin `Style` özelliğinde bu anahtarı belirterek yalnızca belirli bir türün belirli denetimlerine stil uygulayabilirsiniz.  Stiller hakkında daha fazla bilgi için [Stil ve Templating'e](../../../desktop-wpf/fundamentals/styles-templates-overview.md)bakın.  
  
### <a name="creating-a-controltemplate"></a>Denetim Şablonu Oluşturma  
 A, <xref:System.Windows.Style> aynı anda birden çok denetimde özellikleri ayarlamanızı sağlar, ancak <xref:System.Windows.Controls.Control> bazen bir <xref:System.Windows.Style>. Sınıftan <xref:System.Windows.Controls.Control> devralan sınıfların <xref:System.Windows.Controls.ControlTemplate>yapısı ve görünümünü tanımlayan bir <xref:System.Windows.Controls.Control>, . A'nın <xref:System.Windows.Controls.Control.Template%2A> <xref:System.Windows.Controls.Control> özelliği herkese açıktır, bu <xref:System.Windows.Controls.Control> <xref:System.Windows.Controls.ControlTemplate> nedenle bir a'yı varsayılanından farklı bir özellik verebilirsiniz. Genellikle bir denetim <xref:System.Windows.Controls.ControlTemplate> görünümünü <xref:System.Windows.Controls.Control> özelleştirmek için bir denetim devralma yerine yeni <xref:System.Windows.Controls.Control>belirtebilirsiniz .  
  
 Çok yaygın kontrolü <xref:System.Windows.Controls.Button>göz önünde bulundurun.  A'nın birincil <xref:System.Windows.Controls.Button> davranışı, kullanıcı tıklattığında bir uygulamanın bazı eylemlerde durmasını sağlamaktır.  Varsayılan olarak, <xref:System.Windows.Controls.Button> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] in yükseltilmiş bir dikdörtgen olarak görünür.  Bir uygulama geliştirirken, düğmenin tıklama olayını ele <xref:System.Windows.Controls.Button>alarak bir uygulamanın davranışından yararlanmak isteyebilirsiniz, ancak düğmenin özelliklerini değiştirerek düğmenin görünümünü değiştirebilirsiniz.  Bu durumda, yeni <xref:System.Windows.Controls.ControlTemplate>bir .  
  
 Aşağıdaki örnek için <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.Button>bir .  Yuvarlak <xref:System.Windows.Controls.ControlTemplate> köşeleri <xref:System.Windows.Controls.Button> ve degrade arka plan ile oluşturur.  İki <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.Border> <xref:System.Windows.Media.GradientStop> nesneile <xref:System.Windows.Controls.Border.Background%2A> a <xref:System.Windows.Media.LinearGradientBrush> olan içerir.  İlk <xref:System.Windows.Media.GradientStop> olarak, düğmenin <xref:System.Windows.Media.GradientStop.Color%2A> arka planının <xref:System.Windows.Media.GradientStop> rengine özelliğini bağlamak için veri bağlama kullanır.  <xref:System.Windows.Controls.Control.Background%2A> Özelliğini <xref:System.Windows.Controls.Button>ayarladığınızda, bu değerin rengi ilk <xref:System.Windows.Media.GradientStop>olarak kullanılacaktır. Veri bağlama hakkında daha fazla bilgi için [bkz.](../../../desktop-wpf/data/data-binding-overview.md) <xref:System.Windows.Trigger> Örnek, <xref:System.Windows.Controls.Button> ne zaman <xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A> görünümünü değiştiren bir de `true`oluşturur.  
  
 [!code-xaml[ControlsOverview#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#6)]  
[!code-xaml[ControlsOverview#7](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#7)]  
  
> [!NOTE]
> Düzgün <xref:System.Windows.Controls.Control.Background%2A> çalışması <xref:System.Windows.Controls.Button> için örneğin özelliği <xref:System.Windows.Media.SolidColorBrush> a olarak ayarlanmalıdır.  
  
<a name="subscribing_to_events"></a>
## <a name="subscribing-to-events"></a>Etkinliklere Abone Olma  
 Bir denetimin olayına ya da [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kodu kullanarak abone olabilirsiniz, ancak bir olayı yalnızca kod olarak işleyebilirsiniz.  Aşağıdaki örnekte, `Click` bir <xref:System.Windows.Controls.Button>.  
  
 [!code-xaml[ControlsOverview#10](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#10)]  
  
 [!code-csharp[ControlsOverview#8](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#8)]
 [!code-vb[ControlsOverview#8](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#8)]  
  
 Aşağıdaki örnekte bir `Click` <xref:System.Windows.Controls.Button>. olayını işler  
  
 [!code-csharp[ControlsOverview#9](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#9)]
 [!code-vb[ControlsOverview#9](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#9)]  
  
<a name="rich_content_in_controls"></a>
## <a name="rich-content-in-controls"></a>Denetimlerde Zengin İçerik  
 <xref:System.Windows.Controls.Control> Sınıftan devralan çoğu sınıf zengin içerik içerme kapasitesine sahiptir. Örneğin, bir <xref:System.Windows.Controls.Label> dize, bir <xref:System.Windows.Controls.Image>, veya bir . <xref:System.Windows.Controls.Panel>gibi herhangi bir nesne içerebilir.  Aşağıdaki sınıflar zengin içerik için destek sağlar ve 'deki [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]denetimlerin çoğu için temel sınıflar olarak hareket eder.  
  
- <xref:System.Windows.Controls.ContentControl>-- Bu sınıftan devralan bazı <xref:System.Windows.Controls.Label> <xref:System.Windows.Controls.Button>sınıflara <xref:System.Windows.Controls.ToolTip>örnekler , , ve .  
  
- <xref:System.Windows.Controls.ItemsControl>-- Bu sınıftan devralan bazı <xref:System.Windows.Controls.ListBox> <xref:System.Windows.Controls.Menu>sınıflara <xref:System.Windows.Controls.Primitives.StatusBar>örnekler , , ve .  
  
- <xref:System.Windows.Controls.HeaderedContentControl>-- Bu sınıftan devralan bazı <xref:System.Windows.Controls.TabItem> <xref:System.Windows.Controls.GroupBox>sınıflara <xref:System.Windows.Controls.Expander>örnekler , , ve .  
  
- <xref:System.Windows.Controls.HeaderedItemsControl>--Bu sınıftan devralan bazı <xref:System.Windows.Controls.MenuItem>sınıflara örnekler , , <xref:System.Windows.Controls.TreeViewItem>ve <xref:System.Windows.Controls.ToolBar>.  

 Bu temel sınıflar hakkında daha fazla bilgi için [WPF İçerik Modeli'ne](wpf-content-model.md)bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Stil ve Şablon Oluşturma](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Kategoriye Göre Denetimler](controls-by-category.md)
- [Denetim Kitaplığı](control-library.md)
- [Veri Şablonu Oluşturmaya Genel Bakış](../data/data-templating-overview.md)
- [Veri Bağlama Genel Bakış](../../../desktop-wpf/data/data-binding-overview.md)
- [Giriş](../advanced/input-wpf.md)
- [Komutu Etkinleştirme](../advanced/how-to-enable-a-command.md)
- [İzlenecek yollar: Özel Animasyonlu Düğme Oluşturma](walkthroughs-create-a-custom-animated-button.md)
- [Denetim Özelleştirme](control-customization.md)
