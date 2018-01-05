---
title: "Hizalama, Kenar Boşlukları ve Doldurmaya Genel Bakış"
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
- cpp
helpviewer_keywords:
- margins [WPF]
- padding [WPF]
- aligning [WPF]
ms.assetid: 9c6a2009-9b86-4e40-8605-0a2664dc3973
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9d53ec57bdd6126aa1b82e3fa34d01b8907ca169
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="alignment-margins-and-padding-overview"></a>Hizalama, Kenar Boşlukları ve Doldurmaya Genel Bakış
<xref:System.Windows.FrameworkElement> Sınıfı tam olarak alt öğeleri konumlandırmak için kullanılan çeşitli özellikler sunar. Bu konuda en önemli özelliklerinin dördünü ele alınmıştır: <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, <xref:System.Windows.FrameworkElement.Margin%2A>, <xref:System.Windows.Controls.Border.Padding%2A>, ve <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>. Öğelerin konumlarını denetlemek için temel sağladıkları için bu özelliklerin etkilerini anlamak önemli olan [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] uygulamalar.  
  
  
<a name="wcpsdk_layout_amp_introduction"></a>   
## <a name="introduction-to-element-positioning"></a>Öğe konumlandırmaya giriş  
 Kullanarak öğeleri yerleştirmek için çok çeşitli yollar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Ancak, ideal düzeni sağlamak yalnızca sağa seçmenin ötesine geçer <xref:System.Windows.Controls.Panel> öğesi. Konumlandırmanın daha iyi denetim gerektiren bir anlayış <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, <xref:System.Windows.FrameworkElement.Margin%2A>, <xref:System.Windows.Controls.Border.Padding%2A>, ve <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> özellikleri.  
  
 Aşağıdaki çizim birkaç konumlandırma özelliklerini kullanan bir düzen senaryosunu gösterir.  
  
 ![WPF özellikleri örnek konumlandırma](../../../../docs/framework/wpf/advanced/media/layout-margins-padding-alignment-graphic1.PNG "layout_margins_padding_alignment_graphic1")  
  
 İlk bakışta, <xref:System.Windows.Controls.Button> Bu çizim öğeleri rasgele yerleştirilmesi gibi görünebilir. Ancak, konumlarına gerçekte tam olarak kenar boşlukları, hizalamaları ve doldurma birleşimi kullanılarak denetlenir.  
  
 Aşağıdaki örnek, önceki çizimde düzeni oluşturmayı açıklar. A <xref:System.Windows.Controls.Border> öğesi bir üst yalıtır <xref:System.Windows.Controls.StackPanel>, ile bir <xref:System.Windows.Controls.Border.Padding%2A> 15 aygıttan bağımsız piksel değeri. Bu daraltmak için hesapları <xref:System.Windows.Media.Brushes.LightBlue%2A> alt bölmeyi çevreleyen bant <xref:System.Windows.Controls.StackPanel>. Alt öğelerinin <xref:System.Windows.Controls.StackPanel> her bu konudaki ayrıntılı çeşitli konumlandırma özelliklerini göstermek için kullanılır. Üç <xref:System.Windows.Controls.Button> öğeleri göstermek için kullanılan <xref:System.Windows.FrameworkElement.Margin%2A> ve <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> özellikleri.  
  
 [!code-csharp[MPALayoutSampleIntro#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutSampleIntro/CSharp/MPA_Layout_Sample_Intro.cs#1)]
 [!code-vb[MPALayoutSampleIntro#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutSampleIntro/VisualBasic/MPALayoutIntro.vb#1)]  
  
 Aşağıdaki diyagramda önceki örnekte kullanılan çeşitli konumlandırma özellikleri yakından görüntülemenizi sağlar. Bu konunun sonraki bölümlerinde daha ayrıntılı biçimde her konumlandırma özelliğinin nasıl kullanılacağını açıklar.  
  
 ![Ekran çağrı &#45; özelliklerle konumlandırma aşımı ayarlarına](../../../../docs/framework/wpf/advanced/media/layout-margins-padding-alignment-graphic2.PNG "layout_margins_padding_alignment_graphic2")  
  
<a name="wcpsdk_layout_amp_alignment_properties"></a>   
## <a name="understanding-alignment-properties"></a>Hizalama özelliklerini anlama  
 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> Ve <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> özellikleri, bir alt öğesi bir üst öğenin ayrılmış düzen alanına içinde nasıl konumlandırılacağını açıklar. Bu özellikleri birlikte kullanarak, alt öğelerini tam olarak yerleştirebilirsiniz. Örneğin, alt öğelerinin bir <xref:System.Windows.Controls.DockPanel> dört farklı yatay hizalamaları belirtebilirsiniz: <xref:System.Windows.HorizontalAlignment.Left>, <xref:System.Windows.HorizontalAlignment.Right>, veya <xref:System.Windows.HorizontalAlignment.Center>, veya <xref:System.Windows.HorizontalAlignment.Stretch> kullanılabilir alanı dolduracak şekilde. Benzer değerler dikey konumlandırma için kullanılabilir.  
  
> [!NOTE]
>  Açıkça kümesi <xref:System.Windows.FrameworkElement.Height%2A> ve <xref:System.Windows.FrameworkElement.Width%2A> bir öğede özellikleri önceliklidir <xref:System.Windows.HorizontalAlignment.Stretch> özellik değeri. Ayarlama girişimi <xref:System.Windows.FrameworkElement.Height%2A>, <xref:System.Windows.FrameworkElement.Width%2A>ve bir <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> değerini `Stretch` sonuçlanır `Stretch` yoksayılıyor isteyin.  
  
<a name="wcpsdk_layout_amp_horizontalalignment_properties"></a>   
### <a name="horizontalalignment-property"></a>HorizontalAlignment özelliği  
 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> Özelliği alt öğelerine uygulamak için yatay hizalama özelliklerini bildirir. Aşağıdaki tabloda her olası değerlerini gösterir <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> özelliği.  
  
|Üye|Açıklama|  
|------------|-----------------|  
|<xref:System.Windows.HorizontalAlignment.Left>|Alt öğeler, üst öğenin ayrılmış düzenindeki alanın soluna hizalanır.|  
|<xref:System.Windows.HorizontalAlignment.Center>|Alt öğeler, üst öğenin ayrılmış düzenindeki alanın merkezine hizalanır.|  
|<xref:System.Windows.HorizontalAlignment.Right>|Alt öğeler, üst öğenin ayrılmış düzen alanı sağa hizalanır.|  
|<xref:System.Windows.HorizontalAlignment.Stretch>(Varsayılan)|Alt öğeler, üst öğenin ayrılmış düzen alanı dolduracak şekilde uzatılır. Açık <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> değerleri öncelik alır.|  
  
 Aşağıdaki örnekte nasıl uygulanacağını gösterir <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> özelliğine <xref:System.Windows.Controls.Button> öğeleri. Çeşitli işleme davranışlarını daha iyi anlamak için her bir öznitelik değeri gösterilir.  
  
 [!code-csharp[MPALayoutHorizontalAlignment#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutHorizontalAlignment/CSharp/MPA_Layout_HorizontalAlignment.cs#2)]
 [!code-vb[MPALayoutHorizontalAlignment#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutHorizontalAlignment/VisualBasic/MPA_Layout_HorizontalAlignment.vb#2)]  
  
 Yukarıdaki kod aşağıdaki görüntüye benzer bir düzeni verir. Her konumlandırma etkileri <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> değeri çizimde görünür.  
  
 ![HorizontalAlignment örneği](../../../../docs/framework/wpf/advanced/media/layout-horizontal-alignment-graphic.PNG "layout_horizontal_alignment_graphic")  
  
<a name="wcpsdk_layout_amp_verticalalignment_properties"></a>   
### <a name="verticalalignment-property"></a>VerticalAlignment özelliği  
 <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> Özelliği alt öğelerine uygulamak için dikey hizalama özelliklerini açıklar. Her biri için olası değerler aşağıdaki tabloda gösterilmektedir <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> özelliği.  
  
|Üye|Açıklama|  
|------------|-----------------|  
|<xref:System.Windows.VerticalAlignment.Top>|Alt öğeler, üst öğenin ayrılmış düzenindeki alanın üstüne hizalanır.|  
|<xref:System.Windows.VerticalAlignment.Center>|Alt öğeler, üst öğenin ayrılmış düzenindeki alanın merkezine hizalanır.|  
|<xref:System.Windows.VerticalAlignment.Bottom>|Alt öğeler, üst öğenin ayrılmış düzenindeki alanın altına hizalanır.|  
|<xref:System.Windows.VerticalAlignment.Stretch>(Varsayılan)|Alt öğeler, üst öğenin ayrılmış düzen alanı dolduracak şekilde uzatılır. Açık <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> değerleri öncelik alır.|  
  
 Aşağıdaki örnekte nasıl uygulanacağını gösterir <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> özelliğine <xref:System.Windows.Controls.Button> öğeleri. Çeşitli işleme davranışlarını daha iyi anlamak için her bir öznitelik değeri gösterilir. Bu örnek amacıyla bir <xref:System.Windows.Controls.Grid> , her özellik değerinin düzen davranışını daha iyi anlamak için üst öğe olarak görünür kılavuz ile öğe kullanılır.  
  
 [!code-csharp[MPALayoutVerticalAlignment#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutVerticalAlignment/CSharp/MPA_Layout_VerticalAlignment.cs#2)]
 [!code-vb[MPALayoutVerticalAlignment#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutVerticalAlignment/VisualBasic/MPA_Layout_VerticalAlignment.vb#2)]
 [!code-xaml[MPALayoutVerticalAlignment#2](../../../../samples/snippets/xaml/VS_Snippets_Wpf/MPALayoutVerticalAlignment/XAML/default.xaml#2)]  
  
 Yukarıdaki kod aşağıdaki görüntüye benzer bir düzeni verir. Her konumlandırma etkileri <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> değeri çizimde görünür.  
  
 ![VerticalAlignment özelliği örneği](../../../../docs/framework/wpf/advanced/media/layout-vertical-alignment-graphic.PNG "layout_vertical_alignment_graphic")  
  
<a name="wcpsdk_layout_amp_margin_properties"></a>   
## <a name="understanding-margin-properties"></a>Dış boşlukların özelliklerini anlama  
 <xref:System.Windows.FrameworkElement.Margin%2A> Özelliği bir öğeyi ve alt öğeleri veya eşleri arasındaki uzaklığı açıklar. <xref:System.Windows.FrameworkElement.Margin%2A>değerleri olabilir Tekdüzen, benzer bir sözdizimi kullanarak `Margin="20"`. Bir Tekdüzen bu sözdizimine sahip <xref:System.Windows.FrameworkElement.Margin%2A> öğesine 20 aygıtı bağımsız piksel uygulanması. <xref:System.Windows.FrameworkElement.Margin%2A>değerleri de alabilir dört farklı değerleri, form sol, üst, sağ ve alt (bu sırayla) uygulamak için ayrı bir kenar boşluğu açıklayan her değeri gibi `Margin="0,10,5,25"`. Uygun kullanımı <xref:System.Windows.FrameworkElement.Margin%2A> özelliği, bir öğenin işleme konumu ve komşu öğeleri ve alt işleme konumunu ve çok daha iyi denetim sağlar.  
  
> [!NOTE]
>  Öğenin dışında alanı sıfır olmayan kenar boşluğu uygular <xref:System.Windows.FrameworkElement.ActualWidth%2A> ve <xref:System.Windows.FrameworkElement.ActualHeight%2A>.  
  
 Aşağıdaki örnek, bir grup Tekdüzen kenar boşluklarını uygulamak gösterilmiştir <xref:System.Windows.Controls.Button> öğeleri. <xref:System.Windows.Controls.Button> Öğeleri aralıklandırılmıştır her yön on piksel kenar boşluğu arabelleği ile.  
  
 [!code-cpp[MarginPaddingAlignmentSample#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#1)]
 [!code-csharp[MarginPaddingAlignmentSample#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#1)]
 [!code-vb[MarginPaddingAlignmentSample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#1)]
 [!code-xaml[MarginPaddingAlignmentSample#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#1)]  
  
 Çoğu durumda, Tekdüzen kenar boşluğu uygun değil. Bu durumlarda, Tekdüzen olmayan aralık uygulanabilir. Aşağıdaki örnek, Tekdüzen olmayan kenar boşluğu alt öğelerine uygulamak gösterilmiştir. Kenar boşlukları, bu sırada açıklanmıştır: sol, üst, sağ, alt.  
  
 [!code-cpp[MarginPaddingAlignmentSample#2](../../../../samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#2)]
 [!code-csharp[MarginPaddingAlignmentSample#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#2)]
 [!code-vb[MarginPaddingAlignmentSample#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#2)]
 [!code-xaml[MarginPaddingAlignmentSample#2](../../../../samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#2)]  
  
<a name="wcpsdk_layout_amp_padding_properties"></a>   
## <a name="understanding-the-padding-property"></a>Doldurma özelliğinin anlama  
 Doldurma benzer <xref:System.Windows.FrameworkElement.Margin%2A> Birçok bakımdan. Padding özelliği üzerinde sadece birkaç sınıflarında öncelikle kolaylık olarak sunulur: <xref:System.Windows.Documents.Block>, <xref:System.Windows.Controls.Border>, <xref:System.Windows.Controls.Control>, ve <xref:System.Windows.Controls.TextBlock> Doldurma özelliğini sergileyen sınıflarının örnekleridir. <xref:System.Windows.Controls.Border.Padding%2A> Özelliği etkin bir alt öğesi boyutunu tarafından belirtilen büyütür <xref:System.Windows.Thickness> değeri.  
  
 Aşağıdaki örnekte nasıl uygulanacağını gösterir <xref:System.Windows.Controls.Border.Padding%2A> üst <xref:System.Windows.Controls.Border> öğesi.  
  
 [!code-cpp[MarginPaddingAlignmentSample#3](../../../../samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#3)]
 [!code-csharp[MarginPaddingAlignmentSample#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#3)]
 [!code-vb[MarginPaddingAlignmentSample#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#3)]
 [!code-xaml[MarginPaddingAlignmentSample#3](../../../../samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#3)]  
  
<a name="wcpsdk_layout_amp_summary"></a>   
## <a name="using-alignment-margins-and-padding-in-an-application"></a>Bir uygulamada doldurma ve hizalama, kenar boşluklarını kullanma  
 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, <xref:System.Windows.FrameworkElement.Margin%2A>, <xref:System.Windows.Controls.Border.Padding%2A>, ve <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> karmaşık oluşturmak gerekli olan konumlandırma denetimini sağlamak [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. Her bir özellik etkilerini alt öğeli konumlandırma, dinamik uygulama ve kullanıcı deneyimleri oluşturma esneklik etkinleştirme değiştirmek için kullanabilirsiniz.  
  
 Aşağıdaki örnek, bu konudaki ayrıntılı kavramlar her gösterir. İlk örnekte bu konuda bulunan altyapı oluşturan, bu örnek, bir <xref:System.Windows.Controls.Grid> öğesi bir alt öğesi olarak <xref:System.Windows.Controls.Border> ilk örnekteki. <xref:System.Windows.Controls.Border.Padding%2A>üst öğeye uygulanan <xref:System.Windows.Controls.Border> öğesi. <xref:System.Windows.Controls.Grid> Üç alt arasındaki boşluğu bölümlemek için kullanılan <xref:System.Windows.Controls.StackPanel> öğeleri. <xref:System.Windows.Controls.Button>öğeleri çeşitli etkilerini göstermek için kullanılan yeniden <xref:System.Windows.FrameworkElement.Margin%2A> ve <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>. <xref:System.Windows.Controls.TextBlock>öğelerin her birini eklenir <xref:System.Windows.Controls.ColumnDefinition> uygulanan çeşitli özellikleri daha iyi tanımlamak için <xref:System.Windows.Controls.Button> her sütunda öğeleri.  
  
 [!code-cpp[MarginPaddingAlignmentSample#4](../../../../samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#4)]
 [!code-csharp[MarginPaddingAlignmentSample#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#4)]
 [!code-vb[MarginPaddingAlignmentSample#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#4)]
 [!code-xaml[MarginPaddingAlignmentSample#4](../../../../samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#4)]  
  
 Derlendiğinde, önceki uygulama verir bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] aşağıdaki çizimde gibi görünüyor. Çeşitli özellik değerlerinin etkilerini aralıklarda öğeler arasındaki fark edilir ve her sütunda öğelerin önemli özellik değerleri içinde gösterilir <xref:System.Windows.Controls.TextBlock> öğeleri.  
  
 ![Bir uygulamadaki çeşitli konumlandırma özellikleri](../../../../docs/framework/wpf/advanced/media/layout-margins-padding-aligment-graphic3.PNG "layout_margins_padding_aligment_graphic3")  
  
<a name="wcpsdk_layout_amp_alignment_whatsnext"></a>   
## <a name="whats-next"></a>Sırada ne var?  
 Tarafından tanımlanan konumlandırma özellikleri <xref:System.Windows.FrameworkElement> sınıfı içinde öğe yerleşiminin ayrıntılı denetimini etkinleştirir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalar. Şimdi daha iyi kullanarak öğeleri konumlandırmak için kullanabileceğiniz çeşitli teknikler vardır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Ek kaynaklar kullanılabilir biçimde açıklayan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] daha ayrıntılı düzeni. [Paneller genel bakış](../../../../docs/framework/wpf/controls/panels-overview.md) konu çeşitli hakkında daha fazla ayrıntı içerir <xref:System.Windows.Controls.Panel> öğeleri. Konu [gözden geçirme: ilk WPF Masaüstü Uygulamam](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md) bileşenleri konumlandırmak ve eylemlerini veri kaynaklarına bağlamak için düzen öğelerini kullanan gelişmiş teknikleri tanıtır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.FrameworkElement>  
 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>  
 <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>  
 <xref:System.Windows.FrameworkElement.Margin%2A>  
 [Panellere Genel Bakış](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [Düzen](../../../../docs/framework/wpf/advanced/layout.md)  
 [WPF Düzen Galerisi örneği](http://go.microsoft.com/fwlink/?LinkID=160054)
