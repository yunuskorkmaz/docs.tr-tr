---
title: Açılan Pencere Yerleştirme Davranışı
ms.date: 03/30/2017
helpviewer_keywords:
- popups [WPF]
- Popup control [WPF], placing
- placing popups [WPF]
- positioning popups [WPF]
ms.assetid: fbf642e9-f670-4efd-a7af-a67468a1c8e1
ms.openlocfilehash: ca984aa724cf3f076d6073aa8b8179abfb91d26c
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "69951729"
---
# <a name="popup-placement-behavior"></a>Açılan Pencere Yerleştirme Davranışı
<xref:System.Windows.Controls.Primitives.Popup> denetim, içeriği bir uygulama üzerinde gezinen ayrı bir pencerede görüntüler. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>, <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>ve <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> özelliklerini kullanarak bir denetimin, fare veya ekranın göreli <xref:System.Windows.Controls.Primitives.Popup> konumunu belirtebilirsiniz.  Bu özellikler, <xref:System.Windows.Controls.Primitives.Popup>konumunu belirtirken esneklik sağlamak için birlikte çalışır.  
  
> [!NOTE]
> <xref:System.Windows.Controls.ToolTip> ve <xref:System.Windows.Controls.ContextMenu> sınıfları bu beş özelliği de tanımlar ve benzer şekilde davranır.  

