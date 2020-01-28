---
title: Denetim performansını iyileştirme
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], improving performance
- container recycling [WPF]
- user interface virtualization [WPF]
ms.assetid: 45a31c43-ea8a-4546-96c8-0631b9934179
ms.openlocfilehash: d02fde7076cd6a24fdfb171ed54161b20f3d465e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746734"
---
# <a name="optimizing-performance-controls"></a>Performansı İyileştirme: denetimler

Windows Presentation Foundation (WPF), çoğu Windows uygulamasında kullanılan birçok ortak kullanıcı arabirimi (UI) bileşenini içerir. Bu konu, UI 'nizin performansını iyileştirmeye yönelik teknikler içerir.

## <a name="displaying-large-data-sets"></a>Büyük veri kümelerini görüntüleme

<xref:System.Windows.Controls.ListView> ve <xref:System.Windows.Controls.ComboBox> gibi WPF denetimleri, bir uygulamadaki öğelerin listesini göstermek için kullanılır. Görüntülenecek liste büyükse, uygulamanın performansı etkilenebilir. Bunun nedeni, standart düzen sisteminin liste denetimiyle ilişkili her öğe için bir düzen kapsayıcısı oluşturması ve düzen boyutunu ve konumunu hesaplamasıdır. Genellikle, tüm öğeleri aynı anda göstermek zorunda değilsiniz; Bunun yerine, bir alt küme görüntüler ve Kullanıcı listede kaydırılır. Bu durumda, UI *sanallaştırmayı*kullanmak mantıklı olur, bu, öğe için öğe kapsayıcısı oluşturma ve ilişkili düzen hesaplamasının, öğe görünene kadar ertelenmesi anlamına gelir.

UI Sanallaştırması liste denetimlerinin önemli bir yönüdür. UI Sanallaştırması veri sanallaştırmayla karıştırılmamalıdır. UI Sanallaştırması yalnızca bellekteki görünür öğeleri depolar, ancak veri bağlama senaryosunda veri yapısının tamamını bellekte depolar. Buna karşılık, veri sanallaştırma yalnızca bellekte ekranda görünür olan veri öğelerini depolar.

Varsayılan olarak, <xref:System.Windows.Controls.ListView> için UI Sanallaştırması etkinleştirilir ve liste öğeleri veriye bağlandığında denetimleri <xref:System.Windows.Controls.ListBox>. <xref:System.Windows.Controls.TreeView> sanallaştırma, <xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizing%2A?displayProperty=nameWithType> iliştirilmiş özelliği `true`ayarlanarak etkinleştirilebilir. <xref:System.Windows.Controls.ComboBox>gibi <xref:System.Windows.Controls.StackPanel> sınıfını kullanan <xref:System.Windows.Controls.ItemsControl> veya varolan öğe denetimlerinden türetilen özel denetimler için UI sanallaştırmayı etkinleştirmek istiyorsanız, <xref:System.Windows.Controls.ItemsControl.ItemsPanel%2A> <xref:System.Windows.Controls.VirtualizingStackPanel> ve <xref:System.Windows.Controls.VirtualizingPanel.IsVirtualizing%2A> olarak ayarlayabilirsiniz. Ne yazık ki, bu denetimler için UI sanallaştırmayı uygulamadan devre dışı bırakabilirsiniz. Aşağıda, UI sanallaştırmayı devre dışı bırakan koşulların bir listesi verilmiştir.

- Öğe kapsayıcıları doğrudan <xref:System.Windows.Controls.ItemsControl>eklenir. Örneğin, bir uygulama bir <xref:System.Windows.Controls.ListBox>açıkça <xref:System.Windows.Controls.ListBoxItem> nesneleri eklerse, <xref:System.Windows.Controls.ListBox> <xref:System.Windows.Controls.ListBoxItem> nesneleri sanallaştırmaz.

- <xref:System.Windows.Controls.ItemsControl> öğe kapsayıcıları farklı türlerdir. Örneğin, <xref:System.Windows.Controls.Menu> <xref:System.Windows.Controls.Separator> ve <xref:System.Windows.Controls.MenuItem>türünde nesneler içerdiğinden, <xref:System.Windows.Controls.Separator> nesneleri kullanan bir <xref:System.Windows.Controls.Menu> öğe geri dönüşümü uygulayamaz.

