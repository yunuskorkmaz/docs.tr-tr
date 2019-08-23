---
title: Hizalama, Kenar Boşlukları ve Doldurmaya Genel Bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- margins [WPF]
- padding [WPF]
- aligning [WPF]
ms.assetid: 9c6a2009-9b86-4e40-8605-0a2664dc3973
ms.openlocfilehash: bf351b6df972dc992f214ddfe899bfa808d0cd53
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963645"
---
# <a name="alignment-margins-and-padding-overview"></a>Hizalama, Kenar Boşlukları ve Doldurmaya Genel Bakış
Sınıfı <xref:System.Windows.FrameworkElement> , alt öğeleri tam olarak konumlandırmak için kullanılan birkaç özelliği kullanıma sunar. Bu konu, en önemli özelliklerin dördünü anlatmaktadır <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>: <xref:System.Windows.FrameworkElement.Margin%2A>, <xref:System.Windows.Controls.Border.Padding%2A>, ve <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>. Bu özelliklerin etkileri, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] uygulamalardaki öğelerin konumunu denetlemek için temel sağladıkları için anlaşılması önemlidir.  

<a name="wcpsdk_layout_amp_introduction"></a>   
## <a name="introduction-to-element-positioning"></a>Öğe konumlandırmaya giriş  
 Kullanarak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]öğeleri yerleştirmek için çok çeşitli yollar vardır. Ancak ideal düzen elde etmek, doğru <xref:System.Windows.Controls.Panel> öğeyi seçmeye göre daha fazla ilerler. <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>Konumlandırma üzerinde ince denetim <xref:System.Windows.FrameworkElement.Margin%2A> <xref:System.Windows.Controls.Border.Padding%2A>,,, ve <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> özelliklerinin anlaşılmasını gerektirir.  
  
 Aşağıdaki çizimde, çeşitli konumlandırma özelliklerini kullanan bir düzen senaryosu gösterilmektedir.  
  
 ![WPF Konumlandırma özellikleri örneği](./media/layout-margins-padding-alignment-graphic1.PNG "layout_margins_padding_alignment_graphic1")  
  
 İlk bakışta, <xref:System.Windows.Controls.Button> bu çizimdeki öğeler rastgele yerleştirilmiş gibi görünebilir. Ancak, konumları, bir kenar boşlukları, hizalamalar ve doldurma birleşimi kullanılarak aslında tam olarak denetlenir.  
  
 Aşağıdaki örnek, önceki çizimde düzenin nasıl oluşturulacağını açıklar. Bir <xref:System.Windows.Controls.Border> öğesi, 15 cihazdan <xref:System.Windows.Controls.StackPanel>bağımsız piksel <xref:System.Windows.Controls.Border.Padding%2A> değeri ile bir üst öğeyi kapsüller. Bu, alt öğenin <xref:System.Windows.Media.Brushes.LightBlue%2A> <xref:System.Windows.Controls.StackPanel>çevrelediği dar bant için bu hesaplar. Öğesinin alt öğeleri, <xref:System.Windows.Controls.StackPanel> bu konuda ayrıntılı olan çeşitli konumlandırma özelliklerinin her birini göstermek için kullanılır. Hem hem de <xref:System.Windows.Controls.Button> <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> özelliklerini göstermek için üç öğe kullanılır. <xref:System.Windows.FrameworkElement.Margin%2A>  
  
 [!code-csharp[MPALayoutSampleIntro#1](~/samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutSampleIntro/CSharp/MPA_Layout_Sample_Intro.cs#1)]
 [!code-vb[MPALayoutSampleIntro#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutSampleIntro/VisualBasic/MPALayoutIntro.vb#1)]  
  
 Aşağıdaki diyagramda, önceki örnekte kullanılan çeşitli konumlandırma özelliklerinin yakından görünümü sunulmaktadır. Bu konunun sonraki bölümlerinde, her konumlandırma özelliğinin nasıl kullanılacağı daha ayrıntılı olarak açıklanmıştır.  
  
 ![Ekran çağrısı&#45;ile özellikleri konumlandırma](./media/layout-margins-padding-alignment-graphic2.PNG "layout_margins_padding_alignment_graphic2")  
  
<a name="wcpsdk_layout_amp_alignment_properties"></a>   
## <a name="understanding-alignment-properties"></a>Hizalama özelliklerini anlama  
 Ve özellikleri <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> bir alt öğenin, bir üst öğenin ayrılmış düzen alanı içinde nasıl konumlandırılacağını açıklamaktadır. <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> Bu özellikleri birlikte kullanarak, alt öğeleri kesin bir şekilde konumlandırabilirsiniz. Örneğin, <xref:System.Windows.Controls.DockPanel> öğesinin alt öğeleri dört farklı yatay hizalamaları belirtebilir: <xref:System.Windows.HorizontalAlignment.Right> <xref:System.Windows.HorizontalAlignment.Left>,, veya <xref:System.Windows.HorizontalAlignment.Center>, ya da kullanılabilir alanı <xref:System.Windows.HorizontalAlignment.Stretch> dolduracak şekilde. Benzer değerler dikey konumlandırma için kullanılabilir.  
  
> [!NOTE]
> Açık olarak ayarlı <xref:System.Windows.FrameworkElement.Height%2A> ve <xref:System.Windows.FrameworkElement.Width%2A> Özellikler bir <xref:System.Windows.HorizontalAlignment.Stretch> öğe üzerinde özellik değerinden önceliklidir. <xref:System.Windows.FrameworkElement.Height%2A> <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> İstek yoksayılmakta olan istekte, ve `Stretch` sonuç değeri ayarlamaya çalışılıyor. `Stretch`  
  
<a name="wcpsdk_layout_amp_horizontalalignment_properties"></a>   
### <a name="horizontalalignment-property"></a>HorizontalAlignment özelliği  
 Özelliği <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> , alt öğelere uygulanacak yatay hizalama özelliklerini bildirir. Aşağıdaki tabloda, <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> özelliğinin olası değerlerinin her biri gösterilmektedir.  
  
|Üye|Açıklama|  
|------------|-----------------|  
|<xref:System.Windows.HorizontalAlignment.Left>|Alt öğeler, üst öğenin ayrılan düzen alanının soluna hizalanır.|  
|<xref:System.Windows.HorizontalAlignment.Center>|Alt öğeler, üst öğenin ayrılan düzen alanının merkezine hizalanır.|  
|<xref:System.Windows.HorizontalAlignment.Right>|Alt öğeler, üst öğenin ayrılan düzen alanının sağına hizalanır.|  
|<xref:System.Windows.HorizontalAlignment.Stretch>Varsayılanını|Alt öğeler, üst öğenin ayrılan düzen alanını dolduracak şekilde uzatılır. Açık <xref:System.Windows.FrameworkElement.Width%2A> ve<xref:System.Windows.FrameworkElement.Height%2A> değer öncelik kazanır.|  
  
 Aşağıdaki örnek <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> <xref:System.Windows.Controls.Button> öğelerine özelliğinin nasıl uygulanacağını gösterir. Çeşitli işleme davranışlarını daha iyi göstermek için her öznitelik değeri gösterilir.  
  
 [!code-csharp[MPALayoutHorizontalAlignment#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutHorizontalAlignment/CSharp/MPA_Layout_HorizontalAlignment.cs#2)]
 [!code-vb[MPALayoutHorizontalAlignment#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutHorizontalAlignment/VisualBasic/MPA_Layout_HorizontalAlignment.vb#2)]  
  
 Yukarıdaki kod, aşağıdaki görüntüye benzer bir düzen verir. Her <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> değerin konumlandırma etkileri çizimde görünür.  
  
 ![HorizontalAlignment örneği](./media/layout-horizontal-alignment-graphic.PNG "layout_horizontal_alignment_graphic")  
  
<a name="wcpsdk_layout_amp_verticalalignment_properties"></a>   
### <a name="verticalalignment-property"></a>VerticalAlignment özelliği  
 <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> Özelliği alt öğelere uygulanacak dikey hizalama özelliklerini açıklar. Aşağıdaki tabloda, <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> özelliği için olası değerlerin her biri gösterilmektedir.  
  
|Üye|Açıklama|  
|------------|-----------------|  
|<xref:System.Windows.VerticalAlignment.Top>|Alt öğeler, üst öğenin ayrılan düzen alanının üst kısmına hizalanır.|  
|<xref:System.Windows.VerticalAlignment.Center>|Alt öğeler, üst öğenin ayrılan düzen alanının merkezine hizalanır.|  
|<xref:System.Windows.VerticalAlignment.Bottom>|Alt öğeler, üst öğenin ayrılan düzen alanının altına hizalanır.|  
|<xref:System.Windows.VerticalAlignment.Stretch>Varsayılanını|Alt öğeler, üst öğenin ayrılan düzen alanını dolduracak şekilde uzatılır. Açık <xref:System.Windows.FrameworkElement.Width%2A> ve<xref:System.Windows.FrameworkElement.Height%2A> değer öncelik kazanır.|  
  
 Aşağıdaki örnek <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> <xref:System.Windows.Controls.Button> öğelerine özelliğinin nasıl uygulanacağını gösterir. Çeşitli işleme davranışlarını daha iyi göstermek için her öznitelik değeri gösterilir. Bu örneğin amaçları doğrultusunda, her bir <xref:System.Windows.Controls.Grid> Özellik değerinin düzen davranışını daha iyi göstermek için, görünür kılavuz çizgileri olan bir öğe üst öğe olarak kullanılır.  
  
 [!code-csharp[MPALayoutVerticalAlignment#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutVerticalAlignment/CSharp/MPA_Layout_VerticalAlignment.cs#2)]
 [!code-vb[MPALayoutVerticalAlignment#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutVerticalAlignment/VisualBasic/MPA_Layout_VerticalAlignment.vb#2)]
 [!code-xaml[MPALayoutVerticalAlignment#2](~/samples/snippets/xaml/VS_Snippets_Wpf/MPALayoutVerticalAlignment/XAML/default.xaml#2)]  
  
 Yukarıdaki kod, aşağıdaki görüntüye benzer bir düzen verir. Her <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> değerin konumlandırma etkileri çizimde görünür.  
  
 ![VerticalAlignment özelliği örneği](./media/layout-vertical-alignment-graphic.PNG "layout_vertical_alignment_graphic")  
  
<a name="wcpsdk_layout_amp_margin_properties"></a>   
## <a name="understanding-margin-properties"></a>Kenar boşluğu özelliklerini anlama  
 <xref:System.Windows.FrameworkElement.Margin%2A> Özelliği, bir öğe ile onun alt öğesi veya eşleri arasındaki mesafeyi açıklar. <xref:System.Windows.FrameworkElement.Margin%2A>değerler, gibi `Margin="20"`bir sözdizimi kullanılarak Tekdüzen olabilir. Bu söz dizimi ile, öğe <xref:System.Windows.FrameworkElement.Margin%2A> için 20 cihazdan bağımsız piksel tek bir şekilde uygulanır. <xref:System.Windows.FrameworkElement.Margin%2A>değerler aynı zamanda dört ayrı değer biçiminde de olabilir, bu her değer sol, üst, sağ ve alt (Bu sırada) `Margin="0,10,5,25"`uygulanacak şekilde ayrı bir kenar boşluğunu tanımlar. Özelliğinin uygun kullanımı, <xref:System.Windows.FrameworkElement.Margin%2A> bir öğenin işleme konumunun çok ince denetimini ve komşu öğelerinin ve alt öğelerinin işleme konumunu sunar.  
  
> [!NOTE]
> Sıfır olmayan bir kenar boşluğu, <xref:System.Windows.FrameworkElement.ActualWidth%2A> ve <xref:System.Windows.FrameworkElement.ActualHeight%2A>öğelerinin dışında boşluk uygular.  
  
 Aşağıdaki örnek bir <xref:System.Windows.Controls.Button> öğe grubunun çevresine tek biçimli kenar boşluklarının nasıl uygulanacağını gösterir. <xref:System.Windows.Controls.Button> Öğeler her yönde on piksellik bir kenar boşluğu arabelleği ile eşit aralıklıdır.  
  
 [!code-cpp[MarginPaddingAlignmentSample#1](~/samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#1)]
 [!code-csharp[MarginPaddingAlignmentSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#1)]
 [!code-vb[MarginPaddingAlignmentSample#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#1)]
 [!code-xaml[MarginPaddingAlignmentSample#1](~/samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#1)]  
  
 Birçok örnekte, Tekdüzen kenar boşluğu uygun değildir. Bu durumlarda, tek biçimli olmayan boşluklar uygulanabilir. Aşağıdaki örnek, alt öğelerine Tekdüzen olmayan kenar boşluğu aralıklarının nasıl uygulanacağını gösterir. Kenar boşlukları şu sırada açıklanmıştır: sol, üst, sağ, alt.  
  
 [!code-cpp[MarginPaddingAlignmentSample#2](~/samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#2)]
 [!code-csharp[MarginPaddingAlignmentSample#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#2)]
 [!code-vb[MarginPaddingAlignmentSample#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#2)]
 [!code-xaml[MarginPaddingAlignmentSample#2](~/samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#2)]  
  
<a name="wcpsdk_layout_amp_padding_properties"></a>   
## <a name="understanding-the-padding-property"></a>Padding özelliğini anlama  
 Doldurma çoğu yönden benzerdir <xref:System.Windows.FrameworkElement.Margin%2A> . Padding özelliği yalnızca birkaç sınıfta, öncelikle kolaylık olarak <xref:System.Windows.Documents.Block>sunulur: <xref:System.Windows.Controls.Control>, <xref:System.Windows.Controls.Border>,, ve <xref:System.Windows.Controls.TextBlock> bir doldurma özelliği sunan sınıfların örnekleridir. Özelliği, bir alt öğenin etkin boyutunu belirtilen <xref:System.Windows.Thickness> değere büyütür. <xref:System.Windows.Controls.Border.Padding%2A>  
  
 Aşağıdaki örnek, bir üst <xref:System.Windows.Controls.Border.Padding%2A> <xref:System.Windows.Controls.Border> öğe için nasıl uygulanacağını gösterir.  
  
 [!code-cpp[MarginPaddingAlignmentSample#3](~/samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#3)]
 [!code-csharp[MarginPaddingAlignmentSample#3](~/samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#3)]
 [!code-vb[MarginPaddingAlignmentSample#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#3)]
 [!code-xaml[MarginPaddingAlignmentSample#3](~/samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#3)]  
  
<a name="wcpsdk_layout_amp_summary"></a>   
## <a name="using-alignment-margins-and-padding-in-an-application"></a>Bir uygulamada hizalama, kenar boşlukları ve doldurma kullanma  
 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>,,, ve<xref:System.Windows.FrameworkElement.VerticalAlignment%2A> karmaşık[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]oluşturmak için gereken konumlandırma denetimini sağlar. <xref:System.Windows.FrameworkElement.Margin%2A> <xref:System.Windows.Controls.Border.Padding%2A> Alt öğe konumlandırmayı değiştirmek, dinamik uygulamalar ve kullanıcı deneyimleri oluşturma esnekliği sağlamak için her bir özelliğin etkilerini kullanabilirsiniz.  
  
 Aşağıdaki örnek, bu konuda ayrıntılı olarak açıklanan kavramların her birini gösterir. Bu konunun ilk örneğinde bulunan altyapı üzerinde oluşturma, bu örnek, ilk örnekteki öğesinin bir alt <xref:System.Windows.Controls.Grid> <xref:System.Windows.Controls.Border> öğesi olarak bir öğesi ekler. <xref:System.Windows.Controls.Border.Padding%2A>üst <xref:System.Windows.Controls.Border> öğeye uygulanır. , <xref:System.Windows.Controls.Grid> Üç alt <xref:System.Windows.Controls.StackPanel> öğe arasındaki boşluğu bölümlemek için kullanılır. <xref:System.Windows.Controls.Button>öğeleri, <xref:System.Windows.FrameworkElement.Margin%2A> ve <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>öğelerinin çeşitli efektlerini göstermek için kullanılır. <xref:System.Windows.Controls.TextBlock>Her sütunda <xref:System.Windows.Controls.Button> öğelere uygulanan çeşitli <xref:System.Windows.Controls.ColumnDefinition> özellikleri daha iyi tanımlamak için her birine öğeler eklenir.  
  
 [!code-cpp[MarginPaddingAlignmentSample#4](~/samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#4)]
 [!code-csharp[MarginPaddingAlignmentSample#4](~/samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#4)]
 [!code-vb[MarginPaddingAlignmentSample#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#4)]
 [!code-xaml[MarginPaddingAlignmentSample#4](~/samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#4)]  
  
 Derlendiğinde, önceki uygulama aşağıdaki çizimde gösterildiği gibi [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] bir oluşturur. Çeşitli özellik değerlerinin etkileri, öğeler arasındaki aralığa göre görünür ve her bir sütundaki öğeler için önemli özellik değerleri öğeler içinde <xref:System.Windows.Controls.TextBlock> gösterilir.  
  
 ![Bir uygulamadaki çeşitli konumlandırma özellikleri](./media/layout-margins-padding-aligment-graphic3.PNG "layout_margins_padding_aligment_graphic3")  
  
<a name="wcpsdk_layout_amp_alignment_whatsnext"></a>   
## <a name="whats-next"></a>Sıradaki  
 Sınıfı tarafından tanımlanan konumlandırma özellikleri <xref:System.Windows.FrameworkElement> , uygulamalar içindeki [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] öğe yerleşiminin ince denetimini etkinleştirir. Artık kullanarak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]öğeleri daha iyi konumlandırmak için kullanabileceğiniz çeşitli teknikler vardır.  
  
 Daha ayrıntılı olarak düzeni açıklayan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ek kaynaklar mevcuttur. [Panellere genel bakış](../controls/panels-overview.md) konusu çeşitli <xref:System.Windows.Controls.Panel> öğeler hakkında daha fazla ayrıntı içerir. Bu konuda [izlenecek yol: İlk WPF Masaüstü Uygulamam](../getting-started/walkthrough-my-first-wpf-desktop-application.md) , bileşenleri konumlandırmak ve eylemlerini veri kaynaklarına bağlamak için düzen öğelerini kullanan gelişmiş teknikler sunmaktadır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.FrameworkElement>
- <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>
- <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>
- <xref:System.Windows.FrameworkElement.Margin%2A>
- [Panellere Genel Bakış](../controls/panels-overview.md)
- [Düzen](layout.md)
- [WPF düzen Galerisi örneği](https://go.microsoft.com/fwlink/?LinkID=160054)
