---
title: Denetimler
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
helpviewer_keywords: controls [WPF], about WPF controls
ms.assetid: 3f255a8a-35a8-4712-9065-472ff7d75599
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 66c6cc58423a2af8d0fd6de93b8884918888fb48
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="controls"></a>Denetimler
<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]birçok neredeyse her Windows uygulamasında gibi kullanılan ortak UI bileşenleri ile birlikte gelen <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.TextBox>, <xref:System.Windows.Controls.Menu>, ve <xref:System.Windows.Controls.ListBox>. Tarihsel olarak, bu nesneler için denetimler olarak adlandırılmıştır. Sırada [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] SDK devam geniş bir uygulamada görünür nesneyi temsil eden herhangi bir sınıf anlamına gelir "Denetim" terimini kullanmak bir sınıf devralınmalıdır gerekmez dikkate almak önemlidir <xref:System.Windows.Controls.Control> görünür varlığı için sınıf. Sınıfından devralınan sınıflar <xref:System.Windows.Controls.Control> sınıfı içeren bir <xref:System.Windows.Controls.ControlTemplate>, yeni bir alt sınıf oluşturmak zorunda kalmadan denetimin görünümünü tüketicisinin değiştirmeye tüketici denetimi sağlar.  Bu konuda ele alınmıştır nasıl denetimleri (her iki olanlar devralınan <xref:System.Windows.Controls.Control> sınıfı ve değişmeyen) yaygın olarak kullanılan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  

