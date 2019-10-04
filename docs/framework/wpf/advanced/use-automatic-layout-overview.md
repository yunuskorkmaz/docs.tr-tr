---
title: Otomatik Düzen Kullanımına Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- layout [WPF], automatic
- automatic layout [WPF]
ms.assetid: 6fed9264-18bb-4d05-8867-1fe356c6f687
ms.openlocfilehash: 0253c57f080705b648d9f416368d0fe974ac83ab
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834664"
---
# <a name="use-automatic-layout-overview"></a>Otomatik Düzen Kullanımına Genel Bakış

Bu konu, yerelleştirilebilir [!INCLUDE[TLA#tla_ui#plural](../../../../includes/tlasharptla-uisharpplural-md.md)] ile [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] uygulamalarının nasıl yazılacağı konusunda geliştiriciler için yönergeler tanıtır. Geçmişte, bir kullanıcı arabiriminin yerelleştirilmesi zaman alan bir işlemdir. Kullanıcı arabiriminin uyarlandığı her dil piksel ayarı için gereken bir piksel. Günümüzde, doğru tasarım ve doğru kodlama standartlarıyla [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)], Yerellerle yeniden boyutlandırılması ve bunu yeniden konumlandırılması için oluşturulabilir. Daha kolay yeniden boyutlandırılabilir ve yeniden konumlandırılabilir uygulamaları yazma yaklaşımına otomatik düzen denir ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama tasarımı kullanılarak elde edilebilir.

<a name="advantages_of_autolayout"></a>

## <a name="advantages-of-using-automatic-layout"></a>Otomatik düzen kullanmanın avantajları

@No__t-0 sunum sistemi güçlü ve esnek olduğundan, bir uygulamadaki öğeleri farklı dillerin gereksinimlerine uyacak şekilde ayarlayabilme yeteneği sağlar. Aşağıdaki liste otomatik düzenin avantajlarından bazılarını gösterir.

- UI tüm dillerde iyi görüntülenir.

- Metin çevrildikten sonra denetimlerin yalnızca konumunu ve boyutunu ayarlama gereksinimini azaltır.

- Yalnızca pencere boyutunu ayarlama gereksinimini azaltır.

- Kullanıcı arabirimi düzeni herhangi bir dilde düzgün şekilde işler.

- Yerelleştirme, dize çevirinden çok daha fazla olduğu noktaya azaltılabilir.

<a name="autolayout_controls"></a>

## <a name="automatic-layout-and-controls"></a>Otomatik düzen ve denetimler

Otomatik düzen, bir uygulamanın bir denetimin boyutunu otomatik olarak ayarlamasını sağlar. Örneğin, bir denetim bir dizenin uzunluğuna uyum sağlayacak şekilde değişebilir. Bu özellik, Yerelleştiricilerin dizeyi çevirmesini sağlar; Artık, çevrilmiş metne sığacak şekilde denetimi yeniden boyutlandırmaları gerekmez. Aşağıdaki örnek, Ingilizce içerikli bir düğme oluşturur.

[!code-xaml[LocalizationBtn_snip#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn_snip/CS/Pane1.xaml#1)]

Örnekte, bir Ispanyolca düğme yapmak için yapmanız gerekir, metni değiştirir. Örneğin,

[!code-xaml[LocalizationBtn#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn/CS/Pane1.xaml#1)]

Aşağıdaki grafik kod örneklerinin çıkışını gösterir:

![Farklı dillerdeki metinle aynı düğme](./media/use-automatic-layout-overview/auto-resizable-button.png)

<a name="autolayout_coding"></a>

## <a name="automatic-layout-and-coding-standards"></a>Otomatik düzen ve kodlama standartları

Otomatik düzen yaklaşımını kullanmak, tam olarak yerelleştirilebilir bir kullanıcı arabirimi oluşturmak için bir kodlama ve tasarım standartları ve kuralları gerektirir. Aşağıdaki kılavuzlar otomatik düzen kodlamasına yardımcı olur.

**Mutlak konumlar kullanmayın**

- Öğeleri kesinlikle konumlandırdığından <xref:System.Windows.Controls.Canvas> kullanmayın.

- Denetimleri konumlandırmak için <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.StackPanel> ve <xref:System.Windows.Controls.Grid> kullanın.

Çeşitli panel türleri hakkında bir tartışma için bkz. [panellere genel bakış](../controls/panels-overview.md).

**Pencere için sabit boyut ayarlamayın**

- @No__t-0 kullanın. Örneğin:

  [!code-xaml[LocalizationGrid#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#2)]

**@No__t ekleyin-1**

- Uygulamanızın kök öğesine <xref:System.Windows.FrameworkElement.FlowDirection%2A> ekleyin.

  WPF, yatay, çift yönlü ve dikey düzenleri desteklemek için kullanışlı bir yol sağlar. Sunum çerçevesinde <xref:System.Windows.FrameworkElement.FlowDirection%2A> özelliği düzeni tanımlamak için kullanılabilir. Akış yönü desenleri şunlardır:

  - <xref:System.Windows.FlowDirection.LeftToRight?displayProperty=nameWithType> (LrTb) — Latin, Doğu Asya ve diğerleri için yatay düzen.

  - <xref:System.Windows.FlowDirection.RightToLeft?displayProperty=nameWithType> (RlTb) — Arapça, Ibranice ve diğerleri için çift yönlü.

**Fiziksel yazı tipleri yerine bileşik yazı tiplerini kullanın**

- Bileşik yazı tipleriyle <xref:System.Windows.Controls.Control.FontFamily%2A> özelliğinin yerelleştirilmesi gerekmez.

- Geliştiriciler aşağıdaki yazı tiplerinden birini kullanabilir veya kendi türlerini oluşturabilir.

  - Genel Kullanıcı arabirimi
  - Global San Serif
  - Küresel tırnaklı

**XML ekle: lang**

- @No__t-0 özniteliğini, Kullanıcı arabiriminin kök öğesine (örneğin, Ingilizce bir uygulama için `xml:lang="en-US"`) ekleyin.

- Bileşik yazı tiplerinde kullanılacak yazı tipini belirlemek için `xml:lang` kullanıldığından, bu özelliği çok dilli senaryoları destekleyecek şekilde ayarlayın.

<a name="autolay_grids"></a>

## <a name="automatic-layout-and-grids"></a>Otomatik düzen ve Izgaralar

@No__t-0 öğesi, bir geliştiricinin öğeleri konumlandırmalarını sağladığından otomatik düzen için yararlıdır. @No__t-0 denetimi, bir sütun ve satır düzenlemesi kullanarak, alt öğeleri arasında kullanılabilir alanı dağıtabilme özelliğine sahiptir. UI öğeleri birden çok hücreye yayılabilir ve Kılavuzlar içinde ızgaralar olması mümkündür. Kılavuzlar, karmaşık UI oluşturmanıza ve konumlandıramanıza olanak sağladığından faydalıdır. Aşağıdaki örnek, bazı düğmeleri ve metinleri konumlandırmak için bir kılavuz kullanmayı gösterir. Hücrelerin yüksekliğinin ve genişliğinin <xref:System.Windows.GridUnitType.Auto>; olarak ayarlandığını unutmayın. Bu nedenle, bir görüntüyle birlikte düğme içeren hücre, görüntüye sığacak şekilde ayarlanır.

[!code-xaml[LocalizationGrid#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#1)]

Aşağıdaki grafikte, önceki kod tarafından üretilen kılavuz gösterilmektedir.

![Grid örnek](./media/glob-grid.png "glob_grid") Grid

<a name="autolay_grids_issharedsizescope"></a>

## <a name="automatic-layout-and-grids-using-the-issharedsizescope-property"></a>IsSharedSizeScope özelliğini kullanarak otomatik düzen ve Izgaralar

@No__t-0 öğesi, yerelleştirilebilir uygulamalarda içeriğe uyacak şekilde ayarlanabilecek denetimler oluşturmak için faydalıdır. Ancak, her zaman, içeriklere bakılmaksızın denetimlerin belirli bir boyutunu korumasını istersiniz. Örneğin, "Tamam", "Iptal" ve "gözatmaya" düğmeleri varsa, büyük olasılıkla düğmelerin içeriğe sığması için boyutlandırılmayacağını istemezsiniz. Bu durumda <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A?displayProperty=nameWithType> eklenmiş özelliği, birden çok Grid öğesi arasında aynı boyutlandırmayı paylaşmak için yararlıdır. Aşağıdaki örnek, birden fazla <xref:System.Windows.Controls.Grid> öğesi arasında sütun ve satır boyutlandırma verilerinin nasıl paylaşılacağını gösterir.

[!code-xaml[gridIssharedsizescopeProp#2](~/samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml#2)]

> [!NOTE]
> Tüm kod örneği için bkz. [Kılavuzlar arasında boyutlandırma özelliklerini paylaşma](../controls/how-to-share-sizing-properties-between-grids.md).

## <a name="see-also"></a>Ayrıca bkz.

- [WPF için Genelleştirme](globalization-for-wpf.md)
- [Düğme Oluşturmak için Otomatik Düzeni Kullanma](how-to-use-automatic-layout-to-create-a-button.md)
- [Otomatik Düzen için Kılavuz Kullanma](how-to-use-a-grid-for-automatic-layout.md)
