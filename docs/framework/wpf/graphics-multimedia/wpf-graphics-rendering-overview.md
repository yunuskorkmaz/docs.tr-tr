---
title: Grafik işlemeye genel bakış
description: Her nesnenin Windows Presentation Foundation (WPF) türettiği temel grafik işleme sınıfının rolü hakkında bilgi edinin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], rendering
- rendering graphics [WPF]
ms.assetid: 6dec9657-4d8c-4e46-8c54-40fb80008265
ms.openlocfilehash: 96a7ea999f27e89dc22c10329214de7e3fa60341
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853628"
---
# <a name="wpf-graphics-rendering-overview"></a>WPF Grafik İşlemeye Genel Bakış
Bu konuda görsel katmana genel bakış sunulmaktadır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] . <xref:System.Windows.Media.Visual>Modeldeki işleme desteğinin, sınıfının rolüne odaklanır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] .  

<a name="role_of_visual_object"></a>
## <a name="role-of-the-visual-object"></a>Görsel nesnenin rolü  
 <xref:System.Windows.Media.Visual>Sınıfı her nesnenin türettiği temel soyutlamadır <xref:System.Windows.FrameworkElement> . Ayrıca, içinde yeni denetimler yazmak için giriş noktası görevi görür [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve birçok şekilde Win32 uygulama modelinde pencere tutamacı (hwnd) olarak düşünülebilir.  
  
 <xref:System.Windows.Media.Visual>Nesnesi, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] birincil rolü işleme desteği sağlamak olan bir çekirdek nesnedir. Ve gibi kullanıcı arabirimi denetimleri, <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Media.Visual> sınıfından türetilir ve işleme verilerini kalıcı hale getirmeniz için onu kullanır. <xref:System.Windows.Media.Visual>Nesnesi için destek sağlar:  
  
- Çıktı görüntüleme: bir görselin kalıcı, serileştirilmiş çizim içeriğini Işleme.  
  
- Dönüşümler: bir görselde dönüşümler gerçekleştirme.  
  
- Kırpma: görsel için kırpma bölge desteği sağlama.  
  
- İsabet testi: bir koordinat veya geometrinin bir görselin sınırları içinde olup olmadığını belirleme.  
  
- Sınırlama kutusu hesaplamaları: görselin sınırlayıcı dikdörtgenini belirleme.  
  
 Ancak, <xref:System.Windows.Media.Visual> nesnesi, işleme olmayan özellikler için şu gibi destek içermez:  
  
- Olay işleme  
  
- Layout  
  
- Stiller  
  
- Veri bağlama  
  
- Genelleştirme  
  
 <xref:System.Windows.Media.Visual>, alt sınıfların türetilmesi gereken ortak bir soyut sınıf olarak sunulur. Aşağıdaki çizimde, içinde gösterilen görsel nesnelerinin hiyerarşisi gösterilmektedir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] .  
  
 ![Görsel nesneden türetilmiş sınıfların diyagramı](./media/wpf-graphics-rendering-overview/classes-derived-visual-object.png)
  
### <a name="drawingvisual-class"></a>DrawingVisual sınıfı  
 , <xref:System.Windows.Media.DrawingVisual> Şekilleri, resimleri veya metinleri işlemek için kullanılan basit bir çizim sınıfıdır. Bu sınıf, çalışma zamanının performansını artıran düzen veya olay işleme sağlamadığından hafif olarak değerlendirilir. Bu nedenle, çizimler arka planlar ve küçük resim için idealdir. <xref:System.Windows.Media.DrawingVisual>Özel bir görsel nesne oluşturmak için kullanılabilir. Daha fazla bilgi için bkz. [DrawingVisual nesnelerini kullanma](using-drawingvisual-objects.md).  
  
### <a name="viewport3dvisual-class"></a>Viewport3DVisual sınıfı  
 , <xref:System.Windows.Media.Media3D.Viewport3DVisual> 2B ve nesneler arasında bir köprü sağlar <xref:System.Windows.Media.Visual> <xref:System.Windows.Media.Media3D.Visual3D> . <xref:System.Windows.Media.Media3D.Visual3D>Sınıfı, tüm 3D görsel öğeleri için temel sınıftır. , <xref:System.Windows.Media.Media3D.Viewport3DVisual> Bir <xref:System.Windows.Media.Media3D.Viewport3DVisual.Camera%2A> değer ve değer tanımlamanızı gerektirir <xref:System.Windows.Media.Media3D.Viewport3DVisual.Viewport%2A> . Kamera sahneyi görüntülemenize izin verir. Görünüm penceresi, projeksiyonun 2B yüzey üzerine eşlendiğini belirler. İçindeki 3B hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bkz. [3B grafiklere genel bakış](3-d-graphics-overview.md).  
  
