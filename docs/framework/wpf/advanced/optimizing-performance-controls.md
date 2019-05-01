---
title: 'Performansı iyileştirme: Denetimler - WPF'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], improving performance
- container recycling [WPF]
- user interface virtualization [WPF]
ms.assetid: 45a31c43-ea8a-4546-96c8-0631b9934179
ms.openlocfilehash: 20b2b20c2f7f37b4ae01159e70bc8c0945777152
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61961401"
---
# <a name="optimizing-performance-controls"></a>Performansı iyileştirme: Denetimler

Windows Presentation Foundation (WPF) çoğu Windows uygulamalarında kullanılan ortak bir kullanıcı arabirimi (UI) bileşenleri çoğunu içerir. Bu konu, UI performansını iyileştirme tekniklerini içerir.

## <a name="displaying-large-data-sets"></a>Büyük veri kümelerini görüntüleme

WPF denetimleri gibi <xref:System.Windows.Controls.ListView> ve <xref:System.Windows.Controls.ComboBox> öğe listeleri içeren bir uygulamada görüntülemek için kullanılır. Görüntülemek için listede büyükse, uygulamanın performansı etkilenebilir. Bu, Standart Düzen sistemi liste denetimi ile ilişkili her öğe için bir düzen kapsayıcısı oluşturur çünkü ve Düzen boyutunu ve konumunu hesaplar. Genellikle, aynı anda tüm öğeleri görüntülemek gerekmez; Bunun yerine, bir alt kümesini görüntüleme ve kullanıcı listede kaydırma. Bu durumda, kullanıcı arabirimini kullanarak mantıklıdır *sanallaştırma*, öğe container oluşturulması anlamına gelir ve bir öğe öğesi görünene kadar ertelenmiştir için Düzen hesaplama ilişkili.

Kullanıcı Arabirimi sanallaştırma, liste denetimleri, önemli bir yönüdür. Kullanıcı Arabirimi sanallaştırma verileri sanallaştırma ile karıştırılmamalıdır. Kullanıcı Arabirimi sanallaştırma depoları yalnızca görünen öğeler bellekte ancak veri bağlama senaryosunda tüm veri yapısını bellekte depolar. Buna karşılık, veri sanallaştırma bellekte ekranda görünür olan veri öğeleri depolar.

Varsayılan olarak, kullanıcı Arabirimi sanallaştırma için etkin <xref:System.Windows.Controls.ListView> ve <xref:System.Windows.Controls.ListBox> , liste öğelerini veriye bağlıyken denetler. <xref:System.Windows.Controls.TreeView> Sanallaştırma ayarlayarak etkinleştirilebilir <xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizing%2A?displayProperty=nameWithType> özelliğine bağlı `true`. Öğesinden türetilen özel denetimler için UI sanallaştırmasını etkinleştirmek istiyorsanız <xref:System.Windows.Controls.ItemsControl> ya da var olan öğe denetimleri kullanan <xref:System.Windows.Controls.StackPanel> gibi sınıf <xref:System.Windows.Controls.ComboBox>, ayarlayabileceğiniz <xref:System.Windows.Controls.ItemsControl.ItemsPanel%2A> için <xref:System.Windows.Controls.VirtualizingStackPanel> ayarlayıp <xref:System.Windows.Controls.VirtualizingPanel.IsVirtualizing%2A> için`true`. Ne yazık ki, bu denetimler için kullanıcı Arabirimi sanallaştırma fark etmeden devre dışı bırakabilirsiniz. Devre dışı kullanıcı Arabirimi sanallaştırma koşulların listesi verilmiştir.

- Öğe kapsayıcılarını doğrudan eklenir <xref:System.Windows.Controls.ItemsControl>. Örneğin, bir uygulamayı açıkça eklerse <xref:System.Windows.Controls.ListBoxItem> nesneleri için bir <xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.ListBox> değil sanallaştırmak <xref:System.Windows.Controls.ListBoxItem> nesneleri.

