---
title: "Performansı İyileştirme: Denetimler"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [WPF], improving performance
- container recycling [WPF]
- user interface virtualization [WPF]
ms.assetid: 45a31c43-ea8a-4546-96c8-0631b9934179
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d1b414aee19082196ab242706c7730c031cf3a76
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="optimizing-performance-controls"></a>Performansı İyileştirme: Denetimler
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]çok kullanılan ortak kullanıcı arabirimi (UI) bileşenlerinin çoğu Windows uygulamalarında içerir. Bu konu, kullanıcı Arabirimi performansını iyileştirme tekniklerini içerir.  
  
 
  
<a name="Displaying"></a>   
## <a name="displaying-large-data-sets"></a>Büyük veri kümelerinde görüntüleme  
 WPF denetimleri gibi <xref:System.Windows.Controls.ListView> ve <xref:System.Windows.Controls.ComboBox> bir uygulamada öğeleri listesini görüntülemek için kullanılır. Görüntülemek için listede büyükse, uygulamanızın performansı etkilenebilir. Bu standart düzen sistemi liste denetimi ile ilişkilendirilmiş her öğe için bir düzen kapsayıcı oluşturduğundan ve düzeni boyutunu ve konumunu hesaplar. Genellikle, aynı anda tüm öğeleri görüntülemek gerekmez; Bunun yerine bir alt görüntülemek ve kullanıcı listesi ile birlikte kayar. Bu durumda, kullanıcı arabirimini kullanmak üzere mantıklıdır *sanallaştırma*, öğesi kapsayıcı oluşturma anlamına gelir ve bir öğe öğesi görünene kadar ertelenir için Düzen hesaplama ilişkilendirilmiş.  
  
 UI sanallaştırma liste denetimleri önemli bir yönüdür. UI sanallaştırma veri sanallaştırma ile karıştırılmamalıdır. UI sanallaştırma depoları yalnızca görünen öğeleri bellek ancak veri bağlama senaryosu tüm veri yapısı bellekte depolar. Buna karşılık, veri sanallaştırma bellekte ekranında görünür olan veri öğeleri depolar.  
  
 Varsayılan olarak UI sanallaştırma için etkin <xref:System.Windows.Controls.ListView> ve <xref:System.Windows.Controls.ListBox> , liste öğelerini veriye bağlıyken denetler. <xref:System.Windows.Controls.TreeView>Sanallaştırma ayarlayarak etkinleştirilebilir <!--zz <xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizing%2A?displayProperty=nameWithType> --> `IsVirtualizing` özelliğine bağlı `true`. Öğesinden türetilen özel denetimler için UI sanallaştırma etkinleştirmek isteyip istemediğinizi <xref:System.Windows.Controls.ItemsControl> ya da var olan öğeyi denetimleri kullanan <xref:System.Windows.Controls.StackPanel> gibi sınıfı <xref:System.Windows.Controls.ComboBox>, ayarlayabileceğiniz <xref:System.Windows.Controls.ItemsControl.ItemsPanel%2A> için <xref:System.Windows.Controls.VirtualizingStackPanel> ve <xref:System.Windows.Controls.VirtualizingPanel.IsVirtualizing%2A> için`true`. Ne yazık ki, bu denetimler için UI sanallaştırma kullanıldıklarını olmadan devre dışı bırakabilirsiniz. Bir kullanıcı Arabirimi sanallaştırmayı devre dışı koşullar listesi verilmiştir.  
  
-   Öğe kapsayıcılarını doğrudan eklenir <xref:System.Windows.Controls.ItemsControl>. Örneğin, bir uygulama açıkça eklerse <xref:System.Windows.Controls.ListBoxItem> nesneleri için bir <xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.ListBox> değil sanallaştırmak <xref:System.Windows.Controls.ListBoxItem> nesneleri.  
  
-   Öğe kapsayıcılarını <xref:System.Windows.Controls.ItemsControl> farklı türde. Örneğin, bir <xref:System.Windows.Controls.Menu> kullanan <xref:System.Windows.Controls.Separator> nesneleri, çünkü madde geri dönüştürme uygulayamaz <xref:System.Windows.Controls.Menu> türünde nesneler içeren <xref:System.Windows.Controls.Separator> ve <xref:System.Windows.Controls.MenuItem>.  
  