### <a name="containervisual-class"></a>ContainerVisual sınıfı  
 <xref:System.Windows.Media.ContainerVisual>Sınıfı bir nesne koleksiyonu için kapsayıcı olarak kullanılır <xref:System.Windows.Media.Visual> . <xref:System.Windows.Media.DrawingVisual>Sınıfı sınıfından türetiliyor ve <xref:System.Windows.Media.ContainerVisual> bir görsel nesneler koleksiyonu içermesine izin verir.  
  
### <a name="drawing-content-in-visual-objects"></a>Görsel nesnelerde Içerik çizme  
 Bir <xref:System.Windows.Media.Visual> nesnesi, işleme verilerini **vektör grafik yönerge listesi**olarak depolar. Yönerge listesindeki her öğe, bir seri hale getirilmiş biçimdeki Grafik verilerinin ve ilişkili kaynakların düşük düzeyli bir kümesini temsil eder. Çizim içeriği içerebilen dört farklı tür işleme verisi vardır.  
  
|Çizim içerik türü|Description|  
|--------------------------|-----------------|  
|Vektör grafikleri|Vektör grafik verilerini ve tüm ilişkili <xref:System.Windows.Media.Brush> ve bilgileri temsil eder <xref:System.Windows.Media.Pen> .|  
|Görüntü|Tarafından tanımlanan bölge içindeki bir görüntüyü temsil eder <xref:System.Windows.Rect> .|  
|Simge|Belirtilen bir yazı tipi kaynağından bir karakter dizisi olan, işleyen bir çizimi temsil eder <xref:System.Windows.Media.GlyphRun> . Bu, metnin temsil edildiği bir değer.|  
|Video|Videoyu işleyen bir çizimi temsil eder.|  
  
 , <xref:System.Windows.Media.DrawingContext> Bir <xref:System.Windows.Media.Visual> görsel içerikle birlikte doldurmanıza olanak sağlar. Bir <xref:System.Windows.Media.DrawingContext> nesnenin çizim komutlarını kullandığınızda, aslında grafik sistemi tarafından daha sonra kullanılacak olan bir dizi işleme verisini depoluyorsanız, gerçek zamanlı olarak ekrana çizmeyin.  
  
 , Gibi bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetim oluşturduğunuzda <xref:System.Windows.Controls.Button> Denetim, kendisini çizmek için örtülü olarak işleme verileri oluşturur. Örneğin, <xref:System.Windows.Controls.ContentControl.Content%2A> öğesinin özelliğinin ayarlanması <xref:System.Windows.Controls.Button> denetimin bir glifin işleme gösterimini depolamasına neden olur.  
  
 <xref:System.Windows.Media.Visual>, İçeriğini bir veya daha fazla nesne içinde bulunan bir veya daha fazla nesne olarak açıklar <xref:System.Windows.Media.Drawing> <xref:System.Windows.Media.DrawingGroup> . <xref:System.Windows.Media.DrawingGroup>Ayrıca, opaklık maskeleri, dönüşümler, bit eşlem efektleri ve içeriğine uygulanan diğer işlemler de açıklanmaktadır. <xref:System.Windows.Media.DrawingGroup>işlemler, içerik işlendiğinde şu sırada uygulanır:,,,, <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A> <xref:System.Windows.Media.DrawingGroup.Opacity%2A> <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A> <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A> <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A> ve <xref:System.Windows.Media.DrawingGroup.Transform%2A> .  
  
 Aşağıdaki çizimde, <xref:System.Windows.Media.DrawingGroup> işleme sırası sırasında işlemlerin uygulanma sırası gösterilmektedir.  
  
 ![DrawingGroup işlem sırası](./media/graphcismm-drawinggroup-order.png "graphcismm_drawinggroup_order")  
DrawingGroup işlemleri sırası  
  
 Daha fazla bilgi için bkz. [çizim nesnelerine genel bakış](drawing-objects-overview.md).  
  