- <xref:System.Windows.Controls.ScrollViewer.CanContentScroll%2A> `false`olarak ayarlanıyor.

- <xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizing%2A> `false`olarak ayarlanıyor.

Öğe kapsayıcılarını sanallaştırdığınızda önemli bir önemi, öğe ile ilgili olan bir öğe kapsayıcısı ile ilişkili ek durum bilgilerinizin olmasına bakılmaksızın. Bu durumda, ek durumu kaydetmeniz gerekir. Örneğin, bir <xref:System.Windows.Controls.Expander> denetiminde bulunan bir öğeye sahip olabilirsiniz ve <xref:System.Windows.Controls.Expander.IsExpanded%2A> durumu öğenin kendine değil öğenin kapsayıcısına bağlanır. Kapsayıcı yeni bir öğe için tekrar kullanıldığında, yeni öğe için <xref:System.Windows.Controls.Expander.IsExpanded%2A> geçerli değeri kullanılır. Ayrıca, eski öğe doğru <xref:System.Windows.Controls.Expander.IsExpanded%2A> değerini kaybeder.

Şu anda, veri sanallaştırma için yerleşik destek sunan WPF denetimleri yoktur.

## <a name="container-recycling"></a>Kapsayıcı geri dönüştürme

<xref:System.Windows.Controls.ItemsControl> öğesinden devraldığı denetimler için .NET Framework 3,5 SP1 'e uygulanan UI sanallaştırmaya en iyi duruma getirme, kayan performansı de iyileştirebilecek *kapsayıcı geri Dönüşümleridir* . UI sanallaştırmayı kullanan bir <xref:System.Windows.Controls.ItemsControl> doldurulduğu zaman, görünüm olarak kayan her öğe için bir öğe kapsayıcısı oluşturur ve görünümün dışına kayan her öğe için öğe kapsayıcısını yok eder. *Kapsayıcı geri dönüştürme* , denetimin farklı veri öğeleri için varolan öğe kapsayıcılarını yeniden kullanmasına olanak sağlar. böylece, Kullanıcı <xref:System.Windows.Controls.ItemsControl>kaydırıldığında öğe kapsayıcıları sürekli olarak oluşturulmaz ve yok edilir. <xref:System.Windows.Controls.VirtualizingPanel.VirtualizationMode%2A> ekli özelliği <xref:System.Windows.Controls.VirtualizationMode.Recycling>olarak ayarlayarak öğe geri dönüşümünü etkinleştirmeyi seçebilirsiniz.

