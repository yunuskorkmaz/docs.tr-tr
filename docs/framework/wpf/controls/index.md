---
title: Denetimler
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], about WPF controls
ms.assetid: 3f255a8a-35a8-4712-9065-472ff7d75599
ms.openlocfilehash: f4aeb3dd60186a4060f7825257c7adb274fc8b24
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57363156"
---
# <a name="controls"></a>Denetimler
<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] neredeyse tüm Windows uygulamasında gibi kullanılan ortak bir kullanıcı Arabirimi bileşenleri birçoğu ile birlikte gelen <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.TextBox>, <xref:System.Windows.Controls.Menu>, ve <xref:System.Windows.Controls.ListBox>. Tarihsel olarak, bu nesneler için denetimleri adlandırılmıştır. Sırada [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] SDK devam gevşek bir uygulamada görünür bir nesneyi temsil eden herhangi bir sınıf auto'yu "control" terimini kullanmak bir sınıf devralma gerekmez dikkat edin önemlidir <xref:System.Windows.Controls.Control> görünür varlığı için sınıf. Devralınan sınıflar <xref:System.Windows.Controls.Control> sınıfı içeren bir <xref:System.Windows.Controls.ControlTemplate>, önemli ölçüde yeni bir alt sınıf oluşturmak zorunda kalmadan denetimin görünümünü değiştirmek tüketici bir denetim sağlar.  Bu konuda ele alınmıştır nasıl denetimleri (her iki bu devralınan <xref:System.Windows.Controls.Control> sınıfı ve olmayanlar) yaygın olarak kullanılan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  

