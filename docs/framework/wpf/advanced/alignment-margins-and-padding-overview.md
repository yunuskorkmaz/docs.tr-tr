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
ms.openlocfilehash: 58af8848a6b8a5e4ded453831f5a7ef985548492
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59209170"
---
# <a name="alignment-margins-and-padding-overview"></a>Hizalama, Kenar Boşlukları ve Doldurmaya Genel Bakış
<xref:System.Windows.FrameworkElement> Sınıfı, tam olarak alt öğeleri konumlandırmak için kullanılan çeşitli özellikler sunar. Bu konuda dört en önemli özellikleri anlatılmaktadır: <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, <xref:System.Windows.FrameworkElement.Margin%2A>, <xref:System.Windows.Controls.Border.Padding%2A>, ve <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>. Temel öğeler konumunu kontrol etmek için sağladıkları için bu özellikleri etkilerini anlamak önemli olan [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] uygulamalar.  

<a name="wcpsdk_layout_amp_introduction"></a>   
## <a name="introduction-to-element-positioning"></a>Öğe konumlandırma giriş  
 Kullanarak öğeleri konumlandırmak için çok çeşitli yollar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Ancak, ideal düzeni elde sağ seçmenin ötesine giden <xref:System.Windows.Controls.Panel> öğesi. Konumlandırma ince denetim gerektiren bir anlayış <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, <xref:System.Windows.FrameworkElement.Margin%2A>, <xref:System.Windows.Controls.Border.Padding%2A>, ve <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> özellikleri.  
  
 Aşağıdaki resimde, birkaç konumlandırma özelliklerini kullanan bir düzen senaryosunu gösterir.  
  
 ![Konumlandırma özelliklerini örnek WPF](./media/layout-margins-padding-alignment-graphic1.PNG "layout_margins_padding_alignment_graphic1")  
  
 İlk bakışta <xref:System.Windows.Controls.Button> rastgele yerleştirilecek öğeler bu şekilde görünebilir. Ancak, konumlarına gerçekte tam olarak kenar boşlukları, hizalama ve doldurma bir birleşimi kullanılarak denetlenir.  
  
 Aşağıdaki örnek, önceki resimde düzeni oluşturmayı açıklar. A <xref:System.Windows.Controls.Border> kapsülleyen bir üst öğe <xref:System.Windows.Controls.StackPanel>, ile bir <xref:System.Windows.Controls.Border.Padding%2A> 15 cihaz bağımsız piksel değeri. Bu daraltmak için hesapları <xref:System.Windows.Media.Brushes.LightBlue%2A> alt çevreleyen bant <xref:System.Windows.Controls.StackPanel>. Alt öğeleri <xref:System.Windows.Controls.StackPanel> her biri, bu konudaki ayrıntılı çeşitli konumlandırma özelliklerini göstermek için kullanılır. Üç <xref:System.Windows.Controls.Button> öğeleri göstermek için kullanılan <xref:System.Windows.FrameworkElement.Margin%2A> ve <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> özellikleri.  
  
 [!code-csharp[MPALayoutSampleIntro#1](~/samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutSampleIntro/CSharp/MPA_Layout_Sample_Intro.cs#1)]
 [!code-vb[MPALayoutSampleIntro#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutSampleIntro/VisualBasic/MPALayoutIntro.vb#1)]  
  
 Aşağıdaki diyagramda önceki örnekte kullanılan çeşitli konumlandırma özelliklerini daha yakından bir görünümünü sağlar. Bu konunun sonraki bölümlerinde daha ayrıntılı olarak konumlandırma her özelliğinin nasıl kullanılacağını açıklar.  
  
 ![Konumlandırma özelliklerini ekran çağrısı ile&#45;çıkarmayı](./media/layout-margins-padding-alignment-graphic2.PNG "layout_margins_padding_alignment_graphic2")  
  
<a name="wcpsdk_layout_amp_alignment_properties"></a>   
## <a name="understanding-alignment-properties"></a>Hizalama özelliklerini anlama  
 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> Ve <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> özellikleri, bir alt öğesi bir üst öğenin içinde ayrılmış düzen alanı nasıl konumlandırılması gerektiğini açıklar. Bu özellikler birlikte kullanarak alt öğelerini tam olarak konumlandırabilirsiniz. Örneğin, alt öğelerini bir <xref:System.Windows.Controls.DockPanel> dört farklı yatay hizalama belirtebilirsiniz: <xref:System.Windows.HorizontalAlignment.Left>, <xref:System.Windows.HorizontalAlignment.Right>, veya <xref:System.Windows.HorizontalAlignment.Center>, veya <xref:System.Windows.HorizontalAlignment.Stretch> kullanılabilir alanı dolduracak şekilde. Benzer değerler dikey yerleştirme için kullanılabilir.  
  
> [!NOTE]
>  Açıkça kümesi <xref:System.Windows.FrameworkElement.Height%2A> ve <xref:System.Windows.FrameworkElement.Width%2A> özellikleri bir öğe üzerinde önceliklidir <xref:System.Windows.HorizontalAlignment.Stretch> özellik değeri. Ayarlama girişimi <xref:System.Windows.FrameworkElement.Height%2A>, <xref:System.Windows.FrameworkElement.Width%2A>ve <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> değerini `Stretch` sonuçlanır `Stretch` istek yoksayılıyor.  
  
<a name="wcpsdk_layout_amp_horizontalalignment_properties"></a>   
### <a name="horizontalalignment-property"></a>HorizontalAlignment özelliği  
 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> Özelliğini, alt öğelerine uygulanacak olan yatay hizalama özelliğini bildirir. Aşağıdaki tabloda her olası değerleri gösterir <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> özelliği.  
  
|Üye|Açıklama|  
|------------|-----------------|  
|<xref:System.Windows.HorizontalAlignment.Left>|Alt öğeleri üst öğe ayrılmış düzen alan sola hizalanır.|  
|<xref:System.Windows.HorizontalAlignment.Center>|Alt öğe üst öğe ayrılmış bir düzen alanı merkezine hizalanır.|  
|<xref:System.Windows.HorizontalAlignment.Right>|Alt öğeleri üst öğe ayrılmış düzen alan sağa hizalanır.|  
|<xref:System.Windows.HorizontalAlignment.Stretch> (Varsayılan)|Alt öğeleri üst öğenin Düzen ayrılmış alanı dolduracak şekilde uzatılır. Açık <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> değerleri öncelik alır.|  
  
 Aşağıdaki örnek nasıl uygulanacağını gösterir <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> özelliğini <xref:System.Windows.Controls.Button> öğeleri. Çeşitli işleme davranışlarını daha iyi anlamak için her bir öznitelik değeri gösterilir.  
  
 [!code-csharp[MPALayoutHorizontalAlignment#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutHorizontalAlignment/CSharp/MPA_Layout_HorizontalAlignment.cs#2)]
 [!code-vb[MPALayoutHorizontalAlignment#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutHorizontalAlignment/VisualBasic/MPA_Layout_HorizontalAlignment.vb#2)]  
  
 Yukarıdaki kod, aşağıdaki görüntüye benzer bir düzen verir. Her konumlandırma etkilerini <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> değeri çizimde görünür.  
  
 ![HorizontalAlignment örneği](./media/layout-horizontal-alignment-graphic.PNG "layout_horizontal_alignment_graphic")  
  
<a name="wcpsdk_layout_amp_verticalalignment_properties"></a>   
### <a name="verticalalignment-property"></a>VerticalAlignment özelliği  
 <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> Özelliği, alt öğelerine uygulamak için dikey hizalama özelliğini açıklar. Her biri için olası değerler aşağıdaki tabloda gösterilmektedir <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> özelliği.  
  
|Üye|Açıklama|  
|------------|-----------------|  
|<xref:System.Windows.VerticalAlignment.Top>|Alt öğeleri, ayrılmış bir düzen alanı üst öğenin üstüne hizalanır.|  
|<xref:System.Windows.VerticalAlignment.Center>|Alt öğe üst öğe ayrılmış bir düzen alanı merkezine hizalanır.|  
|<xref:System.Windows.VerticalAlignment.Bottom>|Alt öğeleri için üst öğe ayrılmış bir düzen alanı altındaki hizalanır.|  
|<xref:System.Windows.VerticalAlignment.Stretch> (Varsayılan)|Alt öğeleri üst öğenin Düzen ayrılmış alanı dolduracak şekilde uzatılır. Açık <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> değerleri öncelik alır.|  
  
 Aşağıdaki örnek nasıl uygulanacağını gösterir <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> özelliğini <xref:System.Windows.Controls.Button> öğeleri. Çeşitli işleme davranışlarını daha iyi anlamak için her bir öznitelik değeri gösterilir. Bu örnek, amacıyla bir <xref:System.Windows.Controls.Grid> öğesi görünür kılavuz ile her bir özellik değeri, düzen davranışını daha iyi anlamak için üst öğe olarak kullanılır.  
  
 [!code-csharp[MPALayoutVerticalAlignment#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutVerticalAlignment/CSharp/MPA_Layout_VerticalAlignment.cs#2)]
 [!code-vb[MPALayoutVerticalAlignment#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutVerticalAlignment/VisualBasic/MPA_Layout_VerticalAlignment.vb#2)]
 [!code-xaml[MPALayoutVerticalAlignment#2](~/samples/snippets/xaml/VS_Snippets_Wpf/MPALayoutVerticalAlignment/XAML/default.xaml#2)]  
  
 Yukarıdaki kod, aşağıdaki görüntüye benzer bir düzen verir. Her konumlandırma etkilerini <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> değeri çizimde görünür.  
  
 ![VerticalAlignment özelliği örneği](./media/layout-vertical-alignment-graphic.PNG "layout_vertical_alignment_graphic")  
  
<a name="wcpsdk_layout_amp_margin_properties"></a>   
## <a name="understanding-margin-properties"></a>Kenar boşluğu özelliklerini anlama  
 <xref:System.Windows.FrameworkElement.Margin%2A> Özelliği, bir öğe ve alt öğeleri veya eşleri arasındaki uzaklığı açıklar. <xref:System.Windows.FrameworkElement.Margin%2A> değerleri tek biçimli olabilir gibi bir söz dizimi kullanarak `Margin="20"`. Bu sözdizimi, bir Tekdüzen ile <xref:System.Windows.FrameworkElement.Margin%2A> 20 CİHAZDAN bağımsız piksel öğesine uygulanır. <xref:System.Windows.FrameworkElement.Margin%2A> değerleri de gerçekleştirebilir dört farklı değer biçiminde sol, üst, sağ ve alt (bu sırayla) uygulamak için ayrı bir kenar boşluğu açıklayan her değer gibi `Margin="0,10,5,25"`. Uygun kullanımı <xref:System.Windows.FrameworkElement.Margin%2A> özelliği, bir öğenin işleme konumunu ve ve komşu öğeleri ve alt öğeleri işleme konumunu çok ayrıntılı denetim sağlar.  
  
> [!NOTE]
>  Sıfır olmayan bir kenar boşluğu öğenin dış boşluk geçerlidir <xref:System.Windows.FrameworkElement.ActualWidth%2A> ve <xref:System.Windows.FrameworkElement.ActualHeight%2A>.  
  
 Aşağıdaki örnek, bir grup Tekdüzen kenar boşluklarını uygulamak gösterilmektedir <xref:System.Windows.Controls.Button> öğeleri. <xref:System.Windows.Controls.Button> Öğeleri aralıklı eşit her yönde bir piksel on kenar boşluğu arabellek ile.  
  
 [!code-cpp[MarginPaddingAlignmentSample#1](~/samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#1)]
 [!code-csharp[MarginPaddingAlignmentSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#1)]
 [!code-vb[MarginPaddingAlignmentSample#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#1)]
 [!code-xaml[MarginPaddingAlignmentSample#1](~/samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#1)]  
  
 Çoğu durumda, Tekdüzen bir kenar boşluğu uygun değil. Bu gibi durumlarda, Tekdüzen olmayan boşluk uygulanabilir. Aşağıdaki örnek, Tekdüzen olmayan kenar boşluğu alt öğelere uygulama işlemini gösterir. Kenar boşlukları, bu sırada açıklanmıştır: sol, üst, sağ, alt.  
  
 [!code-cpp[MarginPaddingAlignmentSample#2](~/samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#2)]
 [!code-csharp[MarginPaddingAlignmentSample#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#2)]
 [!code-vb[MarginPaddingAlignmentSample#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#2)]
 [!code-xaml[MarginPaddingAlignmentSample#2](~/samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#2)]  
  
<a name="wcpsdk_layout_amp_padding_properties"></a>   
## <a name="understanding-the-padding-property"></a>Padding özelliği anlama  
 Doldurma benzer <xref:System.Windows.FrameworkElement.Margin%2A> Birçok bakımdan. Padding özelliği üzerinde yalnızca birkaç sınıflarında öncelikle bir kolaylık olarak sunulur: <xref:System.Windows.Documents.Block>, <xref:System.Windows.Controls.Border>, <xref:System.Windows.Controls.Control>, ve <xref:System.Windows.Controls.TextBlock> Doldurma özelliğini kullanıma sınıflarının örneklerdir. <xref:System.Windows.Controls.Border.Padding%2A> Özelliği etkin bir alt öğesi boyutunu tarafından belirtilen büyütür <xref:System.Windows.Thickness> değeri.  
  
 Aşağıdaki örnek nasıl uygulanacağını gösterir <xref:System.Windows.Controls.Border.Padding%2A> üst <xref:System.Windows.Controls.Border> öğesi.  
  
 [!code-cpp[MarginPaddingAlignmentSample#3](~/samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#3)]
 [!code-csharp[MarginPaddingAlignmentSample#3](~/samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#3)]
 [!code-vb[MarginPaddingAlignmentSample#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#3)]
 [!code-xaml[MarginPaddingAlignmentSample#3](~/samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#3)]  
  
<a name="wcpsdk_layout_amp_summary"></a>   
## <a name="using-alignment-margins-and-padding-in-an-application"></a>Hizalama, kenar boşlukları, kullanma ve bir uygulamada doldurma  
 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, <xref:System.Windows.FrameworkElement.Margin%2A>, <xref:System.Windows.Controls.Border.Padding%2A>, ve <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> karmaşık oluşturmak gerekli olan konumlandırma denetimini sağlamak [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. Her bir özellik etkilerini alt öğeli konumlandırma, dinamik uygulama ve kullanıcı deneyimleri oluşturmak için esneklik etkinleştirme değiştirmek için kullanabilirsiniz.  
  
 Aşağıdaki örnek, her biri, bu konudaki ayrıntılı kavramlarını gösterir. Bu örnek ekler ilk örnekte bu konuda bulunan bir altyapı oluşturan, bir <xref:System.Windows.Controls.Grid> öğesi alt öğesi olarak <xref:System.Windows.Controls.Border> ilk örnekte. <xref:System.Windows.Controls.Border.Padding%2A> üst öğeye uygulanan <xref:System.Windows.Controls.Border> öğesi. <xref:System.Windows.Controls.Grid> Üç alt arasındaki boşluk bölümlemek için kullanılan <xref:System.Windows.Controls.StackPanel> öğeleri. <xref:System.Windows.Controls.Button> öğeleri çeşitli etkilerini göstermek için kullanılan yeniden <xref:System.Windows.FrameworkElement.Margin%2A> ve <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>. <xref:System.Windows.Controls.TextBlock> öğeleri her eklenir <xref:System.Windows.Controls.ColumnDefinition> uygulanan çeşitli özelliklerini daha iyi tanımlamak için <xref:System.Windows.Controls.Button> her sütunda öğeleri.  
  
 [!code-cpp[MarginPaddingAlignmentSample#4](~/samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#4)]
 [!code-csharp[MarginPaddingAlignmentSample#4](~/samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#4)]
 [!code-vb[MarginPaddingAlignmentSample#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#4)]
 [!code-xaml[MarginPaddingAlignmentSample#4](~/samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#4)]  
  
 Önceki uygulama derlendiğinde verir bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] aşağıda gibi görünüyor. Çeşitli özellik değerlerinin etkilerini öğeler arasındaki aralık belirgindir ve içinde gösterilen her sütunda öğelerin önemli özellik değerleri <xref:System.Windows.Controls.TextBlock> öğeleri.  
  
 ![Bir uygulamadaki birkaç konumlandırma özelliklerini](./media/layout-margins-padding-aligment-graphic3.PNG "layout_margins_padding_aligment_graphic3")  
  
<a name="wcpsdk_layout_amp_alignment_whatsnext"></a>   
## <a name="whats-next"></a>Yenilikler  
 Konumlandırma özelliklerini tarafından tanımlanan <xref:System.Windows.FrameworkElement> sınıfı içinde öğe yerleşiminin ince denetimini etkinleştirme [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalar. Artık daha iyi kullanarak öğeleri konumlandırmak için kullanabileceğiniz çeşitli teknikler vardır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Ek kaynaklar kullanılabilir biçimde açıklayan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] daha ayrıntılı düzen. [Panellere genel bakış](../controls/panels-overview.md) konu çeşitli hakkında daha fazla ayrıntı içeren <xref:System.Windows.Controls.Panel> öğeleri. Konu [izlenecek yol: İlk WPF Masaüstü Uygulamam](../getting-started/walkthrough-my-first-wpf-desktop-application.md) düzeni öğelerinin bileşenleri getirin ve eylemlerini veri kaynaklarına bağlamak için kullandığınız gelişmiş teknikleri sunar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.FrameworkElement>
- <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>
- <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>
- <xref:System.Windows.FrameworkElement.Margin%2A>
- [Panellere Genel Bakış](../controls/panels-overview.md)
- [Düzen](layout.md)
- [WPF Düzen Galerisi örneği](https://go.microsoft.com/fwlink/?LinkID=160054)