Sanallaştırmayı destekleyen <xref:System.Windows.Controls.ItemsControl>, kapsayıcı geri dönüşümü kullanabilir. <xref:System.Windows.Controls.ListBox>kapsayıcının geri dönüşümünü etkinleştirme örneği için, bkz. [ListBox 'ın kayan performansını geliştirme](../controls/how-to-improve-the-scrolling-performance-of-a-listbox.md).

## <a name="supporting-bidirectional-virtualization"></a>Çift yönlü sanallaştırmayı destekleme

<xref:System.Windows.Controls.VirtualizingStackPanel>, UI Sanallaştırması için yatay veya dikey olarak bir yönde yerleşik destek sunar. Denetimleriniz için çift yönlü sanallaştırma kullanmak istiyorsanız, <xref:System.Windows.Controls.VirtualizingStackPanel> sınıfını genişleten özel bir panel uygulamanız gerekir. <xref:System.Windows.Controls.VirtualizingStackPanel> sınıfı <xref:System.Windows.Controls.VirtualizingStackPanel.OnViewportSizeChanged%2A>, <xref:System.Windows.Controls.VirtualizingStackPanel.LineUp%2A>, <xref:System.Windows.Controls.VirtualizingStackPanel.PageUp%2A>ve <xref:System.Windows.Controls.VirtualizingStackPanel.MouseWheelUp%2A>gibi sanal yöntemler sunar. Bu sanal yöntemler, listenin görünür bölümündeki bir değişikliği algılamanıza ve buna uygun şekilde işleme sağlar.

## <a name="optimizing-templates"></a>Şablonları iyileştirme

Görsel ağaç, bir uygulamadaki tüm görsel öğeleri içerir. Doğrudan oluşturulan nesnelere ek olarak, şablon genişletmesinden kaynaklanan nesneler de bulunur. Örneğin, bir <xref:System.Windows.Controls.Button>oluşturduğunuzda, ayrıca görsel ağaçta <xref:Microsoft.Windows.Themes.ClassicBorderDecorator> ve <xref:System.Windows.Controls.ContentPresenter> nesneleri de alırsınız. Denetim şablonlarınızı en iyi duruma almadıysanız, görsel ağaçta çok fazla sayıda gereksiz nesne oluşturuyor olabilirsiniz. Görsel ağaç hakkında daha fazla bilgi için bkz. [WPF Grafik Işlemeye genel bakış](../graphics-multimedia/wpf-graphics-rendering-overview.md).

## <a name="deferred-scrolling"></a>Ertelenmiş kaydırma

Varsayılan olarak, Kullanıcı Thumb öğesini bir ScrollBar üzerine sürüklediğinde içerik görünümü sürekli olarak güncellenir. Denetiminiz içinde kaydırma yavaşsa, ertelenmiş kaydırma kullanmayı düşünün. Ertelenmiş kaydırma ' de, içerik yalnızca Kullanıcı Thumb 'i yayınlarsa güncelleştirilir.

Ertelenmiş kaydırma uygulamak için <xref:System.Windows.Controls.ScrollViewer.IsDeferredScrollingEnabled%2A> özelliğini `true`olarak ayarlayın. <xref:System.Windows.Controls.ScrollViewer.IsDeferredScrollingEnabled%2A>, ekli bir özelliktir ve <xref:System.Windows.Controls.ScrollViewer> ve denetim şablonunda <xref:System.Windows.Controls.ScrollViewer> olan herhangi bir denetimde ayarlanabilir.

## <a name="controls-that-implement-performance-features"></a>Performans özelliklerini uygulayan denetimler

Aşağıdaki tabloda, verileri görüntülemek için ortak denetimler ve performans özellikleri desteği listelenmektedir. Bu özelliklerin nasıl etkinleştirileceği hakkında bilgi için önceki bölümlere bakın.

|Denetim|Sanallaştırma|Kapsayıcı geri dönüştürme|Ertelenmiş kaydırma|
|-------------|--------------------|-------------------------|------------------------|
|<xref:System.Windows.Controls.ComboBox>|Etkinleştirilebilir|Etkinleştirilebilir|Etkinleştirilebilir|
|<xref:System.Windows.Controls.ContextMenu>|Etkinleştirilebilir|Etkinleştirilebilir|Etkinleştirilebilir|
|<xref:System.Windows.Controls.DocumentViewer>|Yok|Yok|Etkinleştirilebilir|
|<xref:System.Windows.Controls.ListBox>|Varsayılan|Etkinleştirilebilir|Etkinleştirilebilir|
|<xref:System.Windows.Controls.ListView>|Varsayılan|Etkinleştirilebilir|Etkinleştirilebilir|
|<xref:System.Windows.Controls.TreeView>|Etkinleştirilebilir|Etkinleştirilebilir|Etkinleştirilebilir|
|<xref:System.Windows.Controls.ToolBar>|Yok|Yok|Etkinleştirilebilir|

> [!NOTE]
> <xref:System.Windows.Controls.TreeView>sanallaştırma ve kapsayıcı geri dönüşümünü etkinleştirme örneği için bkz. [bir TreeView 'un performansını geliştirme](../controls/how-to-improve-the-performance-of-a-treeview.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Düzen](layout.md)
- [Düzen ve Tasarım](optimizing-performance-layout-and-design.md)
- [Veri Bağlama](optimizing-performance-data-binding.md)
- [Denetimler](../controls/index.md)
- [Stil ve Şablon Oluşturma](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [İzlenecek yol: WPF Uygulamasında Uygulama Verilerini Önbelleğe Alma](walkthrough-caching-application-data-in-a-wpf-application.md)
