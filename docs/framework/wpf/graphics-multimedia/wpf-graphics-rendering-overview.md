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
ms.openlocfilehash: da455adb23dd70a915e81217c6c30f2d523e001c
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2019
ms.locfileid: "58409659"
---
# <a name="wpf-graphics-rendering-overview"></a>WPF Grafik İşlemeye Genel Bakış
Bu konu, genel bir bakış sağlar. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] görsel katman. Rolü üzerinde odaklanır <xref:System.Windows.Media.Visual> desteği işlemeye sınıfı [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] modeli.  
  
  
<a name="role_of_visual_object"></a>   
## <a name="role-of-the-visual-object"></a>Görsel nesnenin rolü  
 <xref:System.Windows.Media.Visual> Sınıf içinden temel soyutlama, her <xref:System.Windows.FrameworkElement> nesne türetilir. Ayrıca yeni denetimler yazmakla için giriş noktası olarak hizmet [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ve birçok yolla, Win32 uygulama modeli pencere tutucu (HWND) olarak düşünülebilir.  
  
 <xref:System.Windows.Media.Visual> Nesnedir çekirdek [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] olan birincil rolü, işleme desteği sağlamak için nesne. Kullanıcı arabirimi denetimleri, gibi <xref:System.Windows.Controls.Button> ve <xref:System.Windows.Controls.TextBox>, türetilen <xref:System.Windows.Media.Visual> sınıfı ve bunların işleme verileri kalıcı hale getirmeniz için kullanın. <xref:System.Windows.Media.Visual> Nesnesi için destek sağlar:  
  
-   Çıkış ekranı: Görselin çizim içeriğini kalıcı olarak işleme seri hale getirilmiş.  
  
-   Dönüştürme seçenekleri: Bir görselde dönüşümleri gerçekleştirme.  
  
-   Kırpma: Kırpma bölgesini desteği için bir görsel sağlama.  
  
-   Tıklama testi: Bir görsel sınırları içinde bir koordinat veya geometri bulunup bulunmadığını belirleyin.  
  
-   Sınırlama kutusu hesaplama: Bir görsel sınırlayıcı dikdörtgenini belirleme.  
  
 Ancak, <xref:System.Windows.Media.Visual> nesne olmayan işleme özellikleri için destek gibi içermez:  
  
-   Olay işleme  
  
-   Düzen  
  
-   Stilleri  
  
-   Veri bağlama  
  
-   Genelleştirme  
  
 <xref:System.Windows.Media.Visual> alt sınıfların türetilmesi gerekir ortak soyut bir sınıf kullanıma sunulur. Aşağıda sunulan görsel nesneler hiyerarşisini gösterir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 ![Görsel nesneden türetilen sınıf diyagramı](./media/wpf-graphics-rendering-overview/classes-derived-visual-object.png)    
  
### <a name="drawingvisual-class"></a>DrawingVisual sınıfı  
 <xref:System.Windows.Media.DrawingVisual> Olan şekil, görüntü veya metin işlemek için kullanılan sınıf çizim basit. Bu sınıf, çalışma zamanı performansını artırır, düzen veya olay işleme sağlamadığı basit olarak değerlendirilir. Bu nedenle, çizimleri, arka plan ve küçük resim için idealdir. <xref:System.Windows.Media.DrawingVisual> Özel görsel bir nesne oluşturmak için kullanılabilir. Daha fazla bilgi için [DrawingVisual nesnelerini kullanma](using-drawingvisual-objects.md).  
  
### <a name="viewport3dvisual-class"></a>Viewport3DVisual sınıfı  
 <xref:System.Windows.Media.Media3D.Viewport3DVisual> 2B arasında bir köprü sağlar <xref:System.Windows.Media.Visual> ve <xref:System.Windows.Media.Media3D.Visual3D> nesneleri. <xref:System.Windows.Media.Media3D.Visual3D> 3B tüm görsel öğeleri için temel sınıfı. <xref:System.Windows.Media.Media3D.Viewport3DVisual> Tanımladığınız gerektiren bir <xref:System.Windows.Media.Media3D.Viewport3DVisual.Camera%2A> değeri ve <xref:System.Windows.Media.Media3D.Viewport3DVisual.Viewport%2A> değeri. Kamerayı sahnenin görüntülemenize olanak sağlar. Görünüm penceresinin nerede projeksiyon 2B yüzeyine eşler oluşturur. 3D hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], bkz: [3B Grafiklere Genel Bakış](3-d-graphics-overview.md).  
  
