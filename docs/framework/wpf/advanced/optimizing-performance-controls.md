---
title: Denetim performansını iyileştirme
description: Windows Presentation Foundation çoğu Windows uygulamasında kullanılan birçok ortak bileşeni içerir. Kullanıcı arabirimi performansını geliştirmeyi öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], improving performance
- container recycling [WPF]
- user interface virtualization [WPF]
ms.assetid: 45a31c43-ea8a-4546-96c8-0631b9934179
ms.openlocfilehash: de348dd93e5710b5b81af035ec7aa56e01dc4981
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168307"
---
# <a name="optimizing-performance-controls"></a>Performansı İyileştirme: denetimler

Windows Presentation Foundation (WPF), çoğu Windows uygulamasında kullanılan birçok ortak kullanıcı arabirimi (UI) bileşenini içerir. Bu konu, UI 'nizin performansını iyileştirmeye yönelik teknikler içerir.

## <a name="displaying-large-data-sets"></a>Büyük veri kümelerini görüntüleme

Ve gibi WPF denetimleri, <xref:System.Windows.Controls.ListView> <xref:System.Windows.Controls.ComboBox> bir uygulamadaki öğelerin listesini göstermek için kullanılır. Görüntülenecek liste büyükse, uygulamanın performansı etkilenebilir. Bunun nedeni, standart düzen sisteminin liste denetimiyle ilişkili her öğe için bir düzen kapsayıcısı oluşturması ve düzen boyutunu ve konumunu hesaplamasıdır. Genellikle, tüm öğeleri aynı anda göstermek zorunda değilsiniz; Bunun yerine, bir alt küme görüntüler ve Kullanıcı listede kaydırılır. Bu durumda, UI *sanallaştırmayı*kullanmak mantıklı olur, bu, öğe için öğe kapsayıcısı oluşturma ve ilişkili düzen hesaplamasının, öğe görünene kadar ertelenmesi anlamına gelir.

UI Sanallaştırması liste denetimlerinin önemli bir yönüdür. UI Sanallaştırması veri sanallaştırmayla karıştırılmamalıdır. UI Sanallaştırması yalnızca bellekteki görünür öğeleri depolar, ancak veri bağlama senaryosunda veri yapısının tamamını bellekte depolar. Buna karşılık, veri sanallaştırma yalnızca bellekte ekranda görünür olan veri öğelerini depolar.

Varsayılan olarak, <xref:System.Windows.Controls.ListView> <xref:System.Windows.Controls.ListBox> liste öğeleri veriye bağlandığında, ve DENETIMLERI için UI Sanallaştırması etkindir. <xref:System.Windows.Controls.TreeView>Sanallaştırma, <xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizing%2A?displayProperty=nameWithType> ekli özelliği olarak ayarlanarak etkinleştirilebilir `true` . Sınıfını kullanan özel denetimler için UI sanallaştırmayı etkinleştirmek istiyorsanız (örneğin, gibi), öğesini <xref:System.Windows.Controls.ItemsControl> <xref:System.Windows.Controls.StackPanel> olarak <xref:System.Windows.Controls.ComboBox> ayarlayabilir <xref:System.Windows.Controls.ItemsControl.ItemsPanel%2A> ve olarak <xref:System.Windows.Controls.VirtualizingStackPanel> ayarlayabilirsiniz <xref:System.Windows.Controls.VirtualizingPanel.IsVirtualizing%2A> `true` . Ne yazık ki, bu denetimler için UI sanallaştırmayı uygulamadan devre dışı bırakabilirsiniz. Aşağıda, UI sanallaştırmayı devre dışı bırakan koşulların bir listesi verilmiştir.

- Öğe kapsayıcıları doğrudan öğesine eklenir <xref:System.Windows.Controls.ItemsControl> . Örneğin, bir uygulama öğesine açıkça nesne eklerse <xref:System.Windows.Controls.ListBoxItem> <xref:System.Windows.Controls.ListBox> , <xref:System.Windows.Controls.ListBox> nesneleri sanallaştırmaz <xref:System.Windows.Controls.ListBoxItem> .

