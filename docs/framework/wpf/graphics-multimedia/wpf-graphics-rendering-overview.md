---
title: Grafik işleme genel bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], rendering
- rendering graphics [WPF]
ms.assetid: 6dec9657-4d8c-4e46-8c54-40fb80008265
ms.openlocfilehash: 9d58aa973f7de6c073611e13f2889913ff26dd55
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111926"
---
# <a name="wpf-graphics-rendering-overview"></a>WPF Grafik İşlemeye Genel Bakış
Bu konu, görsel [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] katmana genel bir bakış sağlar. Modelde destek işlemek için <xref:System.Windows.Media.Visual> sınıfın rolüne odaklanır. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]  

<a name="role_of_visual_object"></a>
## <a name="role-of-the-visual-object"></a>Görsel Nesnenin Rolü  
 Sınıf, <xref:System.Windows.Media.Visual> her <xref:System.Windows.FrameworkElement> nesnenin türetildiği temel soyutlamadır. Ayrıca yeni denetimler yazmak için giriş [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]noktası olarak hizmet vermektedir , ve birçok yönden Win32 uygulama modelinde pencere kolu (HWND) olarak düşünülebilir.  
  
 Nesne, <xref:System.Windows.Media.Visual> birincil [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] rolü oluşturma desteği sağlamak olan bir temel nesnedir. Kullanıcı arabirimi denetimleri, örneğin <xref:System.Windows.Controls.Button> ve, <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Media.Visual> sınıftan türetilmiştir ve kendi işleme verilerini kalıcı olarak kullanmak. Nesne <xref:System.Windows.Media.Visual> aşağıdakiler için destek sağlar:  
  
- Çıktı ekranı: Görselin kalıcı, seri leştirilmiş çizim içeriğini oluşturma.  
  
- Dönüşümler: Dönüşümleri görsel olarak gerçekleştirmek.  
  
- Kırpma: Görsel için kırpma bölgesi desteği sağlar.  
  
- Hit testi: Bir koordinat veya geometrinin görsel in sınırları içinde bulunup olmadığını belirleme.  
  
- Sınırlayıcı kutu hesaplamaları: Görselin sınırlayıcı dikdörtgeninin belirlenmesi.  
  
 Ancak, <xref:System.Windows.Media.Visual> nesne gibi işleme olmayan özellikler için destek içermez:  
  
- Olay işleme  
  
- Düzen  
  
- Stiller  
  
- Veri bağlama  
  
- Genelleştirme  
  
 <xref:System.Windows.Media.Visual>alt sınıfların türetilmesi gereken genel soyut bir sınıf olarak ortaya çıkar. Aşağıdaki resimde, 'de açıkta olan görsel nesnelerin [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]hiyerarşisi gösterilmektedir.  
  
 ![Görsel nesneden türetilen sınıfların diyagramı](./media/wpf-graphics-rendering-overview/classes-derived-visual-object.png)
  
### <a name="drawingvisual-class"></a>ÇizimGörsel Sınıf  
 Şekilleri, <xref:System.Windows.Media.DrawingVisual> görüntüleri veya metni işlemek için kullanılan hafif bir çizim sınıfıdır. Bu sınıf, çalışma zamanı performansını artıran düzen veya olay işleme sağlamadığından hafif olarak kabul edilir. Bu nedenle, çizimler arka planlar ve küçük resim için idealdir. Özel <xref:System.Windows.Media.DrawingVisual> bir görsel nesne oluşturmak için kullanılabilir. Daha fazla bilgi için [Bkz. ÇizimGörsel Nesneleri Kullanma.](using-drawingvisual-objects.md)  
  
### <a name="viewport3dvisual-class"></a>Viewport3DVisual Sınıfı  
 2B <xref:System.Windows.Media.Media3D.Viewport3DVisual> <xref:System.Windows.Media.Visual> ve <xref:System.Windows.Media.Media3D.Visual3D> nesneler arasında bir köprü sağlar. Sınıf, <xref:System.Windows.Media.Media3D.Visual3D> tüm 3B görsel öğelerin taban sınıfıdır. Bir <xref:System.Windows.Media.Media3D.Viewport3DVisual> değer ve <xref:System.Windows.Media.Media3D.Viewport3DVisual.Camera%2A> bir <xref:System.Windows.Media.Media3D.Viewport3DVisual.Viewport%2A> değer tanımlamanızı gerektirir. Kamera sahneyi görüntülemenizi sağlar. Viewport, projeksiyonun 2B yüzeye eşleştiği yeri belirler. 3D hakkında daha [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]fazla bilgi için, [3D Grafik Genel Bakış](3-d-graphics-overview.md)bakın.  
  
