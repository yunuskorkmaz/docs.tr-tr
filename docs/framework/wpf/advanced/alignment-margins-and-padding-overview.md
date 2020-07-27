---
title: Hizalama, Kenar Boşlukları ve Doldurmaya Genel Bakış
description: Windows Presentation Foundation uygulamalarında alt öğe konumunu denetleyen HorizontalAlignment, Margin, Padding ve VerticalAlignment hakkında bilgi edinin.
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
ms.openlocfilehash: 832325086c85a7b044876e825d93e0b680a0b99c
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165882"
---
# <a name="alignment-margins-and-padding-overview"></a>Hizalama, Kenar Boşlukları ve Doldurmaya Genel Bakış
<xref:System.Windows.FrameworkElement>Sınıfı, alt öğeleri tam olarak konumlandırmak için kullanılan birkaç özelliği kullanıma sunar. Bu konu, en önemli özelliklerin dördünü anlatmaktadır: <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> , <xref:System.Windows.FrameworkElement.Margin%2A> , <xref:System.Windows.Controls.Border.Padding%2A> ve <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> . Bu özelliklerin etkileri, uygulamalardaki öğelerin konumunu denetlemek için temel sağladıkları için anlaşılması önemlidir [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] .  

<a name="wcpsdk_layout_amp_introduction"></a>
## <a name="introduction-to-element-positioning"></a>Öğe konumlandırmaya giriş  
 Kullanarak öğeleri yerleştirmek için çok çeşitli yollar vardır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] . Ancak ideal düzen elde etmek, doğru öğeyi seçmeye göre daha fazla ilerler <xref:System.Windows.Controls.Panel> . Konumlandırma üzerinde ince denetim,,, <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> <xref:System.Windows.FrameworkElement.Margin%2A> <xref:System.Windows.Controls.Border.Padding%2A> ve özelliklerinin anlaşılmasını gerektirir <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> .  
  
 Aşağıdaki çizimde, çeşitli konumlandırma özelliklerini kullanan bir düzen senaryosu gösterilmektedir.  
  
 ![WPF Konumlandırma özellikleri örneği](./media/layout-margins-padding-alignment-graphic1.PNG "layout_margins_padding_alignment_graphic1")  
  
 İlk bakışta, <xref:System.Windows.Controls.Button> bu çizimdeki öğeler rastgele yerleştirilmiş gibi görünebilir. Ancak, konumları, bir kenar boşlukları, hizalamalar ve doldurma birleşimi kullanılarak aslında tam olarak denetlenir.  
  
 Aşağıdaki örnek, önceki çizimde düzenin nasıl oluşturulacağını açıklar. Bir <xref:System.Windows.Controls.Border> öğesi <xref:System.Windows.Controls.StackPanel> , <xref:System.Windows.Controls.Border.Padding%2A> 15 cihazdan bağımsız piksel değeri ile bir üst öğeyi kapsüller. Bu <xref:System.Windows.Media.Brushes.LightBlue%2A> , alt öğenin çevrelediği dar bant için bu hesaplar <xref:System.Windows.Controls.StackPanel> . Öğesinin alt öğeleri, <xref:System.Windows.Controls.StackPanel> Bu konuda ayrıntılı olan çeşitli konumlandırma özelliklerinin her birini göstermek için kullanılır. <xref:System.Windows.Controls.Button>Hem hem de özelliklerini göstermek için üç öğe <xref:System.Windows.FrameworkElement.Margin%2A> kullanılır <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> .  
  
 [!code-csharp[MPALayoutSampleIntro#1](~/samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutSampleIntro/CSharp/MPA_Layout_Sample_Intro.cs#1)]
 [!code-vb[MPALayoutSampleIntro#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutSampleIntro/VisualBasic/MPALayoutIntro.vb#1)]  
  
 Aşağıdaki diyagramda, önceki örnekte kullanılan çeşitli konumlandırma özelliklerinin yakından görünümü sunulmaktadır. Bu konunun sonraki bölümlerinde, her konumlandırma özelliğinin nasıl kullanılacağı daha ayrıntılı olarak açıklanmıştır.  
  
 ![Özellikleri ekran çağrısıyla yerleştirme&#45;aşımları](./media/layout-margins-padding-alignment-graphic2.PNG "layout_margins_padding_alignment_graphic2")  
  
<a name="wcpsdk_layout_amp_alignment_properties"></a>
## <a name="understanding-alignment-properties"></a>Hizalama özelliklerini anlama  
 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>Ve <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> özellikleri bir alt öğenin, bir üst öğenin ayrılmış düzen alanı içinde nasıl konumlandırılacağını açıklamaktadır. Bu özellikleri birlikte kullanarak, alt öğeleri kesin bir şekilde konumlandırabilirsiniz. Örneğin, öğesinin alt öğeleri <xref:System.Windows.Controls.DockPanel> dört farklı yatay hizalamaları belirtebilir: <xref:System.Windows.HorizontalAlignment.Left> , <xref:System.Windows.HorizontalAlignment.Right> , veya <xref:System.Windows.HorizontalAlignment.Center> , ya da <xref:System.Windows.HorizontalAlignment.Stretch> kullanılabilir alanı dolduracak şekilde. Benzer değerler dikey konumlandırma için kullanılabilir.  
  
> [!NOTE]
> Açık olarak ayarlı <xref:System.Windows.FrameworkElement.Height%2A> ve <xref:System.Windows.FrameworkElement.Width%2A> Özellikler bir öğe üzerinde <xref:System.Windows.HorizontalAlignment.Stretch> özellik değerinden önceliklidir. <xref:System.Windows.FrameworkElement.Height%2A> <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> `Stretch` `Stretch` İstek yoksayılmakta olan istekte, ve sonuç değeri ayarlamaya çalışılıyor.  
  
<a name="wcpsdk_layout_amp_horizontalalignment_properties"></a>
### <a name="horizontalalignment-property"></a>HorizontalAlignment özelliği  
 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>Özelliği, alt öğelere uygulanacak yatay hizalama özelliklerini bildirir. Aşağıdaki tabloda, özelliğinin olası değerlerinin her biri gösterilmektedir <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> .  
  
|Üye|Açıklama|  
|------------|-----------------|  
|<xref:System.Windows.HorizontalAlignment.Left>|Alt öğeler, üst öğenin ayrılan düzen alanının soluna hizalanır.|  
|<xref:System.Windows.HorizontalAlignment.Center>|Alt öğeler, üst öğenin ayrılan düzen alanının merkezine hizalanır.|  
|<xref:System.Windows.HorizontalAlignment.Right>|Alt öğeler, üst öğenin ayrılan düzen alanının sağına hizalanır.|  
|<xref:System.Windows.HorizontalAlignment.Stretch>Varsayılanını|Alt öğeler, üst öğenin ayrılan düzen alanını dolduracak şekilde uzatılır. Açık <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> değer öncelik kazanır.|  
  
 Aşağıdaki örnek öğelerine özelliğinin nasıl uygulanacağını gösterir <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> <xref:System.Windows.Controls.Button> . Çeşitli işleme davranışlarını daha iyi göstermek için her öznitelik değeri gösterilir.  
  
 [!code-csharp[MPALayoutHorizontalAlignment#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutHorizontalAlignment/CSharp/MPA_Layout_HorizontalAlignment.cs#2)]
 [!code-vb[MPALayoutHorizontalAlignment#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutHorizontalAlignment/VisualBasic/MPA_Layout_HorizontalAlignment.vb#2)]  
  
 Yukarıdaki kod, aşağıdaki görüntüye benzer bir düzen verir. Her değerin konumlandırma etkileri <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> çizimde görünür.  
  
 ![HorizontalAlignment örneği](./media/layout-horizontal-alignment-graphic.PNG "layout_horizontal_alignment_graphic")  
  
<a name="wcpsdk_layout_amp_verticalalignment_properties"></a>
### <a name="verticalalignment-property"></a>VerticalAlignment özelliği  
 <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>Özelliği alt öğelere uygulanacak dikey hizalama özelliklerini açıklar. Aşağıdaki tabloda, özelliği için olası değerlerin her biri gösterilmektedir <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> .  
  
|Üye|Açıklama|  
|------------|-----------------|  
|<xref:System.Windows.VerticalAlignment.Top>|Alt öğeler, üst öğenin ayrılan düzen alanının üst kısmına hizalanır.|  
|<xref:System.Windows.VerticalAlignment.Center>|Alt öğeler, üst öğenin ayrılan düzen alanının merkezine hizalanır.|  
|<xref:System.Windows.VerticalAlignment.Bottom>|Alt öğeler, üst öğenin ayrılan düzen alanının altına hizalanır.|  
|<xref:System.Windows.VerticalAlignment.Stretch>Varsayılanını|Alt öğeler, üst öğenin ayrılan düzen alanını dolduracak şekilde uzatılır. Açık <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> değer öncelik kazanır.|  
  
 Aşağıdaki örnek öğelerine özelliğinin nasıl uygulanacağını gösterir <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> <xref:System.Windows.Controls.Button> . Çeşitli işleme davranışlarını daha iyi göstermek için her öznitelik değeri gösterilir. Bu örneğin amaçları doğrultusunda, her bir <xref:System.Windows.Controls.Grid> özellik değerinin düzen davranışını daha iyi göstermek için, görünür kılavuz çizgileri olan bir öğe üst öğe olarak kullanılır.  
  
 [!code-csharp[MPALayoutVerticalAlignment#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutVerticalAlignment/CSharp/MPA_Layout_VerticalAlignment.cs#2)]
 [!code-vb[MPALayoutVerticalAlignment#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutVerticalAlignment/VisualBasic/MPA_Layout_VerticalAlignment.vb#2)]
 [!code-xaml[MPALayoutVerticalAlignment#2](~/samples/snippets/xaml/VS_Snippets_Wpf/MPALayoutVerticalAlignment/XAML/default.xaml#2)]  
  
 Yukarıdaki kod, aşağıdaki görüntüye benzer bir düzen verir. Her değerin konumlandırma etkileri <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> çizimde görünür.  
  
 ![VerticalAlignment özelliği örneği](./media/layout-vertical-alignment-graphic.PNG "layout_vertical_alignment_graphic")  
  
<a name="wcpsdk_layout_amp_margin_properties"></a>
## <a name="understanding-margin-properties"></a>Kenar boşluğu özelliklerini anlama  
 <xref:System.Windows.FrameworkElement.Margin%2A>Özelliği, bir öğe ile onun alt öğesi veya eşleri arasındaki mesafeyi açıklar. <xref:System.Windows.FrameworkElement.Margin%2A>değerler, gibi bir sözdizimi kullanılarak Tekdüzen olabilir `Margin="20"` . Bu söz dizimi ile, <xref:System.Windows.FrameworkElement.Margin%2A> öğe için 20 cihazdan bağımsız piksel tek bir şekilde uygulanır. <xref:System.Windows.FrameworkElement.Margin%2A>değerler aynı zamanda dört ayrı değer biçiminde de olabilir, bu her değer sol, üst, sağ ve alt (Bu sırada) uygulanacak şekilde ayrı bir kenar boşluğunu tanımlar `Margin="0,10,5,25"` . Özelliğinin uygun kullanımı, <xref:System.Windows.FrameworkElement.Margin%2A> bir öğenin işleme konumunun çok ince denetimini ve komşu öğelerinin ve alt öğelerinin işleme konumunu sunar.  
  
> [!NOTE]
> Sıfır olmayan bir kenar boşluğu, ve öğelerinin dışında boşluk uygular <xref:System.Windows.FrameworkElement.ActualWidth%2A> <xref:System.Windows.FrameworkElement.ActualHeight%2A> .  
  
 Aşağıdaki örnek bir öğe grubunun çevresine tek biçimli kenar boşluklarının nasıl uygulanacağını gösterir <xref:System.Windows.Controls.Button> . <xref:System.Windows.Controls.Button>Öğeler her yönde on piksellik bir kenar boşluğu arabelleği ile eşit aralıklıdır.  
  
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
 Doldurma <xref:System.Windows.FrameworkElement.Margin%2A> çoğu yönden benzerdir. Padding özelliği yalnızca birkaç sınıfta, öncelikle kolaylık olarak sunulur: <xref:System.Windows.Documents.Block> ,, <xref:System.Windows.Controls.Border> <xref:System.Windows.Controls.Control> , ve <xref:System.Windows.Controls.TextBlock> bir doldurma özelliği sunan sınıfların örnekleridir. <xref:System.Windows.Controls.Border.Padding%2A>Özelliği, bir alt öğenin etkin boyutunu belirtilen <xref:System.Windows.Thickness> değere büyütür.  
  
 Aşağıdaki örnek, <xref:System.Windows.Controls.Border.Padding%2A> bir üst öğe için nasıl uygulanacağını gösterir <xref:System.Windows.Controls.Border> .  
  
 [!code-cpp[MarginPaddingAlignmentSample#3](~/samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#3)]
 [!code-csharp[MarginPaddingAlignmentSample#3](~/samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#3)]
 [!code-vb[MarginPaddingAlignmentSample#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#3)]
 [!code-xaml[MarginPaddingAlignmentSample#3](~/samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#3)]  
  
<a name="wcpsdk_layout_amp_summary"></a>
## <a name="using-alignment-margins-and-padding-in-an-application"></a>Bir uygulamada hizalama, kenar boşlukları ve doldurma kullanma  
 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>,,, <xref:System.Windows.FrameworkElement.Margin%2A> <xref:System.Windows.Controls.Border.Padding%2A> ve <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> karmaşık oluşturmak için gereken konumlandırma denetimini sağlar [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] . Alt öğe konumlandırmayı değiştirmek, dinamik uygulamalar ve kullanıcı deneyimleri oluşturma esnekliği sağlamak için her bir özelliğin etkilerini kullanabilirsiniz.  
  
 Aşağıdaki örnek, bu konuda ayrıntılı olarak açıklanan kavramların her birini gösterir. Bu konunun ilk örneğinde bulunan altyapı üzerinde oluşturma, bu örnek, <xref:System.Windows.Controls.Grid> ilk örnekteki öğesinin bir alt öğesi olarak bir öğesi ekler <xref:System.Windows.Controls.Border> . <xref:System.Windows.Controls.Border.Padding%2A>üst <xref:System.Windows.Controls.Border> öğeye uygulanır. , <xref:System.Windows.Controls.Grid> Üç alt öğe arasındaki boşluğu bölümlemek için kullanılır <xref:System.Windows.Controls.StackPanel> . <xref:System.Windows.Controls.Button>öğeleri, ve öğelerinin çeşitli efektlerini göstermek için kullanılır <xref:System.Windows.FrameworkElement.Margin%2A> <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> . <xref:System.Windows.Controls.TextBlock>Her <xref:System.Windows.Controls.ColumnDefinition> sütunda öğelere uygulanan çeşitli özellikleri daha iyi tanımlamak için her birine öğeler eklenir <xref:System.Windows.Controls.Button> .  
  
 [!code-cpp[MarginPaddingAlignmentSample#4](~/samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#4)]
 [!code-csharp[MarginPaddingAlignmentSample#4](~/samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#4)]
 [!code-vb[MarginPaddingAlignmentSample#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#4)]
 [!code-xaml[MarginPaddingAlignmentSample#4](~/samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#4)]  
  
 Derlendiğinde, önceki uygulama [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Aşağıdaki çizimde gösterildiği gibi bir oluşturur. Çeşitli özellik değerlerinin etkileri, öğeler arasındaki aralığa göre görünür ve her bir sütundaki öğeler için önemli özellik değerleri öğeler içinde gösterilir <xref:System.Windows.Controls.TextBlock> .  
  
 ![Bir uygulamadaki çeşitli konumlandırma özellikleri](./media/layout-margins-padding-aligment-graphic3.PNG "layout_margins_padding_aligment_graphic3")  
  
<a name="wcpsdk_layout_amp_alignment_whatsnext"></a>
## <a name="whats-next"></a>Sırada Ne Var?  
 Sınıfı tarafından tanımlanan Konumlandırma Özellikleri, <xref:System.Windows.FrameworkElement> uygulamalar içindeki öğe yerleşiminin ince denetimini etkinleştirir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] . Artık kullanarak öğeleri daha iyi konumlandırmak için kullanabileceğiniz çeşitli teknikler vardır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] .  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Daha ayrıntılı olarak düzeni açıklayan ek kaynaklar mevcuttur. [Panellere genel bakış](../controls/panels-overview.md) konusu çeşitli öğeler hakkında daha fazla ayrıntı içerir <xref:System.Windows.Controls.Panel> . [Izlenecek yol: Ilk WPF Masaüstü Uygulamam](../getting-started/walkthrough-my-first-wpf-desktop-application.md) , bileşenleri konumlandırmak ve eylemlerini veri kaynaklarına bağlamak için düzen öğelerini kullanan gelişmiş teknikler sunmaktadır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.FrameworkElement>
- <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>
- <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>
- <xref:System.Windows.FrameworkElement.Margin%2A>
- [Panellere Genel Bakış](../controls/panels-overview.md)
- [Düzen](layout.md)
- [WPF düzen Galerisi örneği](https://go.microsoft.com/fwlink/?LinkID=160054)