- İçindeki öğe kapsayıcıları <xref:System.Windows.Controls.ItemsControl> farklı türlerdir. Örneğin, <xref:System.Windows.Controls.Menu> nesneleri kullanan bir <xref:System.Windows.Controls.Separator> öğesi, <xref:System.Windows.Controls.Menu> ve türünde nesneler içerdiğinden öğe geri dönüşümü uygulayamaz <xref:System.Windows.Controls.Separator> <xref:System.Windows.Controls.MenuItem> .

- <xref:System.Windows.Controls.ScrollViewer.CanContentScroll%2A>Olarak ayarlanıyor `false` .

- <xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizing%2A>Olarak ayarlanıyor `false` .

Öğe kapsayıcılarını sanallaştırdığınızda önemli bir önemi, öğe ile ilgili olan bir öğe kapsayıcısı ile ilişkili ek durum bilgilerinizin olmasına bakılmaksızın. Bu durumda, ek durumu kaydetmeniz gerekir. Örneğin, bir denetimde bulunan bir öğeye sahip olabilirsiniz <xref:System.Windows.Controls.Expander> ve <xref:System.Windows.Controls.Expander.IsExpanded%2A> durum öğenin kendine değil öğenin kapsayıcısına bağlanır. Kapsayıcı yeni bir öğe için tekrar kullanıldığında, geçerli değeri <xref:System.Windows.Controls.Expander.IsExpanded%2A> Yeni öğe için kullanılır. Ayrıca, eski öğe doğru <xref:System.Windows.Controls.Expander.IsExpanded%2A> değeri kaybeder.

Şu anda, veri sanallaştırma için yerleşik destek sunan WPF denetimleri yoktur.

## <a name="container-recycling"></a>Kapsayıcı geri dönüştürme

Öğesinden kalıtımla alan denetim için .NET Framework 3,5 SP1 'e en iyi duruma getirme, <xref:System.Windows.Controls.ItemsControl> kayan performansı de iyileştirebilen *kapsayıcı geri Dönüşümleridir* . <xref:System.Windows.Controls.ItemsControl>UI sanallaştırmayı kullanan bir öğesi doldurulduktan sonra, Görünüm ' ü kaydıran her öğe için bir öğe kapsayıcısı oluşturur ve görünümün dışında kaydığı her öğe için öğe kapsayıcısını yok eder. *Kapsayıcı geri dönüştürme* , denetimin farklı veri öğeleri için varolan öğe kapsayıcılarını yeniden kullanmasına olanak sağlar. böylece, Kullanıcı tarafından kaydırıldığında öğe kapsayıcıları sürekli olarak oluşturulmaz ve yok edilir <xref:System.Windows.Controls.ItemsControl> . İliştirilmiş özelliği ' ye ayarlayarak öğe geri dönüşümünü etkinleştirmeyi seçebilirsiniz <xref:System.Windows.Controls.VirtualizingPanel.VirtualizationMode%2A> <xref:System.Windows.Controls.VirtualizationMode.Recycling> .

