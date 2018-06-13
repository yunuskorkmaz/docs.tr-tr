---
title: WPF Grafik İşlemeye Genel Bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], rendering
- rendering graphics [WPF]
ms.assetid: 6dec9657-4d8c-4e46-8c54-40fb80008265
ms.openlocfilehash: 305af1025abb98950d90f46e75a9f261704a8ebe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33566736"
---
# <a name="wpf-graphics-rendering-overview"></a>WPF Grafik İşlemeye Genel Bakış
Bu konu genel bir bakış sağlar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] görsel katmanı. Rolü üzerinde odaklanır <xref:System.Windows.Media.Visual> desteği işlemeye sınıfı [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] modeli.  
  
  
<a name="role_of_visual_object"></a>   
## <a name="role-of-the-visual-object"></a>Görsel nesne rolü  
 <xref:System.Windows.Media.Visual> Sınıfı, temel soyutlama içinden her <xref:System.Windows.FrameworkElement> nesne türetilir. Ayrıca yeni denetimler yazma için giriş noktası olarak hizmet [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ve birçok yolla, Win32 uygulama modelinde pencere işleyicisi (HWND) olarak değerlendirilebilir.  
  
 <xref:System.Windows.Media.Visual> Nesnesidir çekirdek [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , birincil rolü işleme desteği sağlamak üzere nesnesi,. Kullanıcı arabirimi denetimlerini, gibi <xref:System.Windows.Controls.Button> ve <xref:System.Windows.Controls.TextBox>, türetilen <xref:System.Windows.Media.Visual> sınıfı ve işleme verilerini sürdürmek için kullanın. <xref:System.Windows.Media.Visual> Nesnesi için destek sağlar:  
  
-   Çıktı görüntü: kalıcı, işleme serileştirilmiş bir görsel çizim içeriği.  
  
-   Dönüşümler: görüntü üzerine dönüşümleri gerçekleştiriliyor.  
  
-   Kırpma: kırpma bölge desteği için bir görsel sağlama.  
  
-   İsabet testi: koordinat veya geometri görsel sınırları içinde yer alan olup olmadığını belirleme.  
  
-   Sınırlama kutusu hesaplamalar: görsel sınırlayıcı dikdörtgenini belirleme.  
  
 Ancak, <xref:System.Windows.Media.Visual> nesne işleme olmayan özellikleri için destek gibi içermez:  
  
-   Olay işleme  
  
-   Düzen  
  
-   Stilleri  
  
-   Veri bağlama  
  
-   Genelleştirme  
  
 <xref:System.Windows.Media.Visual> alt sınıfların türetilmesi gerekir ortak soyut bir sınıf sunulur. Aşağıda sunulan visual nesne gösterilmiştir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 ![Sınıfları diyagramı Visual nesnesinden türetilmiş](../../../../docs/framework/wpf/graphics-multimedia/media/visualclass01.png "VisualClass01")  
Görsel sınıf hiyerarşisi  
  
### <a name="drawingvisual-class"></a>DrawingVisual sınıfı  
 <xref:System.Windows.Media.DrawingVisual> Olan şekil, görüntü veya metin işlemek için kullanılan sınıf çizim basit. Bu sınıf, çalışma zamanı performansını artırır, düzen veya olay işleme sağlamadığından basit olarak değerlendirilir. Bu nedenle, çizimler arka planlar ve küçük resim için idealdir. <xref:System.Windows.Media.DrawingVisual> Özel görsel bir nesne oluşturmak için kullanılabilir. Daha fazla bilgi için bkz: [kullanarak DrawingVisual nesneleri](../../../../docs/framework/wpf/graphics-multimedia/using-drawingvisual-objects.md).  
  
### <a name="viewport3dvisual-class"></a>Viewport3DVisual sınıfı  
 <xref:System.Windows.Media.Media3D.Viewport3DVisual> 2B arasında bir köprü sağlar <xref:System.Windows.Media.Visual> ve <xref:System.Windows.Media.Media3D.Visual3D> nesneleri. <xref:System.Windows.Media.Media3D.Visual3D> Sınıfı, tüm 3B görsel öğeleri için temel sınıf. <xref:System.Windows.Media.Media3D.Viewport3DVisual> Belirlediğiniz gerektiren bir <xref:System.Windows.Media.Media3D.Viewport3DVisual.Camera%2A> değeri ve <xref:System.Windows.Media.Media3D.Viewport3DVisual.Viewport%2A> değeri. Kamera, Sahne görüntülemenizi sağlar. Görünüm penceresinin burada projeksiyon 2B yüzeyine eşlemeleri oluşturur. 3D hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], bkz: [3-b grafiklere genel bakış](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md).  
  
### <a name="containervisual-class"></a>ContainerVisual sınıfı  
 <xref:System.Windows.Media.ContainerVisual> Sınıfı bir koleksiyonu için bir kapsayıcı olarak kullanılan <xref:System.Windows.Media.Visual> nesneleri. <xref:System.Windows.Media.DrawingVisual> Sınıfı türer <xref:System.Windows.Media.ContainerVisual> görsel nesneler koleksiyonunu içeren izin veren sınıfı.  
  
### <a name="drawing-content-in-visual-objects"></a>Görsel nesneler çizim içeriği  
 A <xref:System.Windows.Media.Visual> nesne olarak işleme verilerini depolayan bir **vektör grafikleri yönerge listesi**. Yönerge listedeki her öğeye bir alt düzey grafik veri kümesini ve seri hale getirilmiş bir biçimde ilişkili kaynakları temsil eder. Çizim içeriği içerebilir işleme veri dört farklı türde vardır.  
  
|İçerik türü çizme|Açıklama|  
|--------------------------|-----------------|  
|Vektör grafikleri|Temsil vektör grafik veri ve varsa ilişkili <xref:System.Windows.Media.Brush> ve <xref:System.Windows.Media.Pen> bilgi.|  
|Görüntü|Görüntüyü tarafından tanımlanan bir bölgedeki temsil eden bir <xref:System.Windows.Rect>.|  
|Karakter|İşleyen bir çizim temsil eden bir <xref:System.Windows.Media.GlyphRun>, belirtilen yazı tipi kaynaktan karakterlerin dizisi olduğu. Metin nasıl temsil budur.|  
|Video|Video işleyen bir çizim temsil eder.|  
  
 <xref:System.Windows.Media.DrawingContext> Doldurmak sayesinde bir <xref:System.Windows.Media.Visual> visual içeriğe sahip. Kullandığınızda, bir <xref:System.Windows.Media.DrawingContext> nesnenin çizim komutları, gerçekte depoladığınız grafik sistem tarafından kullanılan daha sonra işleme veri kümesini; gerçek zamanlı ekrana çizim değil.  
  
 Oluştururken bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetlemek, gibi bir <xref:System.Windows.Controls.Button>, Denetim dolaylı olarak kendisi çizim için işleme veriler üretir. Örneğin, ayarlama <xref:System.Windows.Controls.ContentControl.Content%2A> özelliği <xref:System.Windows.Controls.Button> karaktere işleme gösterimini depolamak denetimi neden olur.  
  
 A <xref:System.Windows.Media.Visual> bir veya daha fazla olarak içeriği açıklar <xref:System.Windows.Media.Drawing> içinde yer alan nesneleri bir <xref:System.Windows.Media.DrawingGroup>. A <xref:System.Windows.Media.DrawingGroup> ayrıca geçirgenlik maskeleri, dönüşümler, bit eşlem efektleri ve içeriğini uygulanan diğer işlemleri açıklanır. <xref:System.Windows.Media.DrawingGroup> işlem, şu sırayla uygulanır, içerik işlendiğinde: <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>, <xref:System.Windows.Media.DrawingGroup.Opacity%2A>, <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>, <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>, <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>ve ardından <xref:System.Windows.Media.DrawingGroup.Transform%2A>.  
  
 Aşağıdaki çizimde sırayı gösterir <xref:System.Windows.Media.DrawingGroup> işlemleri sırasında işleme sırası uygulanır.  
  
 ![DrawingGroup işlem sırası](../../../../docs/framework/wpf/graphics-multimedia/media/graphcismm-drawinggroup-order.png "graphcismm_drawinggroup_order")  
DrawingGroup işlem sırası  
  
 Daha fazla bilgi için bkz: [çizim nesnelere genel bakış](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md).  
  
#### <a name="drawing-content-at-the-visual-layer"></a>Görsel katman çizim içeriği  
 Hiçbir zaman doğrudan örneği bir <xref:System.Windows.Media.DrawingContext>; belirli yöntemlerden çizim bağlamı gibi ancak elde edebilir <xref:System.Windows.Media.DrawingGroup.Open%2A?displayProperty=nameWithType> ve <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A?displayProperty=nameWithType>. Aşağıdaki örnek alır bir <xref:System.Windows.Media.DrawingContext> gelen bir <xref:System.Windows.Media.DrawingVisual> ve dikdörtgen çizmek için kullanır.  
  
 [!code-csharp[drawingvisualsample#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#101)]
 [!code-vb[drawingvisualsample#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#101)]  
  
#### <a name="enumerating-drawing-content-at-the-visual-layer"></a>Çizim içeriği Visual katmanında numaralandırma  
 Diğer kullanımları, ek olarak <xref:System.Windows.Media.Drawing> nesnelerini ayrıca içeriğini numaralandırmak için nesne modeli sağlar bir <xref:System.Windows.Media.Visual>.  
  
> [!NOTE]
>  Görsel içeriği numaralandırılırken alma <xref:System.Windows.Media.Drawing> nesneleri ve vektör grafikleri yönerge listesi olarak işleyici verinin temeldeki gösterimini değil.  
  
 Aşağıdaki örnek kullanır <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> alma yöntemi <xref:System.Windows.Media.DrawingGroup> değerini bir <xref:System.Windows.Media.Visual> ve onu numaralandırır.  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
<a name="how_visual_objects_are_used_to_build_controls"></a>   
## <a name="how-visual-objects-are-used-to-build-controls"></a>Görsel nesneler yapı denetimlere nasıl kullanılır  
 Nesnelerinin birçok [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] diğer görsel nesnelerin alt nesnelerin değişen hiyerarşileri bulunabilir anlamına oluşurlar. Birçok kullanıcı arabirimi öğeleri [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], denetimleri gibi farklı türde öğe işleme temsil eden birden çok visual nesnelerin, oluşurlar. Örneğin, <xref:System.Windows.Controls.Button> denetimi dahil olmak üzere diğer nesnelerin sayısı içerebilir <xref:Microsoft.Windows.Themes.ClassicBorderDecorator>, <xref:System.Windows.Controls.ContentPresenter>, ve <xref:System.Windows.Controls.TextBlock>.  
  
 Aşağıdaki kodda gösterildiği bir <xref:System.Windows.Controls.Button> biçimlendirme tanımlı denetim.  
  
 [!code-xaml[VisualsOverview#VisualsOverviewSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml#visualsoverviewsnippet1)]  
  
 Varsayılan oluşturan visual nesnelerini listeleme olsaydı <xref:System.Windows.Controls.Button> denetim, aşağıda gösterilen visual nesne Bul:  
  
 ![Görsel ağaç hiyerarşi diyagramı](../../../../docs/framework/wpf/graphics-multimedia/media/visuallayeroverview03.gif "VisualLayerOverview03")  
Görsel ağaç hiyerarşi diyagramı  
  
 <xref:System.Windows.Controls.Button> Denetimi içeren bir <xref:Microsoft.Windows.Themes.ClassicBorderDecorator> sırayla içeren öğesi bir <xref:System.Windows.Controls.ContentPresenter> öğesi. <xref:Microsoft.Windows.Themes.ClassicBorderDecorator> Öğesidir kenarlık ve arka plan için çizim için sorumlu <xref:System.Windows.Controls.Button>. <xref:System.Windows.Controls.ContentPresenter> Öğesidir içeriğini görüntülemek için sorumlu <xref:System.Windows.Controls.Button>. Bu durumda, beri görüntüleme metni <xref:System.Windows.Controls.ContentPresenter> öğesi içeren bir <xref:System.Windows.Controls.TextBlock> öğesi. Olgu, <xref:System.Windows.Controls.Button> denetim kullanan bir <xref:System.Windows.Controls.ContentPresenter> gibi diğer öğeleri tarafından içerik gösterilebilir anlamına gelir bir <xref:System.Windows.Controls.Image> veya geometri, gibi bir <xref:System.Windows.Media.EllipseGeometry>.  
  
### <a name="control-templates"></a>Denetim şablonları  
 Bir denetim genişletme denetimlerin bir hiyerarşiye anahtarıdır <xref:System.Windows.Controls.ControlTemplate>. Bir denetim şablonu bir denetim için varsayılan visual hiyerarşi belirtir. Bir denetim açıkça başvurduğunuzda, visual hiyerarşisi örtük olarak başvuru. Bir denetim için özelleştirilmiş bir görünümünü oluşturmak bir denetim şablonu için varsayılan değerleri geçersiz kılabilirsiniz. Örneğin, arka plan rengi değerini değiştirebilir <xref:System.Windows.Controls.Button> bir düz renk değeri yerine bir doğrusal gradyan rengi değeri kullanır, böylece denetim. Daha fazla bilgi için bkz: [düğme stilleri ve şablonları](../../../../docs/framework/wpf/controls/button-styles-and-templates.md).  
  
 Bir kullanıcı arabirimi öğesi gibi bir <xref:System.Windows.Controls.Button> denetlemek, bir denetim tüm işleme tanımını tanımlayan birkaç vektör grafikleri yönerge listesi içerir. Aşağıdaki kodda gösterildiği bir <xref:System.Windows.Controls.Button> biçimlendirme tanımlı denetim.  
  
 [!code-xaml[VisualsOverview#VisualsOverviewSnippet2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml#visualsoverviewsnippet2)]  
  
 Görsel nesneleri numaralandırmak ve oluşturan grafik yönerge listeleri vektör olsaydınız <xref:System.Windows.Controls.Button> denetim, aşağıda gösterilen nesne Bul:  
  
 ![Görsel ağaç ve verileri işleme diyagramı](../../../../docs/framework/wpf/graphics-multimedia/media/visuallayeroverview04.png "VisualLayerOverview04")  
Görsel ağaç ve verileri işleme diyagramı  
  
 <xref:System.Windows.Controls.Button> Denetimi içeren bir <xref:Microsoft.Windows.Themes.ClassicBorderDecorator> sırayla içeren öğesi bir <xref:System.Windows.Controls.ContentPresenter> öğesi. <xref:Microsoft.Windows.Themes.ClassicBorderDecorator> Öğesidir kenarlık ve arka plan düğmesinin oluşturan tüm ayrık grafik öğeleri çizim için sorumlu. <xref:System.Windows.Controls.ContentPresenter> Öğesidir içeriğini görüntülemek için sorumlu <xref:System.Windows.Controls.Button>. Bu durumda, beri görüntüleyen bir görüntü <xref:System.Windows.Controls.ContentPresenter> öğesi içeren bir <xref:System.Windows.Controls.Image> öğesi.  
  
 Görsel nesneler ve vektör grafikleri yönerge listeleri hiyerarşi hakkında dikkat edilecek noktaları vardır:  
  
-   Hiyerarşi içinde sıralama çizim bilgileri işleme sırasını temsil eder. Kök görsel öğeyi, alt öğelerini, sağ, üst-alt sol çapraz geçiş. Bir öğenin görsel alt öğe varsa, bunlar önce öğenin eşdüzey çapraz geçiş.  
  
-   Hiyerarşisinde olmayan yaprak düğümü öğeleri gibi <xref:System.Windows.Controls.ContentPresenter>, alt öğelerini kapsamak için kullanılmış — yönerge listeleri içermez.  
  
-   Vektör grafikleri yönerge listesi ve görsel alt bir görsel öğe içeriyorsa, üst görsel öğe yönerge listesinde herhangi bir görsel alt nesnelerin çizimler önce işlenir.  
  
-   Vektör grafikleri yönerge listesi öğeleri soldan sağa işlenir.  
  
<a name="visual_tree"></a>   
## <a name="visual-tree"></a>Görsel ağaç  
 Görsel ağaç bir uygulamanın kullanıcı arabiriminde kullanılan tüm görsel öğeleri içerir. Bir görsel öğe kalıcı çizim bilgileri içerdiğinden görsel ağacını görüntüleme cihazı için çıktı oluşturmak için gereken tüm işleme bilgileri içeren bir Sahne grafik düşünebilirsiniz. Kod olup olmadığını veya işaretleme doğrudan uygulama tarafından oluşturulan tüm görsel öğelerin toplamı ağacıdır. Görsel ağaç denetimleri ve veri nesneleri gibi öğeler şablon genişlemesi tarafından oluşturulan tüm görsel öğelerini de içerir.  
  
 Aşağıdaki kodda gösterildiği bir <xref:System.Windows.Controls.StackPanel> biçimlendirme içinde tanımlanan öğe.  
  
 [!code-xaml[VisualsOverview#VisualsOverviewSnippet3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml#visualsoverviewsnippet3)]  
  
 Oluşturan visual nesnelerini listeleme olsaydı <xref:System.Windows.Controls.StackPanel> biçimlendirme örneği öğesinde, aşağıda gösterilen visual nesne Bul:  
  
 ![Görsel ağaç hiyerarşi diyagramı](../../../../docs/framework/wpf/graphics-multimedia/media/visuallayeroverview05.gif "VisualLayerOverview05")  
Görsel ağaç hiyerarşi diyagramı  
  
### <a name="rendering-order"></a>Sipariş işleme  
 Görsel ağaç işleme sırasını belirleyen [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] görsel ve çizim nesneleri. Çapraz Geçişi sırasını görsel görsel ağaç en üstteki düğümü kök başlar. Kök görselin alt sonra geçiş soldan sağa doğru. Görsel alt öğe varsa, alt öğelerini önce görselin eşdüzey çapraz geçiş. Bu görsel bir alt içeriğini önünde görselin kendi içerik işlenmeden anlamına gelir.  
  
 ![Görsel ağaç işleme düzeni diyagramı](../../../../docs/framework/wpf/graphics-multimedia/media/visuallayeroverview06.gif "VisualLayerOverview06")  
Görsel ağaç işleme düzeni diyagramı  
  
### <a name="root-visual"></a>Kök Visual  
 **Kök visual** bir görsel ağaç hiyerarşideki en üst öğesidir. Çoğu uygulamada visual kök temel sınıfını bozulmuş <xref:System.Windows.Window> veya <xref:System.Windows.Navigation.NavigationWindow>. Ancak, bir Win32 uygulaması görsel nesneleri barındırma ise visual kök Win32 penceresinde barındırma en üstteki visual olabilir. Daha fazla bilgi için bkz: [Öğreticisi: görsel nesneleri bir Win32 uygulaması barındırma](../../../../docs/framework/wpf/graphics-multimedia/tutorial-hosting-visual-objects-in-a-win32-application.md).  
  
### <a name="relationship-to-the-logical-tree"></a>Mantıksal ağacının ilişkisi  
 Mantıksal ağaçta [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamanın çalışma zamanında öğelerini temsil eder. Bu ağaç doğrudan düzenlersiniz değil de, bu görünüm uygulamanın özellik devralma ve olay yönlendirme anlamak için kullanışlıdır. Görsel ağaç mantıksal ağacının görsel olmayan veri nesneleri gibi gösterebilir <xref:System.Windows.Documents.ListItem>. Çoğu durumda, mantıksal ağacının bir uygulamanın biçimlendirme tanımları çok yakından eşler. Aşağıdaki kodda gösterildiği bir <xref:System.Windows.Controls.DockPanel> biçimlendirme içinde tanımlanan öğe.  
  
 [!code-xaml[VisualsOverview#VisualsOverviewSnippet5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml#visualsoverviewsnippet5)]  
  
 Oluşturan mantıksal nesnelerini listeleme olsaydı <xref:System.Windows.Controls.DockPanel> biçimlendirme örneği öğesinde, aşağıda gösterilen mantıksal nesne Bul:  
  
 ![Ağaç diyagramı](../../../../docs/framework/wpf/graphics-multimedia/media/tree1-wcp.gif "Tree1_wcp")  
Mantıksal ağaç diyagramı  
  
 Görsel ağaç ve mantıksal ağacının herhangi eklenmesi, silinmesi veya değiştirilmesi öğelerinin yansıtma uygulama öğeleri geçerli kümesi ile eşitlenir. Ancak, uygulamanın farklı görünümleri ağaçları sunar. Görsel ağaç mantıksal ağacının bir denetimin genişletmez <xref:System.Windows.Controls.ContentPresenter> öğesi. Bu, mantıksal bir ağaç ve aynı nesne kümesini için görsel bir ağaç arasında doğrudan bir bire değil anlamına gelir. Aslında, çağırma **LogicalTreeHelper** nesnenin <xref:System.Windows.LogicalTreeHelper.GetChildren%2A> yöntemi ve **VisualTreeHelper** nesnenin <xref:System.Windows.Media.VisualTreeHelper.GetChild%2A> bir parametre farklı sonuçlar verir gibi aynı öğesi kullanılarak yöntemi .  
  
 Mantıksal ağacının hakkında daha fazla bilgi için bkz: [WPF ağaçlarında](../../../../docs/framework/wpf/advanced/trees-in-wpf.md).  
  
### <a name="viewing-the-visual-tree-with-xamlpad"></a>Görsel ağaç XamlPad ile görüntüleme  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Aracı, XamlPad'i görüntüleme ve karşılık gelen görsel ağaç şu anda tanımlanmış keşfetmek için bir seçenek sunar [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] içeriği. Tıklatın **Göster görsel ağaç** görsel ağaç görüntülemek için menü çubuğundaki düğmesini. Aşağıdaki genişlemesi gösterilmektedir [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] görsel ağaç düğümleri içine içerik **görsel ağaç Gezgini** XamlPad panelini:  
  
 ![XamlPad'de Görsel Ağaç Gezgini paneli](../../../../docs/framework/wpf/graphics-multimedia/media/visuallayeroverview08.png "VisualLayerOverview08")  
XamlPad'de Görsel Ağaç Gezgini paneli  
  
 Bildirim nasıl <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.TextBox>, ve <xref:System.Windows.Controls.Button> denetimlerini her bir ayrı görsel nesne hiyerarşide görüntülemek **görsel ağaç Gezgini** XamlPad panelini. Bunun nedeni, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimleriniz bir <xref:System.Windows.Controls.ControlTemplate> bu denetimin görsel ağaç içerir. Bir denetim açıkça başvurduğunuzda, visual hiyerarşisi örtük olarak başvuru.  
  
### <a name="profiling-visual-performance"></a>Görsel performans profili oluşturma  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir profil uygulamanızın çalışma zamanı davranışını çözümlemek ve türde uygulayabileceğiniz performans iyileştirmelerini belirlemenize olanak sağlayan araçları performans sağlar. Visual profil oluşturucu araç eşleyerek doğrudan uygulamanın görsel ağaç performans verilerini zengin, grafik bir görünümünü sağlar. Bu ekran görüntüsü **CPU kullanımı** Visual Profil Oluşturucu bölümünde, bir nesnenin kullanımını kesin bir dökümünü verir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] işleme ve düzen gibi hizmetleri.  
  
 ![Visual profil oluşturucu çıktı görüntülemek](../../../../docs/framework/wpf/graphics-multimedia/media/wpfperf-visualprofiler-04.png "WPFPerf_VisualProfiler_04")  
Visual profil oluşturucu görüntüsü çıkışı  
  
<a name="visual_rendering_behavior"></a>   
## <a name="visual-rendering-behavior"></a>Görsel işleme davranışı  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] görsel nesneler işleme davranışını etkileyen çeşitli özellikler sunar: modu grafikleri, vektör grafikleri ve cihaz bağımsız grafikler korunur.  
  
### <a name="retained-mode-graphics"></a>Elde tutulmuş modu grafikleri  
 Görsel nesne rolü anlama anahtarları biri arasındaki farkı anlamak için **anlık mod** ve **modu korunur** grafik sistemleri. GDI veya GDI + göre standart bir Win32 uygulaması anlık kip grafik sistemi kullanır. Uygulamanın yeniden boyutlandırılan, bir pencere gibi bir eylemi nedeniyle geçersiz istemci alanını bölümünü yeniden çizerken için sorumlu olduğu anlamına gelir veya görünümünü değiştirme bir nesne.  
  
 ![Win32 işleme sırası diyagramı](../../../../docs/framework/wpf/graphics-multimedia/media/visuallayeroverview01.png "VisualLayerOverview01")  
Win32 işleme sırası diyagramı  
  
 Buna karşılık, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] saklama modu sistemi kullanır. Bu görsel görünümünü uygulama nesneleri seri hale getirilmiş çizim veri kümesini tanımlamak anlamına gelir. Çizim veri tanımlandıktan sonra bundan sonra uygulama nesneleri işlemek için tüm yeniden çizmeyi isteklerini yanıtlamak için sorumlu bir sistemdir. Bile çalışma zamanında, değiştirebilir veya uygulama nesneleri oluşturmak ve hala sistemi istekleri boyamak için yanıt için kullanır. Saklama modu grafik sistemindeki güç bilgi çizim her zaman bir serileştirilmiş durumda uygulama, ancak işleme sorumluluk sisteme sol tarafından kalıcı olmasını ' dir. Aşağıdaki diyagramda uygulama dayanan nasıl gösterir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] boyamak için isteklerini yanıtlamak için.  
  
 ![WPF işleme sırası diyagramı](../../../../docs/framework/wpf/graphics-multimedia/media/visuallayeroverview02.png "VisualLayerOverview02")  
WPF işleme sırası diyagramı  
  
#### <a name="intelligent-redrawing"></a>Akıllı yeniden çizim  
 Saklama modu grafik kullanmanın en büyük avantajlarından biri, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] verimli bir şekilde ne uygulamada çizilmesi gerektiğinde en iyi duruma getirebilirsiniz. Karmaşık Sahne opaklık değişen düzeylerine sahip olsa bile, genellikle yeniden en iyi duruma getirmek için özel amaçlı kod yazmanız gerekmez. Bu oldukça fazla güncelleştirme bölgede yeniden miktarını en aza indirerek, uygulamanızın en iyi duruma getirme içinde çaba harcamanızı Win32 programlama ile karşılaştırın. Bkz: [güncelleştirme bölgede yeniden](https://msdn.microsoft.com/library/dd162909.aspx) karmaşıklık türünün bir örneği için söz konusu Win32 uygulamalarında yeniden iyileştirme.  
  
### <a name="vector-graphics"></a>Vektör grafikleri  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kullanan **vektör grafikleri** olarak, işleme veri biçimi. Vektör grafikleri — ölçeklenebilir vektör grafikleri (SVG), Windows meta dosyaları (.wmf) ve TrueType yazı tiplerini içerir — işleme verileri depolamak ve grafik temelleri kullanarak görüntü yeniden oluşturmak nasıl açıklayan yönergeler oluşan bir liste olarak iletme. Örneğin, TrueType yazı tipleri çizgiler, eğriler ve komutlar kümesi yerine piksel dizisi açıklamak anahat yazı tipleridir. Vektör grafikleri kilit yararları de herhangi boyutunu ve çözünürlüğü ölçeklendirin yeteneğidir.  
  
 Vektör grafikleri, bit eşlem grafik belirli bir çözüm için önceden oluşturulan bir görüntü piksel piksel gösterimi olarak işleme verileri depolar. Bit eşlem ve vektör grafik biçimleri arasındaki temel farklılıklar orijinal kaynak görüntü kalitesini biridir. Örneğin, bir kaynak görüntü boyutu değiştirildiğinde, görüntü kalitesini koruma görüntünün vektör grafik sistemleri ölçeklendirme ancak bit eşlem grafik sistemleri görüntü uzatma.  
  
 % 300 yeniden boyutlandırılmış bir kaynak görüntüsü aşağıda gösterilmiştir. Kaynak görüntü bir bit eşlem grafik resim esnetilebilir yerine bir vektör grafikleri görüntüsü olarak ölçeklendirilmiş görüntülenen deformasyonları dikkat edin.  
  
 ![Izgara ve vektör grafikleri arasındaki farklar](../../../../docs/framework/wpf/graphics-multimedia/media/vectorgraphics01.png "VectorGraphics01")  
Izgara ve vektör grafikleri arasındaki farklar  
  
 Aşağıdaki biçimlendirmede iki gösterir <xref:System.Windows.Shapes.Path> öğesi tanımlandı. İkinci öğesini kullanan bir <xref:System.Windows.Media.ScaleTransform> ilk öğesi çizim yönergeleri % 300 yeniden boyutlandırmak için. Dikkat çizim yönergeleri <xref:System.Windows.Shapes.Path> öğeleri değişmeden kalır.  
  
 [!code-xaml[VectorGraphicsSnippets#VectorGraphicsSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VectorGraphicsSnippets/CS/PageOne.xaml#vectorgraphicssnippet1)]  
  
### <a name="about-resolution-and-device-independent-graphics"></a>Çözümleme ve aygıttan bağımsız grafikler hakkında  
 Metin ve ekranınızda grafik boyutunu belirleyen iki sistem Etkenler vardır: çözümleme ve DPI. Çözüm ekranda görünen piksel sayısı açıklanır. Çözümleme daha yüksek elde ettiği piksel grafikler ve daha küçük görüntülenecek metni neden küçük alın. Çözümleme 1600 x 1200'e değiştirildiğinde, 1024 x 768'olarak ayarlanmış bir monitörde gösterilen grafik çok daha küçük görünür.  
  
 Diğer sistem ayarı DPI, ekran inç piksel cinsinden boyutu açıklar. Çoğu [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] sistemlerine sahip bir DPI 96, ekran inç 96 piksel olduğu anlamına gelir. DPI ayarı artan büyük ekran inç sağlar; DPI azalan ekran inç küçültür. Başka bir deyişle, ekran inç gerçek inç aynı boyutta değil; Çoğu sistemlerde, bu büyük olasılıkla değil. DPI arttıkça, ekran inç boyutunu artırılmış nedeniyle DPI grafikler ve metin daha büyük hale. DPI artırma metin okunmasını, özellikle yüksek çözünürlüklerde yapabilirsiniz.  
  
 Tüm uygulamalar DPI şunlardır: bazı donanım piksel birincil ölçü; kullanın DPI sistem değiştirme bu uygulamalar üzerinde etkisi yoktur. Diğer birçok uygulama DPI birimleri yazı tipi boyutlarını açıklamaktadır, ancak şey açıklamak için piksel kullanmak için kullanın. Çok küçük ya da çok büyük DPI yapma sistemin DPI ayarı ile uygulamaları metin ölçekler, ancak uygulamalar UI yok olduğundan bu uygulamalar için düzeni sorunlara neden olabilir. Bu sorunu kullanılarak geliştirilen uygulamaları için ortadan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kendi birincil ölçü, donanım piksel yerine olarak aygıttan bağımsız piksel kullanarak otomatik ölçeklendirmeyi destekler; grafikler ve metin uygulama geliştiriciden ek iş olmadan düzgün şekilde ölçeklendirilir. Nasıl bir örneği aşağıda gösterilmiştir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] metin ve grafikler farklı DPI ayarları görünür olan.  
  
 ![Grafikler ve metin farklı DPI ayarlarıyla](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-dpi-setting-examples.png "graphicsmm_dpi_setting_examples")  
Grafikler ve farklı DPI ayarlarıyla metin  
  
<a name="visualtreehelper_class"></a>   
## <a name="visualtreehelper-class"></a>VisualTreeHelper sınıfı  
 <xref:System.Windows.Media.VisualTreeHelper> , Yüksek performanslı özel denetimleri geliştirme gibi belirli senaryolarda kullanışlıdır görsel nesne düzeyinde programlama için alt düzey işlevsellik sağlayan statik yardımcı sınıfını bir sınıftır. Çoğu durumda, üst düzey [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] gibi framework nesnelerini <xref:System.Windows.Controls.Canvas> ve <xref:System.Windows.Controls.TextBlock>, esneklik ve kullanım kolaylığı sunar.  
  
### <a name="hit-testing"></a>İsabet testi  
 <xref:System.Windows.Media.VisualTreeHelper> Sınıfı isabet testi destek varsayılan isabet olduğunda görsel nesneler üzerinde sınama gereksinimlerinizi karşılamıyor için yöntemler sağlar. Kullanabileceğiniz <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> yöntemleri <xref:System.Windows.Media.VisualTreeHelper> geometri veya nokta koordinat değeri bir denetim ya da grafik öğesinin gibi belirli bir nesne sınırları içinde olup olmadığını belirlemek için sınıf. Örneğin, isabet testi nesnenin sınırlayıcı dikdörtgenin içindeki fare tıklatma de kendi özel isabet testi gerçekleştirmek için isabet sınama varsayılan uygulama geçersiz kılmayı seçebilirsiniz bir daire geometrisi içinde olup olmadığını belirlemek için kullanabilirsiniz hesaplamalar.  
  
 İsabet testi ile ilgili daha fazla bilgi için bkz: [isabet testi görsel katmandaki](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md).  
  
### <a name="enumerating-the-visual-tree"></a>Görsel ağaç numaralandırma  
 <xref:System.Windows.Media.VisualTreeHelper> Sınıfı bir görsel ağaç üyeleri numaralandırma işlevselliği sağlar. Bir üst almak için arama <xref:System.Windows.Media.VisualTreeHelper.GetParent%2A> yöntemi. Bir alt veya doğrudan alt öğesi, görsel bir nesne almak için çağrı <xref:System.Windows.Media.VisualTreeHelper.GetChild%2A> yöntemi. Bu yöntem bir alt öğesini döndürür <xref:System.Windows.Media.Visual> belirtilen dizindeki üst.  
  
 Aşağıdaki örnek, bir görsel nesne hiyerarşinin tüm işleme bilgileri getirmede ilgileniyorsanız kullanmak isteyebileceği bir tekniktir görsel bir nesne tüm alt öğeleri listeleme gösterilmektedir.  
  
 [!code-csharp[VisualsOverview#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml.cs#101)]
 [!code-vb[VisualsOverview#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsOverview/visualbasic/window1.xaml.vb#101)]  
  
 Çoğu durumda, mantıksal ağacının öğeleri daha kullanışlı bir gösterimi olan bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama. Mantıksal ağacının doğrudan değiştirmeyin karşın, bu görünüm uygulamanın özellik devralma ve olay yönlendirme anlamak için kullanışlıdır. Görsel ağaç mantıksal ağacının görsel olmayan veri nesneleri gibi gösterebilir <xref:System.Windows.Documents.ListItem>. Mantıksal ağacının hakkında daha fazla bilgi için bkz: [WPF ağaçlarında](../../../../docs/framework/wpf/advanced/trees-in-wpf.md).  
  
 <xref:System.Windows.Media.VisualTreeHelper> Sınıfı görsel nesnelerinin sınırlayıcı dikdörtgenini döndürmek için yöntemler sağlar. Görsel bir nesne sınırlayıcı dikdörtgenini çağırarak döndürebilir <xref:System.Windows.Media.VisualTreeHelper.GetContentBounds%2A>. Tüm bağımlı öğelerini çağırarak görsel nesne kendisi de dahil olmak üzere görsel bir nesne sınırlayıcı dikdörtgenini döndürebilir <xref:System.Windows.Media.VisualTreeHelper.GetDescendantBounds%2A>. Aşağıdaki kod, nasıl görsel bir nesne ve tüm alt öğeleri sınırlayıcı dikdörtgenini hesaplar gösterir.  
  
 [!code-csharp[VisualsOverview#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml.cs#102)]
 [!code-vb[VisualsOverview#102](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsOverview/visualbasic/window1.xaml.vb#102)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Media.Visual>  
 <xref:System.Windows.Media.VisualTreeHelper>  
 <xref:System.Windows.Media.DrawingVisual>  
 [2B Grafikleri ve Görüntüleme](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [Görsel Katmanda Tıklama Testi](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md)  
 [DrawingVisual Nesnelerini Kullanma](../../../../docs/framework/wpf/graphics-multimedia/using-drawingvisual-objects.md)  
 [Eğitmen: Win32 Uygulamasında Görsel Nesneler Barındırma](../../../../docs/framework/wpf/graphics-multimedia/tutorial-hosting-visual-objects-in-a-win32-application.md)  
 [WPF Uygulama Performansını İyileştirme](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)