### <a name="containervisual-class"></a>ContainerVisual sınıfı  
 <xref:System.Windows.Media.ContainerVisual> Sınıfı koleksiyonu için bir kapsayıcı kullanılan <xref:System.Windows.Media.Visual> nesneleri. <xref:System.Windows.Media.DrawingVisual> Sınıf türetilir <xref:System.Windows.Media.ContainerVisual> görsel nesneler koleksiyonunu içeren izin veren sınıf.  
  
### <a name="drawing-content-in-visual-objects"></a>Çizim içeriği görsel nesneler  
 A <xref:System.Windows.Media.Visual> nesnesi olarak işleme verilerini depolayan bir **vektör grafikleri yönerge listesi**. Yönerge listedeki her öğe bir alt düzey grafik veri kümesini ve ilişkili kaynakları serileştirilmiş biçiminde temsil eder. Dört farklı çizim içeriği içerebilir işleme veri türleri vardır.  
  
|Çizim içerik türü|Açıklama|  
|--------------------------|-----------------|  
|Vektör grafikleri|Temsil vektör grafik veri ve varsa ilişkili <xref:System.Windows.Media.Brush> ve <xref:System.Windows.Media.Pen> bilgileri.|  
|Görüntü|Görüntü tarafından tanımlanan bir bölge içinde temsil eden bir <xref:System.Windows.Rect>.|  
|Glif|İşleyen çizim temsil eden bir <xref:System.Windows.Media.GlyphRun>, belirtilen yazı tipi kaynak karakter dizisi olduğu. Metin nasıl temsil edildiğini budur.|  
|Video|Video işleyen çizim temsil eder.|  
  
 <xref:System.Windows.Media.DrawingContext> Doldurmak sağlar bir <xref:System.Windows.Media.Visual> görsel içeriğe sahip. Kullandığınızda, bir <xref:System.Windows.Media.DrawingContext> nesnenin çizim komutlar, gerçekten depoladığınız daha sonra grafik sistem tarafından kullanılacak işleme veri kümesi; gerçek zamanlı ekranda çizim değil.  
  
 Oluştururken bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimi gibi bir <xref:System.Windows.Controls.Button>, Denetim dolaylı olarak kendisini çizmek için veri işleme oluşturur. Örneğin, ayarlamak <xref:System.Windows.Controls.ContentControl.Content%2A> özelliği <xref:System.Windows.Controls.Button> glif işleme gösterimini depolamak denetim neden olur.  
  
 A <xref:System.Windows.Media.Visual> içeriğine bir veya daha fazla olarak açıklayan <xref:System.Windows.Media.Drawing> içinde yer alan nesneler bir <xref:System.Windows.Media.DrawingGroup>. A <xref:System.Windows.Media.DrawingGroup> opaklık maskeleri, dönüşüm, bit eşlem efektleri ve içeriğine uygulanan diğer işlemleri de anlatılmaktadır. <xref:System.Windows.Media.DrawingGroup> işlem, şu sırayla uygulanır, içerik işlendiğinde: <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>, <xref:System.Windows.Media.DrawingGroup.Opacity%2A>, <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>, <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>, <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>, ardından <xref:System.Windows.Media.DrawingGroup.Transform%2A>.  
  
 Aşağıdaki çizim sırayı gösterir <xref:System.Windows.Media.DrawingGroup> işlemleri sırasında işleme sırası uygulanır.  
  
 ![DrawingGroup işlem sırası](./media/graphcismm-drawinggroup-order.png "graphcismm_drawinggroup_order")  
DrawingGroup işlemlerin sırası  
  
 Daha fazla bilgi için [çizim nesnelerine genel bakış](drawing-objects-overview.md).  
  