- Öğe kapsayıcı <xref:System.Windows.Controls.ItemsControl> farklı türlere sahip. Örneğin, bir <xref:System.Windows.Controls.Menu> kullanan <xref:System.Windows.Controls.Separator> nesneleri, çünkü öğe geri dönüştürme uygulayamaz <xref:System.Windows.Controls.Menu> türünde nesneler içeren <xref:System.Windows.Controls.Separator> ve <xref:System.Windows.Controls.MenuItem>.

- Ayarı <xref:System.Windows.Controls.ScrollViewer.CanContentScroll%2A> için `false`.

- Ayarı <xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizing%2A> için `false`.

Öğe kapsayıcılarını sanallaştırmak olduğunda önemli bir husus ek durum bilgileri ile öğenin ait olduğu öğe kapsayıcı ile ilişkili olup ' dir. Bu durumda, ek durum kaydetmeniz gerekir. Örneğin, bulunan öğeyi olabilir bir <xref:System.Windows.Controls.Expander> denetimi ve <xref:System.Windows.Controls.Expander.IsExpanded%2A> durumu bağlı öğenin kapsayıcısı ve öğenin kendisi için değil. Ne zaman kapsayıcıyı yeniden kullanılabilir bir yeni öğe için geçerli değerini <xref:System.Windows.Controls.Expander.IsExpanded%2A> yeni öğe için kullanılır. Ayrıca, eski öğesi doğru kaybeder <xref:System.Windows.Controls.Expander.IsExpanded%2A> değeri.

Şu anda hiçbir WPF denetimleri veri sanallaştırma için yerleşik destek sunar.

## <a name="container-recycling"></a>Kapsayıcı geri dönüşümü

.NET Framework 3.5 SP1 devralınan denetimler için eklenen kullanıcı Arabirimi sanallaştırma iyileştirme <xref:System.Windows.Controls.ItemsControl> olduğu *kapsayıcı geri dönüşümü* , ayrıca kayan performansı geliştirebilir. Olduğunda bir <xref:System.Windows.Controls.ItemsControl> kullanan kullanıcı Arabirimi sanallaştırma eklendiğinden, görünüm dışına kaydırdığında her öğe için öğe kapsayıcısı yok eder ve kayan görünüme her öğe için bir öğe kapsayıcı oluşturur. *Kapsayıcı geri dönüşümü* öğe kapsayıcılarını değil, sürekli olarak oluşturulur ve kullanıcı sonuçlarda yok, farklı veri öğeleri için var olan öğe kapsayıcılarını yeniden denetim sağlayan <xref:System.Windows.Controls.ItemsControl>. Ayarlayarak geri dönüştürme öğesini etkinleştirmek seçebileceğiniz <xref:System.Windows.Controls.VirtualizingPanel.VirtualizationMode%2A> özelliğine bağlı <xref:System.Windows.Controls.VirtualizationMode.Recycling>.