<a name="Positioning"></a>   
## <a name="positioning-the-popup"></a>Açılan pencereyi konumlandırma  
 Bir <xref:System.Windows.Controls.Primitives.Popup> yerleşimi <xref:System.Windows.UIElement> veya ekranın tamamına göre olabilir.  Aşağıdaki örnek, bir <xref:System.Windows.UIElement>ilişkili dört <xref:System.Windows.Controls.Primitives.Popup> denetimi oluşturur — Bu durumda bir görüntü. <xref:System.Windows.Controls.Primitives.Popup> denetimlerinin hepsi, <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> özelliği `image1`olarak ayarlanmıştır, ancak her <xref:System.Windows.Controls.Primitives.Popup> yerleştirme özelliği için farklı bir değere sahiptir.  
  
 [!code-xaml[PopupPositionSnippet#3](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#3)]  
  
 Aşağıdaki çizimde resim ve <xref:System.Windows.Controls.Primitives.Popup> denetimleri gösterilmektedir  
  
 ![Dört açılan menü denetimi içeren resim](./media/popup-placement-behavior/popup-placement-intro.png "Dört açıya sahip resim")    
  
 Bu basit örnek, <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> ve <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> özelliklerinin nasıl ayarlanacağını gösterir, ancak <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>ve <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> özelliklerini kullanarak <xref:System.Windows.Controls.Primitives.Popup> konumlandırıldığı yerlerde daha fazla denetime sahip olursunuz.  
  
<a name="Definitions"></a>   
## <a name="definitions-of-terms-the-anatomy-of-a-popup"></a>Koşulların tanımları: bir açılan pencerenin Anatomumu  
 Aşağıdaki koşullar <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>, <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>ve <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> özelliklerinin birbirleriyle ve <xref:System.Windows.Controls.Primitives.Popup>nasıl ilişkilendirildiğini anlamak için yararlıdır:  
  
- Hedef nesne  
  
- Hedef alan  
  
- Hedef kaynak  
  
- Açılan pencere hizalama noktası  
  
 Bu terimler <xref:System.Windows.Controls.Primitives.Popup> ve ilişkili olduğu denetimin çeşitli yönlerini belirtmek için kullanışlı bir yol sağlar.  
  
### <a name="target-object"></a>Hedef nesne  
 *Hedef nesne* , <xref:System.Windows.Controls.Primitives.Popup> ilişkili öğesidir. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> özelliği ayarlandıysa, hedef nesneyi belirtir.  <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> ayarlanmamışsa ve <xref:System.Windows.Controls.Primitives.Popup> bir üst öğesi varsa, üst öğe hedef nesnedir.  <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> değer yoksa ve üst öğe yoksa, hedef nesne yoktur ve <xref:System.Windows.Controls.Primitives.Popup> ekrana göre konumlandırılır.  
  
 Aşağıdaki örnek, bir <xref:System.Windows.Controls.Canvas>alt öğesi olan bir <xref:System.Windows.Controls.Primitives.Popup> oluşturur.  Örnek, <xref:System.Windows.Controls.Primitives.Popup><xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> özelliğini ayarlanmamış. <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> için varsayılan değer <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom?displayProperty=nameWithType>ve <xref:System.Windows.Controls.Primitives.Popup> <xref:System.Windows.Controls.Canvas>altında görünür.  
  
 [!code-xaml[PopupPositionSnippet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#1)]  
  
 Aşağıdaki çizim <xref:System.Windows.Controls.Primitives.Popup> <xref:System.Windows.Controls.Canvas>göre konumlandırıldığını gösterir.  
  
 ![PlacementTarget içermeyen Popup denetimi](./media/popup-placement-behavior/popup-placement-no-placement-target.png "PlacementTarget içermeyen açılan pencere.")  

 Aşağıdaki örnek, bir <xref:System.Windows.Controls.Canvas>alt öğesi olan bir <xref:System.Windows.Controls.Primitives.Popup> oluşturur, ancak bu <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> `ellipse1`olarak ayarlanır, böylece açılan pencere <xref:System.Windows.Shapes.Ellipse>altında görünür.  
  
 [!code-xaml[PopupPositionSnippet#2](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#2)]  
  
 Aşağıdaki çizim <xref:System.Windows.Controls.Primitives.Popup> <xref:System.Windows.Shapes.Ellipse>göre konumlandırıldığını gösterir.  
  
 ![Bir elips 'e göre konumlandırılmış açılan pencere](./media/popup-placement-behavior/popup-placement-with-placement-target.png "PlacementTarget ile açılan pencere")    
  
> [!NOTE]
> <xref:System.Windows.Controls.ToolTip>için <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> varsayılan değeri <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>' dir.  <xref:System.Windows.Controls.ContextMenu>için <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> varsayılan değeri <xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>' dir. Bu değerler daha sonra, "özellikler birlikte nasıl çalışır." bölümünde açıklanmaktadır.  
  
### <a name="target-area"></a>Hedef alan  
 *Hedef alan* , ekranın <xref:System.Windows.Controls.Primitives.Popup> göreli olduğu alandır. Önceki örneklerde <xref:System.Windows.Controls.Primitives.Popup>, hedef nesnenin sınırlarına göre hizalanır, ancak bazı durumlarda, <xref:System.Windows.Controls.Primitives.Popup> hedef nesnesine sahip olsa bile, <xref:System.Windows.Controls.Primitives.Popup> diğer sınırlara hizalanır.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> özelliği ayarlandıysa, hedef alan hedef nesnenin sınırlarından farklıdır.  
  
 Aşağıdaki örnek, her biri <xref:System.Windows.Shapes.Rectangle> ve bir <xref:System.Windows.Controls.Primitives.Popup>içeren iki <xref:System.Windows.Controls.Canvas> nesnesi oluşturur.  Her iki durumda da, <xref:System.Windows.Controls.Primitives.Popup> için hedef nesne <xref:System.Windows.Controls.Canvas>. İlk <xref:System.Windows.Controls.Canvas> <xref:System.Windows.Controls.Primitives.Popup> <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> kümesine sahiptir; <xref:System.Windows.Rect.X%2A>, <xref:System.Windows.Rect.Y%2A>, <xref:System.Windows.Rect.Width%2A>ve <xref:System.Windows.Rect.Height%2A> özellikleri sırasıyla 50, 50, 50 ve 100 olarak ayarlanmıştır. İkinci <xref:System.Windows.Controls.Canvas> <xref:System.Windows.Controls.Primitives.Popup> <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> kümesine sahip değil.  Sonuç olarak, ilk <xref:System.Windows.Controls.Primitives.Popup> <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> altına konumlandırılır ve ikinci <xref:System.Windows.Controls.Primitives.Popup> <xref:System.Windows.Controls.Canvas>altına yerleştirilir. Her <xref:System.Windows.Controls.Canvas> Ayrıca, ilk <xref:System.Windows.Controls.Primitives.Popup><xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> ile aynı sınırlara sahip bir <xref:System.Windows.Shapes.Rectangle> içerir.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> uygulamada görünür bir öğe oluşturmadığını unutmayın. örnek, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>temsil eden bir <xref:System.Windows.Shapes.Rectangle> oluşturur.  
  
 [!code-xaml[PopupPositionSnippet#4](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#4)]  
  
 Aşağıdaki çizimde, önceki örneğin sonucu gösterilmektedir.  
  
 ![PlacementRectangle içeren ve içermeyen açılan pencere](./media/popup-placement-behavior/popup-placement-placement-rectangle.png "PlacementRectangle içeren ve içermeyen açılan pencere.")  

### <a name="target-origin-and-popup-alignment-point"></a>Hedef kaynak ve açılan hizalama noktası  
 *Hedef kaynak* ve *açılan pencere hizalama noktası* , konumlandırma için kullanılan, sırasıyla hedef alandaki ve açılan pencerede bulunan başvuru noktalarıdır. Açılır menüyü hedef alandan kaydırmak için <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> ve <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> özelliklerini kullanabilirsiniz.  <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> ve <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>, hedef kaynağa ve açılır hizalama noktasına göre değişir. <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> özelliğinin değeri, hedef kaynak ve açılan hizalama noktasının bulunduğu yeri belirler.  
  
 Aşağıdaki örnek bir <xref:System.Windows.Controls.Primitives.Popup> oluşturur ve <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> ve <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> özelliklerini 20 olarak ayarlar.  <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> özelliği <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom> (varsayılan) olarak ayarlanır, bu nedenle hedef kaynak hedef alanın sol alt köşesidir ve açılan hizalama noktası <xref:System.Windows.Controls.Primitives.Popup>sol üst köşesidir.  
  
 [!code-xaml[PopupPositionSnippet#5](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#5)]  
  
 Aşağıdaki çizimde, önceki örneğin sonucu gösterilmektedir.  
  
 ![Hedef kaynak hizalama noktasıyla açılan pencere yerleşimi](./media/popup-placement-behavior/popup-placement-target-origin-alignment-point.png "Horizontalkayması ve Verticalkayması içeren açılan pencere.")    
  
<a name="How"></a>   
## <a name="how-the-properties-work-together"></a>Özelliklerin birlikte çalışması  
 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>ve <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> değerlerinin, doğru hedef alanı, hedef kaynağı ve açılan hizalama noktasını anlamak için birlikte değerlendirilmesi gerekir.  Örneğin, <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> değeri <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>, hedef nesne yoktur, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> yok sayılır ve hedef alan fare işaretçisinin sınırları olur. Diğer taraftan, <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>, <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> veya üst hedef nesneyi belirler ve <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> hedef alanı belirler.  
  
 Aşağıdaki tabloda hedef nesne, hedef alanı, hedef kaynağı ve açılan pencere hizalama noktası açıklanmakta ve her bir <xref:System.Windows.Controls.Primitives.PlacementMode> numaralandırma değeri için <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> ve <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> kullanılıp kullanılmayacağını belirtir.  
  
|PlacementMode|Hedef nesne|Hedef alan|Hedef kaynak|Açılan pencere hizalama noktası|  
|-------------------|-------------------|-----------------|-------------------|---------------------------|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>|Yok. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> yoksayıldı.|Ekran veya ayarlandıysa <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> ekrana göredir.|Hedef alanın sol üst köşesi.|<xref:System.Windows.Controls.Primitives.Popup>sol üst köşesi.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>|Yok. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> yoksayıldı.|Ekran veya ayarlandıysa <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> ekrana göredir.|Hedef alanın sol üst köşesi.|<xref:System.Windows.Controls.Primitives.Popup>sol üst köşesi.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> veya üst.|Hedef nesne veya ayarlandıysa <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, hedef nesneye göredir.|Hedef alanın sol alt köşesi.|<xref:System.Windows.Controls.Primitives.Popup>sol üst köşesi.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Center>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> veya üst.|Hedef nesne veya ayarlandıysa <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, hedef nesneye göredir.|Hedef alanın merkezi.|<xref:System.Windows.Controls.Primitives.Popup>merkezi.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> veya üst.|Hedef nesne veya ayarlandıysa <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, hedef nesneye göredir.|<xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>tarafından tanımlanır.|<xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>tarafından tanımlanır.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Left>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> veya üst.|Hedef nesne veya ayarlandıysa <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, hedef nesneye göredir.|Hedef alanın sol üst köşesi.|<xref:System.Windows.Controls.Primitives.Popup>sağ üst köşesi.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>|Yok. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> yoksayıldı.|Fare işaretçisinin sınırları. <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> yoksayıldı.|Hedef alanın sol alt köşesi.|<xref:System.Windows.Controls.Primitives.Popup>sol üst köşesi.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>|Yok. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> yoksayıldı.|Fare işaretçisinin sınırları. <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> yoksayıldı.|Hedef alanın sol üst köşesi.|<xref:System.Windows.Controls.Primitives.Popup>sol üst köşesi.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> veya üst.|Hedef nesne veya ayarlandıysa <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, hedef nesneye göredir.|Hedef alanın sol üst köşesi.|<xref:System.Windows.Controls.Primitives.Popup>sol üst köşesi.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> veya üst.|Hedef nesne veya ayarlandıysa <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, hedef nesneye göredir.|Hedef alanın sol üst köşesi.|<xref:System.Windows.Controls.Primitives.Popup>sol üst köşesi.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Right>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> veya üst.|Hedef nesne veya ayarlandıysa <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, hedef nesneye göredir.|Hedef alanın sağ üst köşesi.|<xref:System.Windows.Controls.Primitives.Popup>sol üst köşesi.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Top>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> veya üst.|Hedef nesne veya ayarlandıysa <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, hedef nesneye göredir.|Hedef alanın sol üst köşesi.|<xref:System.Windows.Controls.Primitives.Popup>sol alt köşesi.|  
  
 Aşağıdaki çizimler her bir <xref:System.Windows.Controls.Primitives.PlacementMode> değeri için <xref:System.Windows.Controls.Primitives.Popup>, hedef alanı, hedef kaynak ve açılan pencere hizalama noktasını gösterir. Her bir şekilde, hedef alan sarı ve <xref:System.Windows.Controls.Primitives.Popup> mavi olur.  
  
 ![Mutlak veya AbsolutePoint yerleşimi olan açılan pencere](./media/popup-placement-behavior/popup-placement-absolute.png "Yerleştirme mutlak veya AbsolutePoint.")    
  
 ![Alt yerleştirme ile açılan pencere](./media/popup-placement-behavior/popup-placement-bottom.png "Yerleştirme alt.")   
  
 ![Orta yerleşimi olan açılan pencere](./media/popup-placement-behavior/popup-placement-center.png "Yerleştirme merkezdir.")    
  
 ![Sol yerleştirme içeren açılan pencere](./media/popup-placement-behavior/popup-placement-left.png "Yerleştirme bırakılır.")   
  
 ![Fare yerleştirme ile açılan pencere](./media/popup-placement-behavior/popup-placement-mouse.png "Yerleştirme fare.")  
  
 ![MousePoint yerleşimi ile açılan pencere](./media/popup-placement-behavior/popup-placement-mousepoint.png "Yerleştirme MousePoint.")  
  
 ![Göreli veya RelativePoint yerleşimi olan açılan pencere](./media/popup-placement-behavior/popup-placement-relative.png "Yerleştirme göreli veya RelativePoint.")    
  
 ![Sağ yerleştirme ile açılan pencere](./media/popup-placement-behavior/popup-placement-right.png "Yerleşim doğru.")    
  
 ![Üst yerleştirme ile açılan pencere](./media/popup-placement-behavior/popup-placement-top.png "Yerleştirme en üst.")    
  
<a name="When"></a>   
## <a name="when-the-popup-encounters-the-edge-of-the-screen"></a>Açılan pencere ekranın kenarına karşılaştığında  
 Güvenlik nedenleriyle, bir <xref:System.Windows.Controls.Primitives.Popup> ekranın kenarıyla gizlenemez. <xref:System.Windows.Controls.Primitives.Popup> bir ekran kenarıyla karşılaştığında aşağıdaki üç şeyin biri gerçekleşir:  
  
- Açılan pencere, <xref:System.Windows.Controls.Primitives.Popup>gizleyebilecek ekran kenarı üzerinde kendisini yeniden hizalar.  
  
- Açılan pencere, farklı bir açılan hizalama noktası kullanır.  
  
- Açılan pencere, farklı bir hedef kaynağı ve açılan hizalama noktası kullanır.  
  
 Bu seçenekler daha sonra bu bölümün ilerleyen kısımlarında açıklanmıştır.  
  
 Bir ekran kenarıyla karşılaştığında <xref:System.Windows.Controls.Primitives.Popup> davranışı, <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> özelliğinin değerine ve açılan pencerenin karşılaştığı ekran kenarına bağlıdır. Aşağıdaki tabloda, <xref:System.Windows.Controls.Primitives.Popup> her <xref:System.Windows.Controls.Primitives.PlacementMode> değeri için bir ekran kenarıyla karşılaştığında oluşan davranış özetlenmektedir.  
  
|PlacementMode|Üst kenar|Alt kenar|Sol kenar|Sağ kenar|  
|-------------------|--------------|-----------------|---------------|----------------|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>|Üst kenara hizalanır.|Alt kenara hizalanır.|Sol kenara hizalanır.|Sağ kenara hizalanır.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>|Üst kenara hizalanır.|Açılır hizalama noktası <xref:System.Windows.Controls.Primitives.Popup>sol alt köşesine dönüşür.|Sol kenara hizalanır.|Açılır hizalama noktası <xref:System.Windows.Controls.Primitives.Popup>sağ üst köşesine değişir.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>|Üst kenara hizalanır.|Hedef kaynak, hedef alanın sol üst köşesinde değişir ve açılan hizalama noktası <xref:System.Windows.Controls.Primitives.Popup>sol alt köşesine değişir.|Sol kenara hizalanır.|Sağ kenara hizalanır.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Center>|Üst kenara hizalanır.|Alt kenara hizalanır.|Sol kenara hizalanır.|Sağ kenara hizalanır.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Left>|Üst kenara hizalanır.|Alt kenara hizalanır.|Hedef kaynak, hedef alanın sağ üst köşesinde değişir ve açılan hizalama noktası <xref:System.Windows.Controls.Primitives.Popup>sol üst köşesine değişir.|Sağ kenara hizalanır.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>|Üst kenara hizalanır.|Hedef kaynak, hedef alanın sol üst köşesine (fare işaretçisinin sınırları), açılan hizalama noktası ise <xref:System.Windows.Controls.Primitives.Popup>sol alt köşesine değişir.|Sol kenara hizalanır.|Sağ kenara hizalanır.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>|Üst kenara hizalanır.|Açılır hizalama noktası <xref:System.Windows.Controls.Primitives.Popup>sol alt köşesine dönüşür.|Sol kenara hizalanır.|Açılan pencere hizalama noktası, açılan pencerenin sağ üst köşesine dönüşür.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>|Üst kenara hizalanır.|Alt kenara hizalanır.|Sol kenara hizalanır.|Sağ kenara hizalanır.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>|Üst kenara hizalanır.|Açılır hizalama noktası <xref:System.Windows.Controls.Primitives.Popup>sol alt köşesine dönüşür.|Sol kenara hizalanır.|Açılan pencere hizalama noktası, açılan pencerenin sağ üst köşesine dönüşür.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Right>|Üst kenara hizalanır.|Alt kenara hizalanır.|Sol kenara hizalanır.|Hedef kaynak, hedef alanın sol üst köşesinde değişir ve açılan hizalama noktası <xref:System.Windows.Controls.Primitives.Popup>sağ üst köşesine değişir.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Top>|Hedef kaynak, hedef alanın sol alt köşesinde değişir ve açılan hizalama noktası <xref:System.Windows.Controls.Primitives.Popup>sol üst köşesine değişir. Bu, <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>ile aynıdır.|Alt kenara hizalanır.|Sol kenara hizalanır.|Sağ kenara hizalanır.|  
  
### <a name="aligning-to-the-screen-edge"></a>Ekran kenarına hizalama  
 <xref:System.Windows.Controls.Primitives.Popup>, ekranın kenarına, tüm <xref:System.Windows.Controls.Primitives.Popup> ekranda görünür olacak şekilde yeniden konumlandırarak hizalayabilirsiniz.  Bu gerçekleştiğinde, hedef kaynak ve açılan hizalama noktası arasındaki mesafe <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> ve <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>değerlerinden farklı olur. <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>, <xref:System.Windows.Controls.Primitives.PlacementMode.Center>veya <xref:System.Windows.Controls.Primitives.PlacementMode.Relative>olduğunda, <xref:System.Windows.Controls.Primitives.Popup> kendisini her ekran kenarına hizalar.  Örneğin, bir <xref:System.Windows.Controls.Primitives.Popup> <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Relative> olarak ayarlandığını ve <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> 100 olarak ayarlandığını varsayalım.  Ekranın alt kenarı <xref:System.Windows.Controls.Primitives.Popup>tümünü veya bir kısmını gizliyorsanız, <xref:System.Windows.Controls.Primitives.Popup>, ekranın alt kenarı ve hedef kaynak ile açılan hizalama noktası arasındaki dikey uzaklık 100 ' den az olur. Aşağıdaki çizimde bu gösterilmektedir.  
  
 ![Ekranın kenarına hizalanan açılan pencere](./media/popup-placement-behavior/popup-placement-relative-screen-edge.png "Açılan pencere, ekranın kenarına hizalanır.")    
  
### <a name="changing-the-popup-alignment-point"></a>Açılır hizalama noktasını değiştirme  
 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>, <xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>veya <xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>ise, açılan pencere aşağı doğru veya sağ ekran kenarıyla karşılaştığında açılır hizalama noktası değişir.  
  
 Aşağıdaki çizim, alt ekran kenarı <xref:System.Windows.Controls.Primitives.Popup>tümünü veya bir kısmını gizlediğini, açılan hizalama noktasının <xref:System.Windows.Controls.Primitives.Popup>sol alt köşesinin olduğunu gösterir.  
  
 ![Alt ekran kenarından kaynaklanan yeni hizalama noktası](./media/popup-placement-behavior/popup-placement-relative-point-screen-edge.png "Açılan pencere, ekranın alt kenarına rastlamaları ve açılan hizalama noktasını değiştirir.")  

 Aşağıdaki çizimde, <xref:System.Windows.Controls.Primitives.Popup> doğru ekran kenarından gizlendiği zaman, açılan pencere hizalama noktası <xref:System.Windows.Controls.Primitives.Popup>sağ üst köşesidir.  
  
 ![Ekran kenarından kaynaklanan yeni açılan hizalama noktası](./media/popup-placement-behavior/popup-placement-relative-point-right-screen-edge.png "Açılan pencere, ekranın sağ kenarına rast, açılan hizalama noktasını değiştiriyor.")    
  
 <xref:System.Windows.Controls.Primitives.Popup>, alt ve sağ ekran kenarları ile karşılaşırsa, açılan hizalama noktası, <xref:System.Windows.Controls.Primitives.Popup>sağ alt köşesidir.  
  
### <a name="changing-the-target-origin-and-popup-alignment-point"></a>Hedef kaynak ve açılan hizalama noktasını değiştirme  
 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>, <xref:System.Windows.Controls.Primitives.PlacementMode.Left>, <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>, <xref:System.Windows.Controls.Primitives.PlacementMode.Right>veya <xref:System.Windows.Controls.Primitives.PlacementMode.Top>olduğunda, belirli bir ekran kenarıyla karşılaşılırsa hedef kaynak ve açılır hizalama noktası değişir.  Konumun değişmesine neden olan ekran kenarı <xref:System.Windows.Controls.Primitives.PlacementMode> değerine bağlıdır.  
  
 Aşağıdaki çizimde, <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom> ve <xref:System.Windows.Controls.Primitives.Popup> alt ekran kenarıyla karşılaştığında, hedef kaynak hedef alanın sol üst köşesidir ve açılan hizalama noktası, <xref:System.Windows.Controls.Primitives.Popup>sol alt köşesidir.  
  
 ![Alt ekran kenarından kaynaklanan yeni hizalama noktası](./media/popup-placement-behavior/popup-placement-bottom-screen-edge.png "Yerleştirme en alttan ve açılan pencere ekranın alt kenarıyla karşılaştığında.")    
  
 Aşağıdaki çizimde <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Left> ve <xref:System.Windows.Controls.Primitives.Popup> sol ekran kenarından karşılaştığında, hedef kaynak hedef alanın sağ üst köşesidir ve açılan hizalama noktası, <xref:System.Windows.Controls.Primitives.Popup>sol üst köşesindedir.  
  
 ![Sol ekran kenarından kaynaklanan yeni hizalama noktası](./media/popup-placement-behavior/popup-placement-left-screen-edge.png "Yerleştirme bırakılır ve açılan pencere ekranın sol kenarıyla karşılaşır.")  
  
 Aşağıdaki çizimde <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Right> ve <xref:System.Windows.Controls.Primitives.Popup> doğru ekran kenarıyla karşılaştığında, hedef kaynak hedef alanın sol üst köşesidir ve açılan hizalama noktası, <xref:System.Windows.Controls.Primitives.Popup>sağ üst köşesidir.  
  
 ![Sağ ekran kenarından kaynaklanan yeni hizalama noktası](./media/popup-placement-behavior/popup-placement-right-screen-edge.png "Yerleştirme hakkına sahiptir ve açılan pencere ekranın sağ kenarıyla karşılaşır.")  

 Aşağıdaki çizimde, <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Top> ve <xref:System.Windows.Controls.Primitives.Popup> üst ekran kenarıyla karşılaştığında, hedef kaynak hedef alanın sol alt köşesidir ve açılan hizalama noktası, <xref:System.Windows.Controls.Primitives.Popup>sol üst köşesindedir.  
  
 ![Üst ekran kenarından kaynaklanan yeni hizalama noktası](./media/popup-placement-behavior/popup-placement-top-screen-edge.png "Yerleştirme üst ve açılan pencere ekranın üst kenarıyla karşılaştığında.")  
  
 Aşağıdaki çizimde <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse> ve <xref:System.Windows.Controls.Primitives.Popup> alt ekran kenarından karşılaştığında, hedef kaynak hedef alanın sol üst köşesidir (fare işaretçisinin sınırları) ve açılan hizalama noktası <xref:System.Windows.Controls.Primitives.Popup>sol alt köşe.  
  
 ![fare yakınında ekranın yakınında yeni hizalama noktası](./media/popup-placement-behavior/popup-placement-mouse-screen-edge.png "Yerleştirme, fare ve açılan pencere ekranın alt kenarı ile karşılaşır.")    
  
### <a name="customizing-popup-placement"></a>Açılan pencere yerleşimini özelleştirme  
 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> özelliğini <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>olarak ayarlayarak hedef kaynak ve açılır hizalama noktasını özelleştirebilirsiniz. Ardından, <xref:System.Windows.Controls.Primitives.Popup>için olası bir yerleştirme noktaları kümesi ve birincil eksenler (tercih sırasına göre) döndüren bir <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> temsilcisi tanımlayın. <xref:System.Windows.Controls.Primitives.Popup> en büyük kısmını gösteren nokta seçilidir.  <xref:System.Windows.Controls.Primitives.Popup> konumu, <xref:System.Windows.Controls.Primitives.Popup> ekranın kenarıyla gizlenmişse otomatik olarak ayarlanır. Bir örnek için bkz. [özel bir açılan pencere konumu belirtme](how-to-specify-a-custom-popup-position.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Açılan pencere yerleştirme örneği](https://github.com/dotnet/samples/tree/master/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS)