#### <a name="drawing-content-at-the-visual-layer"></a>Görsel katmanda Içerik çizme  
 Hiçbir şekilde doğrudan örnekleyemezsiniz <xref:System.Windows.Media.DrawingContext> ; ancak, ve gibi belirli yöntemlerden bir çizim bağlamı elde edebilirsiniz <xref:System.Windows.Media.DrawingGroup.Open%2A?displayProperty=nameWithType> <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A?displayProperty=nameWithType> . Aşağıdaki örnek bir öğesinden bir alır <xref:System.Windows.Media.DrawingContext> <xref:System.Windows.Media.DrawingVisual> ve bir dikdörtgen çizmek için onu kullanır.  
  
 [!code-csharp[drawingvisualsample#101](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#101)]
 [!code-vb[drawingvisualsample#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#101)]  
  
#### <a name="enumerating-drawing-content-at-the-visual-layer"></a>Görsel katmanda çizim Içeriğini numaralandırma  
 Diğer kullanımlarına ek olarak, <xref:System.Windows.Media.Drawing> nesneleri de içeriğini numaralandırmak için bir nesne modeli sağlar <xref:System.Windows.Media.Visual> .  
  
> [!NOTE]
> Görselin içeriğini Numaralandırdığınızda, <xref:System.Windows.Media.Drawing> nesneleri, işleme verilerinin bir vektör grafik yönerge listesi olarak değil, temel gösterimini değil, alıyor olursunuz.  
  
 Aşağıdaki örnek, <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> değerini almak ve numaralandırmak için yöntemini kullanır <xref:System.Windows.Media.DrawingGroup> <xref:System.Windows.Media.Visual> .  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
<a name="how_visual_objects_are_used_to_build_controls"></a>
## <a name="how-visual-objects-are-used-to-build-controls"></a>Görsel nesneler denetimleri derlemek için nasıl kullanılır  
 İçindeki nesnelerin birçoğu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] diğer görsel nesnelerden oluşur ve bu nesnelerin farklı hiyerarşi hiyerarşileri içerebilecekleri anlamına gelir. İçindeki denetimler gibi kullanıcı arabirimi öğelerinin birçoğu, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] farklı işleme öğesi türlerini temsil eden birden çok görsel nesneden oluşur. Örneğin, denetim, <xref:System.Windows.Controls.Button> ve dahil olmak üzere bir dizi diğer nesne içerebilir <xref:Microsoft.Windows.Themes.ClassicBorderDecorator> <xref:System.Windows.Controls.ContentPresenter> <xref:System.Windows.Controls.TextBlock> .  
  
 Aşağıdaki kod, <xref:System.Windows.Controls.Button> Biçimlendirme bölümünde tanımlanan bir denetimi gösterir.  
  
 [!code-xaml[VisualsOverview#VisualsOverviewSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml#visualsoverviewsnippet1)]  
  
 Varsayılan denetimi oluşturan görsel nesneleri numaralandırdıysanız <xref:System.Windows.Controls.Button> , aşağıda gösterilen görsel nesne hiyerarşisini bulacaksınız:  
  
 ![Görsel ağaç hiyerarşisi diyagramı](./media/wpf-graphics-rendering-overview/visual-object-diagram.gif)
  
 Denetim bir öğesi <xref:System.Windows.Controls.Button> içerir, <xref:Microsoft.Windows.Themes.ClassicBorderDecorator> Bu da bir <xref:System.Windows.Controls.ContentPresenter> öğesi içerir. <xref:Microsoft.Windows.Themes.ClassicBorderDecorator>Öğesi, için bir kenarlık ve arka plan çizmekten sorumludur <xref:System.Windows.Controls.Button> . <xref:System.Windows.Controls.ContentPresenter>Öğesi öğesinin içeriğini görüntülemekten sorumludur <xref:System.Windows.Controls.Button> . Bu durumda, metin görüntülemekte olduğunuz için öğesi <xref:System.Windows.Controls.ContentPresenter> bir <xref:System.Windows.Controls.TextBlock> öğesi içerir. Denetimin bir ' ı <xref:System.Windows.Controls.Button> kullanması, <xref:System.Windows.Controls.ContentPresenter> içeriğin bir veya geometrisi gibi diğer öğeler tarafından temsil edildiği anlamına gelir <xref:System.Windows.Controls.Image> <xref:System.Windows.Media.EllipseGeometry> .  
  
### <a name="control-templates"></a>Denetim Şablonları  
 Bir denetimin hiyerarşisine bir denetim genişletmesinin anahtarı <xref:System.Windows.Controls.ControlTemplate> . Denetim şablonu, bir denetim için varsayılan görsel hiyerarşiyi belirler. Açıkça bir denetime başvurmanız durumunda, kendi görsel hiyerarşisine örtülü olarak başvurmanız gerekir. Bir denetimin özelleştirilmiş görsel görünümünü oluşturmak için bir denetim şablonunun varsayılan değerlerini geçersiz kılabilirsiniz. Örneğin, denetimin arka plan rengi değerini <xref:System.Windows.Controls.Button> düz bir renk değeri yerine doğrusal bir gradyan renk değeri kullanacak şekilde değiştirebilirsiniz. Daha fazla bilgi için bkz. [düğme stilleri ve şablonları](../controls/button-styles-and-templates.md).  
  
 Denetim gibi bir kullanıcı arabirimi öğesi, <xref:System.Windows.Controls.Button> bir denetimin tüm işleme tanımını tanımlayan birkaç vektör grafik yönerge listesi içerir. Aşağıdaki kod, <xref:System.Windows.Controls.Button> Biçimlendirme bölümünde tanımlanan bir denetimi gösterir.  
  
 [!code-xaml[VisualsOverview#VisualsOverviewSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml#visualsoverviewsnippet2)]  
  
 Denetimi oluşturan görsel nesneler ve vektör grafik yönerge listeleri numaralandırdıysanız <xref:System.Windows.Controls.Button> , aşağıda gösterilen nesnelerin hiyerarşisini bulursunuz:  
  
 ![Görsel ağaç ve işleme verileri diyagramı](./media/wpf-graphics-rendering-overview/visual-tree-rendering-data.png)  
  
 Denetim bir öğesi <xref:System.Windows.Controls.Button> içerir, <xref:Microsoft.Windows.Themes.ClassicBorderDecorator> Bu da bir <xref:System.Windows.Controls.ContentPresenter> öğesi içerir. <xref:Microsoft.Windows.Themes.ClassicBorderDecorator>Öğesi, bir düğmenin kenarlığını ve arka planını oluşturan tüm ayrık grafik öğelerini çizmekten sorumludur. <xref:System.Windows.Controls.ContentPresenter>Öğesi öğesinin içeriğini görüntülemekten sorumludur <xref:System.Windows.Controls.Button> . Bu durumda, bir resim görüntülediğinizden, <xref:System.Windows.Controls.ContentPresenter> öğesi bir <xref:System.Windows.Controls.Image> öğesi içerir.  
  
 Görsel nesnelerin ve vektör grafik yönerge listelerinin hiyerarşisi hakkında daha fazla bilgi almak için bir dizi noktaya göz vardır:  
  
- Hiyerarşideki sıralama, çizim bilgilerinin işleme sırasını temsil eder. Kök görsel öğesinden, alt öğeler, soldan sağa ve yukarıdan aşağıya doğru yapılır. Bir öğenin görsel alt öğeleri varsa, bunlar öğenin eşdüzey öğelerinden önce çapraz yapılır.  
  
- Hiyerarşisindeki yaprak olmayan düğüm öğeleri <xref:System.Windows.Controls.ContentPresenter> (gibi) alt öğeleri içermek için kullanılır; yönerge listeleri içermez.  
  
- Görsel bir öğe hem vektör grafik yönerge listesi hem de görsel alt öğeler içeriyorsa, üst görsel öğe içindeki yönerge listesi, görsel alt nesnelerinde çizimlerden önce işlenir.  
  
- Vektör grafik Yönerge listesindeki öğeler soldan sağa işlenir.  
  
<a name="visual_tree"></a>
## <a name="visual-tree"></a>Görsel ağaç  
 Görsel ağaç, bir uygulamanın kullanıcı arabiriminde kullanılan tüm görsel öğeleri içerir. Görsel bir öğe kalıcı çizim bilgilerini içerdiğinden, ekran cihazına çıktıyı oluşturmak için gereken tüm işleme bilgilerini içeren görsel ağacı bir sahne grafiği olarak düşünebilirsiniz. Bu ağaç, kodda veya biçimlendirme içinde olsun, uygulama tarafından doğrudan oluşturulan tüm görsel öğelerin birikmesi olur. Görsel ağaç Ayrıca denetimler ve veri nesneleri gibi öğelerin şablon genişlemesiyle oluşturulan tüm görsel öğeleri içerir.  
  
 Aşağıdaki kod, <xref:System.Windows.Controls.StackPanel> Biçimlendirme bölümünde tanımlanan bir öğeyi gösterir.  
  
 [!code-xaml[VisualsOverview#VisualsOverviewSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml#visualsoverviewsnippet3)]  
  
 Biçimlendirme örneğinde öğeyi oluşturan görsel nesneleri numaralandırdıysanız <xref:System.Windows.Controls.StackPanel> , aşağıda gösterilen görsel nesne hiyerarşisini bulacaksınız:  
  
 ![Görsel ağaç hiyerarşisi diyagramı](./media/wpf-graphics-rendering-overview/visual-tree-hierarchy.gif)  
  
### <a name="rendering-order"></a>İşleme sırası  
 Görsel ağaç, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] görsel ve çizim nesnelerinin işleme sırasını belirler. Çapraz geçiş sırası, görsel ağaçtaki en üstteki düğüm olan kök görsele başlar. Kök görselin alt öğeleri, soldan sağa doğru yapılır. Görselde alt öğe varsa, alt öğeleri görselin eşdüzey öğelerinin önüne eklenir. Bu, bir alt görselin içeriğinin, görselin kendi içeriğinin önünde işlendiği anlamına gelir.  
  
 ![Görsel ağaç işleme sırası diyagramı](./media/wpf-graphics-rendering-overview/visual-tree-rendering-order.gif)
  
### <a name="root-visual"></a>Kök görsel  
 **Kök görsel** , görsel ağaç hiyerarşisindeki en üstteki öğedir. Çoğu uygulamada, kök görselin temel sınıfı ya da olur <xref:System.Windows.Window> <xref:System.Windows.Navigation.NavigationWindow> . Ancak, bir Win32 uygulamasında görsel nesneler barındırıyorsanız, kök görsel, Win32 penceresinde barındırmakta olduğunuz en üstteki görseldir. Daha fazla bilgi için bkz. [öğretici: Win32 uygulamasında görsel nesneler barındırma](tutorial-hosting-visual-objects-in-a-win32-application.md).  
  
### <a name="relationship-to-the-logical-tree"></a>Mantıksal ağaç ile ilişki  
 İçindeki mantıksal ağaç, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] çalışma zamanında bir uygulamanın öğelerini temsil eder. Bu ağacı doğrudan işlemeseniz de, uygulamanın bu görünümü Özellik devralmayı ve olay yönlendirmeyi anlamak için kullanışlıdır. Görsel ağacın aksine, mantıksal ağaç gibi görsel olmayan veri nesnelerini temsil edebilir <xref:System.Windows.Documents.ListItem> . Birçok durumda, mantıksal ağaç uygulamanın biçimlendirme tanımlarına çok yakın şekilde eşlenir. Aşağıdaki kod, <xref:System.Windows.Controls.DockPanel> Biçimlendirme bölümünde tanımlanan bir öğeyi gösterir.  
  
 [!code-xaml[VisualsOverview#VisualsOverviewSnippet5](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml#visualsoverviewsnippet5)]  
  
 Biçimlendirme örneğinde öğeyi oluşturan mantıksal nesneleri numaralandırdıysanız <xref:System.Windows.Controls.DockPanel> , aşağıda gösterildiği gibi mantıksal nesnelerin hiyerarşisini bulabilirsiniz:  
  
 ![Ağaç diyagramı](./media/tree1-wcp.gif "Tree1_wcp")  
Mantıksal ağaç diyagramı  
  
 Hem görsel ağaç hem de mantıksal ağaç, geçerli uygulama öğesi kümesiyle eşitlenir ve öğelerin eklenmesini, silinmesini veya değiştirilmesini yansıtır. Ancak, ağaçlar uygulamanın farklı görünümlerini sunar. Görsel ağacın aksine, mantıksal ağaç bir denetimin öğesini genişletmez <xref:System.Windows.Controls.ContentPresenter> . Bu, bir mantıksal ağaç ile aynı nesne kümesi için bir görsel ağaç arasında doğrudan bire bir yazışmalar olmadığı anlamına gelir. Aslında, **LogicalTreeHelper** nesnesinin <xref:System.Windows.LogicalTreeHelper.GetChildren%2A> yöntemini ve bir parametre ile aynı öğeyi kullanan **VisualTreeHelper** nesnesinin <xref:System.Windows.Media.VisualTreeHelper.GetChild%2A> yöntemini çağırmak farklı sonuçlar verir.  
  
 Mantıksal ağaç hakkında daha fazla bilgi için bkz. [WPF Içindeki ağaçlar](../advanced/trees-in-wpf.md).  
  
### <a name="viewing-the-visual-tree-with-xamlpad"></a>XamlPad ile görsel ağacı görüntüleme  
 XamlPad, bu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] araç, şu anda TANıMLANMıŞ xaml içeriğine karşılık gelen görsel ağacı görüntüleme ve keşfetme seçeneği sunar. Görsel ağacı görüntülemek için menü çubuğunda **görsel ağacı göster** düğmesine tıklayın. Aşağıda, XAML içeriğinin, XamlPad 'in **görsel ağaç Gezgini** panelindeki görsel ağaç düğümlerine genişletilmesi gösterilmektedir:  
  
 ![XamlPad 'de görsel ağaç Gezgin paneli](./media/wpf-graphics-rendering-overview/visual-tree-explorer.png)  

 <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.TextBox> Ve <xref:System.Windows.Controls.Button> denetimlerinin her birinin, XamlPad 'In **görsel ağaç Gezgini** panelinde ayrı bir görsel nesne hiyerarşisi görüntülemesine dikkat edin. Bunun nedeni [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimlerin bu <xref:System.Windows.Controls.ControlTemplate> denetimin görsel ağacını içeren bir ' dır. Açıkça bir denetime başvurmanız durumunda, kendi görsel hiyerarşisine örtülü olarak başvurmanız gerekir.  
  
### <a name="profiling-visual-performance"></a>Görsel performansı profil oluşturma  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], uygulamanızın çalışma zamanı davranışını çözümlemenize ve uygulayabileceğiniz performans iyileştirmeleri türlerini belirlemenize olanak tanıyan bir dizi performans profil araçları sağlar. Görsel profil Oluşturucu Aracı, doğrudan uygulamanın görsel ağacına eşleyerek performans verilerinin zengin, grafik bir görünümünü sağlar. Bu ekran görüntüsünde, Visual Profiler 'ın **CPU kullanımı** bölümü, nesnenin [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] işleme ve düzen gibi hizmet kullanımının tam bir dökümünü sağlar.  
  
 ![Görsel profil oluşturucu görüntüleme çıktısı](./media/wpfperf-visualprofiler-04.png "WPFPerf_VisualProfiler_04")  
Görsel profil oluşturucu görüntüleme çıktısı  
  
<a name="visual_rendering_behavior"></a>
## <a name="visual-rendering-behavior"></a>Görsel Işleme davranışı  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]görsel nesnelerin işleme davranışını etkileyen çeşitli özellikler sunar: tutulan mod grafikleri, vektör grafikleri ve cihazdan bağımsız grafikler.  
  
### <a name="retained-mode-graphics"></a>Tutulan mod grafikleri  
 Görsel nesnenin rolünü anlamak için anahtarlardan biri, **anlık mod** ve **tutulan mod** grafik sistemleri arasındaki farkı anlamaktır. GDI veya GDI+ tabanlı standart bir Win32 uygulaması, anlık mod grafik sistemi kullanır. Bu, uygulamanın yeniden boyutlandırılması gibi bir eylem ya da görsel görünümünü değiştiren bir nesne nedeniyle, istemci alanının geçersiz kılınmasından dolayı uygulamanın sorumlu olduğu anlamına gelir.  
  
 ![Win32 işleme sırası diyagramı](./media/wpf-graphics-rendering-overview/win32-rendering-squence.png)  
  
 Buna karşılık, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir tutulan mod sistemi kullanır. Bu, görsel görünümü olan uygulama nesnelerinin seri hale getirilmiş bir çizim verisi kümesini tanımlayan anlamına gelir. Çizim verileri tanımlandıktan sonra, sistem, uygulama nesnelerini işlemeye yönelik tüm yeniden çizme isteklerine yanıt vermemeye başladıktan sonra sorumludur. Çalışma zamanında bile, uygulama nesnelerini değiştirebilir veya oluşturabilir ve yine de boyama isteklerine yanıt vermek için sisteme güvenebilirsiniz. Korunan modda bir grafik sisteminde bulunan güç, çizim bilgilerinin her zaman uygulama tarafından serileştirilmiş bir durumda kalıcı olması, ancak sorumluluğu sisteme işlemesi. Aşağıdaki diyagramda, uygulamanın [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] boyama isteklerine yanıt vermek için nasıl kullanıldığı gösterilmektedir.  
  
 ![WPF işleme sırası diyagramı](./media/wpf-graphics-rendering-overview/wpf-rendering-sequence.png)  

#### <a name="intelligent-redrawing"></a>Akıllı yeniden çizim  
 Korunan mod grafiklerini kullanmanın en büyük avantajlarından biri, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamada yeniden çizilmesi gerekenleri verimli bir şekilde iyileştirmenize olanak sağlar. Değişen opaklık düzeylerine sahip karmaşık bir sahneye sahip olsanız bile, yeniden çizmeyi iyileştirmek için genellikle özel amaçlı kod yazmanız gerekmez. Bunu, güncelleştirme bölgesindeki yeniden çizim miktarını en aza indirerek uygulamanızı iyileştirmek için harika bir çaba harcayabileceğiniz Win32 programlama ile karşılaştırın. Win32 uygulamalarında yeniden çizmeyi en iyi duruma getirme bölümünde yer alan karmaşıklık türünün bir örneği için bkz. [Update bölgesinde yeniden çizme](/windows/desktop/gdi/redrawing-in-the-update-region) .  
  
### <a name="vector-graphics"></a>Vektör grafikleri  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]**vektör grafiklerini** , işleme verileri biçimi olarak kullanır. Ölçeklenebilir vektör grafikleri (SVG), Windows meta dosyaları (. wmf) ve TrueType yazı tiplerini içeren vektör grafikleri — veri işleme verilerini depolar ve grafik temel sürümlerini kullanarak bir görüntüyü yeniden oluşturmayı açıklayan yönergelerin bir listesini olarak iletir. Örneğin, TrueType yazı tipleri bir dizi pikseli, eğrileri ve komutları tanımlayan ana hat yazı tipleridir. Vektör grafiklerinin önemli avantajlarından biri, herhangi bir boyuta ve çözünürlüğe ölçeklendirebilme olanağıdır.  
  
 Vektör grafiklerinden farklı olarak, bit eşlem grafik veri işleme verilerini görüntünün piksel piksel gösterimi olarak, belirli bir çözüm için önceden işlenmiş olarak saklar. Bit eşlem ve vektör grafik biçimleri arasındaki önemli farklılıklardan biri, orijinal kaynak görüntüsüne uygunluk olur. Örneğin, bir kaynak görüntünün boyutu değiştirildiğinde, bitmap grafik sistemleri görüntüyü uzarken vektör grafik sistemleri görüntüyü ölçeklenirken görüntünün aslına uygunluk düzeyini korur.  
  
 Aşağıdaki çizimde %300 tarafından yeniden boyutlandırılmış bir kaynak görüntü gösterilmektedir. Kaynak görüntü, vektör grafik görüntüsü olarak ölçeklendirilmesi yerine bir bit eşlem grafik görüntüsü olarak uzatılır görünen deformasyonları fark edin.  
  
 ![Raster ve vektör grafikleri arasındaki farklar](./media/wpf-graphics-rendering-overview/raster-vector-differences.png)  
  
 Aşağıdaki biçimlendirmede <xref:System.Windows.Shapes.Path> tanımlı iki öğe gösterilmektedir. İkinci öğe, <xref:System.Windows.Media.ScaleTransform> ilk öğenin çizim yönergelerini %300 oranında yeniden boyutlandırmak için bir kullanır. Öğelerin içindeki çizim yönergelerinin <xref:System.Windows.Shapes.Path> değişmeden kaldığına dikkat edin.  
  
 [!code-xaml[VectorGraphicsSnippets#VectorGraphicsSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/VectorGraphicsSnippets/CS/PageOne.xaml#vectorgraphicssnippet1)]  
  
### <a name="about-resolution-and-device-independent-graphics"></a>Çözümleme ve cihazdan bağımsız grafikler hakkında  
 Ekranınızdaki metin ve grafiklerin boyutunu tespit eden iki sistem faktörü vardır: çözünürlük ve DPı. Çözüm, ekranda görünen piksel sayısını açıklar. Çözünürlük daha yüksek olduğundan, piksellerin daha küçük olduğundan, grafiklerin ve metinlerin daha küçük görünmesine neden olur. 1024 x 768 olarak ayarlanan monitörde görüntülenen bir grafik, çözüm 1600 x 1200 olarak değiştirildiğinde çok daha küçük görünür.  
  
 Diğer sistem ayarı olan DPı, piksel cinsinden bir ekran boyutunu tanımlar. Çoğu Windows sisteminde DPı 96 vardır ve bu da ekran inç 96 piksel olur. DPı ayarı arttırıldığında ekran daha büyük olur; DPı 'yi düşürmek ekranı daha küçük hale getirir. Bu, bir ekran inç ' in gerçek dünya ile aynı boyutta olmadığı anlamına gelir; Çoğu sistemde büyük olasılıkla değildir. DPı 'yi artırdıkça DPı kullanan grafikler ve metin daha büyük hale gelir çünkü inç ekran boyutunu artırmış olursunuz. DPı 'nin artırılması metnin daha kolay okunmasını, özellikle de yüksek çözünürlükte kullanılabilmesini sağlayabilir.  
  
 Tüm uygulamalar DPı duyarlı değildir: bazıları, birincil ölçü birimi olarak donanım pikselleri kullanır; Sistem DPI 'sını değiştirmenin bu uygulamalar üzerinde hiçbir etkisi yoktur. Diğer birçok uygulama, yazı tipi boyutlarını betimleyen DPı kullanan birimleri kullanır, ancak diğer her şeyi de anlatmak için pikselleri kullanır. DPı 'nın çok küçük veya çok büyük olması, uygulamaların metni sistemin DPı ayarıyla ölçeklendirilebildiğinden, ancak uygulamaların kullanıcı arabirimi olmadığı için bu uygulamalarda düzen sorunlarına neden olabilir. Bu sorun kullanılarak geliştirilen uygulamalar için ortadan kaldırılmıştır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] .  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], donanım pikselleri yerine, ana ölçü birimi olarak cihazdan bağımsız pikseli kullanarak otomatik ölçeklendirmeyi destekler; uygulama geliştiricisinden ek bir iş olmadan grafik ve metin ölçeği düzgün şekilde ölçeklendirin. Aşağıdaki çizimde, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] metnin ve grafiklerin farklı DPI ayarlarında nasıl göründüğü hakkında bir örnek gösterilmektedir.  
  
 ![Farklı DPı ayarlarındaki grafikler ve metinler](./media/graphicsmm-dpi-setting-examples.png "graphicsmm_dpi_setting_examples")  
Farklı DPı ayarlarındaki grafikler ve metinler  
  
<a name="visualtreehelper_class"></a>
## <a name="visualtreehelper-class"></a>VisualTreeHelper sınıfı  
 <xref:System.Windows.Media.VisualTreeHelper>Sınıfı, görsel nesne düzeyinde programlama için alt düzey işlevsellik sağlayan ve yüksek performanslı özel denetimler geliştirme gibi çok özel senaryolarda yararlı olan bir statik yardımcı sınıftır. Çoğu durumda, ve gibi daha yüksek düzey [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] çerçeve nesneleri, daha <xref:System.Windows.Controls.Canvas> <xref:System.Windows.Controls.TextBlock> fazla esneklik ve kullanım kolaylığı sunar.  
  
### <a name="hit-testing"></a>İsabet testi  
 <xref:System.Windows.Media.VisualTreeHelper>Sınıfı, varsayılan isabet testi desteği gereksinimlerinizi karşılamıyorsa, Visual Objects üzerinde isabet testi için yöntemler sağlar. <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> <xref:System.Windows.Media.VisualTreeHelper> Bir geometri veya nokta koordinat değerinin, bir denetim veya grafik öğesi gibi belirli bir nesnenin sınırının içinde olup olmadığını anlamak için sınıfındaki yöntemleri kullanabilirsiniz. Örneğin, bir nesnenin sınırlayıcı dikdörtgeninin içindeki bir fare tıklamanın bir dairenin geometrisi dahilinde olup olmadığını belirlemek için isabet sınamasını kullanabilirsiniz, ayrıca kendi özel isabet testi hesaplamalarınızı gerçekleştirmek için isabet sınamasının varsayılan uygulamasını geçersiz kılmayı seçebilirsiniz.  
  
 İsabet testi hakkında daha fazla bilgi için bkz. [görsel katmandaki Isabet testi](hit-testing-in-the-visual-layer.md).  
  
### <a name="enumerating-the-visual-tree"></a>Görsel ağaç numaralandırılıyor  
 <xref:System.Windows.Media.VisualTreeHelper>Sınıfı, bir görsel ağacın üyelerini listelemek için işlevsellik sağlar. Bir üst öğe almak için yöntemini çağırın <xref:System.Windows.Media.VisualTreeHelper.GetParent%2A> . Bir görsel nesnenin alt veya doğrudan alt öğesi almak için <xref:System.Windows.Media.VisualTreeHelper.GetChild%2A> yöntemini çağırın. Bu yöntem, belirtilen dizinde üst öğenin bir alt öğesini döndürür <xref:System.Windows.Media.Visual> .  
  
 Aşağıdaki örnek, bir görsel nesne hiyerarşisinin tüm işleme bilgilerini serileştirmede ilgileniyorsanız, kullanmak isteyebileceğiniz bir tekniktir, bir görsel nesnenin tüm alt öğelerinin nasıl numaralandırılacağını gösterir.  
  
 [!code-csharp[VisualsOverview#101](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml.cs#101)]
 [!code-vb[VisualsOverview#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsOverview/visualbasic/window1.xaml.vb#101)]  
  
 Çoğu durumda mantıksal ağaç, bir uygulamadaki öğelerin daha kullanışlı bir gösterimidir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] . Mantıksal ağacı doğrudan değiştirmeseniz de, uygulamanın bu görünümü Özellik devralmayı ve olay yönlendirmeyi anlamak için kullanışlıdır. Görsel ağacın aksine, mantıksal ağaç gibi görsel olmayan veri nesnelerini temsil edebilir <xref:System.Windows.Documents.ListItem> . Mantıksal ağaç hakkında daha fazla bilgi için bkz. [WPF Içindeki ağaçlar](../advanced/trees-in-wpf.md).  
  
 <xref:System.Windows.Media.VisualTreeHelper>Sınıfı, görsel nesnelerin sınırlayıcı dikdörtgenini döndürmek için yöntemler sağlar. Çağırarak, bir görsel nesnenin sınırlayıcı dikdörtgenini döndürebilirsiniz <xref:System.Windows.Media.VisualTreeHelper.GetContentBounds%2A> . Görsel nesnenin kendisi de dahil olmak üzere, bir görsel nesnenin tüm alt öğelerinin sınırlayıcı dikdörtgenini çağırarak ' ı geri getirebilirsiniz <xref:System.Windows.Media.VisualTreeHelper.GetDescendantBounds%2A> . Aşağıdaki kod, bir görsel nesnenin ve tüm alt öğelerinin sınırlayıcı dikdörtgenini nasıl hesaplayabileceğinizi gösterir.  
  
 [!code-csharp[VisualsOverview#102](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml.cs#102)]
 [!code-vb[VisualsOverview#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsOverview/visualbasic/window1.xaml.vb#102)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.Visual>
- <xref:System.Windows.Media.VisualTreeHelper>
- <xref:System.Windows.Media.DrawingVisual>
- [2B Grafikleri ve Görüntüleme](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Görsel Katmanda Tıklama Testi](hit-testing-in-the-visual-layer.md)
- [DrawingVisual Nesnelerini Kullanma](using-drawingvisual-objects.md)
- [Öğretici: Win32 Uygulamasında Görsel Nesneler Barındırma](tutorial-hosting-visual-objects-in-a-win32-application.md)
- [WPF Uygulama Performansını İyileştirme](../advanced/optimizing-wpf-application-performance.md)