<a name="creating_an_instance_of_a_control"></a>   
## <a name="creating-an-instance-of-a-control"></a>Bir denetimin bir örneği oluşturma  
 Kullanarak bir uygulama için bir denetim ekleyebilirsiniz [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] veya kod.  Aşağıdaki örnek, bir kullanıcı için ilk ve son adlarına ister basit bir uygulamanın nasıl oluşturulacağını gösterir.  Bu örnek, altı denetimleri oluşturur: iki etiket, iki metin kutuları ve buna iki düğme [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Tüm denetimleri benzer şekilde oluşturulabilir.  
  
 [!code-xaml[ControlsOverview#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#1)]  
  
 Aşağıdaki örnek aynı uygulama kodunu oluşturur. Kısaltma oluşturulmasını <xref:System.Windows.Controls.Grid>, `grid1`, örnekten çıkarılmıştır. `grid1` Önceki gösterildiği gibi aynı sütun ve satır tanımlarına sahip [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] örnek.  
  
 [!code-csharp[ControlsOverview#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#2)]
 [!code-vb[ControlsOverview#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#2)]  
  
<a name="changing_the_appearance_of_a_control"></a>   
## <a name="changing-the-appearance-of-a-control"></a>Denetiminin görünümünü değiştirme  
 Uygulamanızın Görünüm ve yapısını uyacak şekilde bir denetimin görünümünü değiştirmek için yaygındır. Bir denetimin görünümünü gerçekleştirmek istediğinize bağlı olarak aşağıdakilerden birini yaparak değiştirebilirsiniz:  
  
-   Denetimin bir özelliğine değiştirin.  
  
-   Oluşturma bir <xref:System.Windows.Style> denetimi.  
  
-   Yeni bir <xref:System.Windows.Controls.ControlTemplate> denetimi.  
  
### <a name="changing-a-controls-property-value"></a>Bir denetimin özellik değerini değiştirme  
 Denetim, gibi görüntülenme şeklini değiştirmenize olanak tanıyan özellikler pek çok denetimi olan <xref:System.Windows.Controls.Control.Background%2A> , bir <xref:System.Windows.Controls.Button>. Hem değer özellikleri ayarlayabilirsiniz [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ve kod. Aşağıdaki örnek kümeleri <xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.FontSize%2A>, ve <xref:System.Windows.Controls.Control.FontWeight%2A> özellikleri bir <xref:System.Windows.Controls.Button> içinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 [!code-xaml[ControlsOverview#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#3)]  
  
 Aşağıdaki örnek kodda aynı özelliklerini ayarlar.  
  
 [!code-csharp[ControlsOverview#4](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#4)]
 [!code-vb[ControlsOverview#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#4)]  
  
### <a name="creating-a-style-for-a-control"></a>Bir denetim için stil oluşturma  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimlerin görünümünü tümden oluşturarak uygulamada her örneğinde özellikleri ayarlamak yerine belirtme olanağı sağlar bir <xref:System.Windows.Style>. Aşağıdaki örnek, oluşturur bir <xref:System.Windows.Style> uygulanan her <xref:System.Windows.Controls.Button> uygulama. <xref:System.Windows.Style> tanımları tanımlanmış genellikle [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] içinde bir <xref:System.Windows.ResourceDictionary>, gibi <xref:System.Windows.FrameworkElement.Resources%2A> özelliği <xref:System.Windows.FrameworkElement>.  
  
 [!code-xaml[ControlsOverview#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#5)]  
  
 Ayrıca bir stil belirli bir türdeki belirli denetimler stili için bir anahtar atama ve bu anahtar belirterek uygulayabilirsiniz `Style` denetiminizin özelliği.  Stilleri hakkında daha fazla bilgi için bkz. [stil ve şablon oluşturma](styling-and-templating.md).  
  
### <a name="creating-a-controltemplate"></a>ControlTemplate oluşturarak  
 A <xref:System.Windows.Style> özellikleri aynı anda birden çok denetim üzerinde ayarlamanıza olanak tanır, ancak bazen görünümünü özelleştirmek isteyebilirsiniz bir <xref:System.Windows.Controls.Control> oluşturarak yapabileceklerinizin bir <xref:System.Windows.Style>. Devralınan sınıflar <xref:System.Windows.Controls.Control> sınıfı bir <xref:System.Windows.Controls.ControlTemplate>, yapı ve görünümünü tanımlayan bir <xref:System.Windows.Controls.Control>. <xref:System.Windows.Controls.Control.Template%2A> Özelliği bir <xref:System.Windows.Controls.Control> , verebilir böylece geneldir bir <xref:System.Windows.Controls.Control> bir <xref:System.Windows.Controls.ControlTemplate> varsayılan farklı. Genellikle yeni bir belirtebilirsiniz <xref:System.Windows.Controls.ControlTemplate> için bir <xref:System.Windows.Controls.Control> görünümünü özelleştirmek için bir denetimden devralan yerine bir <xref:System.Windows.Controls.Control>.  
  
 Çok yaygın bir denetim göz önünde bulundurun <xref:System.Windows.Controls.Button>.  Birincil davranışını bir <xref:System.Windows.Controls.Button> kullanıcı tıkladığında bazı işlemler yapması bir uygulama etkinleştirmektir.  Varsayılan olarak, <xref:System.Windows.Controls.Button> içinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yükseltilmiş bir dikdörtgen gibi görünür.  Bir uygulama geliştirirken, davranışını yararlanmak isteyebilirsiniz bir <xref:System.Windows.Controls.Button>--yani işleyerek düğme tıklatma olayını ancak düğmenin özelliklerini değiştirerek yapabileceklerinizin düğmenin görünümünü değişebilir.  Bu durumda, yeni bir oluşturabilirsiniz <xref:System.Windows.Controls.ControlTemplate>.  
  
 Aşağıdaki örnek, oluşturur bir <xref:System.Windows.Controls.ControlTemplate> için bir <xref:System.Windows.Controls.Button>.  <xref:System.Windows.Controls.ControlTemplate> Oluşturur bir <xref:System.Windows.Controls.Button> yuvarlatılmış köşeler ve arka plan gradyan ile.  <xref:System.Windows.Controls.ControlTemplate> İçeren bir <xref:System.Windows.Controls.Border> olan <xref:System.Windows.Controls.Border.Background%2A> olduğu bir <xref:System.Windows.Media.LinearGradientBrush> iki <xref:System.Windows.Media.GradientStop> nesneleri.  İlk <xref:System.Windows.Media.GradientStop> bağlamak için veri bağlama kullanır <xref:System.Windows.Media.GradientStop.Color%2A> özelliği <xref:System.Windows.Media.GradientStop> için düğmenin arka plan rengi.  Ayarladığınızda <xref:System.Windows.Controls.Control.Background%2A> özelliği <xref:System.Windows.Controls.Button>, ilk bu değer rengi kullanılacak <xref:System.Windows.Media.GradientStop>. Veri bağlama hakkında daha fazla bilgi için bkz. [Data Binding Overview](../data/data-binding-overview.md). Bu örnek ayrıca oluşturur bir <xref:System.Windows.Trigger> görünümünü değiştirir <xref:System.Windows.Controls.Button> olduğunda <xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A> olduğu `true`.  
  
 [!code-xaml[ControlsOverview#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#6)]  
[!code-xaml[ControlsOverview#7](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#7)]  
  
> [!NOTE]
>  <xref:System.Windows.Controls.Control.Background%2A> Özelliği <xref:System.Windows.Controls.Button> ayarlanmalıdır bir <xref:System.Windows.Media.SolidColorBrush> örneğin düzgün çalışması.  
  
<a name="subscribing_to_events"></a>   
## <a name="subscribing-to-events"></a>Olaylara abone olma  
 Kullanarak, bir denetimin olayına abone olabilirsiniz [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] veya kod, ancak yalnızca işleyebilir kodda bir olay.  Aşağıdaki örnek nasıl abone olunacağı gösterilmektedir `Click` olayı bir <xref:System.Windows.Controls.Button>.  
  
 [!code-xaml[ControlsOverview#10](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#10)]  
  
 [!code-csharp[ControlsOverview#8](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#8)]
 [!code-vb[ControlsOverview#8](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#8)]  
  
 Aşağıdaki örnek tutamaçları `Click` olayı bir <xref:System.Windows.Controls.Button>.  
  
 [!code-csharp[ControlsOverview#9](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#9)]
 [!code-vb[ControlsOverview#9](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#9)]  
  
<a name="rich_content_in_controls"></a>   
## <a name="rich-content-in-controls"></a>Zengin içerik denetimlerinde  
 Devralınan çoğu sınıf <xref:System.Windows.Controls.Control> sınıfı zengin içerik içerecek kapasiteye sahip. Örneğin, bir <xref:System.Windows.Controls.Label> bir dize gibi herhangi bir nesne içerebilir bir <xref:System.Windows.Controls.Image>, veya bir <xref:System.Windows.Controls.Panel>.  Aşağıdaki sınıflar çoğu denetimleri için temel sınıflar görür ve destek sağlamak için zengin içerik [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
-   <xref:System.Windows.Controls.ContentControl>--Bu sınıftan devralınan sınıflar bazı örnekleri şunlardır <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Button>, ve <xref:System.Windows.Controls.ToolTip>.  
  
-   <xref:System.Windows.Controls.ItemsControl>--Bu sınıftan devralınan sınıflar bazı örnekleri şunlardır <xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.Menu>, ve <xref:System.Windows.Controls.Primitives.StatusBar>.  
  
-   <xref:System.Windows.Controls.HeaderedContentControl>--Bu sınıftan devralınan sınıflar bazı örnekleri şunlardır <xref:System.Windows.Controls.TabItem>, <xref:System.Windows.Controls.GroupBox>, ve <xref:System.Windows.Controls.Expander>.  
  
-   <xref:System.Windows.Controls.HeaderedItemsControl>--Bu sınıftan devralınan sınıflar bazı örnekleri şunlardır <xref:System.Windows.Controls.MenuItem>, <xref:System.Windows.Controls.TreeViewItem>, ve <xref:System.Windows.Controls.ToolBar>.  

  
 Temel sınıflar hakkında daha fazla bilgi için bkz: [WPF içerik modeli](wpf-content-model.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Stil ve Şablon Oluşturma](styling-and-templating.md)
- [Kategoriye Göre Denetimler](controls-by-category.md)
- [Denetim Kitaplığı](control-library.md)
- [Veri Şablonu Oluşturmaya Genel Bakış](../data/data-templating-overview.md)
- [Veri Bağlamaya Genel Bakış](../data/data-binding-overview.md)
- [Giriş](../advanced/input-wpf.md)
- [Komutu Etkinleştirme](../advanced/how-to-enable-a-command.md)
- [İzlenecek yollar: Özel Animasyonlu Düğme oluşturma](walkthroughs-create-a-custom-animated-button.md)
- [Denetim Özelleştirme](control-customization.md)