Tüm <xref:System.Windows.Controls.ItemsControl> destekleyen sanallaştırma kapsayıcı geri dönüşümü kullanabilirsiniz. Bir örneği üzerinde kapsayıcı geri dönüşümü etkinleştirmek nasıl bir <xref:System.Windows.Controls.ListBox>, bakın [ListBox'ın kaydırma performansını](../controls/how-to-improve-the-scrolling-performance-of-a-listbox.md).

## <a name="supporting-bidirectional-virtualization"></a>Çift yönlü sanallaştırma destekleme

<xref:System.Windows.Controls.VirtualizingStackPanel> yatay veya dikey yönde bir kullanıcı Arabirimi sanallaştırma için yerleşik destek sunar. Çift yönlü sanallaştırma denetimleriniz için kullanmak istiyorsanız, genişleten bir özel panel uygulamalıdır <xref:System.Windows.Controls.VirtualizingStackPanel> sınıfı. <xref:System.Windows.Controls.VirtualizingStackPanel> Sınıfı gösterir sanal yöntemler gibi <xref:System.Windows.Controls.VirtualizingStackPanel.OnViewportSizeChanged%2A>, <xref:System.Windows.Controls.VirtualizingStackPanel.LineUp%2A>, <xref:System.Windows.Controls.VirtualizingStackPanel.PageUp%2A>, ve <xref:System.Windows.Controls.VirtualizingStackPanel.MouseWheelUp%2A>. Bu sanal yöntemler, bir liste görünür kısmında bir değişikliği algılar ve uygun şekilde işlemelidir sağlar.

## <a name="optimizing-templates"></a>Şablonları en iyi duruma getirme

Görsel ağacı, uygulamadaki tüm görsel öğeleri içerir. Doğrudan oluşturulan nesnelerin yanı sıra, ayrıca şablon genişletmesi nedeniyle nesneleri içerir. Örneğin, oluşturduğunuzda bir <xref:System.Windows.Controls.Button>, ayrıca Al <xref:Microsoft.Windows.Themes.ClassicBorderDecorator> ve <xref:System.Windows.Controls.ContentPresenter> görsel ağaç nesneleri. Denetim şablonlarınızı iyileştirilmiş yapmadıysanız, fazladan gereksiz nesneleri birçok görsel ağaçta oluşturuyor olabilir. Görsel ağacı hakkında daha fazla bilgi için bkz. [WPF Grafik işlemeye genel bakış](../graphics-multimedia/wpf-graphics-rendering-overview.md).

## <a name="deferred-scrolling"></a>Kaydırma ertelendi

Kullanıcı bir scrollbar üzerinde parmak sürüklediğinde, varsayılan olarak, içerik görünümü sürekli olarak güncelleştirir. Kaydırma denetiminizi yavaşsa, kaydırma kullanarak ertelenmiş göz önünde bulundurun. Yalnızca kullanıcı thumb bıraktığında kaydırma ertelenmiş, içerik güncelleştirildi.

Ertelenmiş kaydırma uygulamak için ayarlanmış <xref:System.Windows.Controls.ScrollViewer.IsDeferredScrollingEnabled%2A> özelliğini `true`. <xref:System.Windows.Controls.ScrollViewer.IsDeferredScrollingEnabled%2A> bağlı bir özelliktir ve ayarlanabilir <xref:System.Windows.Controls.ScrollViewer> ve sahip herhangi bir denetime bir <xref:System.Windows.Controls.ScrollViewer> onun Denetim şablonunda.

## <a name="controls-that-implement-performance-features"></a>Performans özelliklerini uygulama denetimleri

Aşağıdaki tabloda, verileri ve Destek performans özelliklerini görüntülemek için ortak denetimleri listeler. Bu özellikleri etkinleştirme hakkında bilgi için önceki bölümlere bakın.

|Denetim|Sanallaştırma|Kapsayıcı geri dönüşümü|Kaydırma ertelendi|
|-------------|--------------------|-------------------------|------------------------|
|<xref:System.Windows.Controls.ComboBox>|Etkin hale getirilebilir|Etkin hale getirilebilir|Etkin hale getirilebilir|
|<xref:System.Windows.Controls.ContextMenu>|Etkin hale getirilebilir|Etkin hale getirilebilir|Etkin hale getirilebilir|
|<xref:System.Windows.Controls.DocumentViewer>|Yok|Yok|Etkin hale getirilebilir|
|<xref:System.Windows.Controls.ListBox>|Varsayılan|Etkin hale getirilebilir|Etkin hale getirilebilir|
|<xref:System.Windows.Controls.ListView>|Varsayılan|Etkin hale getirilebilir|Etkin hale getirilebilir|
|<xref:System.Windows.Controls.TreeView>|Etkin hale getirilebilir|Etkin hale getirilebilir|Etkin hale getirilebilir|
|<xref:System.Windows.Controls.ToolBar>|Yok|Yok|Etkin hale getirilebilir|

> [!NOTE]
> Sanallaştırma ve kapsayıcı üzerinde geri dönüşümü etkinleştirmek nasıl bir örnek için bir <xref:System.Windows.Controls.TreeView>, bkz: [TreeView'ın performansını](../controls/how-to-improve-the-performance-of-a-treeview.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Düzen](layout.md)
- [Düzen ve Tasarım](optimizing-performance-layout-and-design.md)
- [Veri Bağlama](optimizing-performance-data-binding.md)
- [Denetimler](../controls/index.md)
- [Stil ve Şablon Oluşturma](../controls/styling-and-templating.md)
- [İzlenecek yol: Bir WPF uygulamasında uygulama verilerini önbelleğe alma](walkthrough-caching-application-data-in-a-wpf-application.md)