-   Ayarı <xref:System.Windows.Controls.ScrollViewer.CanContentScroll%2A> için `false`.  
  
-   Ayarı <!--zz <xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizing%2A>--> `IsVirtualizing` için `false`.    
  
 Öğe kapsayıcılarını sanallaştırmanızı, önemli bir öğesiyle ait bir öğe kapsayıcı ile ilişkili ek durum bilgileri yüklü olup olmadığını konudur. Bu durumda, ek durum kaydetmeniz gerekir. Örneğin, bir öğe içinde yer alan olabilir bir <xref:System.Windows.Controls.Expander> denetim ve <xref:System.Windows.Controls.Expander.IsExpanded%2A> durum öğesi'nin kapsayıcısı ve öğesi için bağlı. Ne zaman kapsayıcı yeniden kullanılabilir, geçerli değeri gibi yeni bir öğe için <xref:System.Windows.Controls.Expander.IsExpanded%2A> yeni öğe için kullanılır. Buna ek olarak, eski öğe doğru kaybederse <xref:System.Windows.Controls.Expander.IsExpanded%2A> değeri.  
  
 Şu anda hiçbir WPF denetimleri veri sanallaştırma için yerleşik destek sunar.  
  
<a name="Container"></a>   
## <a name="container-recycling"></a>Kapsayıcı geri dönüşümü  
 Bir en iyi duruma getirme devralınmalıdır denetimleri için .NET Framework 3.5 SP1 eklenen UI sanallaştırma <xref:System.Windows.Controls.ItemsControl> olan *kapsayıcı geri dönüşümü* , ayrıca kaydırma performansı geliştirebilir.  Zaman bir <xref:System.Windows.Controls.ItemsControl> kullandığı UI sanallaştırma doldurulur, kayarak görünüme ve görünüm dışına kaydırdığında her bir öğe için öğe kapsayıcısı yok eder her öğe için bir öğe kapsayıcı oluşturur. *Kapsayıcı geri dönüştürme* öğe kapsayıcılarını değil sürekli olarak oluşturulur ve kullanıcı kayarken yok böylece farklı veri öğeleri için var olan öğe kapsayıcılarını yeniden denetimi sağlar <xref:System.Windows.Controls.ItemsControl>. Öğeyi ayarlayarak geri dönüştürülmesini etkinleştirmek seçebileceğiniz <xref:System.Windows.Controls.VirtualizingPanel.VirtualizationMode%2A> özelliğine bağlı <xref:System.Windows.Controls.VirtualizationMode.Recycling>.  
  
 Tüm <xref:System.Windows.Controls.ItemsControl> destekleyen sanallaştırma kapsayıcı geri dönüşümü kullanabilirsiniz.  Kapsayıcı üzerinde geri dönüşümünü etkinleştirmek nasıl bir örneği için bir <xref:System.Windows.Controls.ListBox>, bkz: [ListBox kaydırma performansı](../../../../docs/framework/wpf/controls/how-to-improve-the-scrolling-performance-of-a-listbox.md).  
  
<a name="Supporting"></a>   
## <a name="supporting-bidirectional-virtualization"></a>Çift yönlü sanallaştırma destekleme  
 <xref:System.Windows.Controls.VirtualizingStackPanel>yatay veya dikey bir yönde UI sanallaştırma için yerleşik destek sunar. Çift yönlü sanallaştırma denetimleriniz için kullanmak istiyorsanız, genişleten bir özel panel uygulamalıdır <xref:System.Windows.Controls.VirtualizingStackPanel> sınıfı. <xref:System.Windows.Controls.VirtualizingStackPanel> Sınıfı sunar sanal yöntemler gibi <xref:System.Windows.Controls.VirtualizingStackPanel.OnViewportSizeChanged%2A>, <xref:System.Windows.Controls.VirtualizingStackPanel.LineUp%2A>, <xref:System.Windows.Controls.VirtualizingStackPanel.PageUp%2A>, ve <xref:System.Windows.Controls.VirtualizingStackPanel.MouseWheelUp%2A>. Bu sanal yöntemleri bir liste görünür bölümünde bir değişikliği algılar ve uygun şekilde işlemesine olanak sağlar.  
  
