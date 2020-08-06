---
title: Açılan Pencere Yerleştirme Davranışı
description: Özellikleri kullanarak Windows Presentation Foundation açılan penceresinin bir denetime, fareye veya ekrana göre konumunu belirtmeyi öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- popups [WPF]
- Popup control [WPF], placing
- placing popups [WPF]
- positioning popups [WPF]
ms.assetid: fbf642e9-f670-4efd-a7af-a67468a1c8e1
ms.openlocfilehash: 8184805518bc56693ead4c7d1f0e9a1bff9bff8f
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167744"
---
# <a name="popup-placement-behavior"></a>Açılan Pencere Yerleştirme Davranışı
<xref:System.Windows.Controls.Primitives.Popup> denetimi, içeriği uygulamanın üzerinde kayan ayrı bir pencerede görüntüler. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>, <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> ve <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> özelliklerini kullanarak <xref:System.Windows.Controls.Primitives.Popup> nesnesinin bir denetime, fareye veya ekrana göre konumunu belirtebilirsiniz.  Bu özellikler birlikte çalışarak size <xref:System.Windows.Controls.Primitives.Popup> nesnesinin konumunu belirtme esnekliği getirir.  
  
> [!NOTE]
> <xref:System.Windows.Controls.ToolTip> ve <xref:System.Windows.Controls.ContextMenu> sınıfları da bu beş özelliği tanımlar ve benzer şekilde davranır.  

