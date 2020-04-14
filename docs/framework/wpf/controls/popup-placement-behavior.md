---
title: Açılan Pencere Yerleştirme Davranışı
ms.date: 03/30/2017
helpviewer_keywords:
- popups [WPF]
- Popup control [WPF], placing
- placing popups [WPF]
- positioning popups [WPF]
ms.assetid: fbf642e9-f670-4efd-a7af-a67468a1c8e1
ms.openlocfilehash: 1c377e62ffd334638031baee4d4831ac5a31acf3
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243264"
---
# <a name="popup-placement-behavior"></a>Açılan Pencere Yerleştirme Davranışı
Denetim, <xref:System.Windows.Controls.Primitives.Popup> içeriği bir uygulamanın üzerinde yüzen ayrı bir pencerede görüntüler. Bir denetime, fareye veya <xref:System.Windows.Controls.Primitives.Popup> ekrana göre bir görüşün <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>konumunu <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>, <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> , ve özelliklerini kullanarak belirtebilirsiniz.  Bu özellikler, <xref:System.Windows.Controls.Primitives.Popup>'nin konumunu belirtmede esneklik sağlamak için birlikte çalışır.  
  
> [!NOTE]
> Ve <xref:System.Windows.Controls.ToolTip> <xref:System.Windows.Controls.ContextMenu> sınıflar da bu beş özellikleri tanımlamak ve benzer şekilde.  