<xref:System.Windows.Controls.ItemsControl>Sanallaştırmayı destekleyen her türlü, kapsayıcı geri dönüşümü kullanabilir. Bir üzerinde kapsayıcı geri dönüşümünü nasıl etkinleştireceğiniz hakkında bir örnek için <xref:System.Windows.Controls.ListBox> bkz. [ListBox 'ın kayan performansını geliştirme](../controls/how-to-improve-the-scrolling-performance-of-a-listbox.md).

## <a name="supporting-bidirectional-virtualization"></a>Çift yönlü sanallaştırmayı destekleme

<xref:System.Windows.Controls.VirtualizingStackPanel>UI Sanallaştırması için yatay veya dikey olarak bir yönde yerleşik destek sunar. Denetimleriniz için çift yönlü sanallaştırma kullanmak istiyorsanız, sınıfı genişleten özel bir panel uygulamanız gerekir <xref:System.Windows.Controls.VirtualizingStackPanel> . <xref:System.Windows.Controls.VirtualizingStackPanel>Sınıfı,,, ve gibi sanal yöntemler sunar <xref:System.Windows.Controls.VirtualizingStackPanel.OnViewportSizeChanged%2A> <xref:System.Windows.Controls.VirtualizingStackPanel.LineUp%2A> <xref:System.Windows.Controls.VirtualizingStackPanel.PageUp%2A> <xref:System.Windows.Controls.VirtualizingStackPanel.MouseWheelUp%2A> . Bu sanal yöntemler, listenin görünür bölümündeki bir değişikliği algılamanıza ve buna uygun şekilde işleme sağlar.

## <a name="optimizing-templates"></a>Şablonları iyileştirme

Görsel ağaç, bir uygulamadaki tüm görsel öğeleri içerir. Doğrudan oluşturulan nesnelere ek olarak, şablon genişletmesinden kaynaklanan nesneler de bulunur. Örneğin, oluşturduğunuzda <xref:System.Windows.Controls.Button> , ayrıca <xref:Microsoft.Windows.Themes.ClassicBorderDecorator> <xref:System.Windows.Controls.ContentPresenter> görsel ağaçtaki nesneleri de alır. Denetim şablonlarınızı en iyi duruma almadıysanız, görsel ağaçta çok fazla sayıda gereksiz nesne oluşturuyor olabilirsiniz. Görsel ağaç hakkında daha fazla bilgi için bkz. [WPF Grafik Işlemeye genel bakış](../graphics-multimedia/wpf-graphics-rendering-overview.md).

## <a name="deferred-scrolling"></a>Ertelenmiş kaydırma

Varsayılan olarak, Kullanıcı Thumb öğesini bir ScrollBar üzerine sürüklediğinde içerik görünümü sürekli olarak güncellenir. Denetiminiz içinde kaydırma yavaşsa, ertelenmiş kaydırma kullanmayı düşünün. Ertelenmiş kaydırma ' de, içerik yalnızca Kullanıcı Thumb 'i yayınlarsa güncelleştirilir.

Ertelenmiş kaydırma uygulamak için <xref:System.Windows.Controls.ScrollViewer.IsDeferredScrollingEnabled%2A> özelliğini olarak ayarlayın `true` . <xref:System.Windows.Controls.ScrollViewer.IsDeferredScrollingEnabled%2A>, ekli bir özelliktir ve üzerinde <xref:System.Windows.Controls.ScrollViewer> ve denetim şablonunda bir olan herhangi bir denetime ayarlanabilir <xref:System.Windows.Controls.ScrollViewer> .

## <a name="controls-that-implement-performance-features"></a>Performans özelliklerini uygulayan denetimler

Aşağıdaki tabloda, verileri görüntülemek için ortak denetimler ve performans özellikleri desteği listelenmektedir. Bu özelliklerin nasıl etkinleştirileceği hakkında bilgi için önceki bölümlere bakın.

|Denetim|Sanallaştırma|Kapsayıcı geri dönüştürme|Ertelenmiş kaydırma|
|-------------|--------------------|-------------------------|------------------------|
|<xref:System.Windows.Controls.ComboBox>|Etkinleştirilebilir|Etkinleştirilebilir|Etkinleştirilebilir|
|<xref:System.Windows.Controls.ContextMenu>|Etkinleştirilebilir|Etkinleştirilebilir|Etkinleştirilebilir|
|<xref:System.Windows.Controls.DocumentViewer>|Kullanılamaz|Kullanılamaz|Etkinleştirilebilir|
|<xref:System.Windows.Controls.ListBox>|Varsayılan|Etkinleştirilebilir|Etkinleştirilebilir|
|<xref:System.Windows.Controls.ListView>|Varsayılan|Etkinleştirilebilir|Etkinleştirilebilir|
|<xref:System.Windows.Controls.TreeView>|Etkinleştirilebilir|Etkinleştirilebilir|Etkinleştirilebilir|
|<xref:System.Windows.Controls.ToolBar>|Kullanılamaz|Kullanılamaz|Etkinleştirilebilir|

> [!NOTE]
> Bir üzerinde sanallaştırma ve kapsayıcı geri dönüşümünü etkinleştirme örneği için <xref:System.Windows.Controls.TreeView> bkz. [bir TreeView 'un performansını geliştirme](../controls/how-to-improve-the-performance-of-a-treeview.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Düzen](layout.md)
- [Düzen ve Tasarım](optimizing-performance-layout-and-design.md)
- [Veri Bağlama](optimizing-performance-data-binding.md)
- [Denetimler](../controls/index.md)
- [Stil ve Şablon Oluşturma](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [İzlenecek yol: WPF Uygulamasında Uygulama Verilerini Önbelleğe Alma](walkthrough-caching-application-data-in-a-wpf-application.md)
