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
ms.openlocfilehash: bec2d9cd224febb650e2de67bb7406365d075963
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145481"
---
# <a name="alignment-margins-and-padding-overview"></a>Hizalama, Kenar Boşlukları ve Doldurmaya Genel Bakış
Sınıf, <xref:System.Windows.FrameworkElement> alt öğeleri tam olarak konumlandırmak için kullanılan çeşitli özellikleri ortaya çıkarır. Bu konu en önemli özelliklerinden dördünden <xref:System.Windows.FrameworkElement.Margin%2A> <xref:System.Windows.Controls.Border.Padding%2A>birini <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>tartışır: <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, , ve . Bu özelliklerin etkilerini anlamak önemlidir, çünkü uygulamalardaki [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] öğelerin konumunu denetlemek için temel oluştururlar.  

<a name="wcpsdk_layout_amp_introduction"></a>
## <a name="introduction-to-element-positioning"></a>Element Konumlandırmaya Giriş  
 Öğeleri kullanarak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]konumlandırmanın birçok yolu vardır. Ancak, ideal düzeni elde etmek sadece <xref:System.Windows.Controls.Panel> doğru öğeyi seçmenin ötesine geçer. Konumlandırmanın <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>iyi kontrolü, , , <xref:System.Windows.FrameworkElement.Margin%2A> <xref:System.Windows.Controls.Border.Padding%2A>ve <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> özelliklerinin anlaşılmasını gerektirir.  
  
 Aşağıdaki resimde, birkaç konumlandırma özelliği kullanan bir düzen senaryosu gösterilmektedir.  
  
 ![WPF Konumlandırma Özellikleri Örneği](./media/layout-margins-padding-alignment-graphic1.PNG "layout_margins_padding_alignment_graphic1")  
  
 İlk bakışta, <xref:System.Windows.Controls.Button> bu resimdeki öğeler rasgele yerleştirilmiş gibi görünebilir. Ancak, konumları aslında tam kenar boşlukları, hizalamalar ve dolgu bir arada kullanılarak kontrol edilir.  
  
 Aşağıdaki örnekte, önceki resimde düzenin nasıl oluşturulacak olduğu açıklanmaktadır. Bir <xref:System.Windows.Controls.Border> öğe, 15 aygıt <xref:System.Windows.Controls.StackPanel>bağımsız <xref:System.Windows.Controls.Border.Padding%2A> piksel değeri ile bir üst kapsüller. Bu, çocuğu <xref:System.Windows.Controls.StackPanel> <xref:System.Windows.Media.Brushes.LightBlue%2A> çevreleyen dar bandı hesaplar. Alt öğeleri, <xref:System.Windows.Controls.StackPanel> bu konuda ayrıntılı olarak ayrıntılı çeşitli konumlandırma özellikleri her göstermek için kullanılır. Hem <xref:System.Windows.Controls.Button> özellikleri <xref:System.Windows.FrameworkElement.Margin%2A> hem de <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> özellikleri göstermek için üç öğe kullanılır.  
  
 [!code-csharp[MPALayoutSampleIntro#1](~/samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutSampleIntro/CSharp/MPA_Layout_Sample_Intro.cs#1)]
 [!code-vb[MPALayoutSampleIntro#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutSampleIntro/VisualBasic/MPALayoutIntro.vb#1)]  
  
 Aşağıdaki diyagram, önceki örnekte kullanılan çeşitli konumlandırma özelliklerinin yakın çekim görünümünü sağlar. Bu konuyla ilgili sonraki bölümlerde, her konumlandırma özelliğinin nasıl kullanılacağı daha ayrıntılı olarak açıklanmıştır.  
  
 ![Ekran Arama&#45;çıkışlı Konumlandırma Özellikleri](./media/layout-margins-padding-alignment-graphic2.PNG "layout_margins_padding_alignment_graphic2")  
  
<a name="wcpsdk_layout_amp_alignment_properties"></a>
## <a name="understanding-alignment-properties"></a>Hizalama Özelliklerini Anlama  
 Ve <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> özellikleri, alt öğenin bir üst öğenin ayrılmış düzen alanı içinde nasıl konumlandırılması gerektiğini açıklar. Bu özellikleri birlikte kullanarak, alt öğeleri tam olarak konumlandırabilirsiniz. Örneğin, <xref:System.Windows.Controls.DockPanel> bir alt öğeleri dört farklı yatay <xref:System.Windows.HorizontalAlignment.Left>hizalama belirtebilir: , <xref:System.Windows.HorizontalAlignment.Right>veya <xref:System.Windows.HorizontalAlignment.Center>, veya, kullanılabilir alanı doldurmak için. <xref:System.Windows.HorizontalAlignment.Stretch> Dikey konumlandırma için benzer değerler mevcuttur.  
  
> [!NOTE]
> Bir öğeüzerinde <xref:System.Windows.FrameworkElement.Height%2A> <xref:System.Windows.FrameworkElement.Width%2A> açıkça ayarlanmış ve özellikleri özellik <xref:System.Windows.HorizontalAlignment.Stretch> değerinden önce gelir. Ayarlamaya <xref:System.Windows.FrameworkElement.Height%2A>çalışırken <xref:System.Windows.FrameworkElement.Width%2A>, ve <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> `Stretch` istek `Stretch` yoksayılıyor sonuç değeri.  
  
<a name="wcpsdk_layout_amp_horizontalalignment_properties"></a>
### <a name="horizontalalignment-property"></a>Yatay Hizalama Özelliği  
 Özellik, <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> alt öğelere uygulanacak yatay hizalama özelliklerini bildirir. Aşağıdaki tablo, <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> özelliğin olası değerlerinin her birini gösterir.  
  
|Üye|Açıklama|  
|------------|-----------------|  
|<xref:System.Windows.HorizontalAlignment.Left>|Alt öğeler, üst öğenin ayrılan düzen alanının soluna hizalanır.|  
|<xref:System.Windows.HorizontalAlignment.Center>|Alt öğeler, üst öğenin ayrılan düzen alanının merkezine hizalanır.|  
|<xref:System.Windows.HorizontalAlignment.Right>|Alt öğeler, üst öğenin ayrılan düzen alanının sağına hizalanır.|  
|<xref:System.Windows.HorizontalAlignment.Stretch>(Varsayılan)|Alt öğeler, üst öğenin ayrılan düzen alanını doldurmak için uzatılır. Açık <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Height%2A> ve değerler önceliklidir.|  
  
 Aşağıdaki örnek, özelliğin <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> öğelere <xref:System.Windows.Controls.Button> nasıl uygulanacağı gösterilmektedir. Her öznitelik değeri, çeşitli işleme davranışlarını daha iyi göstermek için gösterilir.  
  
 [!code-csharp[MPALayoutHorizontalAlignment#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutHorizontalAlignment/CSharp/MPA_Layout_HorizontalAlignment.cs#2)]
 [!code-vb[MPALayoutHorizontalAlignment#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutHorizontalAlignment/VisualBasic/MPA_Layout_HorizontalAlignment.vb#2)]  
  
 Önceki kod aşağıdaki görüntüye benzer bir düzen verir. Her <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> değerin konumlandırma efektleri resimde görülebilir.  
  
 ![Yatay Hizalama Örneği](./media/layout-horizontal-alignment-graphic.PNG "layout_horizontal_alignment_graphic")  
  
<a name="wcpsdk_layout_amp_verticalalignment_properties"></a>
### <a name="verticalalignment-property"></a>Dikey Hizalama Özelliği  
 Özellik, <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> alt öğelere uygulanacak dikey hizalama özelliklerini açıklar. Aşağıdaki tablo, <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> özellik için olası değerlerin her birini gösterir.  
  
|Üye|Açıklama|  
|------------|-----------------|  
|<xref:System.Windows.VerticalAlignment.Top>|Alt öğeler, üst öğenin ayrılan düzen alanının en üstüne hizalanır.|  
|<xref:System.Windows.VerticalAlignment.Center>|Alt öğeler, üst öğenin ayrılan düzen alanının merkezine hizalanır.|  
|<xref:System.Windows.VerticalAlignment.Bottom>|Alt öğeler, üst öğenin ayrılan düzen alanının altına hizalanır.|  
|<xref:System.Windows.VerticalAlignment.Stretch>(Varsayılan)|Alt öğeler, üst öğenin ayrılan düzen alanını doldurmak için uzatılır. Açık <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Height%2A> ve değerler önceliklidir.|  
  
 Aşağıdaki örnek, özelliğin <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> öğelere <xref:System.Windows.Controls.Button> nasıl uygulanacağı gösterilmektedir. Her öznitelik değeri, çeşitli işleme davranışlarını daha iyi göstermek için gösterilir. Bu örnek amaçları için, görünür ızgaraçizgileri olan bir <xref:System.Windows.Controls.Grid> öğe, her özellik değerinin düzen davranışını daha iyi göstermek için üst öğe olarak kullanılır.  
  
 [!code-csharp[MPALayoutVerticalAlignment#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutVerticalAlignment/CSharp/MPA_Layout_VerticalAlignment.cs#2)]
 [!code-vb[MPALayoutVerticalAlignment#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutVerticalAlignment/VisualBasic/MPA_Layout_VerticalAlignment.vb#2)]
 [!code-xaml[MPALayoutVerticalAlignment#2](~/samples/snippets/xaml/VS_Snippets_Wpf/MPALayoutVerticalAlignment/XAML/default.xaml#2)]  
  
 Önceki kod aşağıdaki görüntüye benzer bir düzen verir. Her <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> değerin konumlandırma efektleri resimde görülebilir.  
  
 ![VerticalAlignment özellik örneği](./media/layout-vertical-alignment-graphic.PNG "layout_vertical_alignment_graphic")  
  
<a name="wcpsdk_layout_amp_margin_properties"></a>
## <a name="understanding-margin-properties"></a>Kenar Boşluğu Özelliklerini Anlama  
 Özellik, <xref:System.Windows.FrameworkElement.Margin%2A> bir öğe ile alt öğesi veya yaşıtları arasındaki mesafeyi açıklar. <xref:System.Windows.FrameworkElement.Margin%2A>değerleri gibi `Margin="20"`sözdizimi kullanarak, düzgün olabilir. Bu sözdizimi ile <xref:System.Windows.FrameworkElement.Margin%2A> öğeye 20 aygıt bağımsız pikselden oluşan bir üniforma uygulanır. <xref:System.Windows.FrameworkElement.Margin%2A>değerleri de dört farklı değer, her değer sol, üst, sağ ve alt (bu sırada) uygulamak için `Margin="0,10,5,25"`ayrı bir kenar boşluğu açıklayan şeklinde alabilir. Özelliğin doğru <xref:System.Windows.FrameworkElement.Margin%2A> kullanımı, bir öğenin oluşturma konumunun ve komşu elemanlarının ve çocuklarının işleme konumunun çok iyi kontrol edilmesini sağlar.  
  
> [!NOTE]
> Sıfır olmayan bir kenar boşluğu, öğenin <xref:System.Windows.FrameworkElement.ActualWidth%2A> <xref:System.Windows.FrameworkElement.ActualHeight%2A>ve .  
  
 Aşağıdaki örnek, bir grup öğenin etrafında <xref:System.Windows.Controls.Button> tek tip kenar boşluklarının nasıl uygulanacağı gösterilmektedir. Öğeler, <xref:System.Windows.Controls.Button> her yönde on piksellik kenar boşluğu arabelleğiyle eşit aralıklı olarak aralıklı olarak kullanılır.  
  
 [!code-cpp[MarginPaddingAlignmentSample#1](~/samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#1)]
 [!code-csharp[MarginPaddingAlignmentSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#1)]
 [!code-vb[MarginPaddingAlignmentSample#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#1)]
 [!code-xaml[MarginPaddingAlignmentSample#1](~/samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#1)]  
  
 Çoğu durumda, tek tip kenar boşluğu uygun değildir. Bu gibi durumlarda, tek düze olmayan aralık uygulanabilir. Aşağıdaki örnekte, alt öğelere tekdüze kenar boşluğu aralığının nasıl uygulanacağı gösterilmektedir. Kenar boşlukları bu sırada açıklanır: sol, üst, sağ, alt.  
  
 [!code-cpp[MarginPaddingAlignmentSample#2](~/samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#2)]
 [!code-csharp[MarginPaddingAlignmentSample#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#2)]
 [!code-vb[MarginPaddingAlignmentSample#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#2)]
 [!code-xaml[MarginPaddingAlignmentSample#2](~/samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#2)]  
  
<a name="wcpsdk_layout_amp_padding_properties"></a>
## <a name="understanding-the-padding-property"></a>Dolgu Özelliğini Anlama  
 Dolgu çoğu açıdan <xref:System.Windows.FrameworkElement.Margin%2A> benzer. Dolgu özelliği, öncelikle bir kolaylık olarak, sadece birkaç <xref:System.Windows.Documents.Block>sınıflarda maruz kalır: , <xref:System.Windows.Controls.Border>, <xref:System.Windows.Controls.Control>, bir <xref:System.Windows.Controls.TextBlock> Dolgu özelliği ortaya sınıfların örnekleridir. Özellik, <xref:System.Windows.Controls.Border.Padding%2A> bir alt öğenin etkin boyutunu belirtilen <xref:System.Windows.Thickness> değere göre büyütür.  
  
 Aşağıdaki örnek, bir <xref:System.Windows.Controls.Border.Padding%2A> üst <xref:System.Windows.Controls.Border> öğeye nasıl uygulanacağı gösterilmektedir.  
  
 [!code-cpp[MarginPaddingAlignmentSample#3](~/samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#3)]
 [!code-csharp[MarginPaddingAlignmentSample#3](~/samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#3)]
 [!code-vb[MarginPaddingAlignmentSample#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#3)]
 [!code-xaml[MarginPaddingAlignmentSample#3](~/samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#3)]  
  
<a name="wcpsdk_layout_amp_summary"></a>
## <a name="using-alignment-margins-and-padding-in-an-application"></a>Uygulamada Hizalama, Kenar Boşlukları ve Dolgu Kullanma  
 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, <xref:System.Windows.FrameworkElement.Margin%2A> <xref:System.Windows.Controls.Border.Padding%2A>, <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> , ve karmaşık [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]oluşturmak için gerekli konumlandırma kontrolü sağlar. Dinamik uygulamalar ve kullanıcı deneyimleri oluşturmada esneklik sağlayarak alt öğe konumlandırmasını değiştirmek için her özelliğin etkilerini kullanabilirsiniz.  
  
 Aşağıdaki örnek, bu konuda ayrıntılı olarak ayrıntılı olan kavramların her birini gösterir. Bu konudaki ilk örnekte bulunan altyapıyı temel <xref:System.Windows.Controls.Grid> alan bu örnek, <xref:System.Windows.Controls.Border> ilk örnekteki alt öğeolarak bir öğe ekler. <xref:System.Windows.Controls.Border.Padding%2A>üst <xref:System.Windows.Controls.Border> öğeye uygulanır. Üç <xref:System.Windows.Controls.Grid> alt <xref:System.Windows.Controls.StackPanel> öğe arasındaki boşluğu bölmek için kullanılır. <xref:System.Windows.Controls.Button>elemanları yine çeşitli etkilerini göstermek için <xref:System.Windows.FrameworkElement.Margin%2A> <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>kullanılır ve. <xref:System.Windows.Controls.TextBlock>öğeler her sütundaki <xref:System.Windows.Controls.ColumnDefinition> <xref:System.Windows.Controls.Button> öğelere uygulanan çeşitli özellikleri daha iyi tanımlamak için her birine eklenir.  
  
 [!code-cpp[MarginPaddingAlignmentSample#4](~/samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#4)]
 [!code-csharp[MarginPaddingAlignmentSample#4](~/samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#4)]
 [!code-vb[MarginPaddingAlignmentSample#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#4)]
 [!code-xaml[MarginPaddingAlignmentSample#4](~/samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#4)]  
  
 Derlendiğinde, önceki uygulama aşağıdaki çizime benzeyen bir uygulama [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] verir. Çeşitli özellik değerlerinin etkileri öğeler arasındaki aralıkta belirgindir ve her sütundaki öğeler için <xref:System.Windows.Controls.TextBlock> önemli özellik değerleri öğeler içinde gösterilir.  
  
 ![Bir uygulamada çeşitli konumlandırma özellikleri](./media/layout-margins-padding-aligment-graphic3.PNG "layout_margins_padding_aligment_graphic3")  
  
<a name="wcpsdk_layout_amp_alignment_whatsnext"></a>
## <a name="whats-next"></a>Sırada Ne Var  
 <xref:System.Windows.FrameworkElement> Sınıf tarafından tanımlanan konumlandırma özellikleri, uygulamalar içinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] öğe yerleşiminin hassas denetimini sağlar. Şimdi kullanarak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]elemanları daha iyi konumlandırmak için kullanabileceğiniz çeşitli teknikler var.  
  
 Düzeni daha ayrıntılı [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] olarak açıklayan ek kaynaklar kullanılabilir. [Paneller Genel Bakış](../controls/panels-overview.md) konu çeşitli <xref:System.Windows.Controls.Panel> öğeler hakkında daha fazla ayrıntı içerir. Konu [Walkthrough: Benim ilk WPF masaüstü uygulaması](../getting-started/walkthrough-my-first-wpf-desktop-application.md) bileşenleri konumlandırmak ve veri kaynaklarına eylemlerini bağlamak için düzen öğeleri ni kullanan gelişmiş teknikler tanıttı.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.FrameworkElement>
- <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>
- <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>
- <xref:System.Windows.FrameworkElement.Margin%2A>
- [Panellere Genel Bakış](../controls/panels-overview.md)
- [Düzen](layout.md)
- [WPF Düzen Galerisi Örneği](https://go.microsoft.com/fwlink/?LinkID=160054)