#### <a name="drawing-content-at-the-visual-layer"></a>Görsel katman çizim içeriği  
 Hiçbir zaman doğrudan örneği bir <xref:System.Windows.Media.DrawingContext>; belirli yöntemlerini çizim bağlamı gibi ancak elde edebilir <xref:System.Windows.Media.DrawingGroup.Open%2A?displayProperty=nameWithType> ve <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A?displayProperty=nameWithType>. Aşağıdaki örnek alır bir <xref:System.Windows.Media.DrawingContext> gelen bir <xref:System.Windows.Media.DrawingVisual> ve bir dikdörtgen çizmek için kullanır.  
  
 [!code-csharp[drawingvisualsample#101](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#101)]
 [!code-vb[drawingvisualsample#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#101)]  
  
#### <a name="enumerating-drawing-content-at-the-visual-layer"></a>Görsel katman çizim içeriğini numaralandırma  
 Diğer kullanımları, ek olarak <xref:System.Windows.Media.Drawing> nesneleri ayrıca içeriğini numaralandırma için nesne modeli sağlar bir <xref:System.Windows.Media.Visual>.  
  
> [!NOTE]
>  Görselin içeriklerini sıralanırken alınırken <xref:System.Windows.Media.Drawing> nesneleri ve vektör grafik yönerge listesi olarak işleme verileri temel alınan gösterimini değil.  
  
 Aşağıdaki örnekte <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> alınacak yöntemi <xref:System.Windows.Media.DrawingGroup> değerini bir <xref:System.Windows.Media.Visual> ve onu numaralandırır.  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
<a name="how_visual_objects_are_used_to_build_controls"></a>   
## <a name="how-visual-objects-are-used-to-build-controls"></a>Görsel nesneler denetimleri oluşturmak için nasıl kullanılır  
 ' Daki nesnelerin pek çok [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] alt nesnelerin farklı Hiyerarşiler bulunabilir, yani visual diğer nesnelerin oluşurlar. Birçok kullanıcı arabirimi öğelerinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], denetimleri gibi farklı türde öğe işleme temsil eden birden çok görsel nesneler oluşurlar. Örneğin, <xref:System.Windows.Controls.Button> denetimi gibi diğer nesneler, bir dizi içerebilir <xref:Microsoft.Windows.Themes.ClassicBorderDecorator>, <xref:System.Windows.Controls.ContentPresenter>, ve <xref:System.Windows.Controls.TextBlock>.  
  
 Aşağıdaki kodda gösterildiği bir <xref:System.Windows.Controls.Button> biçimlendirme içinde tanımlanan denetimi.  
  
 [!code-xaml[VisualsOverview#VisualsOverviewSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml#visualsoverviewsnippet1)]  
  
 Varsayılan kapsayan görsel nesneler listeleme olsaydı <xref:System.Windows.Controls.Button> denetimi, aşağıda gösterilen görsel nesneler hiyerarşi bulma:  
  
 ![Görsel ağacı hiyerarşi diyagramı](./media/wpf-graphics-rendering-overview/visual-object-diagram.gif) 
  
 <xref:System.Windows.Controls.Button> Denetimi içeren bir <xref:Microsoft.Windows.Themes.ClassicBorderDecorator> sırayla içeren öğe bir <xref:System.Windows.Controls.ContentPresenter> öğesi. <xref:Microsoft.Windows.Themes.ClassicBorderDecorator> Öğedir kenarlık ve arka plan bilgileri için çizmek için sorumlu <xref:System.Windows.Controls.Button>. <xref:System.Windows.Controls.ContentPresenter> Öğedir içeriğini görüntülemek için sorumlu <xref:System.Windows.Controls.Button>. Bu durumda, beri görüntüleme metni <xref:System.Windows.Controls.ContentPresenter> öğesi içeren bir <xref:System.Windows.Controls.TextBlock> öğesi. Olgu, <xref:System.Windows.Controls.Button> denetimi kullanan bir <xref:System.Windows.Controls.ContentPresenter> içeriği gibi diğer öğeleri tarafından gösterilebilir anlamına gelir bir <xref:System.Windows.Controls.Image> veya geometri gibi bir <xref:System.Windows.Media.EllipseGeometry>.  
  
### <a name="control-templates"></a>Denetim şablonları  
 Bir denetimin genişletme denetimlerin bir hiyerarşiye anahtar <xref:System.Windows.Controls.ControlTemplate>. Varsayılan visual hiyerarşi bir denetim için bir denetim şablonu belirtir. Bir denetim açıkça başvuruda bulunduğunuzda visual hiyerarşi dolaylı başvuru. Bir denetim için özelleştirilmiş bir görünümünü oluşturmak bir denetim şablonu için varsayılan değerleri geçersiz kılabilir. Örneğin, arka plan rengi değerini değiştirebilir <xref:System.Windows.Controls.Button> böylece bir doğrusal gradyan renk değeri yerine düz renk değeri kullanır. Daha fazla bilgi için [düğme stilleri ve şablonları](../controls/button-styles-and-templates.md).  
  
 Bir kullanıcı arabirimi öğesi gibi bir <xref:System.Windows.Controls.Button> denetiminde, bir denetimin tüm işleme tanımını açıklayan çeşitli vektör grafik yönerge listeleri içerir. Aşağıdaki kodda gösterildiği bir <xref:System.Windows.Controls.Button> biçimlendirme içinde tanımlanan denetimi.  
  
 [!code-xaml[VisualsOverview#VisualsOverviewSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml#visualsoverviewsnippet2)]  
  
 Görsel nesneler sıralaması ve vektör grafik yönerge oluşturan bir listesi için olsaydı <xref:System.Windows.Controls.Button> denetimi, aşağıda gösterilen nesne hiyerarşisini bulun:  
  
 ![Görsel ağacı ve verileri işleme diyagramı](./media/wpf-graphics-rendering-overview/visual-tree-rendering-data.png)  
  
 <xref:System.Windows.Controls.Button> Denetimi içeren bir <xref:Microsoft.Windows.Themes.ClassicBorderDecorator> sırayla içeren öğe bir <xref:System.Windows.Controls.ContentPresenter> öğesi. <xref:Microsoft.Windows.Themes.ClassicBorderDecorator> Öğedir kenarlık ve arka plan düğmesinin oluşturan tüm ayrık grafik öğelerini çizmek için sorumlu. <xref:System.Windows.Controls.ContentPresenter> Öğedir içeriğini görüntülemek için sorumlu <xref:System.Windows.Controls.Button>. Bu durumda, beri görüntüleyen bir görüntü <xref:System.Windows.Controls.ContentPresenter> öğesi içeren bir <xref:System.Windows.Controls.Image> öğesi.  
  
 Görsel nesneler ve vektör grafik yönerge listeleri hiyerarşi hakkında dikkat edilecek noktaları vardır:  
  
-   Hiyerarşide sıralama, işleme sırası çizim bilgileri temsil eder. Kök visual öğeden sağa, yukarıdan aşağıya sol alt öğeleri geçirilir. Bir öğenin görsel alt öğe varsa, bunlar önce öğenin eşdüzey geçirilir.  
  
-   Yaprak olmayan düğüm öğeleri hiyerarşisinde gibi <xref:System.Windows.Controls.ContentPresenter>, alt öğeleri içerecek şekilde kullanılır — yönerge listeleri içermez.  
  
-   Bir görsel öğe hem bir vektör grafik yönerge listesi hem de visual alt öğeler içeriyorsa, üst görsel öğe yönerge listede herhangi bir görsel alt nesnelerin çizimler önce işlenir.  
  
-   Vektör grafikleri yönerge listesi öğeleri soldan sağa doğru işlenir.  
  
<a name="visual_tree"></a>   
## <a name="visual-tree"></a>Görsel ağaç  
 Görsel ağacı, bir uygulamanın kullanıcı arabiriminde kullanılan tüm görsel öğeleri içerir. Bir görsel öğe kalıcı çizim bilgileri içerdiğinden, görsel ağacını görüntü cihazı çıktı oluşturmak için gereken tüm işleme bilgileri içeren bir Sahne grafiği düşünebilirsiniz. Olmadığını kodda veya biçimlendirmede doğrudan uygulama tarafından oluşturulan tüm görsel öğeleri birikmesi ağacıdır. Görsel ağaç denetimleri ve veri nesneleri gibi öğelerin şablon genişletmesi tarafından oluşturulan tüm görsel öğeleri de içerir.  
  
 Aşağıdaki kodda gösterildiği bir <xref:System.Windows.Controls.StackPanel> biçimlendirme içinde tanımlanan öğe.  
  
 [!code-xaml[VisualsOverview#VisualsOverviewSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml#visualsoverviewsnippet3)]  
  
 Kapsayan görsel nesneler listeleme olsaydı <xref:System.Windows.Controls.StackPanel> öğesi işaretleme örnekte aşağıda gösterilen görsel nesneler hiyerarşi bulma:  
  
 ![Görsel ağacı hiyerarşi diyagramı](./media/wpf-graphics-rendering-overview/visual-tree-hierarchy.gif)  
  
### <a name="rendering-order"></a>Sipariş işleme  
 Görsel ağacı işleme sırasını belirleyen [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] görsel ve çizim nesneleri. Görsel en üstteki düğümü görsel ağaç kök sırası geçişi başlar. Kök görselin alt ardından, sağdan sola geçirilir. Bir görsel alt öğeleri varsa, alt önce görselin eşdüzey geçirilir. Başka bir deyişle, görsel bir alt içeriğin önünde görselin kendi içerik işlenir.  
  
 ![Görsel ağaç işleme düzeni diyagramı](./media/wpf-graphics-rendering-overview/visual-tree-rendering-order.gif) 
  
### <a name="root-visual"></a>Kök Visual  
 **Kök visual** bir görsel ağacı hiyerarşideki en üst öğedir. Kök visual temel sınıfını çoğu uygulamada geçerli <xref:System.Windows.Window> veya <xref:System.Windows.Navigation.NavigationWindow>. Win32 uygulamasında görsel nesneler barındırma, ancak visual kök Win32 penceresinde barındırma en üstteki görsel olacaktır. Daha fazla bilgi için [Öğreticisi: Win32 uygulamasında görsel nesneler barındırma](tutorial-hosting-visual-objects-in-a-win32-application.md).  
  
### <a name="relationship-to-the-logical-tree"></a>Mantıksal ağacı ilişki  
 Mantıksal ağaçta [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir uygulamanın çalışma zamanında öğelerini temsil eder. Bu ağaç doğrudan değiştiremez ancak uygulama bu görünümü özelliği devralma ve olay yönlendirme anlamak için kullanışlıdır. Görsel ağacı mantıksal ağaç görsel olmayan veri nesneleri gibi temsil edebilen <xref:System.Windows.Documents.ListItem>. Çoğu durumda, mantıksal ağacı çok yakın bir uygulamanın biçimlendirme tanımları eşler. Aşağıdaki kodda gösterildiği bir <xref:System.Windows.Controls.DockPanel> biçimlendirme içinde tanımlanan öğe.  
  
 [!code-xaml[VisualsOverview#VisualsOverviewSnippet5](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml#visualsoverviewsnippet5)]  
  
 Oluşturan mantıksal nesnelerini listeleme olsaydı <xref:System.Windows.Controls.DockPanel> öğesi işaretleme örnekte, aşağıda gösterilen mantıksal nesne hiyerarşisini bulma:  
  
 ![Ağaç görünümünü](./media/tree1-wcp.gif "Tree1_wcp")  
Mantıksal ağaç diyagramı  
  
 Görsel ağacı ve mantıksal ağaç herhangi eklenmesi, silinmesi veya değiştirilmesi öğelerin yansıtan uygulama öğelerin geçerli kümesi ile eşitlenir. Ancak, uygulamanın farklı görünümleri ağaçları sunar. Görsel ağacı, bir denetimin mantıksal ağaç genişletmeyen <xref:System.Windows.Controls.ContentPresenter> öğesi. Bu, bir mantıksal ağaç ve aynı nesne kümesini görsel ağacını arasında doğrudan bir bire yok anlamına gelir. Aslında, çağırma **LogicalTreeHelper** nesnenin <xref:System.Windows.LogicalTreeHelper.GetChildren%2A> yöntemi ve **VisualTreeHelper** nesnenin <xref:System.Windows.Media.VisualTreeHelper.GetChild%2A> parametre farklı sonuçlar verir gibi aynı öğeye kullanarak yöntemi .  
  
 Mantıksal ağacı hakkında daha fazla bilgi için bkz. [WPF içinde ağaçlar](../advanced/trees-in-wpf.md).  
  
### <a name="viewing-the-visual-tree-with-xamlpad"></a>Görsel ağacı XamlPad ile görüntüleme  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Aracı XamlPad, görüntüleme ve karşılık gelen görsel ağacı şu anda tanımlı için keşfetmek için bir seçenek sağlar [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] içeriği. Tıklayın **görsel ağacını Göster** görsel ağacı görüntülemek için menü çubuğunda düğme. Aşağıdaki genişletilmiş hali gösterilmiştir [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] görsel ağaç düğümleri içine içerik **görsel ağacı Gezgini** XamlPad panelini:  
  
 ![Görsel ağacı Gezgini panelinde XamlPad](./media/wpf-graphics-rendering-overview/visual-tree-explorer.png)  

 Bildirim nasıl <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.TextBox>, ve <xref:System.Windows.Controls.Button> denetimlerini her bir ayrı görsel nesne hiyerarşisinde görüntülemek **görsel ağacı Gezgini** XamlPad panelini. Bunun nedeni, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetiminiz bir <xref:System.Windows.Controls.ControlTemplate> , denetimin görsel ağacını içerir. Bir denetim açıkça başvuruda bulunduğunuzda visual hiyerarşi dolaylı başvuru.  
  
### <a name="profiling-visual-performance"></a>Görsel performans profili oluşturma  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Performans profili oluşturma, uygulamanızın çalışma zamanı davranışını çözümlemenize ve türde uygulayabilirsiniz performans iyileştirmelerini belirlemenize olanak tanıyan araçlar sağlar. Görsel Profiler aracı ile eşleştirerek doğrudan uygulamanın görsel ağaç performans verileri zengin, grafik bir görünümünü sağlar. Bu ekran görüntüsünde **CPU kullanımı** Visual Profiler bölümünü kesin bir nesnenin kullanımı dökümünü verir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] işleme ve düzen gibi hizmetler.  
  
 ![Görsel Profiler görüntüleme çıkış](./media/wpfperf-visualprofiler-04.png "WPFPerf_VisualProfiler_04")  
Görsel Profiler görüntüsü çıkışı  
  
<a name="visual_rendering_behavior"></a>   
## <a name="visual-rendering-behavior"></a>Visual işlemesi davranışı  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] görsel nesneler işleme davranışını etkileyen çeşitli özellikler sunar: modu grafikleri, vektör grafikleri ve cihaz bağımsız grafik korunur.  
  
### <a name="retained-mode-graphics"></a>Tutulan modu grafikleri  
 Görsel nesnenin rolünü anlamak için anahtarların biridir arasındaki farkı anlamak için **anlık mod** ve **modu korunur** grafik sistemleri. GDI veya GDI +'da temel, standart bir Win32 uygulaması, bir anlık mod grafik sistemi kullanır. Uygulamanın yeniden çizerken yeniden boyutlandırılmakta olan bir pencere gibi bir eylem nedeniyle geçersiz istemci alanını bölümü için sorumlu olduğu anlamına gelir veya nesnenin görsel görünümünü değiştirme.  
  
 ![Win32 işleme sıralı diyagramı](./media/wpf-graphics-rendering-overview/win32-rendering-squence.png)  
  
 Buna karşılık, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] saklama modu sistemi kullanır. Başka bir deyişle, görsel görünümüne sahip uygulama nesneleri seri hale getirilmiş çizim veri kümesi tanımlarsınız. Çizim veri ile tanımlandıktan sonra sistemin bundan sonra uygulama nesneleri işleme için tüm yeniden çizmeyi isteklerine yanıt için sorumludur. Bile çalışma zamanında, değiştirme veya uygulama nesneleri oluşturmak ve istekleri boyama yanıtlama sistem hala dayanır. Tutulan modu grafik sistemindeki bilgi çizim her zaman serileştirilmiş bir durumda uygulama, ancak sisteme sol işleme sorumluluk kalıcı olmasını güçtür. Aşağıdaki diyagramda uygulama dayanan nasıl gösterir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] boyamak için istekleri yanıtlamak için.  
  
 ![WPF işleme sıralı diyagramı](./media/wpf-graphics-rendering-overview/wpf-rendering-sequence.png)  

#### <a name="intelligent-redrawing"></a>Akıllı yeniden  
 Tutulan modu grafikleri kullanarak en büyük avantajlarından biri olan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] verimli bir şekilde uygulamada çizilmesini için gerekenler en iyi duruma getirebilirsiniz. Farklı düzeylerde opaklık ile karmaşık Sahne olsa bile, genellikle yeniden en iyi duruma getirmek için özel amaçlı kod yazma gerekmez. Bu, büyük ölçüde çaba güncelleştirme bölgede yeniden miktarını en aza indirerek, uygulamanızın en iyi duruma getirme, harcama Win32 programlama ile karşılaştırın. Bkz: [güncelleştirme bölgede yeniden](/windows/desktop/gdi/redrawing-in-the-update-region) karmaşıklık türünün bir örneği için söz konusu Win32 uygulamaları yeniden iyileştirme içinde.  
  
### <a name="vector-graphics"></a>Vektör grafikleri  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kullanan **vektör grafikleri** olarak işleme veri biçimi. Vektör grafikleri — ölçeklenebilir vektör grafiği (SVG) ve Windows Meta dosyası (.wmf) TrueType yazı tiplerini içerir — işleme verileri depolamak ve grafik temelleri kullanarak görüntü yeniden oluşturmak nasıl açıklayan yönergeler listesi olarak aktarabilir. Örneğin, çizgiler, eğriler ve komutları bir dizi yerine bir dizi piksel açıklayan anahat yazı tipleri TrueType yazı tiplerini yararlanabilirsiniz. Vektör grafikleri başlıca avantajlarından herhangi bir boyuttaki ve çözümleme ölçeklendirme olanağı biridir.  
  
 Vektör grafikleri, bit eşlem grafik, belirli bir çözümleme için önceden işlenmiş görüntü, piksel piksel temsili olarak işleme verileri depolar. Bit eşlem ve vektör grafik biçimleri arasındaki önemli farklılıkları uygunluk için orijinal kaynak görüntü biridir. Örneğin, bir kaynak görüntüsünün boyutu değiştirildiğinde görüntü kalitesini koruyarak görüntü, vektör grafik sistemleri ölçeklendirme ise görüntü bit eşlem grafik sistemleri esnetin.  
  
 Aşağıdaki çizim, %300 tarafından yeniden boyutlandırılmış bir kaynak görüntüyü gösterir. Kaynak görüntü bit eşlem grafik görüntüsüne esnetilmiş yerine, bir vektör grafik resmi olarak Ölçeklendirildi görüntülenen deformasyonları dikkat edin.  
  
 ![Izgara ve vektör grafik arasındaki farklar](./media/wpf-graphics-rendering-overview/raster-vector-differences.png)  
  
 Aşağıdaki biçimlendirmede iki gösterir <xref:System.Windows.Shapes.Path> tanımlanan öğe. İkinci öğe kullanan bir <xref:System.Windows.Media.ScaleTransform> ilk öğenin çizim yönergeleri %300 yeniden boyutlandırabilirsiniz. Dikkat çizim yönergeleri <xref:System.Windows.Shapes.Path> öğeleri değişmeden kalır.  
  
 [!code-xaml[VectorGraphicsSnippets#VectorGraphicsSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/VectorGraphicsSnippets/CS/PageOne.xaml#vectorgraphicssnippet1)]  
  
### <a name="about-resolution-and-device-independent-graphics"></a>Çözüm ve CİHAZDAN bağımsız grafikler hakkında  
 Metin ve grafikleri ekranınızdaki boyutunu belirleyen iki sistem faktör vardır: Çözüm ve DPI. Çözüm, ekranda görünen piksel sayısı açıklanır. Çözüm daha yüksek ettiği piksel grafikler ve daha küçük görüntülenecek metin neden küçük alın. Çözüm 1600 x 1200'e değiştirildiğinde 1024 x 768'olarak ayarlanmış bir monitörde gösterilen grafik çok daha küçük görünür.  
  
 Diğer sistem ayarı, DPI bir ekran inç piksel cinsinden boyutu açıklar. Çoğu [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] sistemleri, yani bir ekran inç 96 piksel etkin DPI 96, sahiptir. DPI ayarı artan büyük ekran inç yapar; DPI azalan ekran inç küçültür. Başka bir deyişle, bir ekran inç gerçek inç aynı boyutta değil; Çoğu sistemde, büyük olasılıkla değil. DPI arttıkça ekran inç boyutunu artırdık çünkü DPI kullanan grafikler ve metin daha büyük hale gelir. DPI artırma metin okuma, özellikle yüksek çözünürlüklerde daha kolay yapabilirsiniz.  
  
 Tüm uygulamalar DPI kullanan uygulamalardır: bazı donanım piksel ölçü; birincil birimi olarak kullanın DPI sistemini değiştirmek bu uygulamalar üzerinde etkisi yoktur. Diğer birçok uygulama DPI kullanan birimleri, yazı tipi boyutlarını açıklamaktadır, ancak diğer her şey açıklamak için piksel kullanmak için kullanın. DPI değeri çok küçük veya çok büyük yapma sistemin DPI ayarı ile uygulamalarınızın metin ölçeklendirir ancak uygulamalarınızın kullanıcı Arabirimi yoktur çünkü bu uygulamalar için Düzen sorunlara neden olabilir. Bu sorunun kullanılarak geliştirilen uygulamalar için ortadan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Ölçüm, donanım piksel yerine birincil biriminin cihaz bağımsız piksel kullanarak otomatik ölçeklendirmeyi destekler. grafikler ve metin uygulama geliştiriciden herhangi bir ek çalışma yapmadan düzgün bir şekilde ölçeklendirin. İlişkin bir örnek aşağıda gösterilmiştir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] metin ve grafikleri farklı DPI ayarları görünür olan.  
  
 ![Grafikler ve metin farklı DPI ayarlarıyla](./media/graphicsmm-dpi-setting-examples.png "graphicsmm_dpi_setting_examples")  
Grafikler ve farklı DPI ayarlarıyla metin  
  
<a name="visualtreehelper_class"></a>   
## <a name="visualtreehelper-class"></a>VisualTreeHelper sınıfı  
 <xref:System.Windows.Media.VisualTreeHelper> Yüksek performanslı özel denetimleri geliştirme gibi belirli senaryolarda yararlıdır visual nesne düzeyinde programlama için alt düzey işlevsellik sağlayan bir statik yardımcı sınıfı. Çoğu durumda, üst düzey [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] gibi framework nesneleri <xref:System.Windows.Controls.Canvas> ve <xref:System.Windows.Controls.TextBlock>, esneklik ve kullanım kolaylığı sunar.  
  
### <a name="hit-testing"></a>Tıklama testi  
 <xref:System.Windows.Media.VisualTreeHelper> Sınıfı isabet varsayılan test desteği ulaştığınızda görsel nesneler üzerine sınama gereksinimlerinizi karşılamıyor için yöntemler sağlar. Kullanabileceğiniz <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> yöntemleri <xref:System.Windows.Media.VisualTreeHelper> geometri veya nokta bir koordinat değeri bir denetim veya grafik öğesi gibi belirli bir nesnenin sınırları içinde olup olmadığını belirlemek için sınıf. Örneğin, isabet sınaması bir fare tıklaması bir nesnenin sınırlayıcı dikdörtgeni içinde geometrisini Ayrıca kendi özel isabet testi gerçekleştirmek için isabet testi varsayılan uygulama geçersiz kılmayı seçebilirsiniz bir daire içinde olup olmadığını belirlemek için kullanabilirsiniz hesaplamalar.  
  
 İsabet testi ile ilgili daha fazla bilgi için bkz: [isabet testi görsel katmandaki](hit-testing-in-the-visual-layer.md).  
  
### <a name="enumerating-the-visual-tree"></a>Görsel ağacı numaralandırma  
 <xref:System.Windows.Media.VisualTreeHelper> Sınıfı görsel ağacı üyelerini numaralandırma için işlevsellik sağlar. Bir üst almak için arama <xref:System.Windows.Media.VisualTreeHelper.GetParent%2A> yöntemi. Bir alt veya doğrudan alt öğesi, bir görsel nesneyi almak için arama <xref:System.Windows.Media.VisualTreeHelper.GetChild%2A> yöntemi. Bu yöntem bir alt öğesini döndürür <xref:System.Windows.Media.Visual> belirtilen dizindeki üst.  
  
 Aşağıdaki örnek, bir görsel nesneyi hiyerarşinin tüm işleme bilgileri getirmede ilgileniyorsanız kullanmak isteyebileceğiniz bir tekniktir bir görsel nesnesinin tüm öğelerini listeleme gösterilmiştir.  
  
 [!code-csharp[VisualsOverview#101](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml.cs#101)]
 [!code-vb[VisualsOverview#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsOverview/visualbasic/window1.xaml.vb#101)]  
  
 Çoğu durumda, mantıksal ağacı öğeleri daha kullanışlı bir temsilini olduğu bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama. Mantıksal ağacı doğrudan değiştirmeyin ancak bu görünüm uygulamanın özellik devralma ve olay yönlendirmeyi anlamak için kullanışlıdır. Görsel ağacı mantıksal ağaç görsel olmayan veri nesneleri gibi temsil edebilen <xref:System.Windows.Documents.ListItem>. Mantıksal ağacı hakkında daha fazla bilgi için bkz. [WPF içinde ağaçlar](../advanced/trees-in-wpf.md).  
  
 <xref:System.Windows.Media.VisualTreeHelper> Sınıfı görsel nesneler sınırlayıcı dikdörtgenini döndürmek için yöntemler sağlar. Görsel bir nesnenin sınırlayıcı dikdörtgenini çağırarak döndürebilir <xref:System.Windows.Media.VisualTreeHelper.GetContentBounds%2A>. Görsel nesnenin kendisini çağırarak dahil olmak üzere, görsel bir nesne tüm alt öğeleri sınırlayıcı dikdörtgenini döndürebilir <xref:System.Windows.Media.VisualTreeHelper.GetDescendantBounds%2A>. Aşağıdaki kod nasıl görsel bir nesne ve tüm alt öğelerini sınırlayıcı dikdörtgenini hesaplar gösterir.  
  
 [!code-csharp[VisualsOverview#102](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml.cs#102)]
 [!code-vb[VisualsOverview#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsOverview/visualbasic/window1.xaml.vb#102)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Media.Visual>
- <xref:System.Windows.Media.VisualTreeHelper>
- <xref:System.Windows.Media.DrawingVisual>
- [2B Grafikleri ve Görüntüleme](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Görsel Katmanda Tıklama Testi](hit-testing-in-the-visual-layer.md)
- [DrawingVisual Nesnelerini Kullanma](using-drawingvisual-objects.md)
- [Öğretici: Win32 uygulamasında görsel nesneler barındırma](tutorial-hosting-visual-objects-in-a-win32-application.md)
- [WPF Uygulama Performansını İyileştirme](../advanced/optimizing-wpf-application-performance.md)