<a name="Positioning"></a>
## <a name="positioning-the-popup"></a>Açılan Pencereyi Konumlandırma  
 <xref:System.Windows.Controls.Primitives.Popup> nesnesi <xref:System.Windows.UIElement> öğesine veya ekranın tamamına göre olarak yerleştirilebilir.  Aşağıdaki örnek bir <xref:System.Windows.UIElement> öğesine (bu örnekte bir resme) göre dört <xref:System.Windows.Controls.Primitives.Popup> denetimi oluşturur. <xref:System.Windows.Controls.Primitives.Popup> denetimlerinin tümünün <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> özelliği `image1` olarak ayarlanmıştır ancak her <xref:System.Windows.Controls.Primitives.Popup>, yerleşim özelliği için farklı bir değere sahiptir.  
  
 [!code-xaml[PopupPositionSnippet#3](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#3)]  
  
 Aşağıdaki şekilde resim ve <xref:System.Windows.Controls.Primitives.Popup> denetimleri gösterilir  
  
 ![Dört açılan pencere denetiminin resmi](./media/popup-placement-behavior/popup-placement-intro.png "Dört açılan pencerenin resmi")
  
 Bu basit örnekte <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> ve <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> özelliklerinin nasıl ayarlanacağı gösterilir ama <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> ve <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> özelliklerini kullanarak <xref:System.Windows.Controls.Primitives.Popup> nesnesinin nerede konumlandırılacağı üzerinde daha da fazla denetim sahibi olursunuz.  
  
<a name="Definitions"></a>
## <a name="definitions-of-terms-the-anatomy-of-a-popup"></a>Terimlerin Tanımı: Açılan Pencerenin Anatomisi  
 Aşağıdaki terimler <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>, <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> ve <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> özelliklerinin birbirleriyle ve <xref:System.Windows.Controls.Primitives.Popup> ile ilişkisini anlamak için yararlıdır:  
  
- Hedef nesne  
  
- Hedef alan  
  
- Hedef başlangıç noktası  
  
- Açılan pencere hizalama noktası  
  
 Bu terimler <xref:System.Windows.Controls.Primitives.Popup> nesnesinin çeşitli yönlerine ve ilişkilendirilmiş olduğu denetimlere başvurmak için kullanışlı bir yol sağlar.  
  
### <a name="target-object"></a>Hedef Nesne  
 *Hedef nesne*, <xref:System.Windows.Controls.Primitives.Popup> nesnesinin ilişkilendirildiği öğedir. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> özelliği ayarlanırsa, hedef nesneyi belirtir.  <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> ayarlanmazsa ve <xref:System.Windows.Controls.Primitives.Popup> nesnesinin bir üst nesnesi varsa, üst nesne hedef nesnedir.  <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> değeri ve üst nesne yoksa hedef nesne de yoktur ve <xref:System.Windows.Controls.Primitives.Popup>, ekrana göre konumlandırılır.  
  
 Aşağıdaki örnek, <xref:System.Windows.Controls.Canvas> nesnesinin alt nesnesi olan bir <xref:System.Windows.Controls.Primitives.Popup> oluşturur.  Örnekte, <xref:System.Windows.Controls.Primitives.Popup> nesnesinde <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> özelliği ayarlanmaz. <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> için varsayılan değer <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom?displayProperty=nameWithType> değeridir, dolayısıyla <xref:System.Windows.Controls.Primitives.Popup>, <xref:System.Windows.Controls.Canvas> nesnesinin altında görüntülenir.  
  
 [!code-xaml[PopupPositionSnippet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#1)]  
  
 Aşağıdaki resimde <xref:System.Windows.Controls.Primitives.Popup> nesnesinin <xref:System.Windows.Controls.Canvas> nesnesine göre konumlandırıldığı gösterilir.  
  
 ![PlacementTarget içermeyen açılan pencere denetimi](./media/popup-placement-behavior/popup-placement-no-placement-target.png "PlacementTarget içermeyen açılan pencere.")  

 Aşağıdaki örnekte <xref:System.Windows.Controls.Canvas> nesnesinin alt nesnesi olan bir <xref:System.Windows.Controls.Primitives.Popup> oluşturulur ancak bu kez <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>, `ellipse1` olarak ayarlanır, dolayısıyla açılan pencere <xref:System.Windows.Shapes.Ellipse> nesnesinin altında görüntülenir.  
  
 [!code-xaml[PopupPositionSnippet#2](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#2)]  
  
 Aşağıdaki resimde <xref:System.Windows.Controls.Primitives.Popup> nesnesinin <xref:System.Windows.Shapes.Ellipse> nesnesine göre konumlandırıldığı gösterilir.  
  
 ![Elipse göre konumlandırılmış açılan pencere](./media/popup-placement-behavior/popup-placement-with-placement-target.png "PlacementTarget içeren açılan pencere")
  
> [!NOTE]
> <xref:System.Windows.Controls.ToolTip> için <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> varsayılan değeri <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse> değeridir.  <xref:System.Windows.Controls.ContextMenu> için <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> varsayılan değeri <xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint> değeridir. Bu değerler daha sonra "Özelliklerin Birlikte Çalışması" bölümünde açıklanmaktadır.  
  
### <a name="target-area"></a>Hedef Alan  
 *Hedef alan*, ekranda <xref:System.Windows.Controls.Primitives.Popup> nesnesinin göreli olarak yerleştirildiği alandır. Önceki örneklerde <xref:System.Windows.Controls.Primitives.Popup> hedef nesnenin sınırlarına hizalanır ama bazı durumlarda <xref:System.Windows.Controls.Primitives.Popup> nesnesinin bir hedef nesnesi olsa bile <xref:System.Windows.Controls.Primitives.Popup> başka sınırlara hizalanır.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> özelliği ayarlanırsa hedef alan hedef nesnenin sınırlarından farklı olur.  
  
 Aşağıdaki örnek, her biri bir <xref:System.Windows.Shapes.Rectangle> ve <xref:System.Windows.Controls.Primitives.Popup> içeren iki <xref:System.Windows.Controls.Canvas> nesnesi oluşturur.  Her iki durumda da <xref:System.Windows.Controls.Primitives.Popup> için hedef nesne <xref:System.Windows.Controls.Canvas> nesnesidir. İlk <xref:System.Windows.Controls.Canvas> nesnesindeki <xref:System.Windows.Controls.Primitives.Popup> üzerinde <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> ayarlanmıştır ve <xref:System.Windows.Rect.X%2A>, <xref:System.Windows.Rect.Y%2A>, <xref:System.Windows.Rect.Width%2A> ile <xref:System.Windows.Rect.Height%2A> özellikleri de sırasıyla 50, 50, 50 ve 100 olarak ayarlanmıştır. İkinci <xref:System.Windows.Controls.Canvas> nesnesindeki <xref:System.Windows.Controls.Primitives.Popup> için <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> ayarlanmamıştır.  Sonuç olarak ilk <xref:System.Windows.Controls.Primitives.Popup>, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> öğesinin altına ve ikinci <xref:System.Windows.Controls.Primitives.Popup> ise <xref:System.Windows.Controls.Canvas> nesnesinin altına konumlandırılır. Ayrıca her <xref:System.Windows.Controls.Canvas>, ilk <xref:System.Windows.Controls.Primitives.Popup> için <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> ile aynı sınırlara sahip bir <xref:System.Windows.Shapes.Rectangle> içerir.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> öğesinin uygulamada görünür bir öğe oluşturmadığına dikkat edin; örnekte <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> öğesini temsil etmek üzere bir <xref:System.Windows.Shapes.Rectangle> oluşturur.  
  
 [!code-xaml[PopupPositionSnippet#4](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#4)]  
  
 Aşağıdaki resimde önceki örneğin sonucu gösterilir.  
  
 ![PlacementRectangle içeren ve içermeyen açılan pencere](./media/popup-placement-behavior/popup-placement-placement-rectangle.png "PlacementRectangle içeren ve içermeyen açılan pencere.")  

### <a name="target-origin-and-popup-alignment-point"></a>Hedef Başlangıç Noktası ve Açılan Pencere Hizalama Noktası  
 *Hedef başlangıç noktası* ve *açılan pencere hizalama noktası* konumlandırma için kullanılan, sırasıyla hedef alandaki ve açılan penceredeki başvuru noktalarıdır. Açılan pencereyi hedef alandan kaydırmak için <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> ve <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> özelliklerini kullanabilirsiniz.  <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> ve <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> hedef başlangıç noktasına ve açılan pencere hizalama noktasına göre belirlenir. <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> özelliğinin değeri hedef başlangıç noktası ile açılan pencere hizalama noktasının nerede konumlandırılacağını belirler.  
  
 Aşağıdaki örnek bir <xref:System.Windows.Controls.Primitives.Popup> oluşturur ve <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> ile <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> özelliklerini 20 değerine ayarlar.  <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> özelliği <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom> (varsayılan) değerine ayarlanmıştır, dolayısıyla hedef başlangıç noktası hedef alanın sol alt köşesi ve açılan pencere hizalama noktası da <xref:System.Windows.Controls.Primitives.Popup> nesnesinin sol üst köşesidir.  
  
 [!code-xaml[PopupPositionSnippet#5](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#5)]  
  
 Aşağıdaki resimde önceki örneğin sonucu gösterilir.  
  
 ![Hedef başlangıç noktası hizalama noktasıyla açılan pencere yerleşimi](./media/popup-placement-behavior/popup-placement-target-origin-alignment-point.png "HorizontalOffset ve VerticalOffset içeren açılan pencere.")
  
<a name="How"></a>
## <a name="how-the-properties-work-together"></a>Özelliklerin Birlikte Çalışması  
 Doğru hedef alanı, hedef başlangıç noktasını ve açılan pencere hizalama noktasını belirlemek için <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> ve <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> öğelerinin değerleri birlikte dikkate alınmalıdır.  Örneğin <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> değeri <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse> olduğunda hedef nesne yoktur, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> yoksayılır ve hedef alan da fare işaretçisinin sınırlarıdır. Öte yandan <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> değeri <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom> olduğunda, <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> veya üst öğesi hedef nesneyi ve <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, hedef alanı belirler.  
  
 Aşağıdaki tabloda hedef nesne, hedef alan, hedef başlangıç noktası ve açılan pencere hizalama noktası belirlenir, ayrıca her <xref:System.Windows.Controls.Primitives.PlacementMode> sabit listesi değeri için <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> ve <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> kullanılıp kullanılmadığını gösterir.  
  
|PlacementMode|Hedef nesne|Hedef alan|Hedef başlangıç noktası|Açılan pencere hizalama noktası|  
|-------------------|-------------------|-----------------|-------------------|---------------------------|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>|Yok. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> yoksayılır.|Ekran veya ayarlandıysa <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> ekrana göre yerleştirilir.|Hedef alanın sol üst köşesi.|<xref:System.Windows.Controls.Primitives.Popup> nesnesinin sol üst köşesi.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>|Yok. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> yoksayılır.|Ekran veya ayarlandıysa <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> ekrana göre yerleştirilir.|Hedef alanın sol üst köşesi.|<xref:System.Windows.Controls.Primitives.Popup> nesnesinin sol üst köşesi.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> veya üst öğe.|Hedef nesne veya ayarlandıysa <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> hedef nesneye göre yerleştirilir.|Hedef alanın sol alt köşesi.|<xref:System.Windows.Controls.Primitives.Popup> nesnesinin sol üst köşesi.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Center>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> veya üst öğe.|Hedef nesne veya ayarlandıysa <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> hedef nesneye göre yerleştirilir.|Hedef alanın ortası.|<xref:System.Windows.Controls.Primitives.Popup> nesnesinin ortası.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> veya üst öğe.|Hedef nesne veya ayarlandıysa <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> hedef nesneye göre yerleştirilir.|<xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> tarafından tanımlanır.|<xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> tarafından tanımlanır.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Left>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> veya üst öğe.|Hedef nesne veya ayarlandıysa <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> hedef nesneye göre yerleştirilir.|Hedef alanın sol üst köşesi.|<xref:System.Windows.Controls.Primitives.Popup> nesnesinin sağ üst köşesi.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>|Yok. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> yoksayılır.|Fare işaretçisinin sınırları. <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> yoksayılır.|Hedef alanın sol alt köşesi.|<xref:System.Windows.Controls.Primitives.Popup> nesnesinin sol üst köşesi.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>|Yok. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> yoksayılır.|Fare işaretçisinin sınırları. <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> yoksayılır.|Hedef alanın sol üst köşesi.|<xref:System.Windows.Controls.Primitives.Popup> nesnesinin sol üst köşesi.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> veya üst öğe.|Hedef nesne veya ayarlandıysa <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> hedef nesneye göre yerleştirilir.|Hedef alanın sol üst köşesi.|<xref:System.Windows.Controls.Primitives.Popup> nesnesinin sol üst köşesi.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> veya üst öğe.|Hedef nesne veya ayarlandıysa <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> hedef nesneye göre yerleştirilir.|Hedef alanın sol üst köşesi.|<xref:System.Windows.Controls.Primitives.Popup> nesnesinin sol üst köşesi.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Right>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> veya üst öğe.|Hedef nesne veya ayarlandıysa <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> hedef nesneye göre yerleştirilir.|Hedef alanın sağ üst köşesi.|<xref:System.Windows.Controls.Primitives.Popup> nesnesinin sol üst köşesi.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Top>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> veya üst öğe.|Hedef nesne veya ayarlandıysa <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> hedef nesneye göre yerleştirilir.|Hedef alanın sol üst köşesi.|<xref:System.Windows.Controls.Primitives.Popup> nesnesinin sol alt köşesi.|  
  
 Aşağıdaki resimlerde her <xref:System.Windows.Controls.Primitives.PlacementMode> değeri için <xref:System.Windows.Controls.Primitives.Popup>, hedef alan, hedef başlangıç noktası ve açılan pencere hizalama noktası gösterilir. Bu şekillerde hedef alan sarı ve <xref:System.Windows.Controls.Primitives.Popup> ise mavidir.  
  
 ![Absolute veya AbsolutePoint yerleşimine sahip açılan pencere](./media/popup-placement-behavior/popup-placement-absolute.png "Yerleşim Absolute veya AbsolutePoint olur.")
  
 ![Bottom yerleşimine sahip açılan pencere](./media/popup-placement-behavior/popup-placement-bottom.png "Yerleşim Bottom olur.")
  
 ![Center yerleşimine sahip açılan pencere](./media/popup-placement-behavior/popup-placement-center.png "Yerleşim Center olur.")
  
 ![Left yerleşimine sahip açılan pencere](./media/popup-placement-behavior/popup-placement-left.png "Yerleşim Left olur.")
  
 ![Mouse yerleşimine sahip açılan pencere](./media/popup-placement-behavior/popup-placement-mouse.png "Yerleşim Mouse olur.")  
  
 ![MousePoint yerleşimine sahip açılan pencere](./media/popup-placement-behavior/popup-placement-mousepoint.png "Yerleşim MousePoint olur.")  
  
 ![Relative veya RelativePoint yerleşimine sahip açılan pencere](./media/popup-placement-behavior/popup-placement-relative.png "Yerleşim Relative veya RelativePoint olur.")
  
 ![Right yerleşimine sahip açılan pencere](./media/popup-placement-behavior/popup-placement-right.png "Yerleşim Right olur.")
  
 ![Top yerleşimine sahip açılan pencere](./media/popup-placement-behavior/popup-placement-top.png "Yerleşim Top olur.")
  
<a name="When"></a>
## <a name="when-the-popup-encounters-the-edge-of-the-screen"></a>Açılan Pencere Ekranın Kenarıyla Karşılaştığında  
 <xref:System.Windows.Controls.Primitives.Popup>, güvenlik nedeniyle ekranın kenarı tarafından gizlenemez. <xref:System.Windows.Controls.Primitives.Popup> ekranın kenarıyla karşılaştığında aşağıdaki üç durumdan biri oluşur:  
  
- Açılan pencere ekranın <xref:System.Windows.Controls.Primitives.Popup> nesnesini gizleyebilecek olan kenarı boyunca kendini yeniden hizalar.  
  
- Açılan pencere farklı bir açılan pencere hizalama noktasını kullanır.  
  
- Açılan pencere farklı bir hedef başlangıç noktası ve açılan pencere hizalama noktasını kullanır.  
  
 Bu seçenekler bu bölümün devamında daha ayrıntılı açıklanmıştır.  
  
 <xref:System.Windows.Controls.Primitives.Popup> nesnesinin ekran kenarıyla karşılaştığı durumdaki davranışı <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> özelliğinin değerine ve açılan pencerenin hangi ekran kenarıyla karşılaştığına bağlıdır. Aşağıdaki tabloda, her <xref:System.Windows.Controls.Primitives.PlacementMode> değeri için <xref:System.Windows.Controls.Primitives.Popup> bir ekran kenarıyla karşılaştığında gerçekleşen davranış özetlenir.  
  
|PlacementMode|Üst kenar|Alt kenar|Sol kenar|Sağ kenar|  
|-------------------|--------------|-----------------|---------------|----------------|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>|Üst kenara hizalanır.|Alt kenara hizalanır.|Sol kenara hizalanır.|Sağ kenara hizalanır.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>|Üst kenara hizalanır.|Açılan pencere hizalama noktası <xref:System.Windows.Controls.Primitives.Popup> nesnesinin sol alt köşesi olacak şekilde değişir.|Sol kenara hizalanır.|Açılan pencere hizalama noktası <xref:System.Windows.Controls.Primitives.Popup> nesnesinin sağ üst köşesi olacak şekilde değişir.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>|Üst kenara hizalanır.|Hedef başlangıç noktası hedef alanın sol üst köşesi olarak ve açılan pencere hizalama noktası da <xref:System.Windows.Controls.Primitives.Popup> nesnesinin sol alt köşesi olarak değişir.|Sol kenara hizalanır.|Sağ kenara hizalanır.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Center>|Üst kenara hizalanır.|Alt kenara hizalanır.|Sol kenara hizalanır.|Sağ kenara hizalanır.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Left>|Üst kenara hizalanır.|Alt kenara hizalanır.|Hedef başlangıç noktası hedef alanın sağ üst köşesi olarak ve açılan pencere hizalama noktası da <xref:System.Windows.Controls.Primitives.Popup> nesnesinin sol üst köşesi olarak değişir.|Sağ kenara hizalanır.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>|Üst kenara hizalanır.|Hedef başlangıç noktası hedef alanın (fare işaretçisinin sınırları) sol üst köşesi olarak ve açılan pencere hizalama noktası da <xref:System.Windows.Controls.Primitives.Popup> nesnesinin sol alt köşesi olarak değişir.|Sol kenara hizalanır.|Sağ kenara hizalanır.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>|Üst kenara hizalanır.|Açılan pencere hizalama noktası <xref:System.Windows.Controls.Primitives.Popup> nesnesinin sol alt köşesi olacak şekilde değişir.|Sol kenara hizalanır.|Açılan pencere hizalama noktası açılan pencerenin sağ üst köşesi olacak şekilde değişir.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>|Üst kenara hizalanır.|Alt kenara hizalanır.|Sol kenara hizalanır.|Sağ kenara hizalanır.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>|Üst kenara hizalanır.|Açılan pencere hizalama noktası <xref:System.Windows.Controls.Primitives.Popup> nesnesinin sol alt köşesi olacak şekilde değişir.|Sol kenara hizalanır.|Açılan pencere hizalama noktası açılan pencerenin sağ üst köşesi olacak şekilde değişir.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Right>|Üst kenara hizalanır.|Alt kenara hizalanır.|Sol kenara hizalanır.|Hedef başlangıç noktası hedef alanın sol üst köşesi olarak ve açılan pencere hizalama noktası da <xref:System.Windows.Controls.Primitives.Popup> nesnesinin sağ üst köşesi olarak değişir.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Top>|Hedef başlangıç noktası hedef alanın sol alt köşesi olarak ve açılan pencere hizalama noktası da <xref:System.Windows.Controls.Primitives.Popup> nesnesinin sol üst köşesi olarak değişir. Aslında bu durum, <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> öğesinin <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom> ayarıyla aynıdır.|Alt kenara hizalanır.|Sol kenara hizalanır.|Sağ kenara hizalanır.|  
  
### <a name="aligning-to-the-screen-edge"></a>Ekran Kenarına Hizalama  
 <xref:System.Windows.Controls.Primitives.Popup>, kendini yeniden konumlandırarak ekranın kenarına hizalanabilir ve böylece <xref:System.Windows.Controls.Primitives.Popup> tam olarak ekranda görünür olur.  Bu durum oluştuğunda hedef başlangıç noktası ile açılan pencere hizalama noktası arasındaki uzaklık <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> ve <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> değerlerinden farklı olabilir. <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> değeri <xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>, <xref:System.Windows.Controls.Primitives.PlacementMode.Center> veya <xref:System.Windows.Controls.Primitives.PlacementMode.Relative> olduğunda <xref:System.Windows.Controls.Primitives.Popup>, kendini ekranın her kenarına hizalar.  Örneğin <xref:System.Windows.Controls.Primitives.Popup> nesnesinde <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> özelliğinin <xref:System.Windows.Controls.Primitives.PlacementMode.Relative> değerine ve <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> özelliğinin 100 değerine ayarlandığını düşünün.  <xref:System.Windows.Controls.Primitives.Popup> kısmen veya tamamen ekranın alt kenarı tarafından gizleniyorsa, <xref:System.Windows.Controls.Primitives.Popup> kendini ekranın alt kenarı boyunca yeniden konumlandırır ve hedef başlangıç noktası ile açılan pencere hizalama noktası arasındaki dikey uzaklık 100'den az olur. Aşağıdaki resimde bu gösterilmektedir.  
  
 ![Ekranın kenarına hizalanan açılan pencere](./media/popup-placement-behavior/popup-placement-relative-screen-edge.png "Açılan pencere ekranın kenarına hizalanır.")
  
### <a name="changing-the-popup-alignment-point"></a>Açılan Pencere Hizalama Noktasını Değiştirme  
 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> değeri <xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>, <xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint> veya <xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint> olduğunda, açılan pencerenin ekranın alt veya sağ kenarıyla karşılaşması durumunda açılan pencere hizalama noktası değişir.  
  
 Aşağıdaki resimde alt ekran kenarı <xref:System.Windows.Controls.Primitives.Popup> nesnesini tamamen veya kısmen gizlediğinde, açılan pencere hizalama noktasının <xref:System.Windows.Controls.Primitives.Popup> nesnesinin sol alt köşesi olduğu gösterilir.  
  
 ![Alt ekran kenarından dolayı yeni hizalama noktası](./media/popup-placement-behavior/popup-placement-relative-point-screen-edge.png "Açılan pencere ekranın alt kenarıyla karşılaşır ve açılan pencere hizalama noktasını değiştirir.")  

 Aşağıdaki resimde <xref:System.Windows.Controls.Primitives.Popup> sağ ekran kenarı tarafından gizlendiğinde açılan pencere hizalama noktasının <xref:System.Windows.Controls.Primitives.Popup> nesnesinin sağ üst köşesi olduğu gösterilir.  
  
 ![Ekran kenarından dolayı yeni açılan pencere hizalama noktası](./media/popup-placement-behavior/popup-placement-relative-point-right-screen-edge.png "Açılan pencere ekranın sağ kenarıyla karşılaşır ve açılan pencere hizalama noktasını değiştirir.")
  
 <xref:System.Windows.Controls.Primitives.Popup> ekranın alt ve sağ kenarlarıyla karşılaştığında açılan pencere hizalama noktası <xref:System.Windows.Controls.Primitives.Popup> nesnesinin sağ alt köşesi olur.  
  
### <a name="changing-the-target-origin-and-popup-alignment-point"></a>Hedef Başlangıç Noktası ve Açılan Pencere Hizalama Noktasını Değiştirme  
 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> değeri <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>, <xref:System.Windows.Controls.Primitives.PlacementMode.Left>, <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>, <xref:System.Windows.Controls.Primitives.PlacementMode.Right> veya <xref:System.Windows.Controls.Primitives.PlacementMode.Top> olduğunda, hedef başlangıç noktası ve açılan pencere hizalama noktası belirli bir ekran kenarıyla karşılaşırsa değişir.  Konumun değişmesine neden olan ekran kenarı, <xref:System.Windows.Controls.Primitives.PlacementMode> değerine bağlıdır.  
  
 Aşağıdaki resimde <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> değeri <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom> olduğunda ve <xref:System.Windows.Controls.Primitives.Popup> ekranın alt kenarıyla karşılaştığında hedef başlangıç noktasının hedef alanın sol üst köşesi ve açılan pencere hizalama noktasının <xref:System.Windows.Controls.Primitives.Popup> nesnesinin sol alt köşesi olduğu gösterilir.  
  
 ![Alt ekran kenarından dolayı yeni hizalama noktası](./media/popup-placement-behavior/popup-placement-bottom-screen-edge.png "Yerleşim Bottom olur ve açılan pencere ekranın alt kenarıyla karşılaşır.")
  
 Aşağıdaki resimde <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> değeri <xref:System.Windows.Controls.Primitives.PlacementMode.Left> olduğunda ve <xref:System.Windows.Controls.Primitives.Popup> ekranın sol kenarıyla karşılaştığında hedef başlangıç noktasının hedef alanın sağ üst köşesi ve açılan pencere hizalama noktasının <xref:System.Windows.Controls.Primitives.Popup> nesnesinin sol üst köşesi olduğu gösterilir.  
  
 ![Sol ekran kenarından dolayı yeni hizalama noktası](./media/popup-placement-behavior/popup-placement-left-screen-edge.png "Yerleşim Left olur ve açılan pencere ekranın sol kenarıyla karşılaşır.")  
  
 Aşağıdaki resimde <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> değeri <xref:System.Windows.Controls.Primitives.PlacementMode.Right> olduğunda ve <xref:System.Windows.Controls.Primitives.Popup> ekranın sağ kenarıyla karşılaştığında hedef başlangıç noktasının hedef alanın sol üst köşesi ve açılan pencere hizalama noktasının <xref:System.Windows.Controls.Primitives.Popup> nesnesinin sağ üst köşesi olduğu gösterilir.  
  
 ![Sağ ekran kenarından dolayı yeni hizalama noktası](./media/popup-placement-behavior/popup-placement-right-screen-edge.png "Yerleşim Right olur ve açılan pencere ekranın sağ kenarıyla karşılaşır.")  

 Aşağıdaki resimde <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> değeri <xref:System.Windows.Controls.Primitives.PlacementMode.Top> olduğunda ve <xref:System.Windows.Controls.Primitives.Popup> ekranın üst kenarıyla karşılaştığında hedef başlangıç noktasının hedef alanın sol alt köşesi ve açılan pencere hizalama noktasının <xref:System.Windows.Controls.Primitives.Popup> nesnesinin sol üst köşesi olduğu gösterilir.  
  
 ![Üst ekran kenarından dolayı yeni hizalama noktası](./media/popup-placement-behavior/popup-placement-top-screen-edge.png "Yerleşim Top olur ve açılan pencere ekranın üst kenarıyla karşılaşır.")  
  
 Aşağıdaki resimde <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> değeri <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse> olduğunda ve <xref:System.Windows.Controls.Primitives.Popup> ekranın alt kenarıyla karşılaştığında hedef başlangıç noktasının hedef alanın sol üst köşesi (fare işaretçisinin sınırları) ve açılan pencere hizalama noktasının <xref:System.Windows.Controls.Primitives.Popup> nesnesinin sol alt köşesi olduğu gösterilir.  
  
 ![Farenin ekran kenarına yakın olmasından dolayı yeni hizalama noktası](./media/popup-placement-behavior/popup-placement-mouse-screen-edge.png "Yerleşim Mouse olur ve açılan pencere ekranın alt kenarıyla karşılaşır.")
  
### <a name="customizing-popup-placement"></a>Açılan Pencere Yerleşimini Özelleştirme  
 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> özelliğini <xref:System.Windows.Controls.Primitives.PlacementMode.Custom> değerine ayarlayarak hedef başlangıç noktasını ve açılan pencere hizalama noktasını özelleştirebilirsiniz. Ardından <xref:System.Windows.Controls.Primitives.Popup> için olası yerleşim noktaları ve birincil eksenler kümesini (tercih sırasıyla) döndüren bir <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> temsilcisi tanımlayın. <xref:System.Windows.Controls.Primitives.Popup> nesnesinin en büyük bölümünü gösteren nokta seçilidir.  <xref:System.Windows.Controls.Primitives.Popup> ekranın kenarı tarafından gizlenmişse <xref:System.Windows.Controls.Primitives.Popup> konumu otomatik olarak ayarlanır. [Özel Açılan Pencere Konumu Belirtme](how-to-specify-a-custom-popup-position.md) konusunda bir örnek görebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Açılan Pencere Yerleşim Örneği](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS)
