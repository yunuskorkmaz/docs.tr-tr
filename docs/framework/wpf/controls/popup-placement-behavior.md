---
title: Açılan Pencere Yerleştirme Davranışı
ms.date: 03/30/2017
helpviewer_keywords:
- popups [WPF]
- Popup control [WPF], placing
- placing popups [WPF]
- positioning popups [WPF]
ms.assetid: fbf642e9-f670-4efd-a7af-a67468a1c8e1
ms.openlocfilehash: 924d099a17390eeac61bd87a0c3ca0e05b1c8172
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54672090"
---
# <a name="popup-placement-behavior"></a>Açılan Pencere Yerleştirme Davranışı
A <xref:System.Windows.Controls.Primitives.Popup> denetimi, bir uygulamanın yükünü gezinen ayrı bir pencerede içeriğini görüntüler. Konumu belirleyebileceğiniz bir <xref:System.Windows.Controls.Primitives.Popup> göre bir denetim, fare ve kullanarak ekrandaki <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>, <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>, ve <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> özellikleri.  Bu özellikler konumunu belirten esneklik sunmak için birlikte çalışır. <xref:System.Windows.Controls.Primitives.Popup>.  
  
> [!NOTE]
>  <xref:System.Windows.Controls.ToolTip> Ve <xref:System.Windows.Controls.ContextMenu> sınıflar da bu beş özelliklerini tanımlayın ve benzer şekilde davranır.  
  

  
<a name="Positioning"></a>   
## <a name="positioning-the-popup"></a>Açılan Pencere yerleştirme  
 Yerleşimini bir <xref:System.Windows.Controls.Primitives.Popup> göreli olabilir bir <xref:System.Windows.UIElement> veya ekranın tamamını.  Aşağıdaki örnek, dört oluşturur <xref:System.Windows.Controls.Primitives.Popup> göreli olan denetimler bir <xref:System.Windows.UIElement>— bu durumda, bir resim. Tüm <xref:System.Windows.Controls.Primitives.Popup> denetiminiz <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> özelliğini `image1`, ancak her <xref:System.Windows.Controls.Primitives.Popup> yerleştirme özelliği için farklı bir değere sahip.  
  
 [!code-xaml[PopupPositionSnippet#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#3)]  
  
 Görüntüyü aşağıda gösterilmiştir ve <xref:System.Windows.Controls.Primitives.Popup> denetimleri  
  
 ![Dört açılan denetim görüntüsüyle](../../../../docs/framework/wpf/controls/media/popupplacementintro.png "PopupPlacementIntro")  
Görüntü ile dört açılan pencereler  
  
 Bu basit örnek nasıl ayarlanacağı gösterilmektedir <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> ve <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> özellikleri, ancak kullanarak <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>, ve <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> özellikleri nereden daha fazla denetime sahip <xref:System.Windows.Controls.Primitives.Popup> konumlandırıldı.  
  
<a name="Definitions"></a>   
## <a name="definitions-of-terms-the-anatomy-of-a-popup"></a>Terimlerin tanımları: Açılan pencere anatomisi  
 Aşağıdaki koşulları içinde anlamak yararlı nasıl <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>, <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>, ve <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> özellikleri birbiriyle ilgilidir ve <xref:System.Windows.Controls.Primitives.Popup>:  
  
-   Hedef nesne  
  
-   Hedef alan  
  
-   Hedef kaynak  
  
-   Açılan kutu hizalama noktası  
  
 Bu terimler için çeşitli yönlerini başvurmak için kullanışlı bir yol sağlar <xref:System.Windows.Controls.Primitives.Popup> ve ilişkili olduğu denetimi.  
  
### <a name="target-object"></a>Hedef nesne  
 *Hedef nesne* öğe, <xref:System.Windows.Controls.Primitives.Popup> ilişkilidir. Varsa <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> özelliği ayarlanmışsa, hedef nesneyi belirtir.  Varsa <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> ayarlı değil ve <xref:System.Windows.Controls.Primitives.Popup> bir üst öğeye sahip ana hedef nesnedir.  Yoksa hiçbir <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> değeri ve üst öğe, hedef nesnesi yok ve <xref:System.Windows.Controls.Primitives.Popup> kutusunun ekrana göreli konumlandırıldı.  
  
 Aşağıdaki örnek, oluşturur bir <xref:System.Windows.Controls.Primitives.Popup> alt öğesi olan bir <xref:System.Windows.Controls.Canvas>.  Örnek ayarlı değil <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> özellikte <xref:System.Windows.Controls.Primitives.Popup>. İçin varsayılan değer <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> olduğu <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom?displayProperty=nameWithType>, bu nedenle <xref:System.Windows.Controls.Primitives.Popup> altında görünen <xref:System.Windows.Controls.Canvas>.  
  
 [!code-xaml[PopupPositionSnippet#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#1)]  
  
 Aşağıdaki çizimde gösterilmektedir <xref:System.Windows.Controls.Primitives.Popup> göreli konumlu <xref:System.Windows.Controls.Canvas>.  
  
 ![Açılan pencere denetimi PlacementTarget içermeyen](../../../../docs/framework/wpf/controls/media/popupplacementnoplacementtarget.PNG "PopupPlacementNoPlacementTarget")  
Açılan pencere PlacementTarget içermeyen  
  
 Aşağıdaki örnek, oluşturur bir <xref:System.Windows.Controls.Primitives.Popup> alt öğesi olan bir <xref:System.Windows.Controls.Canvas>, ancak bu kez <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> ayarlanır `ellipse1`, açılan pencerenin altında görünecek şekilde <xref:System.Windows.Shapes.Ellipse>.  
  
 [!code-xaml[PopupPositionSnippet#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#2)]  
  
 Aşağıdaki çizimde gösterilmektedir <xref:System.Windows.Controls.Primitives.Popup> göreli konumlu <xref:System.Windows.Shapes.Ellipse>.  
  
 ![Elips göreli konumlu açılan](../../../../docs/framework/wpf/controls/media/popupplacementwithplacementtarget.PNG "PopupPlacementWithPlacementTarget")  
Açılır penceresi ile PlacementTarget  
  
> [!NOTE]
>  İçin <xref:System.Windows.Controls.ToolTip>, varsayılan değerini <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> olduğu <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>.  İçin <xref:System.Windows.Controls.ContextMenu>, varsayılan değerini <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> olduğu <xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>. Bu değerler daha sonra "Nasıl özellikleri birlikte çalışacak." açıklanmaktadır  
  
### <a name="target-area"></a>Hedef alan  
 *Hedef alan* alanı ekranında, <xref:System.Windows.Controls.Primitives.Popup> göreli olduğu. Önceki örneklerde, <xref:System.Windows.Controls.Primitives.Popup> sınırları hedef nesnenin, ancak bazı durumlarda, birlikte hizalanır <xref:System.Windows.Controls.Primitives.Popup> diğer sınırları için hizalı bile <xref:System.Windows.Controls.Primitives.Popup> hedef nesnesi vardır.  Varsa <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> özelliği ayarlanmışsa, hedef alan hedef nesnenin sınırları farklıdır.  
  
 Aşağıdaki örnek iki oluşturur <xref:System.Windows.Controls.Canvas> nesneleri, her birini içeren bir <xref:System.Windows.Shapes.Rectangle> ve <xref:System.Windows.Controls.Primitives.Popup>.  Her iki durumda da, hedef nesne için <xref:System.Windows.Controls.Primitives.Popup> olduğu <xref:System.Windows.Controls.Canvas>. <xref:System.Windows.Controls.Primitives.Popup> İlk <xref:System.Windows.Controls.Canvas> sahip <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Ayarla ile kendi <xref:System.Windows.Rect.X%2A>, <xref:System.Windows.Rect.Y%2A>, <xref:System.Windows.Rect.Width%2A>, ve <xref:System.Windows.Rect.Height%2A> sırasıyla 50, 50 50 ve 100 için ayarlanan özellikler. <xref:System.Windows.Controls.Primitives.Popup> İkinci <xref:System.Windows.Controls.Canvas> olmayan <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> ayarlayın.  Sonuç olarak, ilk <xref:System.Windows.Controls.Primitives.Popup> altında konumlandırılmış <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> ve ikinci <xref:System.Windows.Controls.Primitives.Popup> altında konumlandırılmış <xref:System.Windows.Controls.Canvas>. Her <xref:System.Windows.Controls.Canvas> de içeren bir <xref:System.Windows.Shapes.Rectangle> olarak aynı sınırları olan <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> ilk <xref:System.Windows.Controls.Primitives.Popup>.  Unutmayın <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> görünür bir öğe uygulamada; oluşturmaz örnek bir <xref:System.Windows.Shapes.Rectangle> temsil etmek için <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>.  
  
 [!code-xaml[PopupPositionSnippet#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#4)]  
  
 Aşağıdaki çizim, yukarıdaki örnekte sonucunu gösterir.  
  
 ![Açılır ve PlacementRectangle olmadan](../../../../docs/framework/wpf/controls/media/popupplacementplacementrectangle.PNG "PopupPlacementPlacementRectangle")  
Açılır ve PlacementRectangle olmadan  
  
### <a name="target-origin-and-popup-alignment-point"></a>Hedef kaynak ve açılan hizalama noktası  
 *Hedef kaynak* ve *açılan hizalama noktası* başvuru noktalarında hedef alan ve açılan, sırasıyla konumlandırma için kullanılır. Kullanabileceğiniz <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> ve <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> açılır penceresinden hedef alan dengelemek için özellikleri.  <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> Ve <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> hedef kaynağı ve açılan hizalama noktası göre. Değerini <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> özelliği, hedef kaynak ve açılan hizalama noktası yerleştirildiği belirler.  
  
 Aşağıdaki örnek, oluşturur bir <xref:System.Windows.Controls.Primitives.Popup> ve ayarlar <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> ve <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> 20 özellikleri.  <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> Özelliği <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom> (varsayılan), hedef kaynak, hedef alanın sol alt köşesine etmektedir ve sol üst köşesindeki açılır hizalama noktası <xref:System.Windows.Controls.Primitives.Popup>.  
  
 [!code-xaml[PopupPositionSnippet#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#5)]  
  
 Aşağıdaki çizim, yukarıdaki örnekte sonucunu gösterir.  
  
 ![Açılan Pencere yerleştirme hedef kaynak hizalama noktasıyla](../../../../docs/framework/wpf/controls/media/popupplacementtargetoriginalignmentpoint.PNG "PopupPlacementTargetOriginAlignmentPoint")  
HorizontalOffset ve VerticalOffset açılan menüsü  
  
<a name="How"></a>   
## <a name="how-the-properties-work-together"></a>Özellikleri birlikte nasıl çalışır  
 Değerlerini <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, ve <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> birlikte doğru hedef alan, hedef kaynağı ve açılan hizalama noktası şekil kabul etmek gerekir.  Örneğin, değeri <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> olduğu <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>, hedef nesnesi yok <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> göz ardı edilir ve hedef alanı sınırları fare işaretçisi. Öte yandan, varsa <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> olduğu <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>, <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> veya ana hedef nesne belirler ve <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> hedef alanı belirler.  
  
 Aşağıdaki tabloda, hedef nesne, hedef alan, hedef kaynağı ve açılan hizalama noktası açıklar ve belirtir olup olmadığını <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> ve <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> her biri için kullanılan <xref:System.Windows.Controls.Primitives.PlacementMode> numaralandırma değeri.  
  
|PlacementMode|Hedef nesne|Hedef alan|Hedef kaynak|Açılan kutu hizalama noktası|  
|-------------------|-------------------|-----------------|-------------------|---------------------------|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>|Uygulanamaz. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> göz ardı edilir.|Ekran veya <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> ayarlanmış ise.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Göre ekrandır.|Sol üst köşedeki hedef alan.|Sol üst köşesinde <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>|Uygulanamaz. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> göz ardı edilir.|Ekran veya <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> ayarlanmış ise.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Göre ekrandır.|Sol üst köşedeki hedef alan.|Sol üst köşesinde <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> veya üst.|Hedef nesne veya <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> ayarlanmış ise.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Göre hedef nesnesi.|Hedef alan sol alt köşesindeki.|Sol üst köşesinde <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Center>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> veya üst.|Hedef nesne veya <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> ayarlanmış ise.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Göre hedef nesnesi.|Hedef alan Merkezi.|Merkezi <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> veya üst.|Hedef nesne veya <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> ayarlanmış ise.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Göre hedef nesnesi.|Tarafından tanımlanan <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>.|Tarafından tanımlanan <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Left>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> veya üst.|Hedef nesne veya <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> ayarlanmış ise.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Göre hedef nesnesi.|Sol üst köşedeki hedef alan.|Sağ üst köşesindeki <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>|Uygulanamaz. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> göz ardı edilir.|Fare işaretçisi sınırları. <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> göz ardı edilir.|Hedef alan sol alt köşesindeki.|Sol üst köşesinde <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>|Uygulanamaz. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> göz ardı edilir.|Fare işaretçisi sınırları. <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> göz ardı edilir.|Sol üst köşedeki hedef alan.|Sol üst köşesinde <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> veya üst.|Hedef nesne veya <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> ayarlanmış ise.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Göre hedef nesnesi.|Sol üst köşedeki hedef alan.|Sol üst köşesinde <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> veya üst.|Hedef nesne veya <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> ayarlanmış ise.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Göre hedef nesnesi.|Sol üst köşedeki hedef alan.|Sol üst köşesinde <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Right>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> veya üst.|Hedef nesne veya <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> ayarlanmış ise.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Göre hedef nesnesi.|Sağ üst köşedeki hedef alan.|Sol üst köşesinde <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Top>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> veya üst.|Hedef nesne veya <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> ayarlanmış ise.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Göre hedef nesnesi.|Sol üst köşedeki hedef alan.|Sol alt köşesindeki <xref:System.Windows.Controls.Primitives.Popup>.|  
  
 Aşağıdaki resimlerde gösterildiği <xref:System.Windows.Controls.Primitives.Popup>, hedef alan, hedef kaynağı ve açılan hizalama noktası her biri için <xref:System.Windows.Controls.Primitives.PlacementMode> değeri. Her şekilde hedef alan sarı, ve <xref:System.Windows.Controls.Primitives.Popup> mavi.  
  
 ![Mutlak veya AbsolutePoint yerleşimiyle](../../../../docs/framework/wpf/controls/media/popupplacementabsolute.png "PopupPlacementAbsolute")  
Yerleştirme mutlak AbsolutePoint mi  
  
 ![Alt yerleşimiyle](../../../../docs/framework/wpf/controls/media/popupplacementbottom.png "PopupPlacementBottom")  
Yerleştirme alt vardır.  
  
 ![Merkezi yerleşimiyle](../../../../docs/framework/wpf/controls/media/popupplacementcenter.png "PopupPlacementCenter")  
Yerleştirme merkezidir.  
  
 ![Sol yerleşimiyle](../../../../docs/framework/wpf/controls/media/popupplacementleft.png "PopupPlacementLeft")  
Yerleştirme olan sol  
  
 ![Fare yerleşimiyle](../../../../docs/framework/wpf/controls/media/popupplacementmouse.png "PopupPlacementMouse")  
Fare yerleştirme olan  
  
 ![MousePoint yerleşimiyle](../../../../docs/framework/wpf/controls/media/popupplacementmousepoint.png "PopupPlacementMousePoint")  
Yerleştirme MousePoint olduğu  
  
 ![Göreli veya RelativePoint yerleşimiyle](../../../../docs/framework/wpf/controls/media/popupplacementrelative.png "PopupPlacementRelative")  
Yerleştirme göreli RelativePoint mi  
  
 ![Doğru yerleşimiyle](../../../../docs/framework/wpf/controls/media/popupplacementright.png "PopupPlacementRight")  
Yerleştirme unsurdur.  
  
 ![Üst yerleşimiyle](../../../../docs/framework/wpf/controls/media/popupplacementtop.png "PopupPlacementTop")  
Yerleştirme üst bulunuyor  
  
<a name="When"></a>   
## <a name="when-the-popup-encounters-the-edge-of-the-screen"></a>Açılan pencerenin kenarında karşılaştığında  
 Güvenlik nedenleriyle bir <xref:System.Windows.Controls.Primitives.Popup> ekranın kenarı tarafından gizlenemez. Aşağıdaki işlemlerden birini olur olduğunda <xref:System.Windows.Controls.Primitives.Popup> ekran kenarı karşılaşır:  
  
-   Açılan gizlememeniz ekranın kenarındaki kendisi yeniden hizalar <xref:System.Windows.Controls.Primitives.Popup>.  
  
-   Açılan farklı açılan hizalama noktası kullanır.  
  
-   Açılan farklı bir hedef kaynak ve açılan hizalama noktası kullanır.  
  
 Bu seçenekler daha sonra bu bölümde daha ayrıntılı açıklanmıştır.  
  
 Davranışını <xref:System.Windows.Controls.Primitives.Popup> bu karşılaştığında ekran kenarı değerine bağlıdır. <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> özelliği ve hangi ekran açılır karşılaştığında edge. Davranış aşağıdaki tabloda özetlenmiştir olduğunda <xref:System.Windows.Controls.Primitives.Popup> her biri için bir ekran edge karşılaştığında <xref:System.Windows.Controls.Primitives.PlacementMode> değeri.  
  
|PlacementMode|Üst kenarı|Alt kenar|Sol kenarı|Sağ kenarı|  
|-------------------|--------------|-----------------|---------------|----------------|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>|Üst kenarına hizalanır.|Alt kenarına hizalanır.|Sol kenarına hizalanır.|Sağ kenarına hizalanır.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>|Üst kenarına hizalanır.|Açılan hizalama noktası için sol alt köşesindeki değişiklikleri <xref:System.Windows.Controls.Primitives.Popup>.|Sol kenarına hizalanır.|İçin sağ üst köşesindeki açılır hizalama noktası değişiklikleri <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>|Üst kenarına hizalanır.|Hedef kaynak hedef alan sol üst köşesinde ve açılan hizalama noktası için sol alt köşesindeki değiştirir <xref:System.Windows.Controls.Primitives.Popup>.|Sol kenarına hizalanır.|Sağ kenarına hizalanır.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Center>|Üst kenarına hizalanır.|Alt kenarına hizalanır.|Sol kenarına hizalanır.|Sağ kenarına hizalanır.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Left>|Üst kenarına hizalanır.|Alt kenarına hizalanır.|Hedef kaynak hedef alan sağ üst köşesindeki ve için sol üst köşesindeki açılır hizalama noktası değiştirir <xref:System.Windows.Controls.Primitives.Popup>.|Sağ kenarına hizalanır.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>|Üst kenarına hizalanır.|Hedef kaynak hedef alan (fare işaretçisi sınırları) sol üst köşesinde ve açılan hizalama noktası için sol alt köşesindeki değiştirir <xref:System.Windows.Controls.Primitives.Popup>.|Sol kenarına hizalanır.|Sağ kenarına hizalanır.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>|Üst kenarına hizalanır.|Açılan hizalama noktası için sol alt köşesindeki değişiklikleri <xref:System.Windows.Controls.Primitives.Popup>.|Sol kenarına hizalanır.|Açılan hizalama değişiklikleri açılan pencerenin sağ üst köşesine gelin.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>|Üst kenarına hizalanır.|Alt kenarına hizalanır.|Sol kenarına hizalanır.|Sağ kenarına hizalanır.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>|Üst kenarına hizalanır.|Açılan hizalama noktası için sol alt köşesindeki değişiklikleri <xref:System.Windows.Controls.Primitives.Popup>.|Sol kenarına hizalanır.|Açılan hizalama değişiklikleri açılan pencerenin sağ üst köşesine gelin.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Right>|Üst kenarına hizalanır.|Alt kenarına hizalanır.|Sol kenarına hizalanır.|Hedef kaynak hedef alan sol üst köşesinde ve için sağ üst köşesindeki açılır hizalama noktası değiştirir <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Top>|Hedef kaynak hedef alan sol alt köşesindeki ve için sol üst köşesindeki açılır hizalama noktası değiştirir <xref:System.Windows.Controls.Primitives.Popup>. Aslında, bu ne zaman aynı olur <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> olduğu <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>.|Alt kenarına hizalanır.|Sol kenarına hizalanır.|Sağ kenarına hizalanır.|  
  
### <a name="aligning-to-the-screen-edge"></a>Ekran uca hizalama  
 A <xref:System.Windows.Controls.Primitives.Popup> kenarında için kendisi kadar yeniden konumlandırma tarafından tüm hizalayabilirsiniz <xref:System.Windows.Controls.Primitives.Popup> ekranda görülebilir.  Böyle bir durumda, hedef kaynak ve açılan hizalama noktası arasındaki uzaklığı değerlerden farklı olabilir <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> ve <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>. Zaman <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> olduğu <xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>, <xref:System.Windows.Controls.Primitives.PlacementMode.Center>, veya <xref:System.Windows.Controls.Primitives.PlacementMode.Relative>, <xref:System.Windows.Controls.Primitives.Popup> kendisini her ekran kenarına hizalanır.  Örneğin, varsayımında bir <xref:System.Windows.Controls.Primitives.Popup> sahip <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> kümesine <xref:System.Windows.Controls.Primitives.PlacementMode.Relative> ve <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> 100 olarak ayarlayın.  Ekranın alt kenarı kısmını veya tamamını gizlerse <xref:System.Windows.Controls.Primitives.Popup>, <xref:System.Windows.Controls.Primitives.Popup> kendisi yeniden konumlandırır ekran ve dikey uzaklığı açılan ve hedef kaynak arasında alt kenarı boyunca hizalama 100'den küçük noktasıdır. Aşağıdaki çizimde bu gösterir.  
  
 ![Ekran kenarına hizalanır açılan](../../../../docs/framework/wpf/controls/media/popupplacementrelativescreenedge.png "PopupPlacementRelativeScreenEdge")  
Açılan ekran ucuna hizalar.  
  
### <a name="changing-the-popup-alignment-point"></a>Açılan pencere hizalama noktasını değiştirme  
 Varsa <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> olduğu <xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>, <xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>, veya <xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>, açılan hizalama noktası açılan Alttan veya sağ ekran edge karşılaştığında değiştirir.  
  
 Ekranın alt kenarı kısmını veya tamamını gizlediğinde aşağıda gösteren <xref:System.Windows.Controls.Primitives.Popup>, sol alt köşesindeki açılır hizalama noktasıdır <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Alt ekranın kenarı nedeniyle yeni hizalama noktası](../../../../docs/framework/wpf/controls/media/popupplacementrelativepointscreenedge.png "PopupPlacementRelativePointScreenEdge")  
Açılır ekranın alt kenarı karşılaşır ve açılan hizalama noktası değişiklikleri  
  
 Kullanırken aşağıdaki çizimde gösterilmiştir <xref:System.Windows.Controls.Primitives.Popup> gizli ekranın sağ kenarından açılan hizalama sağ üst köşesindeki noktasıdır <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Yeni açılan hizalama nokta ekran kenar nedeniyle](../../../../docs/framework/wpf/controls/media/popupplacementrelativepointrightscreenedge.png "PopupPlacementRelativePointRightScreenEdge")  
Popup sağ kenarında karşılaşır ve açılan hizalama noktası değişiklikleri  
  
 Varsa <xref:System.Windows.Controls.Primitives.Popup> alt ve sağ ekran kenarlar karşılaştığında sağ alt köşesindeki açılır hizalama noktasıdır <xref:System.Windows.Controls.Primitives.Popup>.  
  
### <a name="changing-the-target-origin-and-popup-alignment-point"></a>Açılan kutu hizalama noktası ve hedef kaynağı değiştirme  
 Zaman <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> olduğu <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>, <xref:System.Windows.Controls.Primitives.PlacementMode.Left>, <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>, <xref:System.Windows.Controls.Primitives.PlacementMode.Right>, veya <xref:System.Windows.Controls.Primitives.PlacementMode.Top>, hedef kaynak ve açılan hizalama belirli bir ekran edge karşılaşılırsa değişiklik gelin.  Konumu değiştirmek neden olan ekran edge bağımlı <xref:System.Windows.Controls.Primitives.PlacementMode> değeri.  
  
 Kullanırken aşağıdaki çizimde gösterilmiştir <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> olduğu <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom> ve <xref:System.Windows.Controls.Primitives.Popup> alt ekranın kenarı karşılaştığında hedef kaynak hedef alanın sol üst köşedeki ve açılan hizalama noktası sol alt köşesindeki <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Alt ekranın kenarı nedeniyle yeni hizalama noktası](../../../../docs/framework/wpf/controls/media/popupplacementbottomscreenedge.png "PopupPlacementBottomScreenEdge")  
Yerleştirme alt vardır ve açılır ekranın alt kenarı karşılaştığında  
  
 Kullanırken aşağıdaki çizimde gösterilmiştir <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> olduğu <xref:System.Windows.Controls.Primitives.PlacementMode.Left> ve <xref:System.Windows.Controls.Primitives.Popup> karşılaştığında ekranın sol kenarı hedef kaynak hedef alanının sağ üst köşedeki ve açılan hizalama noktası solüstköşesinde<xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Ekranın sol kenarı nedeniyle yeni hizalama noktası](../../../../docs/framework/wpf/controls/media/popupplacementleftscreenedge.png "PopupPlacementLeftScreenEdge")  
Yerleştirme sol olduğunu ve açılır ekranın sol kenarında karşılaşır.  
  
 Kullanırken aşağıdaki çizimde gösterilmiştir <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> olduğu <xref:System.Windows.Controls.Primitives.PlacementMode.Right> ve <xref:System.Windows.Controls.Primitives.Popup> doğru ekran edge karşılaştığında hedef alanın sol üst köşesine hedef kaynağı olduğundan ve sağ üst köşesindeki açılır hizalama noktasıdır <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Ekranın sağ kenar nedeniyle yeni hizalama noktası](../../../../docs/framework/wpf/controls/media/popupplacementrightscreenedge.png "PopupPlacementRightScreenEdge")  
Yerleştirme hangisi ve açılan pencerenin sağ kenarında karşılaştığında  
  
 Kullanırken aşağıdaki çizimde gösterilmiştir <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> olduğu <xref:System.Windows.Controls.Primitives.PlacementMode.Top> ve <xref:System.Windows.Controls.Primitives.Popup> ekranın üst kenarı ile karşılaşırsa hedef alanın sol alt köşesine hedef kaynağı olan ve sol üst köşesindeki açılır hizalama noktasıdır <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Ekranın üst kenarı nedeniyle yeni hizalama noktası](../../../../docs/framework/wpf/controls/media/popupplacementtopscreenedge.png "PopupPlacementTopScreenEdge")  
Yerleştirme üst bulunur ve açılır ekranın üst kenarı ile karşılaşırsa  
  
 Kullanırken aşağıdaki çizimde gösterilmiştir <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> olduğu <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse> ve <xref:System.Windows.Controls.Primitives.Popup> alt ekranın kenarı karşılaştığında hedef alan (fare işaretçisi sınırları) ve açılan hizalama sol üst köşesinde hedef kaynağı olan sol alt köşesindeki noktasıdır <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![fare ekranın kenarındaki nedeniyle yeni hizalama noktası](../../../../docs/framework/wpf/controls/media/popupplacementmousescreenedge.png "PopupPlacementMouseScreenEdge")  
Fare yerleştirme olduğunu ve açılır ekranın alt kenarı karşılaşır.  
  
### <a name="customizing-popup-placement"></a>Açılan Pencere yerleştirme özelleştirme  
 Hedef kaynak ve açılan hizalama noktası ayarlayarak özelleştirebileceğiniz <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> özelliğini <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>. Ardından tanımlayan bir <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> için bir dizi olası yerleştirme noktası ve birincil eksenleri (tercih sırasına göre) döndüren bir temsilci <xref:System.Windows.Controls.Primitives.Popup>. En büyük bölümünü gösteren noktası <xref:System.Windows.Controls.Primitives.Popup> seçilir.  Konumunu <xref:System.Windows.Controls.Primitives.Popup> varsa otomatik olarak düzeltilir <xref:System.Windows.Controls.Primitives.Popup> kenarında tarafından gizlenir. Bir örnek için bkz. [özel açılan pencerenin konumunu belirtme](../../../../docs/framework/wpf/controls/how-to-specify-a-custom-popup-position.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Açılan Pencere yerleştirme örnek](https://github.com/dotnet/samples/tree/master/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS)