### <a name="containervisual-class"></a>KonteynerGörsel Sınıf  
 Sınıf <xref:System.Windows.Media.ContainerVisual> <xref:System.Windows.Media.Visual> nesnelerin bir koleksiyon için bir kapsayıcı olarak kullanılır. <xref:System.Windows.Media.ContainerVisual> Sınıf, <xref:System.Windows.Media.DrawingVisual> bir görsel nesne koleksiyonu içermesine izin vererek sınıftan türetilmiştir.  
  
### <a name="drawing-content-in-visual-objects"></a>Görsel Nesnelerde İçerik Çizme  
 Bir <xref:System.Windows.Media.Visual> nesne, render verilerini **vektör grafik yönergelistesi olarak**depolar. Yönerge listesindeki her öğe, seri biçiminde düşük düzeyli grafik verisini ve ilişkili kaynakları temsil eder. Çizim içeriği içerebilen dört farklı render verisi türü vardır.  
  
|İçerik türünü çizme|Açıklama|  
|--------------------------|-----------------|  
|Vektör grafikleri|Vektör grafik verilerini ve <xref:System.Windows.Media.Brush> ilişkili <xref:System.Windows.Media.Pen> tüm bilgileri temsil eder.|  
|Görüntü|Bir <xref:System.Windows.Rect>bölge içinde bir görüntüyü temsil eder.|  
|Glif|Belirli bir yazı tipi <xref:System.Windows.Media.GlyphRun>kaynağından bir glifler dizisi olan bir çizimi temsil eder. Metin bu şekilde temsil edilir.|  
|Video|Videoyu işleyen bir çizimi temsil eder.|  
  
 Görsel <xref:System.Windows.Media.DrawingContext> içerikli bir <xref:System.Windows.Media.Visual> doldurmanızı sağlar. Bir <xref:System.Windows.Media.DrawingContext> nesnenin çizim komutlarını kullandığınızda, aslında daha sonra grafik sistemi tarafından kullanılacak bir render veri kümesini depolarsınız; gerçek zamanlı olarak ekrana çizim değildir.  
  
 Bir denetim [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] oluşturduğunuzda, <xref:System.Windows.Controls.Button>bir , , denetim örtülü çizim kendisi için render veri oluşturur. Örneğin, <xref:System.Windows.Controls.Button> denetimin <xref:System.Windows.Controls.ContentControl.Content%2A> bir gliflerin render gösterimini depolamasına neden olan nedenlerin özelliğini ayarlamak.  
  
 A, <xref:System.Windows.Media.Visual> içeriğini bir <xref:System.Windows.Media.Drawing> <xref:System.Windows.Media.DrawingGroup>içinde bulunan bir veya daha fazla nesne olarak tanımlar. A <xref:System.Windows.Media.DrawingGroup> ayrıca, içeriğine uygulanan opaklık maskelerini, dönüşümleri, bitmap efektlerini ve diğer işlemleri de açıklar. <xref:System.Windows.Media.DrawingGroup>işlemler, içerik işlendiğinde aşağıdaki sırayla <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>uygulanır: <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A> <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>, <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>, <xref:System.Windows.Media.DrawingGroup.Opacity%2A> <xref:System.Windows.Media.DrawingGroup.Transform%2A>, , ve sonra .  
  
 Aşağıdaki resimde, işleme sırası <xref:System.Windows.Media.DrawingGroup> sırasında işlemlerin uygulandığı sıra gösterilmektedir.  
  
 ![DrawingGroup işlem sırası](./media/graphcismm-drawinggroup-order.png "graphcismm_drawinggroup_order")  
DrawingGroup işlemleri sırası  
  
 Daha fazla bilgi için Bkz. [Çizim Nesneleri Genel Bakış.](drawing-objects-overview.md)  
  
