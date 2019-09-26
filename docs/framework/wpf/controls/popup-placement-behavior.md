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
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2019
ms.locfileid: "69951729"
---
# <a name="popup-placement-behavior"></a>Açılan Pencere Yerleştirme Davranışı
Bir <xref:System.Windows.Controls.Primitives.Popup> denetim, içeriği bir uygulama üzerinde gezinen ayrı bir pencerede görüntüler. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>, <xref:System.Windows.Controls.Primitives.Popup> ,,<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>Ve özelliklerinikullanarakbirdenetim,fareveyaekraniçingörelikonumunubelirtebilirsiniz.<xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>  Bu özellikler birlikte çalışarak, <xref:System.Windows.Controls.Primitives.Popup>konumunu belirtirken esneklik sağlar.  
  
> [!NOTE]
> <xref:System.Windows.Controls.ToolTip> Ve<xref:System.Windows.Controls.ContextMenu> sınıfları bu beş özelliği de tanımlar ve benzer şekilde davranır.  

<a name="Positioning"></a>   
## <a name="positioning-the-popup"></a>Açılan pencereyi konumlandırma  
 Öğesinin <xref:System.Windows.Controls.Primitives.Popup> yerleşimi bir <xref:System.Windows.UIElement> veya ekranın tamamına göre olabilir.  Aşağıdaki örnek, bir resim <xref:System.Windows.Controls.Primitives.Popup> olan (Bu örnekte bir <xref:System.Windows.UIElement>görüntü) ile ilgili dört denetimi oluşturur. <xref:System.Windows.Controls.Primitives.Popup> Tüm denetimlerin <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> özelliği <xref:System.Windows.Controls.Primitives.Popup> olarak `image1`ayarlanmış, ancak her biri yerleştirme özelliği için farklı bir değere sahip.  
  
 [!code-xaml[PopupPositionSnippet#3](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#3)]  
  
 Aşağıdaki çizimde resim ve <xref:System.Windows.Controls.Primitives.Popup> denetimler gösterilmektedir  
  
 ![Dört açılan menü denetimi Içeren resim](./media/popup-placement-behavior/popup-placement-intro.png "Dört açıya sahip resim")    
  
 Bu basit örnek, <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> ve <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> özelliklerinin nasıl ayarlanacağını gösterir <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, ancak, <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>, <xref:System.Windows.Controls.Primitives.Popup> ve <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> özelliklerini kullanarak nerede konumlandığını daha da fazla kontrol edersiniz.  
  
<a name="Definitions"></a>   
## <a name="definitions-of-terms-the-anatomy-of-a-popup"></a>Koşulların tanımları: Açılan pencerenin Anatomumu  
 Aşağıdaki terimler,,, <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>, ve <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> <xref:System.Windows.Controls.Primitives.Popup> <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> özelliklerininbirbirleriyle<xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> ve ile ilişkisini anlamak için yararlıdır:  
  
- Hedef nesne  
  
- Hedef alan  
  
- Hedef kaynak  
  
- Açılan pencere hizalama noktası  
  
 Bu terimler, <xref:System.Windows.Controls.Primitives.Popup> ve ile ilişkili olduğu denetimin çeşitli yönlerini belirtmek için kullanışlı bir yol sağlar.  
  
### <a name="target-object"></a>Hedef nesne  
 *Hedef nesne* , ilişkili olduğu öğesidir <xref:System.Windows.Controls.Primitives.Popup> . <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> Özellik ayarlandıysa, hedef nesneyi belirtir.  <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> Ayarlanmamışsa<xref:System.Windows.Controls.Primitives.Popup> ve bir üst öğesi varsa, üst öğe hedef nesnedir.  Hiçbir değer yoksa ve üst öğe yoksa, hedef nesne yoktur <xref:System.Windows.Controls.Primitives.Popup> ve ekrana göre konumlandırılır. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>  
  
 Aşağıdaki örnek, <xref:System.Windows.Controls.Canvas>öğesinin alt <xref:System.Windows.Controls.Primitives.Popup> öğesi olan bir oluşturur.  Örnek <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> ,<xref:System.Windows.Controls.Primitives.Popup>üzerinde özelliğini yapmaz. İçin <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> varsayılan<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom?displayProperty=nameWithType>değer, bu <xref:System.Windows.Controls.Primitives.Popup> nedenlealtındagörünür.<xref:System.Windows.Controls.Canvas>  
  
 [!code-xaml[PopupPositionSnippet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#1)]  
  
 Aşağıdaki çizim, ' <xref:System.Windows.Controls.Primitives.Popup> nin <xref:System.Windows.Controls.Canvas>öğesine göre konumlandırıldığını gösterir.  
  
 ![PlacementTarget Içermeyen Popup denetimi](./media/popup-placement-behavior/popup-placement-no-placement-target.png "PlacementTarget Içermeyen açılan pencere.")  

 Aşağıdaki örnek, <xref:System.Windows.Controls.Canvas>öğesinin alt <xref:System.Windows.Controls.Primitives.Popup> öğesi olan bir oluşturur, ancak bu kez <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> <xref:System.Windows.Shapes.Ellipse>olarak `ellipse1`ayarlandığında, açılan pencerenin altında görünür.  
  
 [!code-xaml[PopupPositionSnippet#2](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#2)]  
  
 Aşağıdaki çizim, ' <xref:System.Windows.Controls.Primitives.Popup> nin <xref:System.Windows.Shapes.Ellipse>öğesine göre konumlandırıldığını gösterir.  
  
 ![Bir elips 'e göre konumlandırılmış açılan pencere](./media/popup-placement-behavior/popup-placement-with-placement-target.png "PlacementTarget Ile açılan pencere")    
  
> [!NOTE]
> İçin <xref:System.Windows.Controls.ToolTip>, varsayılan <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> değeri. <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>  İçin <xref:System.Windows.Controls.ContextMenu>, varsayılan <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> değeri. <xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint> Bu değerler daha sonra, "özellikler birlikte nasıl çalışır." bölümünde açıklanmaktadır.  
  
### <a name="target-area"></a>Hedef alan  
 *Hedef alan* , ekranda göreli olarak görüntülenen <xref:System.Windows.Controls.Primitives.Popup> alandır. Önceki örneklerde,, <xref:System.Windows.Controls.Primitives.Popup> hedef nesnenin sınırlarına hizalanır, ancak bazı durumlarda <xref:System.Windows.Controls.Primitives.Popup> , bir hedef nesnesine <xref:System.Windows.Controls.Primitives.Popup> sahip olsa bile diğer sınırlara hizalanır.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Özellik ayarlandıysa, hedef alan hedef nesnenin limitinden farklıdır.  
  
 Aşağıdaki örnek, her biri <xref:System.Windows.Controls.Canvas> <xref:System.Windows.Shapes.Rectangle> ve <xref:System.Windows.Controls.Primitives.Popup>içeren iki nesne oluşturur.  Her iki durumda da için <xref:System.Windows.Controls.Primitives.Popup> hedef nesnesi <xref:System.Windows.Controls.Canvas>olur. <xref:System.Windows.Controls.Canvas> <xref:System.Windows.Rect.Y%2A> <xref:System.Windows.Rect.Width%2A> İçindekiiçindeki<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> içinde,,, <xref:System.Windows.Rect.X%2A> ve<xref:System.Windows.Rect.Height%2A> özellikleri sırasıyla 50, 50, 50 ve 100 olarak ayarlanmış olarak ayarlanmıştır. <xref:System.Windows.Controls.Primitives.Popup> <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> İkinci <xref:System.Windows.Controls.Primitives.Popup> öğesinde<xref:System.Windows.Controls.Canvas> , kümesi yoktur.  <xref:System.Windows.Controls.Primitives.Popup> Sonuç olarak, ilki <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> altına yerleştirilir ve <xref:System.Windows.Controls.Canvas>ikincisi <xref:System.Windows.Controls.Primitives.Popup> altına yerleştirilir. Her <xref:System.Windows.Controls.Canvas> biri, ilki <xref:System.Windows.Shapes.Rectangle> içinaynı<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> sınırlara sahip bir içerir. <xref:System.Windows.Controls.Primitives.Popup>  Uygulamasının uygulamada görünür bir öğe oluşturmadığını unutmayın; örnek öğesini temsil <xref:System.Windows.Shapes.Rectangle> <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>edecek şekilde oluşturur. <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>  
  
 [!code-xaml[PopupPositionSnippet#4](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#4)]  
  
 Aşağıdaki çizimde, önceki örneğin sonucu gösterilmektedir.  
  
 ![PlacementRectangle içeren ve Içermeyen açılan pencere](./media/popup-placement-behavior/popup-placement-placement-rectangle.png "PlacementRectangle içeren ve Içermeyen açılan pencere.")  

### <a name="target-origin-and-popup-alignment-point"></a>Hedef kaynak ve açılan hizalama noktası  
 *Hedef kaynak* ve *açılan pencere hizalama noktası* , konumlandırma için kullanılan, sırasıyla hedef alandaki ve açılan pencerede bulunan başvuru noktalarıdır. Açılan menüyü hedef alandan <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> kaydırmak <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> için ve özelliklerini kullanabilirsiniz.  <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> Ve<xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> , hedef kaynağa ve açılan hizalama noktasına göre değişir. <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> Özelliğin değeri, hedef kaynak ve açılan hizalama noktasının nerede olduğunu belirler.  
  
 Aşağıdaki örnek bir <xref:System.Windows.Controls.Primitives.Popup> oluşturur ve <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> ve <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> özelliklerini 20 olarak ayarlar.  Özelliği olarak <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom> ayarlanır (varsayılan), bu nedenle hedef kaynak hedef alanın sol alt köşesidir ve açılan hizalama noktası, <xref:System.Windows.Controls.Primitives.Popup>öğesinin sol üst köşesindedir. <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>  
  
 [!code-xaml[PopupPositionSnippet#5](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#5)]  
  
 Aşağıdaki çizimde, önceki örneğin sonucu gösterilmektedir.  
  
 ![Hedef kaynak hizalama noktasıyla açılan pencere yerleşimi](./media/popup-placement-behavior/popup-placement-target-origin-alignment-point.png "Horizontalkayması ve verticalkayması Içeren açılan pencere.")    
  
<a name="How"></a>   
## <a name="how-the-properties-work-together"></a>Özelliklerin birlikte çalışması  
 , Ve <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> değerlerinin<xref:System.Windows.Controls.Primitives.Popup.Placement%2A> doğru hedef alanı, hedef kaynağı ve açılan hizalama noktasını anlamak için birlikte değerlendirilmesi gerekir. <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>  Örneğin, değeri <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> ise <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>, hedef nesne <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> yoktur, yok sayılır ve hedef alan fare işaretçisinin sınırları olur. Diğer taraftan <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> , ise <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom> <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> , veya üst öğesi hedef nesneyi belirler ve <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> hedef alanı belirler.  
  
 Aşağıdaki tabloda hedef nesne, hedef alanı, hedef kaynağı ve açılır hizalama noktası açıklanmakta ve her <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> <xref:System.Windows.Controls.Primitives.PlacementMode> bir numaralandırma değeri için ve <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> kullanılıp kullanılmayacağını gösterir.  
  
|PlacementMode|Hedef nesne|Hedef alan|Hedef kaynak|Açılan pencere hizalama noktası|  
|-------------------|-------------------|-----------------|-------------------|---------------------------|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>|Geçerli değildir. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>yok sayılır.|Ekran veya <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> ayarlanmış ise.  , <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Ekrana göredir.|Hedef alanın sol üst köşesi.|Öğesinin sol üst köşesi <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>|Geçerli değildir. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>yok sayılır.|Ekran veya <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> ayarlanmış ise.  , <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Ekrana göredir.|Hedef alanın sol üst köşesi.|Öğesinin sol üst köşesi <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>ya da üst.|Hedef nesne veya <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> ayarlandıysa.  , <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Hedef nesnesine görelidir.|Hedef alanın sol alt köşesi.|Öğesinin sol üst köşesi <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Center>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>ya da üst.|Hedef nesne veya <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> ayarlandıysa.  , <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Hedef nesnesine görelidir.|Hedef alanın merkezi.|Merkezinin merkezi <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>ya da üst.|Hedef nesne veya <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> ayarlandıysa.  , <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Hedef nesnesine görelidir.|Tarafından <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>tanımlanır.|Tarafından <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>tanımlanır.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Left>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>ya da üst.|Hedef nesne veya <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> ayarlandıysa.  , <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Hedef nesnesine görelidir.|Hedef alanın sol üst köşesi.|Öğesinin sağ üst köşesi <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>|Geçerli değildir. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>yok sayılır.|Fare işaretçisinin sınırları. <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>yok sayılır.|Hedef alanın sol alt köşesi.|Öğesinin sol üst köşesi <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>|Geçerli değildir. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>yok sayılır.|Fare işaretçisinin sınırları. <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>yok sayılır.|Hedef alanın sol üst köşesi.|Öğesinin sol üst köşesi <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>ya da üst.|Hedef nesne veya <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> ayarlandıysa.  , <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Hedef nesnesine görelidir.|Hedef alanın sol üst köşesi.|Öğesinin sol üst köşesi <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>ya da üst.|Hedef nesne veya <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> ayarlandıysa.  , <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Hedef nesnesine görelidir.|Hedef alanın sol üst köşesi.|Öğesinin sol üst köşesi <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Right>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>ya da üst.|Hedef nesne veya <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> ayarlandıysa.  , <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Hedef nesnesine görelidir.|Hedef alanın sağ üst köşesi.|Öğesinin sol üst köşesi <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Top>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>ya da üst.|Hedef nesne veya <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> ayarlandıysa.  , <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Hedef nesnesine görelidir.|Hedef alanın sol üst köşesi.|Öğesinin sol alt köşesi <xref:System.Windows.Controls.Primitives.Popup>.|  
  
 Aşağıdaki çizimler her <xref:System.Windows.Controls.Primitives.PlacementMode> bir değer <xref:System.Windows.Controls.Primitives.Popup>için, hedef alanı, hedef kaynak ve açılan hizalama noktasını gösterir. Her bir şekilde, hedef alan sarı olur ve <xref:System.Windows.Controls.Primitives.Popup> mavi olur.  
  
 ![Mutlak veya AbsolutePoint yerleşimi olan açılan pencere](./media/popup-placement-behavior/popup-placement-absolute.png "Yerleştirme mutlak veya AbsolutePoint.")    
  
 ![Alt yerleştirme Ile açılan pencere](./media/popup-placement-behavior/popup-placement-bottom.png "Yerleştirme alt.")   
  
 ![Orta yerleşimi olan açılan pencere](./media/popup-placement-behavior/popup-placement-center.png "Yerleştirme merkezdir.")    
  
 ![Sol yerleştirme Içeren açılan pencere](./media/popup-placement-behavior/popup-placement-left.png "Yerleştirme bırakılır.")   
  
 ![Fare yerleştirme Ile açılan pencere](./media/popup-placement-behavior/popup-placement-mouse.png "Yerleştirme fare.")  
  
 ![MousePoint yerleşimi Ile açılan pencere](./media/popup-placement-behavior/popup-placement-mousepoint.png "Yerleştirme MousePoint.")  
  
 ![Göreli veya RelativePoint yerleşimi olan açılan pencere](./media/popup-placement-behavior/popup-placement-relative.png "Yerleştirme göreli veya RelativePoint.")    
  
 ![Sağ yerleştirme Ile açılan pencere](./media/popup-placement-behavior/popup-placement-right.png "Yerleşim doğru.")    
  
 ![Üst yerleştirme Ile açılan pencere](./media/popup-placement-behavior/popup-placement-top.png "Yerleştirme en üst.")    
  
<a name="When"></a>   
## <a name="when-the-popup-encounters-the-edge-of-the-screen"></a>Açılan pencere ekranın kenarına karşılaştığında  
 Güvenlik nedenleriyle, bir <xref:System.Windows.Controls.Primitives.Popup> ekranın kenarına göre gizlenemez. Aşağıdaki üç şeyin bir ekran kenarıyla <xref:System.Windows.Controls.Primitives.Popup> karşılaştığında meydana gelir:  
  
- Açılan pencere, kendisini gizleyebilecek <xref:System.Windows.Controls.Primitives.Popup>ekran kenarı üzerinde yeniden hizalar.  
  
- Açılan pencere, farklı bir açılan hizalama noktası kullanır.  
  
- Açılan pencere, farklı bir hedef kaynağı ve açılan hizalama noktası kullanır.  
  
 Bu seçenekler daha sonra bu bölümün ilerleyen kısımlarında açıklanmıştır.  
  
 Bir ekran kenarıyla karşılaştığında <xref:System.Windows.Controls.Primitives.Popup> , <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> özelliğinin değerine ve açılan pencerenin karşılaştığı ekran kenarına bağlıdır. Aşağıdaki tabloda, <xref:System.Windows.Controls.Primitives.Popup> her <xref:System.Windows.Controls.Primitives.PlacementMode> bir değer için bir ekran kenarı karşılaştığı zaman davranış özetlenmektedir.  
  
|PlacementMode|Üst kenar|Alt kenar|Sol kenar|Sağ kenar|  
|-------------------|--------------|-----------------|---------------|----------------|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>|Üst kenara hizalanır.|Alt kenara hizalanır.|Sol kenara hizalanır.|Sağ kenara hizalanır.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>|Üst kenara hizalanır.|Açılan pencere hizalama noktası, <xref:System.Windows.Controls.Primitives.Popup>öğesinin sol alt köşesine dönüşür.|Sol kenara hizalanır.|Açılan hizalama noktası, <xref:System.Windows.Controls.Primitives.Popup>sağ üst köşesine dönüşür.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>|Üst kenara hizalanır.|Hedef kaynak, hedef alanın sol üst köşesinde değişir ve açılan hizalama noktası, <xref:System.Windows.Controls.Primitives.Popup>öğesinin sol alt köşesine dönüşür.|Sol kenara hizalanır.|Sağ kenara hizalanır.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Center>|Üst kenara hizalanır.|Alt kenara hizalanır.|Sol kenara hizalanır.|Sağ kenara hizalanır.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Left>|Üst kenara hizalanır.|Alt kenara hizalanır.|Hedef kaynak, hedef alanın sağ üst köşesine değişir ve açılan hizalama noktası, <xref:System.Windows.Controls.Primitives.Popup>öğesinin sol üst köşesine dönüşür.|Sağ kenara hizalanır.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>|Üst kenara hizalanır.|Hedef kaynak, hedef alanın sol üst köşesine (fare işaretçisinin sınırları) ve açılan hizalama noktasının sol alt köşesine <xref:System.Windows.Controls.Primitives.Popup>değişir.|Sol kenara hizalanır.|Sağ kenara hizalanır.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>|Üst kenara hizalanır.|Açılan pencere hizalama noktası, <xref:System.Windows.Controls.Primitives.Popup>öğesinin sol alt köşesine dönüşür.|Sol kenara hizalanır.|Açılan pencere hizalama noktası, açılan pencerenin sağ üst köşesine dönüşür.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>|Üst kenara hizalanır.|Alt kenara hizalanır.|Sol kenara hizalanır.|Sağ kenara hizalanır.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>|Üst kenara hizalanır.|Açılan pencere hizalama noktası, <xref:System.Windows.Controls.Primitives.Popup>öğesinin sol alt köşesine dönüşür.|Sol kenara hizalanır.|Açılan pencere hizalama noktası, açılan pencerenin sağ üst köşesine dönüşür.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Right>|Üst kenara hizalanır.|Alt kenara hizalanır.|Sol kenara hizalanır.|Hedef kaynak, hedef alanın sol üst köşesinde değişir ve açılan hizalama noktası, <xref:System.Windows.Controls.Primitives.Popup>sağ üst köşesine dönüşür.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Top>|Hedef kaynak, hedef alanın sol alt köşesine değişir ve açılan hizalama noktası, <xref:System.Windows.Controls.Primitives.Popup>öğesinin sol üst köşesine dönüşür. Aslında bu, <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> olduğu <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>gibi aynıdır.|Alt kenara hizalanır.|Sol kenara hizalanır.|Sağ kenara hizalanır.|  
  
### <a name="aligning-to-the-screen-edge"></a>Ekran kenarına hizalama  
 Bir <xref:System.Windows.Controls.Primitives.Popup> , ekranın kenarına, tüm <xref:System.Windows.Controls.Primitives.Popup> ekranda görünür olacak şekilde yeniden konumlandırarak, ekranın kenarına hizalanır.  Bu gerçekleştiğinde, hedef kaynak ve açılan hizalama noktası arasındaki mesafe <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> ve <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>değerlerinden farklı olur. ,Veyaolduğunda<xref:System.Windows.Controls.Primitives.Popup.Placement%2A> ,, ya<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>da, kendisini her ekran kenarına hizalar.<xref:System.Windows.Controls.Primitives.Popup> <xref:System.Windows.Controls.Primitives.PlacementMode.Center> <xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>  Örneğin, bir <xref:System.Windows.Controls.Primitives.Popup> öğesinin <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> olarak <xref:System.Windows.Controls.Primitives.PlacementMode.Relative> ayarlandığını ve <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> 100 olarak ayarlandığını varsayalım.  Ekranın alt kenarı öğesinin tümünü veya bir <xref:System.Windows.Controls.Primitives.Popup>kısmını gizliyorsanız <xref:System.Windows.Controls.Primitives.Popup> , bu, ekranın alt kenarı ve hedef kaynak ile açılan hizalama noktası arasındaki dikey uzaklık 100 ' den az olur. Aşağıdaki çizimde bu gösterilmektedir.  
  
 ![Ekranın kenarına hizalanan açılan pencere](./media/popup-placement-behavior/popup-placement-relative-screen-edge.png "Açılan pencere, ekranın kenarına hizalanır.")    
  
### <a name="changing-the-popup-alignment-point"></a>Açılır hizalama noktasını değiştirme  
 , Veya <xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint> ise,<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>açılan pencere, alt veya sağ ekran kenarıyla karşılaştığında açılır hizalama noktası değişir. <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>  
  
 Aşağıdaki çizim, alt ekran kenarı öğesinin tamamını veya bir <xref:System.Windows.Controls.Primitives.Popup>kısmını gizlediğini, açılan hizalama noktasının <xref:System.Windows.Controls.Primitives.Popup>öğesinin sol alt köşesinin olduğunu gösterir.  
  
 ![Alt ekran kenarından kaynaklanan yeni hizalama noktası](./media/popup-placement-behavior/popup-placement-relative-point-screen-edge.png "Açılan pencere, ekranın alt kenarına rastlamaları ve açılan hizalama noktasını değiştirir.")  

 Aşağıdaki çizimde, doğru ekran kenarı tarafından <xref:System.Windows.Controls.Primitives.Popup> gizlendiği zaman, açılan pencere hizalama noktası, <xref:System.Windows.Controls.Primitives.Popup>öğesinin sağ üst köşesidir.  
  
 ![Ekran kenarından kaynaklanan yeni açılan hizalama noktası](./media/popup-placement-behavior/popup-placement-relative-point-right-screen-edge.png "Açılan pencere, ekranın sağ kenarına rast, açılan hizalama noktasını değiştiriyor.")    
  
 Alt ve sağ ekran kenarları ile <xref:System.Windows.Controls.Primitives.Popup> karşılaştığında,açılanhizalamanoktası,sağaltköşesindedir.<xref:System.Windows.Controls.Primitives.Popup>  
  
### <a name="changing-the-target-origin-and-popup-alignment-point"></a>Hedef kaynak ve açılan hizalama noktasını değiştirme  
 ,,,,<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom> Veya<xref:System.Windows.Controls.Primitives.PlacementMode.Top>olduğunda, belirli bir ekran kenarıyla karşılaşılırsa hedef kaynak ve açılan hizalama noktası değişir. <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Left> <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse> <xref:System.Windows.Controls.Primitives.PlacementMode.Right>  Konumun değişmesine neden olan ekran kenarı <xref:System.Windows.Controls.Primitives.PlacementMode> değere bağlıdır.  
  
 Aşağıdaki çizim, ne zaman <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom> ve <xref:System.Windows.Controls.Primitives.Popup> en alttaki ekran kenarından karşılaştığında, hedef kaynak hedef alanın sol üst köşesidir ve açılan hizalama noktası, <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Alt ekran kenarından kaynaklanan yeni hizalama noktası](./media/popup-placement-behavior/popup-placement-bottom-screen-edge.png "Yerleştirme en alttan ve açılan pencere ekranın alt kenarıyla karşılaştığında.")    
  
 Aşağıdaki çizim, ne zaman <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Left> ve <xref:System.Windows.Controls.Primitives.Popup> sol ekran kenarından karşılaştığında, hedef kaynak hedef alanın sağ üst köşesidir ve açılan hizalama noktası, <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Sol ekran kenarından kaynaklanan yeni hizalama noktası](./media/popup-placement-behavior/popup-placement-left-screen-edge.png "Yerleştirme bırakılır ve açılan pencere ekranın sol kenarıyla karşılaşır.")  
  
 Aşağıdaki çizim, ne zaman <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Right> ve <xref:System.Windows.Controls.Primitives.Popup> doğru ekran kenarı ile karşılaştığında, hedef kaynak hedef alanın sol üst köşesidir ve açılan hizalama noktası, <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Sağ ekran kenarından kaynaklanan yeni hizalama noktası](./media/popup-placement-behavior/popup-placement-right-screen-edge.png "Yerleştirme hakkına sahiptir ve açılan pencere ekranın sağ kenarıyla karşılaşır.")  

 Aşağıdaki çizim, ne zaman <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Top> ve <xref:System.Windows.Controls.Primitives.Popup> en üst ekran kenarından karşılaştığında, hedef kaynak hedef alanın sol alt köşesinin, açılan hizalama noktasının ise <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Üst ekran kenarından kaynaklanan yeni hizalama noktası](./media/popup-placement-behavior/popup-placement-top-screen-edge.png "Yerleştirme üst ve açılan pencere ekranın üst kenarıyla karşılaştığında.")  
  
 Aşağıdaki çizim, ne zaman <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse> ve <xref:System.Windows.Controls.Primitives.Popup> en alttaki ekran kenarından karşılaştığında, hedef kaynak hedef alanın sol üst köşesidir (fare işaretçisinin sınırları) ve açılır hizalama nokta, <xref:System.Windows.Controls.Primitives.Popup>öğesinin sol alt köşesindedir.  
  
 ![fare yakınında ekranın yakınında yeni hizalama noktası](./media/popup-placement-behavior/popup-placement-mouse-screen-edge.png "Yerleştirme, fare ve açılan pencere ekranın alt kenarı ile karşılaşır.")    
  
### <a name="customizing-popup-placement"></a>Açılan pencere yerleşimini özelleştirme  
 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> Özelliğini olarak<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>ayarlayarak hedef kaynağı ve açılır hizalama noktasını özelleştirebilirsiniz. Ardından, <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> <xref:System.Windows.Controls.Primitives.Popup>için olası bir yerleştirme noktaları kümesi ve birincil eksenler (tercih sırasına göre) döndüren bir temsilci tanımlayın. Öğesinin <xref:System.Windows.Controls.Primitives.Popup> en büyük bölümünü gösteren nokta seçilidir.  Konumu <xref:System.Windows.Controls.Primitives.Popup> , ekranın kenarıyla gizlenmişse otomatik olarak ayarlanır <xref:System.Windows.Controls.Primitives.Popup> . Bir örnek için bkz. [özel bir açılan pencere konumu belirtme](how-to-specify-a-custom-popup-position.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Açılan pencere yerleştirme örneği](https://github.com/dotnet/samples/tree/master/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS)