<a name="Positioning"></a>
## <a name="positioning-the-popup"></a>Açılır Pencereyi Konumlandırma  
 A'nın <xref:System.Windows.Controls.Primitives.Popup> yerleşimi bir <xref:System.Windows.UIElement> ekrana veya ekranın tamamına göreolabilir.  Aşağıdaki örnek, bir <xref:System.Windows.Controls.Primitives.Popup> <xref:System.Windows.UIElement>görüntüye göre dört denetim oluşturur. Tüm <xref:System.Windows.Controls.Primitives.Popup> denetimler <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> özelliği ayarlanmış, `image1`ancak <xref:System.Windows.Controls.Primitives.Popup> her yerleşim özelliği için farklı bir değere sahiptir.  
  
 [!code-xaml[PopupPositionSnippet#3](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#3)]  
  
 Aşağıdaki resimde görüntü ve <xref:System.Windows.Controls.Primitives.Popup> denetimler  
  
 ![Dört açılır pencere denetimi olan görüntü](./media/popup-placement-behavior/popup-placement-intro.png "Dört açılır pencereli görüntü")
  
 Bu basit örnek, özelliklerin <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> ve özelliklerin nasıl <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>ayarlanacağını gösterir, ancak , , ve <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> özellikleri kullanarak, konumlandırılmış nerede <xref:System.Windows.Controls.Primitives.Popup> üzerinde daha fazla denetime sahip.  
  
<a name="Definitions"></a>
## <a name="definitions-of-terms-the-anatomy-of-a-popup"></a>Terimlerin Tanımları: Bir Popup'un Anatomisi  
 Aşağıdaki <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>terimler, , , , <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>, ve <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> özellikleri nin birbiriyle <xref:System.Windows.Controls.Primitives.Popup>nasıl ilişkili olduğunu ve aşağıdakileri anlamada yararlıdır:  
  
- Hedef nesne  
  
- Hedef alan  
  
- Hedef kökeni  
  
- Pop-up hizalama noktası  
  
 Bu koşullar, ilişkili olduğu denetimin çeşitli <xref:System.Windows.Controls.Primitives.Popup> yönlerine başvurmak için uygun bir yol sağlar.  
  
### <a name="target-object"></a>Hedef Nesne  
 *Hedef nesne,* ilişkili <xref:System.Windows.Controls.Primitives.Popup> öğedir. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> Özellik ayarlanmışsa, hedef nesneyi belirtir.  <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> Ayarlanmaz ve üst <xref:System.Windows.Controls.Primitives.Popup> öğesi varsa, üst öğe hedef nesnedir.  Değer yoksa <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> ve üst öğe yoksa, hedef nesne <xref:System.Windows.Controls.Primitives.Popup> yoktur ve ekrana göre konumlandırılır.  
  
 Aşağıdaki örnek, bir <xref:System.Windows.Controls.Primitives.Popup> <xref:System.Windows.Controls.Canvas>.  Örnek, <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> özelliği <xref:System.Windows.Controls.Primitives.Popup>. Varsayılan <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> değer, <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom?displayProperty=nameWithType>bu nedenle <xref:System.Windows.Controls.Primitives.Popup> <xref:System.Windows.Controls.Canvas>altında görünür.  
  
 [!code-xaml[PopupPositionSnippet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#1)]  
  
 Aşağıdaki resimde, <xref:System.Windows.Controls.Primitives.Popup> <xref:System.Windows.Controls.Canvas>'ye göre konumlandırılmış olduğunu gösteren.  
  
 ![PlacementTarget olmadan pop-up kontrolü](./media/popup-placement-behavior/popup-placement-no-placement-target.png "PlacementTarget olmadan açılır pencere.")  

 Aşağıdaki örnek, bir <xref:System.Windows.Controls.Primitives.Popup> <xref:System.Windows.Controls.Canvas>çocuğun , ancak bu kez <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> ayarlanır `ellipse1`, böylece pop-up aşağıda <xref:System.Windows.Shapes.Ellipse>görünür bir oluşturur .  
  
 [!code-xaml[PopupPositionSnippet#2](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#2)]  
  
 Aşağıdaki resimde, <xref:System.Windows.Controls.Primitives.Popup> <xref:System.Windows.Shapes.Ellipse>'ye göre konumlandırılmış olduğunu gösteren.  
  
 ![Bir elipse göre konumlandırılmış açılır pencere](./media/popup-placement-behavior/popup-placement-with-placement-target.png "PlacementTarget ile açılır pencere")
  
> [!NOTE]
> Çünkü, <xref:System.Windows.Controls.ToolTip>varsayılan <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>değeri.  Çünkü, <xref:System.Windows.Controls.ContextMenu>varsayılan <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>değeri. Bu değerler daha sonra "Özellikler Birlikte Nasıl Çalışır" adlı nda açıklanır.  
  
### <a name="target-area"></a>Hedef Alan  
 *Hedef alan,* ekrandaki alanın göreli <xref:System.Windows.Controls.Primitives.Popup> olduğu alandır. Önceki örneklerde, <xref:System.Windows.Controls.Primitives.Popup> hedef nesnenin sınırları ile hizalanır, ancak bazı durumlarda, hedef nesne <xref:System.Windows.Controls.Primitives.Popup> <xref:System.Windows.Controls.Primitives.Popup> olsa bile, diğer sınırlara hizalanır.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Özellik ayarlanırsa, hedef alan hedef nesnenin sınırlarından farklıdır.  
  
 Aşağıdaki örnek, her <xref:System.Windows.Controls.Canvas> biri a ve <xref:System.Windows.Shapes.Rectangle> a <xref:System.Windows.Controls.Primitives.Popup>içeren iki nesne oluşturur.  Her iki durumda da, <xref:System.Windows.Controls.Primitives.Popup> hedef <xref:System.Windows.Controls.Canvas>nesne. İlk <xref:System.Windows.Controls.Primitives.Popup> <xref:System.Windows.Controls.Canvas> <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> olarak, onun <xref:System.Windows.Rect.X%2A>, , <xref:System.Windows.Rect.Y%2A> <xref:System.Windows.Rect.Width%2A>ve <xref:System.Windows.Rect.Height%2A> özellikleri 50, 50, 50, 50 ve 100, sırasıyla ayarlanmış olan kümesi vardır. İkinci <xref:System.Windows.Controls.Primitives.Popup> <xref:System.Windows.Controls.Canvas> de <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> set yok.  Sonuç olarak, ilk <xref:System.Windows.Controls.Primitives.Popup> altında konumlandırılmış <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> ve <xref:System.Windows.Controls.Primitives.Popup> ikinci altında konumlandırılmış <xref:System.Windows.Controls.Canvas>. Her <xref:System.Windows.Controls.Canvas> biri <xref:System.Windows.Shapes.Rectangle> de ilk <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> <xref:System.Windows.Controls.Primitives.Popup>için aynı sınırlara sahip bir içerir.  Uygulamada görünür <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> bir öğe oluşturmadığını unutmayın; örnek te temsil <xref:System.Windows.Shapes.Rectangle> etmek <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>için bir oluşturur.  
  
 [!code-xaml[PopupPositionSnippet#4](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#4)]  
  
 Aşağıdaki resimde önceki örneğin sonucu gösterilmektedir.  
  
 ![PlacementRectangle ile ve Olmadan Pop-up](./media/popup-placement-behavior/popup-placement-placement-rectangle.png "PlacementRectangle ile ve olmadan popup.")  

### <a name="target-origin-and-popup-alignment-point"></a>Hedef Kökeni ve Popup Hizalama Noktası  
 *Hedef başlangıç* ve *açılır hizalama noktası,* sırasıyla konumlandırma için kullanılan hedef alan daki referans noktalarıdır ve açılır penceredir. Açılır pencereyi <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> hedef alandan dengelemek için ve özelliklerini kullanabilirsiniz.  Ve <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> hedef kökeni ve açılır hizalama noktasına göre. Özelliğin <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> değeri, hedef kaynağın ve açılır pencere hizalama noktasının nerede olduğunu belirler.  
  
 Aşağıdaki örnek a <xref:System.Windows.Controls.Primitives.Popup> oluşturur ve <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> 20 ve özellikleri ayarlar.  Özellik <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom> (varsayılan) olarak ayarlanır, bu nedenle hedef kaynağı hedef alanın sol alt köşesidir ve açılır pencere hizalama <xref:System.Windows.Controls.Primitives.Popup>noktası.  
  
 [!code-xaml[PopupPositionSnippet#5](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#5)]  
  
 Aşağıdaki resimde önceki örneğin sonucu gösterilmektedir.  
  
 ![Hedef başlangıç hizalama noktası olan açılır pencere yerleşimi](./media/popup-placement-behavior/popup-placement-target-origin-alignment-point.png "HorizontalOffset ve VerticalOffset ile popup.")
  
<a name="How"></a>
## <a name="how-the-properties-work-together"></a>Özellikler Birlikte Nasıl Çalışır?  
 Doğru hedef <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>alanı, <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> hedef kaynağı ve açılır hizalama noktasını anlamak için , ve birlikte düşünülmeli.  Örneğin, değeri <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>, hedef nesne yoksa, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> yoksayılır ve hedef alan fare işaretçisi sınırlarıdır. Diğer taraftan, ise <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>, <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> veya üst hedef nesne <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> belirler ve hedef alanı belirler.  
  
 Aşağıdaki tabloda hedef nesne, hedef alan, hedef kaynağı ve açılır <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> pencere hizalama <xref:System.Windows.Controls.Primitives.PlacementMode> noktası açıklanır ve her numaralandırma değeri için kullanılıp kullanılmadığını gösterir.  
  
|Yerleştirme Modu|Hedef nesne|Hedef alan|Hedef kökeni|Pop-up hizalama noktası|  
|-------------------|-------------------|-----------------|-------------------|---------------------------|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>|Geçerli değildir. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> yoksayılır.|Ekran veya <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> ayarlanmışsa.  Ekrana <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> göre.|Hedef alanın sol üst köşesi.|Sol üst <xref:System.Windows.Controls.Primitives.Popup>köşede.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>|Geçerli değildir. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> yoksayılır.|Ekran veya <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> ayarlanmışsa.  Ekrana <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> göre.|Hedef alanın sol üst köşesi.|Sol üst <xref:System.Windows.Controls.Primitives.Popup>köşede.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>veya ebeveyn.|Hedef nesne veya <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> ayarlanmışsa.  Hedef <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> nesneye göredir.|Hedef alanın sol alt köşesi.|Sol üst <xref:System.Windows.Controls.Primitives.Popup>köşede.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Center>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>veya ebeveyn.|Hedef nesne veya <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> ayarlanmışsa.  Hedef <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> nesneye göredir.|Hedef alanın merkezi.|<xref:System.Windows.Controls.Primitives.Popup>Merkezi.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>veya ebeveyn.|Hedef nesne veya <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> ayarlanmışsa.  Hedef <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> nesneye göredir.|Tarafından tanımlanan <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>.|Tarafından tanımlanan <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Left>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>veya ebeveyn.|Hedef nesne veya <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> ayarlanmışsa.  Hedef <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> nesneye göredir.|Hedef alanın sol üst köşesi.|Sağ üst <xref:System.Windows.Controls.Primitives.Popup>köşede.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>|Geçerli değildir. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> yoksayılır.|Fare işaretçisinin sınırları. <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> yoksayılır.|Hedef alanın sol alt köşesi.|Sol üst <xref:System.Windows.Controls.Primitives.Popup>köşede.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>|Geçerli değildir. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> yoksayılır.|Fare işaretçisinin sınırları. <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> yoksayılır.|Hedef alanın sol üst köşesi.|Sol üst <xref:System.Windows.Controls.Primitives.Popup>köşede.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>veya ebeveyn.|Hedef nesne veya <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> ayarlanmışsa.  Hedef <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> nesneye göredir.|Hedef alanın sol üst köşesi.|Sol üst <xref:System.Windows.Controls.Primitives.Popup>köşede.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>veya ebeveyn.|Hedef nesne veya <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> ayarlanmışsa.  Hedef <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> nesneye göredir.|Hedef alanın sol üst köşesi.|Sol üst <xref:System.Windows.Controls.Primitives.Popup>köşede.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Right>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>veya ebeveyn.|Hedef nesne veya <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> ayarlanmışsa.  Hedef <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> nesneye göredir.|Hedef alanın sağ üst köşesi.|Sol üst <xref:System.Windows.Controls.Primitives.Popup>köşede.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Top>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>veya ebeveyn.|Hedef nesne veya <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> ayarlanmışsa.  Hedef <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> nesneye göredir.|Hedef alanın sol üst köşesi.|Sol alt <xref:System.Windows.Controls.Primitives.Popup>köşede.|  
  
 Aşağıdaki çizimler, her <xref:System.Windows.Controls.Primitives.Popup> <xref:System.Windows.Controls.Primitives.PlacementMode> değer için hedef alanı, hedef kaynağı ve açılır pencere hizalama noktasını gösterir. Her şekilde, hedef alan sarı ve <xref:System.Windows.Controls.Primitives.Popup> mavidir.  
  
 ![Mutlak veya AbsolutePoint yerleşimli açılır pencere](./media/popup-placement-behavior/popup-placement-absolute.png "Yerleşim Mutlak veya AbsolutePoint'tir.")
  
 ![Alt yerleşimli açılır pencere](./media/popup-placement-behavior/popup-placement-bottom.png "Yerleştirme Alttır.")
  
 ![Merkezi yerleştirme ile açılır pencere](./media/popup-placement-behavior/popup-placement-center.png "Yerleştirme Merkezi'dir.")
  
 ![Sol yerleşimli açılır pencere](./media/popup-placement-behavior/popup-placement-left.png "Yerleştirme Sol.")
  
 ![Fare yerleşimli açılır pencere](./media/popup-placement-behavior/popup-placement-mouse.png "Yerleştirme Fare'dir.")  
  
 ![MousePoint yerleşimli açılır pencere](./media/popup-placement-behavior/popup-placement-mousepoint.png "Yerleşim MousePoint'tir.")  
  
 ![Bağıl veya RelativePoint yerleşimli açılır pencere](./media/popup-placement-behavior/popup-placement-relative.png "Yerleşim Göreceli veya RelativePoint'tir.")
  
 ![Doğru yerleşimli açılır pencere](./media/popup-placement-behavior/popup-placement-right.png "Yerleştirme Doğrudur.")
  
 ![Üst yerleştirmeile açılır pencere](./media/popup-placement-behavior/popup-placement-top.png "Yerleştirme Üst' tir.")
  
<a name="When"></a>
## <a name="when-the-popup-encounters-the-edge-of-the-screen"></a>Popup Ekranın Kenarıyla Karşılaştığında  
 Güvenlik nedenleriyle, <xref:System.Windows.Controls.Primitives.Popup> bir ekranın kenarına gizlenemez. Aşağıdaki üç şeyden biri bir <xref:System.Windows.Controls.Primitives.Popup> ekran kenarı karşılaştığında olur:  
  
- Açılır pencere, ekran kenarı boyunca kendini yeniden <xref:System.Windows.Controls.Primitives.Popup>hizalar ve bu da .  
  
- Açılır pencere farklı bir açılır pencere hizalama noktası kullanır.  
  
- Açılır pencere farklı bir hedef kaynağı ve açılır pencere hizalama noktası kullanır.  
  
 Bu seçenekler daha sonra bu bölümde açıklanmıştır.  
  
 Ekran kenarına <xref:System.Windows.Controls.Primitives.Popup> rastladığında ki davranışı <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> özelliğin değerine ve açılır pencerenin hangi ekran kenarına bağlıdır. Aşağıdaki tablo, her <xref:System.Windows.Controls.Primitives.Popup> <xref:System.Windows.Controls.Primitives.PlacementMode> değer için bir ekran kenarı karşılaştığında davranışı özetler.  
  
|Yerleştirme Modu|Üst kenar|Alt kenar|Sol kenar|Sağ kenar|  
|-------------------|--------------|-----------------|---------------|----------------|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>|Üst kenarına hizalar.|Alt kenarına hizalar.|Sol kenara hizalar.|Sağ kenarına hizalar.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>|Üst kenarına hizalar.|Açılır hizalama <xref:System.Windows.Controls.Primitives.Popup>noktası, 'nin sol alt köşesine değişir.|Sol kenara hizalar.|Açılır hizalama noktası, <xref:System.Windows.Controls.Primitives.Popup>listenin sağ üst köşesinde değişir.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>|Üst kenarına hizalar.|Hedef kaynağı hedef alanın sol üst köşesine değişir ve açılır hizalama <xref:System.Windows.Controls.Primitives.Popup>noktası.|Sol kenara hizalar.|Sağ kenarına hizalar.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Center>|Üst kenarına hizalar.|Alt kenarına hizalar.|Sol kenara hizalar.|Sağ kenarına hizalar.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Left>|Üst kenarına hizalar.|Alt kenarına hizalar.|Hedef kaynağı hedef alanın sağ üst köşesine değişir ve açılır hizalama <xref:System.Windows.Controls.Primitives.Popup>noktası.|Sağ kenarına hizalar.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>|Üst kenarına hizalar.|Hedef kaynağı, hedef alanın sol üst köşesine (fare işaretçisinin sınırları) ve açılır hizalama noktası nın sol <xref:System.Windows.Controls.Primitives.Popup>alt köşesine değişir.|Sol kenara hizalar.|Sağ kenarına hizalar.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>|Üst kenarına hizalar.|Açılır hizalama <xref:System.Windows.Controls.Primitives.Popup>noktası, 'nin sol alt köşesine değişir.|Sol kenara hizalar.|Açılır hizalama noktası açılır pencerenin sağ üst köşesinde değişir.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>|Üst kenarına hizalar.|Alt kenarına hizalar.|Sol kenara hizalar.|Sağ kenarına hizalar.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>|Üst kenarına hizalar.|Açılır hizalama <xref:System.Windows.Controls.Primitives.Popup>noktası, 'nin sol alt köşesine değişir.|Sol kenara hizalar.|Açılır hizalama noktası açılır pencerenin sağ üst köşesinde değişir.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Right>|Üst kenarına hizalar.|Alt kenarına hizalar.|Sol kenara hizalar.|Hedef kaynağı hedef alanın sol üst köşesine değişir ve açılır hizalama <xref:System.Windows.Controls.Primitives.Popup>noktası.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Top>|Hedef kaynağı, hedef alanın sol alt köşesine, açılır hizalama noktası ise sol üst <xref:System.Windows.Controls.Primitives.Popup>köşeye değişir. Aslında, bu ne zaman <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> olduğu <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>gibi aynıdır.|Alt kenarına hizalar.|Sol kenara hizalar.|Sağ kenarına hizalar.|  
  
### <a name="aligning-to-the-screen-edge"></a>Ekran Kenarına Hizalama  
 A, <xref:System.Windows.Controls.Primitives.Popup> kendisini yeniden konumlandırarak ekranın kenarına hizalanabilir, böylece ekrandaki tüm <xref:System.Windows.Controls.Primitives.Popup> görünür.  Bu durumda, hedef kaynağı ve açılır pencere hizalama noktası arasındaki <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> mesafe <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>ve . Ne <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>zaman <xref:System.Windows.Controls.Primitives.PlacementMode.Center>, <xref:System.Windows.Controls.Primitives.PlacementMode.Relative>veya <xref:System.Windows.Controls.Primitives.Popup> , , her ekran kenarına kendini hizalar.  Örneğin, a'nın <xref:System.Windows.Controls.Primitives.Popup> <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 100'e <xref:System.Windows.Controls.Primitives.PlacementMode.Relative> ayarladığını ve <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> ayarladığını varsayalım.  Ekranın alt kenarı, ekranın alt <xref:System.Windows.Controls.Primitives.Popup>kenarı boyunca kendini <xref:System.Windows.Controls.Primitives.Popup> yeniden konumlandırıyorsa ve hedef kaynağı ile açılır pencere hizalama noktası arasındaki dikey uzaklık 100'den azdır. Aşağıdaki resimde bunu göstermektedir.  
  
 ![Ekranın kenarına hizalayan açılır pencere](./media/popup-placement-behavior/popup-placement-relative-screen-edge.png "Açılır pencere ekranın kenarına hizalanır.")
  
### <a name="changing-the-popup-alignment-point"></a>Açılır Hizalama Noktasını Değiştirme  
 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> Pop-up <xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint> <xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint> <xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>alt veya sağ ekran kenarı karşılaştığında pop-up hizalama noktası değişirse.  
  
 Aşağıdaki resimde, alt ekran kenarı, açılan pencere hizalama <xref:System.Windows.Controls.Primitives.Popup>noktasının tamamını veya bir kısmını gizlediğinde, açılan pencerenin sol alt köşesi olduğunu <xref:System.Windows.Controls.Primitives.Popup>göstermektedir.  
  
 ![Alt ekran kenarı nedeniyle yeni hizalama noktası](./media/popup-placement-behavior/popup-placement-relative-point-screen-edge.png "Açılır pencere ekranın alt kenarıyla karşılaşır ve açılır pencere hizalama noktasını değiştirir.")  

 Aşağıdaki resimde, sağ ekran <xref:System.Windows.Controls.Primitives.Popup> kenarı tarafından gizlendiğinde, açılır hizalama noktasının sağ üst <xref:System.Windows.Controls.Primitives.Popup>köşe olduğunu göstermektedir.  
  
 ![Ekran kenarı nedeniyle yeni açılır hizalama noktası](./media/popup-placement-behavior/popup-placement-relative-point-right-screen-edge.png "Açılır pencere ekranın sağ kenarıyla karşılaşır ve açılır pencere hizalama noktasını değiştirir.")
  
 Alt <xref:System.Windows.Controls.Primitives.Popup> ve sağ ekran kenarlarıyla karşılaşırsa, açılır hizalama noktası. <xref:System.Windows.Controls.Primitives.Popup>  
  
### <a name="changing-the-target-origin-and-popup-alignment-point"></a>Hedef Kökeni ve Açılır Pencere Hizalama Noktasını Değiştirme  
 Belirli <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom> <xref:System.Windows.Controls.Primitives.PlacementMode.Left>bir <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>ekran kenarına rastlandığında hedef kaynağı ve açılır pencere hizalama noktası ne zaman değişir. <xref:System.Windows.Controls.Primitives.PlacementMode.Right> <xref:System.Windows.Controls.Primitives.PlacementMode.Top>  Konumun değişmesine neden olan ekran kenarı <xref:System.Windows.Controls.Primitives.PlacementMode> değere bağlıdır.  
  
 Aşağıdaki resimde, <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> hedef <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom> kaynağın <xref:System.Windows.Controls.Primitives.Popup> hedef alanın sol üst köşesi, açılır hizalama noktası ise alt ekran kenarı ile karşılaşıldığında, açılan <xref:System.Windows.Controls.Primitives.Popup>hizalama noktasının sol alt köşe olduğunu göstermektedir.  
  
 ![Alt ekran kenarı nedeniyle yeni hizalama noktası](./media/popup-placement-behavior/popup-placement-bottom-screen-edge.png "Yerleşim Alt ve açılır pencere ekranın alt kenarı karşılaşır.")
  
 Aşağıdaki resimde, ne <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> zaman <xref:System.Windows.Controls.Primitives.PlacementMode.Left> ve <xref:System.Windows.Controls.Primitives.Popup> sol ekran kenarı karşılaştığında, hedef kökeni hedef alanın sağ üst köşesinde ve pop-up hizalama <xref:System.Windows.Controls.Primitives.Popup>noktası üst-sol köşe olduğunu göstermektedir.  
  
 ![Sol ekran kenarına bağlı yeni hizalama noktası](./media/popup-placement-behavior/popup-placement-left-screen-edge.png "Yerleşim Sol ve açılır ekranın sol kenarı karşılaşır.")  
  
 Aşağıdaki resimde, ne <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> zaman <xref:System.Windows.Controls.Primitives.PlacementMode.Right> ve <xref:System.Windows.Controls.Primitives.Popup> sağ ekran kenarı karşılaştığında, hedef kökeni hedef alanın sol üst köşesinde ve pop-up hizalama <xref:System.Windows.Controls.Primitives.Popup>noktası nın sağ üst köşesinde olduğunu göstermektedir.  
  
 ![Sağ ekran kenarı nedeniyle yeni hizalama noktası](./media/popup-placement-behavior/popup-placement-right-screen-edge.png "Yerleştirme Doğru ve açılır pencere ekranın sağ kenarı ile karşılaşır.")  

 Aşağıdaki <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> resimde, hedef <xref:System.Windows.Controls.Primitives.PlacementMode.Top> kaynağın <xref:System.Windows.Controls.Primitives.Popup> hedef alanın sol alt köşesi ve açılır hizalama noktasının üst-sol köşe olduğu ve üst ekran <xref:System.Windows.Controls.Primitives.Popup>kenarı ile karşılaştığında, hedef kaynağın .  
  
 ![Üst ekran kenarı nedeniyle yeni hizalama noktası](./media/popup-placement-behavior/popup-placement-top-screen-edge.png "Yerleşim Üst ve açılır pencere ekranın üst kenarı karşılaşır.")  
  
 Aşağıdaki resimde, <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> hedef <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse> <xref:System.Windows.Controls.Primitives.Popup> kaynağın hedef alanın sol üst köşesi (fare işaretçisinin sınırları) ve açılır hizalama noktasının <xref:System.Windows.Controls.Primitives.Popup>ise alt ekran kenarı olduğunu gösteren .  
  
 ![ekran kenarına yakın fare nedeniyle yeni hizalama noktası](./media/popup-placement-behavior/popup-placement-mouse-screen-edge.png "Yerleşim Fare dir ve açılır pencere ekranın alt kenarıyla karşılaşır.")
  
### <a name="customizing-popup-placement"></a>Popup Yerleşimini Özelleştirme  
 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> Özelliği <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>' ye ayarlayarak hedef kaynağını ve açılır hizalama noktasını özelleştirebilirsiniz. Daha sonra <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> olası yerleşim noktaları ve birincil eksenler kümesi (tercih sırasına <xref:System.Windows.Controls.Primitives.Popup>göre) döndüren bir temsilci tanımlayın. En büyük bölümünü <xref:System.Windows.Controls.Primitives.Popup> gösteren nokta seçilir.  Ekranın kenarına <xref:System.Windows.Controls.Primitives.Popup> gizlenirse <xref:System.Windows.Controls.Primitives.Popup> konumu otomatik olarak ayarlanır. Örneğin, bkz. [Özel Açılır Pencere Konumu Belirtin.](how-to-specify-a-custom-popup-position.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Popup Yerleştirme Örneği](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS)