#### <a name="drawing-content-at-the-visual-layer"></a>Görsel Katmanda İçerik Çizme  
 Hiçbir zaman doğrudan bir <xref:System.Windows.Media.DrawingContext>ani lik atamayın; ancak, belirli yöntemlerden bir çizim bağlamı <xref:System.Windows.Media.DrawingGroup.Open%2A?displayProperty=nameWithType> edinebilirsiniz, gibi ve. <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A?displayProperty=nameWithType> Aşağıdaki örnek a'dan <xref:System.Windows.Media.DrawingContext> <xref:System.Windows.Media.DrawingVisual> a alır ve dikdörtgen çizmek için kullanır.  
  
 [!code-csharp[drawingvisualsample#101](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#101)]
 [!code-vb[drawingvisualsample#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#101)]  
  
#### <a name="enumerating-drawing-content-at-the-visual-layer"></a>Görsel Katmanda Çizim İçeriğini Sayısallandırma  
 Diğer kullanımlarına ek <xref:System.Windows.Media.Drawing> olarak, nesneler bir <xref:System.Windows.Media.Visual>nesnenin içeriğini sıralamak için bir nesne modeli de sağlar.  
  
> [!NOTE]
> Görselin içeriğini sıralarken, render verilerinin bir vektör grafik <xref:System.Windows.Media.Drawing> yönergelistesi olarak altta yatan gösterimini değil, nesneleri geri alabilirsiniz.  
  
 Aşağıdaki örnek, <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> a <xref:System.Windows.Media.DrawingGroup> <xref:System.Windows.Media.Visual> değerini almak ve sayısallamak için yöntemi kullanır.  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
<a name="how_visual_objects_are_used_to_build_controls"></a>
## <a name="how-visual-objects-are-used-to-build-controls"></a>Denetimoluşturmak için Görsel Nesneler Nasıl Kullanılır?  
 İçindeki [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nesnelerin çoğu diğer görsel nesnelerden oluşur, yani soyundan gelen nesnelerin değişen hiyerarşilerini içerebilirler. Denetimler gibi kullanıcı [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]arabirimi öğelerinin çoğu, farklı türde oluşturma öğelerini temsil eden birden çok görsel nesneden oluşur. Örneğin, <xref:System.Windows.Controls.Button> denetim <xref:Microsoft.Windows.Themes.ClassicBorderDecorator>, , <xref:System.Windows.Controls.ContentPresenter>ve <xref:System.Windows.Controls.TextBlock>.  
  
 Aşağıdaki kod biçimlendirmede tanımlanan bir <xref:System.Windows.Controls.Button> denetimi gösterir.  
  
 [!code-xaml[VisualsOverview#VisualsOverviewSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml#visualsoverviewsnippet1)]  
  
 Varsayılan <xref:System.Windows.Controls.Button> denetimi oluşturan görsel nesneleri sayısala ederseniz, aşağıda gösterilen görsel nesneler hiyerarşisini bulursunuz:  
  
 ![Görsel ağaç hiyerarşisi diyagramı](./media/wpf-graphics-rendering-overview/visual-object-diagram.gif)
  
 Denetim <xref:System.Windows.Controls.Button> sırayla <xref:Microsoft.Windows.Themes.ClassicBorderDecorator> bir öğe içeren bir <xref:System.Windows.Controls.ContentPresenter> öğe içerir. Öğe <xref:Microsoft.Windows.Themes.ClassicBorderDecorator> için bir kenarlık ve bir <xref:System.Windows.Controls.Button>arka plan çizim sorumludur. Öğe, <xref:System.Windows.Controls.ContentPresenter> <xref:System.Windows.Controls.Button>'nin içeriğini görüntülemekten sorumludur. Bu durumda, metin görüntülediğiniz için <xref:System.Windows.Controls.ContentPresenter> öğe <xref:System.Windows.Controls.TextBlock> bir öğe içerir. Denetimin, <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.ContentPresenter> içeriğin bir <xref:System.Windows.Controls.Image> geometri gibi diğer öğelerle temsil edilebildiği anlamına geliyor <xref:System.Windows.Media.EllipseGeometry>olması.  
  
### <a name="control-templates"></a>Denetim Şablonları  
 Denetimin denetimler hiyerarşisine genişletilmesinin <xref:System.Windows.Controls.ControlTemplate>anahtarı. Denetim şablonu, denetim için varsayılan görsel hiyerarşiyi belirtir. Bir denetime açıkça başvururken, denetime dolaylı olarak başvurursunuz. Denetim için özelleştirilmiş bir görsel görünüm oluşturmak için denetim şablonu için varsayılan değerleri geçersiz kılabilirsiniz. Örneğin, <xref:System.Windows.Controls.Button> denetimin arka plan renk değerini düz renk değeri yerine doğrusal degrade renk değeri kullanabilmesi için değiştirebilirsiniz. Daha fazla bilgi için [Düğme Stilleri ve Şablonlar'a](../controls/button-styles-and-templates.md)bakın.  
  
 Denetim gibi bir <xref:System.Windows.Controls.Button> kullanıcı arabirimi öğesi, denetimin tüm oluşturma tanımını açıklayan birkaç vektör grafik yönergesi listesi içerir. Aşağıdaki kod biçimlendirmede tanımlanan bir <xref:System.Windows.Controls.Button> denetimi gösterir.  
  
 [!code-xaml[VisualsOverview#VisualsOverviewSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml#visualsoverviewsnippet2)]  
  
 <xref:System.Windows.Controls.Button> Denetimi oluşturan görsel nesneleri ve vektör grafik yönerge listelerini sıralarsanız, aşağıda gösterilen nesnelerin hiyerarşisini bulursunuz:  
  
 ![Görsel ağaç diyagramı ve veri oluşturma](./media/wpf-graphics-rendering-overview/visual-tree-rendering-data.png)  
  
 Denetim <xref:System.Windows.Controls.Button> sırayla <xref:Microsoft.Windows.Themes.ClassicBorderDecorator> bir öğe içeren bir <xref:System.Windows.Controls.ContentPresenter> öğe içerir. Öğe, <xref:Microsoft.Windows.Themes.ClassicBorderDecorator> bir düğmenin kenarlığı ve arka planını oluşturan tüm ayrıgrafik öğeleri çizmekten sorumludur. Öğe, <xref:System.Windows.Controls.ContentPresenter> <xref:System.Windows.Controls.Button>'nin içeriğini görüntülemekten sorumludur. Bu durumda, bir görüntü görüntü görüntülediğiniz için, <xref:System.Windows.Controls.ContentPresenter> öğe bir <xref:System.Windows.Controls.Image> öğe içerir.  
  
 Görsel nesneler ve vektör grafik yönergesi listeleri hiyerarşisi hakkında dikkat edilmesi gereken noktalar vardır:  
  
- Hiyerarşideki sıralama, çizim bilgilerinin işleme sırasını temsil eder. Kök görsel öğeden alt öğeler soldan sağa, yukarıdan aşağıya geçilir. Bir öğenin görsel alt öğeleri varsa, öğenin kardeşleri önce çaprazlanır.  
  
- Hiyerarşideki yapraksız düğüm öğeleri, <xref:System.Windows.Controls.ContentPresenter>örneğin, alt öğeleri içermek için kullanılır-bunlar yönerge listeleri içermez.  
  
- Görsel öğe hem vektör grafik talimat listesi hem de görsel alt öğe içeriyorsa, üst görsel öğedeki yönerge listesi, görsel alt nesnelerden herhangi birinde çizimlerden önce işlenir.  
  
- Vektör grafik yönergesi listesindeki öğeler soldan sağa işlenir.  
  
<a name="visual_tree"></a>
## <a name="visual-tree"></a>Görsel Ağaç  
 Görsel ağaç, bir uygulamanın kullanıcı arabiriminde kullanılan tüm görsel öğeleri içerir. Görsel bir öğe kalıcı çizim bilgileri içerdiğinden, görsel ağacı görüntü aygıtına çıktı oluşturmak için gereken tüm işleme bilgilerini içeren bir sahne grafiği olarak düşünebilirsiniz. Bu ağaç, ister kodda ister biçimlendirmede olsun, doğrudan uygulama tarafından oluşturulan tüm görsel öğelerin birikimidir. Görsel ağaç ayrıca denetimler ve veri nesneleri gibi öğelerin şablon genişletme tarafından oluşturulan tüm görsel öğeleri içerir.  
  
 Aşağıdaki kod biçimlendirmede tanımlanan bir <xref:System.Windows.Controls.StackPanel> öğeyi gösterir.  
  
 [!code-xaml[VisualsOverview#VisualsOverviewSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml#visualsoverviewsnippet3)]  
  
 Biçimlendirme örneğinde <xref:System.Windows.Controls.StackPanel> öğeyi oluşturan görsel nesneleri sayısala ederseniz, aşağıda gösterilen görsel nesneler hiyerarşisini bulursunuz:  
  
 ![Görsel ağaç hiyerarşisi diyagramı](./media/wpf-graphics-rendering-overview/visual-tree-hierarchy.gif)  
  
### <a name="rendering-order"></a>İşleme Sırası  
 Görsel ağaç, görsel ve çizim [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nesnelerinin işleme sırasını belirler. Geçiş sırası, görsel ağacın en üstteki düğümü olan kök görseliyle başlar. Kök görselin çocukları daha sonra soldan sağa geçilir. Bir görselin çocukları varsa, çocukları görselin kardeşlerinden önce geçilir. Bu, bir alt görselin içeriğinin görselin kendi içeriğinin önünde işlendiği anlamına gelir.  
  
 ![Görsel ağaç oluşturma sırasıdiyagramı](./media/wpf-graphics-rendering-overview/visual-tree-rendering-order.gif)
  
### <a name="root-visual"></a>Kök Görsel  
 **Kök görsel,** görsel ağaç hiyerarşisindeki en üst öğedir. Çoğu uygulamada, kök görselinin taban sınıfı <xref:System.Windows.Window> <xref:System.Windows.Navigation.NavigationWindow>ya . Ancak, win32 uygulamasında görsel nesneleri barındırıyorsanız, kök görselwin32 penceresinde barındırdığınız en üstteki görsel olurdu. Daha fazla bilgi için, [Bkz. Öğretici: Win32 Uygulamasında Görsel Nesneleri Barındırma.](tutorial-hosting-visual-objects-in-a-win32-application.md)  
  
### <a name="relationship-to-the-logical-tree"></a>Mantıksal Ağaçla İlişki  
 Mantıksal ağaç [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] çalışma zamanında bir uygulamanın öğelerini temsil eder. Bu ağacı doğrudan işlemeseniz ekidir, ancak uygulamanın bu görünümü özellik devralma sını ve olay yönlendirmesini anlamak için yararlıdır. Görsel ağacın aksine, mantıksal ağaç görsel olmayan veri nesnelerini <xref:System.Windows.Documents.ListItem>temsil edebilir, örneğin. Çoğu durumda, mantıksal ağaç, bir uygulamanın biçimlendirme tanımlarına çok yakından eşler. Aşağıdaki kod biçimlendirmede tanımlanan bir <xref:System.Windows.Controls.DockPanel> öğeyi gösterir.  
  
 [!code-xaml[VisualsOverview#VisualsOverviewSnippet5](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml#visualsoverviewsnippet5)]  
  
 Biçimlendirme örneğinde <xref:System.Windows.Controls.DockPanel> öğeyi oluşturan mantıksal nesneleri sayısala ederseniz, aşağıda gösterilen mantıksal nesneler hiyerarşisini bulursunuz:  
  
 ![Ağaç diyagramı](./media/tree1-wcp.gif "Tree1_wcp")  
Mantıksal ağaç diyagramı  
  
 Hem görsel ağaç hem de mantıksal ağaç, öğelerin herhangi bir ekleme, silme veya modifikasyonsunu yansıtan geçerli uygulama öğeleri kümesiyle eşitlenir. Ancak, ağaçlar uygulamanın farklı görünümlerini sunar. Görsel ağacın aksine, mantıksal ağaç bir denetimöğesi <xref:System.Windows.Controls.ContentPresenter> genişletmez. Bu, mantıksal bir ağaç la aynı nesne kümesi için görsel bir ağaç arasında doğrudan bire bir yazışma olmadığı anlamına gelir. Aslında, **LogicalTreeHelper** nesnenin <xref:System.Windows.LogicalTreeHelper.GetChildren%2A> yöntemi ve **VisualTreeHelper** nesnenin <xref:System.Windows.Media.VisualTreeHelper.GetChild%2A> yöntemi bir parametre olarak aynı öğeyi kullanarak çağıran farklı sonuçlar verir.  
  
 Mantıksal ağaç hakkında daha fazla bilgi için [WPF'deki Ağaçlar'a](../advanced/trees-in-wpf.md)bakın.  
  
### <a name="viewing-the-visual-tree-with-xamlpad"></a>XamlPad ile Görsel Ağacı Görüntüleme  
 Araç, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XamlPad, görüntüleme ve şu anda tanımlanan XAML içeriğine karşılık gelen görsel ağacı keşfetmek için bir seçenek sağlar. Görsel **ağacı** görüntülemek için menü çubuğundaki Görsel Ağacı Göster düğmesini tıklatın. XAMLPad'in **Visual Tree Explorer** panelinde XAML içeriğinin görsel ağaç düğümlerine genişletilmesi aşağıda açıklanmaktadır:  
  
 ![XamlPad'de Görsel Ağaç Gezgini paneli](./media/wpf-graphics-rendering-overview/visual-tree-explorer.png)  

 <xref:System.Windows.Controls.Label>XamlPad'in <xref:System.Windows.Controls.TextBox> **Visual Tree Explorer** panelinde her birinin ayrı bir görsel nesne hiyerarşisi görüntülenin ve <xref:System.Windows.Controls.Button> denetimlerinin nasıl görüntülenebildiğini fark edin. Bunun nedeni, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimlerin bu denetimin görsel ağacını içeren bir <xref:System.Windows.Controls.ControlTemplate> Bir denetime açıkça başvururken, denetime dolaylı olarak başvurursunuz.  
  
### <a name="profiling-visual-performance"></a>Görsel Performans Profilleme  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]uygulamanızın çalışma zamanı davranışını çözümlemenize ve uygulayabileceğiniz performans optimizasyonları türlerini belirlemenize olanak tanıyan bir performans profil oluşturma araçları paketi sağlar. Visual Profiler aracı, doğrudan uygulamanın görsel ağacına eşleyerek performans verilerinin zengin, grafiksel görünümünü sağlar. Bu ekran görüntüsünde, Visual Profiler'ın **CPU Kullanımı** bölümü, bir nesnenin oluşturma ve düzen gibi hizmetleri kullanımının [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kesin bir dökümünü sağlar.  
  
 ![Visual Profiler ekran çıktısı](./media/wpfperf-visualprofiler-04.png "WPFPerf_VisualProfiler_04")  
Visual Profiler ekran çıktısı  
  
<a name="visual_rendering_behavior"></a>
## <a name="visual-rendering-behavior"></a>Görsel Görüntüleme Davranışı  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]korunan mod grafikleri, vektör grafikleri ve aygıtbağımsız grafikleri: görsel nesnelerin oluşturma davranışını etkileyen çeşitli özellikleri sunar.  
  
### <a name="retained-mode-graphics"></a>Korunmuş Mod Grafikleri  
 Görsel nesnenin rolünü anlamanın anahtarlarından biri, hemen **mod** ile **tutulan mod** grafik sistemleri arasındaki farkı anlamaktır. GDI veya GDI+ tabanlı standart bir Win32 uygulaması hemen modgrafik sistemi kullanır. Bu, uygulamanın, pencere yeniden boyutlandırılmak veya görsel görünümünü değiştiren bir nesne gibi bir eylem nedeniyle, istemci alanının geçersiz kılınan bölümünü yeniden boyamaktan sorumlu olduğu anlamına gelir.  
  
 ![Win32 oluşturma sırası diyagramı](./media/wpf-graphics-rendering-overview/win32-rendering-squence.png)  
  
 Buna karşılık, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] korunmuş bir mod sistemi kullanır. Bu, görsel görünüme sahip uygulama nesnelerinin serileştirilmiş çizim verileri kümesini tanımladığı anlamına gelir. Çizim verileri tanımlandıktan sonra, sistem uygulama nesnelerinin işlenmesi için tüm yeniden boyama isteklerine yanıt vermekten sorumludur. Çalışma zamanında bile, uygulama nesnelerini değiştirebilir veya oluşturabilir ve yine de boya isteklerine yanıt vermek için sisteme güvenebilirsiniz. Korunan mod grafik sistemindeki güç, çizim bilgilerinin uygulama tarafından her zaman seri hale getirilmiş bir durumda kalıcı olması, ancak sorumluluğun sisteme bırakılmasıdır. Aşağıdaki diyagram, uygulamanın boya [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] isteklerine yanıt vermek için nasıl dayandığını gösterir.  
  
 ![WPF oluşturma sırası diyagramı](./media/wpf-graphics-rendering-overview/wpf-rendering-sequence.png)  

#### <a name="intelligent-redrawing"></a>Akıllı Yeniden Çizim  
 Korunmuş mod grafiklerini kullanmanın en büyük [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] avantajlarından biri, uygulamada yeniden çizilmesi gerekenleri verimli bir şekilde optimize edebilmesidir. Farklı donukluk düzeylerine sahip karmaşık bir sahneniz olsa bile, yeniden çizimi en iyi duruma getirmek için genellikle özel amaçlı kod yazmanız gerekmez. Bunu, güncelleştirme bölgesindeki yeniden çizim miktarını en aza indirerek uygulamanızı optimize etmek için büyük çaba harcayabileceğiniz Win32 programlamasıyla karşılaştırın. Win32 uygulamalarında yeniden [çizimi](/windows/desktop/gdi/redrawing-in-the-update-region) en iyi duruma çıkarmada yer alan karmaşıklık türüne bir örnek olarak Güncelleştirme Bölgesi'nde Yeniden Çizim ekine bakın.  
  
### <a name="vector-graphics"></a>Vektör Grafikleri  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]veri biçimi olarak **vektör grafiklerini** kullanır. Ölçeklenebilir Vektör Grafikleri (SVG), Windows metafiles (.wmf) ve TrueType yazı tiplerini içeren vektör grafikleri, verileri depolar ve grafik ilkellerini kullanarak görüntüyü nasıl yeniden oluşturacağını açıklayan yönergelerin listesi olarak iletir. Örneğin, TrueType yazı tipleri, bir dizi piksel yerine bir dizi satır, eğri ve komut kümesini açıklayan anahat yazı tipleridir. Vektör grafik lerinin en önemli avantajlarından biri, herhangi bir boyut ve çözünürlüğe ölçeklendirme yeteneğidir.  
  
 Vektör grafiklerinden farklı olarak, bitmap grafikleri, belirli bir çözünürlük için önceden işlenmiş bir görüntünün piksel piksel gösterimi olarak verileri depolar. Bitmap ve vektör grafik biçimleri arasındaki temel farklardan biri orijinal kaynak görüntüye sadakattir. Örneğin, bir kaynak resmin boyutu değiştirildiğinde, bitmap grafik sistemleri görüntüyü genişletirken, vektör grafik sistemleri görüntüyü ölçeklendirerek görüntüsadakatini korur.  
  
 Aşağıdaki resimde% 300 tarafından yeniden boyutlandırılmış bir kaynak görüntü gösterilmektedir. Kaynak görüntü vektör grafik görüntüsü olarak ölçeklendirilmiş yerine bitmap grafik görüntüsü olarak gerildiğinde ortaya çıkan bozulmalara dikkat edin.  
  
 ![Raster ve vektör grafikleri arasındaki farklar](./media/wpf-graphics-rendering-overview/raster-vector-differences.png)  
  
 Aşağıdaki biçimlendirme tanımlanan <xref:System.Windows.Shapes.Path> iki öğeyi gösterir. İkinci öğe, <xref:System.Windows.Media.ScaleTransform> ilk öğenin çizim yönergelerini %300 yeniden boyutlandırmak için a kullanır. Öğelerdeki çizim yönergelerinin <xref:System.Windows.Shapes.Path> değişmeden kaldığına dikkat edin.  
  
 [!code-xaml[VectorGraphicsSnippets#VectorGraphicsSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/VectorGraphicsSnippets/CS/PageOne.xaml#vectorgraphicssnippet1)]  
  
### <a name="about-resolution-and-device-independent-graphics"></a>Çözünürlük ve Aygıtbağımsız Grafikler Hakkında  
 Ekranınızdaki metin ve grafiklerin boyutunu belirleyen iki sistem faktörü vardır: çözünürlük ve DPI. Çözünürlük, ekranda görünen piksel sayısını açıklar. Çözünürlük arttıkça pikseller küçülür ve grafiklerin ve metinlerin küçülmesine neden olur. Çözünürlük 1600 x 1200 olarak değiştirildiğinde, 1024 x 768 olarak ayarlanmış bir monitörde görüntülenen bir grafik çok daha küçük görünür.  
  
 Diğer sistem ayarı, DPI, piksel bir ekran inç boyutunu açıklar. Çoğu Windows sisteminde 96 DPI vardır, bu da ekran inçinin 96 piksel olduğu anlamına gelir. DPI ayarını artırmak ekranı inç daha büyük yapar; DPI'yi azaltmak ekranı küçültür. Bu bir ekran inç gerçek bir dünya inç aynı boyutta olmadığı anlamına gelir; çoğu sistemde, muhtemelen değil. DPI'yı artırdıkça, ekran inç boyutunu artırdığınız için DPI'ya duyarlı grafikler ve metinler büyür. DPI'yi artırmak, özellikle yüksek çözünürlüklerde metnin okunmasını kolaylaştırabilir.  
  
 Tüm uygulamalar DPI'ya duyarlı değildir: bazıları birincil ölçüm birimi olarak donanım piksellerini kullanır; sistem DPI değiştirme bu uygulamalar üzerinde hiçbir etkisi yoktur. Diğer birçok uygulama, yazı tipi boyutlarını tanımlamak için DPI'ya duyarlı birimler kullanır, ancak diğer her şeyi tanımlamak için pikselleri kullanır. DPI'yi çok küçük veya çok büyük yapmak bu uygulamalar için düzen sorunlarına neden olabilir, çünkü uygulamaların metin leri sistemin DPI ayarı ile ölçeklendirilir, ancak uygulamaların Kullanıcı Arabirimi oluşturmaz. Bu sorun kullanılarak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]geliştirilen uygulamalar için ortadan kaldırılmış.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]donanım pikselleri yerine aygıtın bağımsız pikselini birincil ölçüm birimi olarak kullanarak otomatik ölçeklemeyi destekler; uygulama geliştiricisinden herhangi bir ekstra çalışma olmadan düzgün grafik ve metin ölçeklendirme. Aşağıdaki resimde, metin ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] grafiklerin farklı DPI ayarlarında nasıl göründüğüne bir örnek gösterilmektedir.  
  
 ![Farklı DPI ayarlarında grafik ve metin](./media/graphicsmm-dpi-setting-examples.png "graphicsmm_dpi_setting_examples")  
Farklı DPI ayarlarında grafik ve metin  
  
<a name="visualtreehelper_class"></a>
## <a name="visualtreehelper-class"></a>VisualTreeHelper Sınıfı  
 Sınıf, <xref:System.Windows.Media.VisualTreeHelper> görsel nesne düzeyinde programlama için düşük düzeyli işlevsellik sağlayan ve yüksek performanslı özel denetimler geliştirmek gibi çok özel senaryolarda kullanışlı olan statik bir yardımcı sınıftır. Çoğu durumda, daha yüksek [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] düzeyli çerçeve <xref:System.Windows.Controls.Canvas> nesneleri, gibi ve, <xref:System.Windows.Controls.TextBlock>daha fazla esneklik ve kullanım kolaylığı sunar.  
  
### <a name="hit-testing"></a>Hit Testi  
 Sınıf, <xref:System.Windows.Media.VisualTreeHelper> varsayılan isabet testi desteği gereksinimlerinizi karşılamadığında görsel nesneler üzerinde isabet testi için yöntemler sağlar. Bir geometri <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> veya nokta koordinat değeri denetim veya grafik öğesi gibi belirli bir nesnenin sınırları içinde olup olmadığını belirlemek için sınıftaki yöntemleri kullanabilirsiniz. <xref:System.Windows.Media.VisualTreeHelper> Örneğin, bir nesnenin sınırlayan dikdörtgeni içindeki fare tıklamasının bir dairenin geometrisine düşüp düşmediğini belirlemek için isabet testi kullanabilirsiniz Kendi özel isabet testinizi gerçekleştirmek için isabet testinin varsayılan uygulamasını geçersiz kılmayı da seçebilirsiniz Hesaplama.  
  
 Isabet testi hakkında daha fazla bilgi için [Görsel Katman'daki Hit Testi'ne](hit-testing-in-the-visual-layer.md)bakın.  
  
### <a name="enumerating-the-visual-tree"></a>Görsel Ağacı Niçin Oyalama  
 Sınıf, <xref:System.Windows.Media.VisualTreeHelper> görsel bir ağacın üyelerini derecelendirmek için işlevsellik sağlar. Bir üst öğeyi <xref:System.Windows.Media.VisualTreeHelper.GetParent%2A> almak için yöntemi arayın. Bir alt bölümü veya doğrudan soyundan gelen görsel <xref:System.Windows.Media.VisualTreeHelper.GetChild%2A> bir nesneyi almak için yöntemi arayın. Bu yöntem, <xref:System.Windows.Media.Visual> belirtilen dizinde üst bir alt döndürür.  
  
 Aşağıdaki örnek, görsel nesne hiyerarşisinin tüm işleme bilgilerini seri hale getirmek istiyorsanız kullanmak isteyabileceğiniz bir teknik olan görsel nesnenin tüm torunlarını nasıl sayısallaştırabileceğinizi gösterir.  
  
 [!code-csharp[VisualsOverview#101](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml.cs#101)]
 [!code-vb[VisualsOverview#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsOverview/visualbasic/window1.xaml.vb#101)]  
  
 Çoğu durumda, mantıksal ağaç bir uygulamadaki öğelerin [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] daha yararlı bir gösterimidir. Mantıksal ağacı doğrudan değiştirmeseniz de, uygulamanın bu görünümü özellik devralma ve olay yönlendirmesini anlamak için yararlıdır. Görsel ağacın aksine, mantıksal ağaç görsel olmayan veri nesnelerini <xref:System.Windows.Documents.ListItem>temsil edebilir, örneğin. Mantıksal ağaç hakkında daha fazla bilgi için [WPF'deki Ağaçlar'a](../advanced/trees-in-wpf.md)bakın.  
  
 Sınıf, <xref:System.Windows.Media.VisualTreeHelper> görsel nesnelerin sınırlayıcı dikdörtgenini döndürmek için yöntemler sağlar. Görsel bir nesnenin sınırlayıcı dikdörtgenini arayarak <xref:System.Windows.Media.VisualTreeHelper.GetContentBounds%2A>döndürebilirsiniz. Görsel nesnenin kendisi de dahil olmak üzere görsel nesnenin tüm torunlarının sınırlayıcı <xref:System.Windows.Media.VisualTreeHelper.GetDescendantBounds%2A>dikdörtgenini arayarak döndürebilirsiniz. Aşağıdaki kod, görsel bir nesnenin ve tüm soyundan gelenlerin sınırlayıcı dikdörtgenini nasıl hesaplayacağınızı gösterir.  
  
 [!code-csharp[VisualsOverview#102](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml.cs#102)]
 [!code-vb[VisualsOverview#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsOverview/visualbasic/window1.xaml.vb#102)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.Visual>
- <xref:System.Windows.Media.VisualTreeHelper>
- <xref:System.Windows.Media.DrawingVisual>
- [2B Grafikleri ve Görüntüleme](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Görsel Katmanda Tıklama Testi](hit-testing-in-the-visual-layer.md)
- [DrawingVisual Nesnelerini Kullanma](using-drawingvisual-objects.md)
- [Eğitmen: Win32 Uygulamasında Görsel Nesneler Barındırma](tutorial-hosting-visual-objects-in-a-win32-application.md)
- [WPF Uygulama Performansını İyileştirme](../advanced/optimizing-wpf-application-performance.md)