<a name="Optimizing"></a>   
## <a name="optimizing-templates"></a>Şablonları en iyi duruma getirme  
 Görsel ağaç bir uygulamadaki tüm görsel öğeleri içerir.  Doğrudan oluşturulan nesnelerin yanı sıra, şablon genişletme nedeniyle nesnelerin de içerir.  Örneğin, oluşturduğunuzda bir <xref:System.Windows.Controls.Button>, ayrıca elde edersiniz <xref:Microsoft.Windows.Themes.ClassicBorderDecorator> ve <xref:System.Windows.Controls.ContentPresenter> görsel ağaçtaki nesneleri.  Denetim şablonlarınızı iyileştirilmiş yapmadıysanız, çok fazla gereksiz nesnelerin görsel ağaçta oluşturuyor olabilir.   Görsel ağaç hakkında daha fazla bilgi için bkz: [WPF Grafik işleme genel bakış](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md).  
  
<a name="Deferred"></a>   
## <a name="deferred-scrolling"></a>Kaydırma ertelenmiş  
 Kullanıcı bir kaydırma çubuğu üzerinde kaydırma sürüklendiğinde varsayılan olarak, içerik görünümü sürekli olarak güncelleştirir.  Kaydırma, denetiminde yavaşsa, kullanarak kaydırma ertelenmiş göz önünde bulundurun.  Yalnızca kullanıcı kaydırma bıraktığında ertelenmiş kaydırma içinde içerik güncelleştirilir.  
  
 Ertelenmiş kaydırma uygulamak için ayarlanmış <xref:System.Windows.Controls.ScrollViewer.IsDeferredScrollingEnabled%2A> özelliğine `true`.  <xref:System.Windows.Controls.ScrollViewer.IsDeferredScrollingEnabled%2A>bağlı bir özelliktir ve ayarlanabilen <xref:System.Windows.Controls.ScrollViewer> ve sahip herhangi bir denetimi bir <xref:System.Windows.Controls.ScrollViewer> , Denetim şablondaki.  
  
<a name="Controls"></a>   
## <a name="controls-that-implement-performance-features"></a>Performans özellikleri uygulamak denetimleri  
 Aşağıdaki tabloda, verileri ve Destek performans özellikleri görüntülemek için ortak denetimler listeler.  Bu özellikleri etkinleştirme konusunda bilgi için önceki bölümlerde bakın.  
  
|Denetim|Sanallaştırma|Kapsayıcı geri dönüşümü|Kaydırma ertelenmiş|  
|-------------|--------------------|-------------------------|------------------------|  
|<xref:System.Windows.Controls.ComboBox>|Etkinleştirilebilir|Etkinleştirilebilir|Etkinleştirilebilir|  
|<xref:System.Windows.Controls.ContextMenu>|Etkinleştirilebilir|Etkinleştirilebilir|Etkinleştirilebilir|  
|<xref:System.Windows.Controls.DocumentViewer>|Yok|Yok|Etkinleştirilebilir|  
|<xref:System.Windows.Controls.ListBox>|Varsayılan|Etkinleştirilebilir|Etkinleştirilebilir|  
|<xref:System.Windows.Controls.ListView>|Varsayılan|Etkinleştirilebilir|Etkinleştirilebilir|  
|<xref:System.Windows.Controls.TreeView>|Etkinleştirilebilir|Etkinleştirilebilir|Etkinleştirilebilir|  
|<xref:System.Windows.Controls.ToolBar>|Yok|Yok|Etkinleştirilebilir|  
  
> [!NOTE]
>  Sanallaştırma ve kapsayıcı üzerinde geri dönüşümü etkinleştirme örneği için bir <xref:System.Windows.Controls.TreeView>, bkz: [TreeView performansını](../../../../docs/framework/wpf/controls/how-to-improve-the-performance-of-a-treeview.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Düzen](../../../../docs/framework/wpf/advanced/layout.md)  
 [Düzen ve tasarım](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)  
 [Veri bağlama](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)  
 [Denetimleri](../../../../docs/framework/wpf/controls/index.md)  
 [Stil ve şablon oluşturma](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [İzlenecek yol: Bir WPF uygulamasında uygulama verileri önbelleğe alma](../../../../docs/framework/wpf/advanced/walkthrough-caching-application-data-in-a-wpf-application.md)