<a name="creating_an_instance_of_a_control"></a>   
## <a name="creating-an-instance-of-a-control"></a>Bir denetimin örneğini oluşturma  
 Kullanarak bir uygulama için bir denetim ekleyebilirsiniz [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] veya kod.  Aşağıdaki örnek ilk ve son kullanıcıların adı için kullanıcıdan basit bir uygulama oluşturmak nasıl gösterir.  Bu örnekte, altı denetim oluşturur: iki etiket, iki metin kutusu ve buna iki düğme [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Tüm denetimler benzer şekilde oluşturulabilir.  
  
 [!code-xaml[ControlsOverview#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#1)]  
  
 Aşağıdaki örnek kodda aynı uygulama oluşturur. Kısaltma oluşturulmasını <xref:System.Windows.Controls.Grid>, `grid1`, örnekten çıkarılmıştır. `grid1`Önceki gösterildiği gibi aynı sütun ve satır tanımlarına sahip [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] örnek.  
  
 [!code-csharp[ControlsOverview#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#2)]
 [!code-vb[ControlsOverview#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#2)]  
  
<a name="changing_the_appearance_of_a_control"></a>   
## <a name="changing-the-appearance-of-a-control"></a>Bir denetimin görünümünü değiştirme  
 Uygulamanızı Görünüm ve yapısını uyacak şekilde denetiminin görünümünü değiştirmek için yaygın bir durumdur. Bir denetimin görünümünü gerçekleştirmek istediğinize bağlı olarak aşağıdakilerden birini yaparak değiştirebilirsiniz:  
  
-   Denetimin bir özelliğin değerini değiştirin.  
  
-   Oluşturma bir <xref:System.Windows.Style> denetimi için.  
  
-   Yeni bir <xref:System.Windows.Controls.ControlTemplate> denetimi için.  
  
### <a name="changing-a-controls-property-value"></a>Bir denetimin özellik değerini değiştirme  
 Çoğu denetim nasıl denetimi, aşağıdaki gibi görünür değiştirmenize izin özelliklere sahip <xref:System.Windows.Controls.Control.Background%2A> , bir <xref:System.Windows.Controls.Button>. İkisi de değer özelliklerini ayarlayabilirsiniz [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ve kod. Aşağıdaki örnek kümeleri <xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.FontSize%2A>, ve <xref:System.Windows.Controls.Control.FontWeight%2A> özellikleri bir <xref:System.Windows.Controls.Button> içinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 [!code-xaml[ControlsOverview#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#3)]  
  
 Aşağıdaki örnek kodda aynı özelliklerini ayarlar.  
  
 [!code-csharp[ControlsOverview#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#4)]
 [!code-vb[ControlsOverview#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#4)]  
  
### <a name="creating-a-style-for-a-control"></a>Bir denetim için bir stil oluşturma  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]denetimlerin görünümünü oluşturarak uygulamada her bir örnek üzerinde özellikleri ayarlamak yerine tümden belirtme olanağı verir bir <xref:System.Windows.Style>. Aşağıdaki örnekte bir <xref:System.Windows.Style> uygulanan her <xref:System.Windows.Controls.Button> uygulamadaki. <xref:System.Windows.Style>tanımları tanımlanmış genellikle [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] içinde bir <xref:System.Windows.ResourceDictionary>, gibi <xref:System.Windows.FrameworkElement.Resources%2A> özelliği <xref:System.Windows.FrameworkElement>.  
  
 [!code-xaml[ControlsOverview#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#5)]  
  
 Ayrıca bir stil belirli bir türün belirli denetimlerine stil bir anahtar atayarak ve içinde bu anahtarı belirterek uygulayabilirsiniz `Style` denetiminizin özelliği.  Stilleri hakkında daha fazla bilgi için bkz: [stil ve şablon](../../../../docs/framework/wpf/controls/styling-and-templating.md).  
  
### <a name="creating-a-controltemplate"></a>ControlTemplate oluşturma  
 A <xref:System.Windows.Style> özellikleri aynı anda birden çok denetimi ayarlamanıza olanak sağlar, ancak bazen görünümünü özelleştirmek isteyebilirsiniz bir <xref:System.Windows.Controls.Control> oluşturarak neler yapabileceğinizi ötesinde bir <xref:System.Windows.Style>. Sınıfından devralınan sınıflar <xref:System.Windows.Controls.Control> sınıfı bir <xref:System.Windows.Controls.ControlTemplate>, yapı ve görünümünü tanımlayan bir <xref:System.Windows.Controls.Control>. <xref:System.Windows.Controls.Control.Template%2A> Özelliği bir <xref:System.Windows.Controls.Control> , verebilirsiniz için ortaktır bir <xref:System.Windows.Controls.Control> bir <xref:System.Windows.Controls.ControlTemplate> , varsayılandan farklı. Genellikle yeni belirtebilirsiniz <xref:System.Windows.Controls.ControlTemplate> için bir <xref:System.Windows.Controls.Control> görünümünü özelleştirmek için denetimden devralma yerine bir <xref:System.Windows.Controls.Control>.  
  
 Çok yaygın bir denetim göz önünde bulundurun <xref:System.Windows.Controls.Button>.  Birincil davranışını bir <xref:System.Windows.Controls.Button> kullanıcı tıklattığında bazı işlemler yapması bir uygulama sağlamaktır.  Varsayılan olarak, <xref:System.Windows.Controls.Button> içinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yükseltilmiş dikdörtgen gibi görünür.  Bir uygulama geliştirirken davranışını yararlanmak isteyebilirsiniz bir <xref:System.Windows.Controls.Button>--diğer bir deyişle, işleyerek düğme tıklama olayı--ancak ne düğmenin özelliklerini değiştirerek yapabilirsiniz ötesinde düğmenin görünümünü değiştirebilirsiniz.  Bu durumda, yeni bir oluşturabilirsiniz <xref:System.Windows.Controls.ControlTemplate>.  
  
 Aşağıdaki örnekte bir <xref:System.Windows.Controls.ControlTemplate> için bir <xref:System.Windows.Controls.Button>.  <xref:System.Windows.Controls.ControlTemplate> Oluşturur bir <xref:System.Windows.Controls.Button> Yuvarlatılmış köşeleri ve gradyan arka planı ile.  <xref:System.Windows.Controls.ControlTemplate> İçeren bir <xref:System.Windows.Controls.Border> , <xref:System.Windows.Controls.Border.Background%2A> olan bir <xref:System.Windows.Media.LinearGradientBrush> iki <xref:System.Windows.Media.GradientStop> nesneleri.  İlk <xref:System.Windows.Media.GradientStop> bağlamak için veri bağlama kullanır <xref:System.Windows.Media.GradientStop.Color%2A> özelliği <xref:System.Windows.Media.GradientStop> düğmenin arka plan rengi.  Ayarladığınızda <xref:System.Windows.Controls.Control.Background%2A> özelliği <xref:System.Windows.Controls.Button>, ilk bu değer rengini kullanılacak <xref:System.Windows.Media.GradientStop>. Veri bağlama hakkında daha fazla bilgi için bkz: [veri bağlama genel bakış](../../../../docs/framework/wpf/data/data-binding-overview.md). Bu örnek ayrıca oluşturur bir <xref:System.Windows.Trigger> görünümünü değiştirir <xref:System.Windows.Controls.Button> zaman <xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A> olan `true`.  
  
 [!code-xaml[ControlsOverview#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#6)]  
[!code-xaml[ControlsOverview#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#7)]  
  
> [!NOTE]
>  <xref:System.Windows.Controls.Control.Background%2A> Özelliği <xref:System.Windows.Controls.Button> ayarlanmalıdır bir <xref:System.Windows.Media.SolidColorBrush> örneğin düzgün çalışması.  
  
<a name="subscribing_to_events"></a>   
## <a name="subscribing-to-events"></a>Olaylara abone olma  
 Kullanarak bir denetimin olayına abone olabilirsiniz [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] veya kod, ancak yalnızca işleyebilir kodda bir olay.  Aşağıdaki örnekte nasıl abone olunacağı gösterir `Click` olayı bir <xref:System.Windows.Controls.Button>.  
  
 [!code-xaml[ControlsOverview#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#10)]  
  
 [!code-csharp[ControlsOverview#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#8)]
 [!code-vb[ControlsOverview#8](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#8)]  
  
 Aşağıdaki örnek tanıtıcıları `Click` olayı bir <xref:System.Windows.Controls.Button>.  
  
 [!code-csharp[ControlsOverview#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#9)]
 [!code-vb[ControlsOverview#9](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#9)]  
  
<a name="rich_content_in_controls"></a>   
## <a name="rich-content-in-controls"></a>Denetimlerde Zengin İçerik  
 Devralınan çoğu sınıf <xref:System.Windows.Controls.Control> sınıfı zengin içerik içerecek kapasiteye sahip. Örneğin, bir <xref:System.Windows.Controls.Label> bir dize gibi herhangi bir nesne içeren bir <xref:System.Windows.Controls.Image>, veya bir <xref:System.Windows.Controls.Panel>.  Aşağıdaki sınıflar zengin içerik desteği sağlar ve çoğu denetimleri için temel sınıflar olarak davranırlar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
-   <xref:System.Windows.Controls.ContentControl>--Bu sınıftan devralınan sınıfları bazı örnekleri şunlardır <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Button>, ve <xref:System.Windows.Controls.ToolTip>.  
  
-   <xref:System.Windows.Controls.ItemsControl>--Bu sınıftan devralınan sınıfları bazı örnekleri şunlardır <xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.Menu>, ve <xref:System.Windows.Controls.Primitives.StatusBar>.  
  
-   <xref:System.Windows.Controls.HeaderedContentControl>--Bu sınıftan devralınan sınıfları bazı örnekleri şunlardır <xref:System.Windows.Controls.TabItem>, <xref:System.Windows.Controls.GroupBox>, ve <xref:System.Windows.Controls.Expander>.  
  
-   <xref:System.Windows.Controls.HeaderedItemsControl>--Bu sınıftan devralınan sınıfları bazı örnekleri şunlardır <xref:System.Windows.Controls.MenuItem>, <xref:System.Windows.Controls.TreeViewItem>, ve <xref:System.Windows.Controls.ToolBar>.  
  
-  
  
 Temel sınıflar hakkında daha fazla bilgi için bkz: [WPF içerik modeli](../../../../docs/framework/wpf/controls/wpf-content-model.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Stil ve Şablon Oluşturma](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Kategoriye Göre Denetimler](../../../../docs/framework/wpf/controls/controls-by-category.md)  
 [Denetim Kitaplığı](../../../../docs/framework/wpf/controls/control-library.md)  
 [Veri Şablonu Oluşturmaya Genel Bakış](../../../../docs/framework/wpf/data/data-templating-overview.md)  
 [Veri Bağlamaya Genel Bakış](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Giriş](../../../../docs/framework/wpf/advanced/input-wpf.md)  
 [Komutu Etkinleştirme](../../../../docs/framework/wpf/advanced/how-to-enable-a-command.md)  
 [İzlenecek yollar: Özel Animasyonlu Düğme Oluşturma](../../../../docs/framework/wpf/controls/walkthroughs-create-a-custom-animated-button.md)  
 [Denetim Özelleştirme](../../../../docs/framework/wpf/controls/control-customization.md)
