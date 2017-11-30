---
title: "Açılan Pencere Yerleştirme Davranışı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- popups [WPF]
- Popup control [WPF], placing
- placing popups [WPF]
- positioning popups [WPF]
ms.assetid: fbf642e9-f670-4efd-a7af-a67468a1c8e1
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 07ac582841fd6b5b6a24c63896821c65eb6687e4
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="popup-placement-behavior"></a>Açılan Pencere Yerleştirme Davranışı
A <xref:System.Windows.Controls.Primitives.Popup> denetimi, bir uygulama gezinen ayrı bir pencerede içeriği görüntüler. Konumunu belirtebilirsiniz bir <xref:System.Windows.Controls.Primitives.Popup> bir denetim, fare veya kullanarak ekran göre <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>, <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>, ve <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> özellikleri.  Bu özellikleri konumunu belirtme esneklik için birlikte çalışan <xref:System.Windows.Controls.Primitives.Popup>.  
  
> [!NOTE]
>  <xref:System.Windows.Controls.ToolTip> Ve <xref:System.Windows.Controls.ContextMenu> sınıfları Ayrıca bu beş özelliklerini tanımlamak ve benzer şekilde davranır.  
  

  
<a name="Positioning"></a>   
## <a name="positioning-the-popup"></a>Açılan konumlandırma  
 Yerleşimini bir <xref:System.Windows.Controls.Primitives.Popup> göreli olabilir bir <xref:System.Windows.UIElement> veya tüm ekranı.  Aşağıdaki örnek dört oluşturur <xref:System.Windows.Controls.Primitives.Popup> göreli denetimleri bir <xref:System.Windows.UIElement>— bu durumda, bir resim. Tüm <xref:System.Windows.Controls.Primitives.Popup> denetimleriniz <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> özelliğini `image1`, ancak her <xref:System.Windows.Controls.Primitives.Popup> yerleştirme özelliği için farklı bir değere sahip.  
  
 [!code-xaml[PopupPositionSnippet#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#3)]  
  
 Görüntü aşağıda gösterilmiştir ve <xref:System.Windows.Controls.Primitives.Popup> denetimleri  
  
 ![Dört açılan denetimler görüntüsüyle](../../../../docs/framework/wpf/controls/media/popupplacementintro.png "PopupPlacementIntro")  
Dört açılan pencereler görüntüsüyle  
  
 Bu basit örnek nasıl ayarlanacağını gösterir <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> ve <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> özellikleri, ancak kullanarak <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>, ve <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> özellikleri, where daha fazla denetime sahip olursunuz <xref:System.Windows.Controls.Primitives.Popup> konumlandırıldı.  
  
<a name="Definitions"></a>   
## <a name="definitions-of-terms-the-anatomy-of-a-popup"></a>Terimlerin tanımları: Popup anatomisi  
 Aşağıdaki terimler içinde anlamak yararlı nasıl <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>, <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>, ve <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> özellikleri birbiriyle ilgili ve <xref:System.Windows.Controls.Primitives.Popup>:  
  
-   Hedef nesne  
  
-   Hedef alan  
  
-   Hedef kaynak  
  
-   Açılan kutu hizalama noktası  
  
 Bu koşulları için çeşitli yönlerini başvurmak için kolay bir yol sağlamak <xref:System.Windows.Controls.Primitives.Popup> ve ilişkili olduğu denetimi.  
  
### <a name="target-object"></a>Hedef nesne  
 *Hedef nesne* öğesi, <xref:System.Windows.Controls.Primitives.Popup> ile ilişkili. Varsa <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> özelliği ayarlanmışsa, hedef nesneyi belirtir.  Varsa <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> ayarlı değil ve <xref:System.Windows.Controls.Primitives.Popup> bir üst öğeye sahip üst hedef nesnesidir.  Varsa hiçbir <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> değeri ve hiçbir üst hedef nesnesi yok ve <xref:System.Windows.Controls.Primitives.Popup> göre ekran konumlandırıldı.  
  
 Aşağıdaki örnekte bir <xref:System.Windows.Controls.Primitives.Popup> öğesinin alt öğesi olan bir <xref:System.Windows.Controls.Canvas>.  Örnek ayarlı değil <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> özelliği <xref:System.Windows.Controls.Primitives.Popup>. İçin varsayılan değer <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> olan <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom?displayProperty=nameWithType>, böylece <xref:System.Windows.Controls.Primitives.Popup> altında görünen <xref:System.Windows.Controls.Canvas>.  
  
 [!code-xaml[PopupPositionSnippet#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#1)]  
  
 Aşağıdaki çizimde gösterilmektedir <xref:System.Windows.Controls.Primitives.Popup> göreli olarak konumlandırılmış <xref:System.Windows.Controls.Canvas>.  
  
 ![Açılan denetim PlacementTarget içermeyen](../../../../docs/framework/wpf/controls/media/popupplacementnoplacementtarget.PNG "PopupPlacementNoPlacementTarget")  
Açılan PlacementTarget içermeyen  
  
 Aşağıdaki örnekte bir <xref:System.Windows.Controls.Primitives.Popup> öğesinin alt öğesi olan bir <xref:System.Windows.Controls.Canvas>, ancak bu kez <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> ayarlanır `ellipse1`, açılan altında görünmesi <xref:System.Windows.Shapes.Ellipse>.  
  
 [!code-xaml[PopupPositionSnippet#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#2)]  
  
 Aşağıdaki çizimde gösterilmektedir <xref:System.Windows.Controls.Primitives.Popup> göreli olarak konumlandırılmış <xref:System.Windows.Shapes.Ellipse>.  
  
 ![Elips göre konumlandırılmış açılan kutu](../../../../docs/framework/wpf/controls/media/popupplacementwithplacementtarget.PNG "PopupPlacementWithPlacementTarget")  
Açılan PlacementTarget ile  
  
> [!NOTE]
>  İçin <xref:System.Windows.Controls.ToolTip>, varsayılan değeri <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> olan <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>.  İçin <xref:System.Windows.Controls.ContextMenu>, varsayılan değeri <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> olan <xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>. Bu değerler, daha sonra "Nasıl özellikleri birlikte çalışır." açıklanmıştır  
  
### <a name="target-area"></a>Hedef alan  
 *Hedef alan* alanı ekranında, <xref:System.Windows.Controls.Primitives.Popup> göreli sağlamaktır. Önceki örneklerde, <xref:System.Windows.Controls.Primitives.Popup> hedef nesnenin, ancak bazı durumlarda, sınırları ile hizalanır <xref:System.Windows.Controls.Primitives.Popup> diğer sınırları için hizalanır olsa bile <xref:System.Windows.Controls.Primitives.Popup> hedef nesnesi sahiptir.  Varsa <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> özelliği ayarlanmışsa, hedef alan hedef nesne sınırları farklı.  
  
 Aşağıdaki örnekte iki oluşturur <xref:System.Windows.Controls.Canvas> nesneleri, her birini içeren bir <xref:System.Windows.Shapes.Rectangle> ve <xref:System.Windows.Controls.Primitives.Popup>.  Her iki durumda da, hedef nesnesi için <xref:System.Windows.Controls.Primitives.Popup> olan <xref:System.Windows.Controls.Canvas>. <xref:System.Windows.Controls.Primitives.Popup> İlk <xref:System.Windows.Controls.Canvas> sahip <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Ayarla ile kendi <xref:System.Windows.Rect.X%2A>, <xref:System.Windows.Rect.Y%2A>, <xref:System.Windows.Rect.Width%2A>, ve <xref:System.Windows.Rect.Height%2A> özellikleri sırasıyla 50, 50, 50 ve 100 ayarlayın. <xref:System.Windows.Controls.Primitives.Popup> İkinci <xref:System.Windows.Controls.Canvas> sahip olmayan <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> ayarlayın.  Sonuç olarak, ilk <xref:System.Windows.Controls.Primitives.Popup> altına yerleştirilmiş <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> ve ikinci <xref:System.Windows.Controls.Primitives.Popup> altına yerleştirilmiş <xref:System.Windows.Controls.Canvas>. Her <xref:System.Windows.Controls.Canvas> de içeren bir <xref:System.Windows.Shapes.Rectangle> olarak aynı sınır olan <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> ilk kez <xref:System.Windows.Controls.Primitives.Popup>.  Unutmayın <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> görünür öğesi uygulamada; oluşturmaz örnekte bir <xref:System.Windows.Shapes.Rectangle> temsil etmek için <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>.  
  
 [!code-xaml[PopupPositionSnippet#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#4)]  
  
 Aşağıdaki çizimde, önceki örnekte sonucunu gösterir.  
  
 ![Açılan ile ve YerleştirmeDikdörtgeni olmadan](../../../../docs/framework/wpf/controls/media/popupplacementplacementrectangle.PNG "PopupPlacementPlacementRectangle")  
Açılan ile ve YerleştirmeDikdörtgeni olmadan  
  
### <a name="target-origin-and-popup-alignment-point"></a>Hedef kaynağı ve açılan kutu hizalama noktası  
 *Hedef kaynak* ve *açılan hizalama noktası* başvuru noktaları hedef alan ve açılan, sırasıyla olan konumlandırma için kullanılır. Kullanabileceğiniz <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> ve <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> özellikleri hedef alanından açılan uzaklığı.  <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> Ve <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> hedef kaynağa ve açılan kutu hizalama noktası göre. Değeri <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> özelliği, hedef kaynak ve açılan hizalama noktası bulunduğu belirler.  
  
 Aşağıdaki örnekte bir <xref:System.Windows.Controls.Primitives.Popup> ve ayarlar <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> ve <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> 20 özellikleri.  <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> Özelliği ayarlanmış <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom> (varsayılan), bu nedenle hedef kaynak hedef alanın sol alt köşesine ve açılan kutu hizalama noktası sol üst köşesindeki <xref:System.Windows.Controls.Primitives.Popup>.  
  
 [!code-xaml[PopupPositionSnippet#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#5)]  
  
 Aşağıdaki çizimde, önceki örnekte sonucunu gösterir.  
  
 ![Hedef kaynak hizalama noktasıyla açılan yerleştirme](../../../../docs/framework/wpf/controls/media/popupplacementtargetoriginalignmentpoint.PNG "PopupPlacementTargetOriginAlignmentPoint")  
Açılan HorizontalOffset ve VerticalOffset  
  
<a name="How"></a>   
## <a name="how-the-properties-work-together"></a>Özellikleri birlikte nasıl çalışır  
 Değerlerini <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, ve <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> birlikte doğru hedef alan, hedef kaynak ve açılan kutu hizalama noktası şekilde ele alınması gerekir.  Örneğin, varsa değerini <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> olan <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>, hedef nesnesi yok, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> göz ardı edilir ve fare işaretçisini sınırlarına hedef alanıdır. Öte yandan, <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> olan <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>, <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> veya ana hedef nesne belirler ve <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> hedef alanını belirler.  
  
 Aşağıdaki tabloda hedef nesnesi, hedef alan, hedef kaynak ve açılan kutu hizalama noktası açıklar ve gösterir olup olmadığını <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> ve <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> her biri için kullanılan <xref:System.Windows.Controls.Primitives.PlacementMode> numaralandırma değeri.  
  
|PlacementMode|Hedef nesne|Hedef alan|Hedef kaynak|Açılan kutu hizalama noktası|  
|-------------------|-------------------|-----------------|-------------------|---------------------------|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>|Yok. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>göz ardı edilir.|Ekran veya <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Bu ayarlanırsa.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Ekran göreli olur.|Hedef alan sol üst köşesindeki.|Sol üst köşesindeki <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>|Yok. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>göz ardı edilir.|Ekran veya <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Bu ayarlanırsa.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Ekran göreli olur.|Hedef alan sol üst köşesindeki.|Sol üst köşesindeki <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>veya üst.|Hedef nesne veya <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Bu ayarlanırsa.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Göre hedef nesnesi.|Hedef alan sol alt köşesindeki.|Sol üst köşesindeki <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Center>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>veya üst.|Hedef nesne veya <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Bu ayarlanırsa.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Göre hedef nesnesi.|Hedef alan Merkezi.|Merkezi <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>veya üst.|Hedef nesne veya <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Bu ayarlanırsa.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Göre hedef nesnesi.|Tarafından tanımlanan <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>.|Tarafından tanımlanan <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Left>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>veya üst.|Hedef nesne veya <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Bu ayarlanırsa.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Göre hedef nesnesi.|Hedef alan sol üst köşesindeki.|Sağ üst köşesindeki <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>|Yok. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>göz ardı edilir.|Fare işaretçisini sınırları. <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>göz ardı edilir.|Hedef alan sol alt köşesindeki.|Sol üst köşesindeki <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>|Yok. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>göz ardı edilir.|Fare işaretçisini sınırları. <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>göz ardı edilir.|Hedef alan sol üst köşesindeki.|Sol üst köşesindeki <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>veya üst.|Hedef nesne veya <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Bu ayarlanırsa.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Göre hedef nesnesi.|Hedef alan sol üst köşesindeki.|Sol üst köşesindeki <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>veya üst.|Hedef nesne veya <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Bu ayarlanırsa.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Göre hedef nesnesi.|Hedef alan sol üst köşesindeki.|Sol üst köşesindeki <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Right>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>veya üst.|Hedef nesne veya <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Bu ayarlanırsa.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Göre hedef nesnesi.|Hedef alana sağ üst köşesindeki.|Sol üst köşesindeki <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Top>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>veya üst.|Hedef nesne veya <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Bu ayarlanırsa.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Göre hedef nesnesi.|Hedef alan sol üst köşesindeki.|Sol alt köşesindeki <xref:System.Windows.Controls.Primitives.Popup>.|  
  
 Aşağıdaki çizimler gösterisini <xref:System.Windows.Controls.Primitives.Popup>, hedef alan, hedef kaynak ve açılan hizalama noktası her biri için <xref:System.Windows.Controls.Primitives.PlacementMode> değeri. Her şekilde, hedef sarı, alanıdır ve <xref:System.Windows.Controls.Primitives.Popup> mavi.  
  
 ![Mutlak veya AbsolutePoint yerleştirme açılan](../../../../docs/framework/wpf/controls/media/popupplacementabsolute.png "PopupPlacementAbsolute")  
Yerleştirme mutlak AbsolutePoint mi  
  
 ![Açılan alt yerleştirme](../../../../docs/framework/wpf/controls/media/popupplacementbottom.png "PopupPlacementBottom")  
Alt yerleştirme vardır  
  
 ![Açılan merkezi yerleştirme](../../../../docs/framework/wpf/controls/media/popupplacementcenter.png "PopupPlacementCenter")  
Yerleştirme merkezidir.  
  
 ![Sol yerleştirme açılan](../../../../docs/framework/wpf/controls/media/popupplacementleft.png "PopupPlacementLeft")  
Sol yerleştirme olduğu  
  
 ![Fare yerleştirme açılan](../../../../docs/framework/wpf/controls/media/popupplacementmouse.png "PopupPlacementMouse")  
Fare yerleştirme olduğu  
  
 ![Açılan MousePoint yerleştirme](../../../../docs/framework/wpf/controls/media/popupplacementmousepoint.png "PopupPlacementMousePoint")  
Yerleştirme MousePoint olduğu  
  
 ![Göreli veya RelativePoint yerleştirme açılan](../../../../docs/framework/wpf/controls/media/popupplacementrelative.png "PopupPlacementRelative")  
Yerleştirme göreli RelativePoint mi  
  
 ![Açılan sağ yerleştirme](../../../../docs/framework/wpf/controls/media/popupplacementright.png "PopupPlacementRight")  
Yerleştirme hangisi  
  
 ![Açılan üst yerleştirme](../../../../docs/framework/wpf/controls/media/popupplacementtop.png "PopupPlacementTop")  
Üst yerleştirme bulunur  
  
<a name="When"></a>   
## <a name="when-the-popup-encounters-the-edge-of-the-screen"></a>Açılan ekranın kenarına karşılaştığında  
 Güvenlik nedeniyle, bir <xref:System.Windows.Controls.Primitives.Popup> bir ekran kenarından gizli olamaz. Aşağıdaki işlemlerden birini olur zaman <xref:System.Windows.Controls.Primitives.Popup> ekran kenarı karşılaşır:  
  
-   Açılan soyutlamaması ekran kenarından kendisini yeniden hizalar <xref:System.Windows.Controls.Primitives.Popup>.  
  
-   Açılan farklı açılan hizalama noktası kullanır.  
  
-   Açılan farklı bir hedef kaynak ve açılan hizalama noktası kullanır.  
  
 Bu seçenekler daha sonra bu bölümde daha ayrıntılı açıklanmıştır.  
  
 Davranışını <xref:System.Windows.Controls.Primitives.Popup> onu karşılaştığında ekran kenarı değerine bağlıdır <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> özelliği ve hangi ekran açılan karşılaştığında sınır. Davranış aşağıdaki tabloda özetlenmiştir zaman <xref:System.Windows.Controls.Primitives.Popup> her biri için bir ekran kenar karşılaştığında <xref:System.Windows.Controls.Primitives.PlacementMode> değeri.  
  
|PlacementMode|Üst kenarı|Kenar|Sol kenar|Sağ kenar|  
|-------------------|--------------|-----------------|---------------|----------------|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>|Üst kenarına hizalanır.|Alt ucuna hizalar.|Sol ucuna hizalar.|Sağ ucuna hizalar.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>|Üst kenarına hizalanır.|Açılan kutu hizalama noktası için sol alt köşesindeki değişiklikleri <xref:System.Windows.Controls.Primitives.Popup>.|Sol ucuna hizalar.|Açılan kutu hizalama noktası için sağ üst köşesindeki değişiklikleri <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>|Üst kenarına hizalanır.|Hedef kaynak hedef alan sol üst köşesindeki ve açılan kutu hizalama noktası için sol alt köşesindeki değiştirir <xref:System.Windows.Controls.Primitives.Popup>.|Sol ucuna hizalar.|Sağ ucuna hizalar.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Center>|Üst kenarına hizalanır.|Alt ucuna hizalar.|Sol ucuna hizalar.|Sağ ucuna hizalar.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Left>|Üst kenarına hizalanır.|Alt ucuna hizalar.|Hedef kaynak hedef alana sağ üst köşesindeki ve için sol üst köşesindeki açılır hizalama noktası değiştirir <xref:System.Windows.Controls.Primitives.Popup>.|Sağ ucuna hizalar.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>|Üst kenarına hizalanır.|Hedef kaynak hedef alan (fare işaretçisi sınırları) sol üst köşesindeki ve açılan kutu hizalama noktası için sol alt köşesindeki değiştirir <xref:System.Windows.Controls.Primitives.Popup>.|Sol ucuna hizalar.|Sağ ucuna hizalar.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>|Üst kenarına hizalanır.|Açılan kutu hizalama noktası için sol alt köşesindeki değişiklikleri <xref:System.Windows.Controls.Primitives.Popup>.|Sol ucuna hizalar.|Açılan hizalama açılan sağ üst köşesindeki değişiklikleri gelin.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>|Üst kenarına hizalanır.|Alt ucuna hizalar.|Sol ucuna hizalar.|Sağ ucuna hizalar.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>|Üst kenarına hizalanır.|Açılan kutu hizalama noktası için sol alt köşesindeki değişiklikleri <xref:System.Windows.Controls.Primitives.Popup>.|Sol ucuna hizalar.|Açılan hizalama açılan sağ üst köşesindeki değişiklikleri gelin.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Right>|Üst kenarına hizalanır.|Alt ucuna hizalar.|Sol ucuna hizalar.|Hedef kaynak hedef alan sol üst köşesindeki ve için sağ üst köşesindeki açılır hizalama noktası değiştirir <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Top>|Hedef kaynak hedef alanın sol alt köşesine ve için sol üst köşesindeki açılır hizalama noktası değiştirir <xref:System.Windows.Controls.Primitives.Popup>. Gerçekte, bu zaman aynıdır <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> olan <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>.|Alt ucuna hizalar.|Sol ucuna hizalar.|Sağ ucuna hizalar.|  
  
### <a name="aligning-to-the-screen-edge"></a>Ekran kenarına hizalama  
 A <xref:System.Windows.Controls.Primitives.Popup> ekran için kendisini şekilde yeniden konumlandırma tarafından tüm hizalar <xref:System.Windows.Controls.Primitives.Popup> ekranda görülebilir.  Bu durumda, hedef kaynak ve açılan hizalama noktası arasındaki uzaklığı değerleri değişebilir <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> ve <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>. Zaman <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> olan <xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>, <xref:System.Windows.Controls.Primitives.PlacementMode.Center>, veya <xref:System.Windows.Controls.Primitives.PlacementMode.Relative>, <xref:System.Windows.Controls.Primitives.Popup> kendisini her ekran ucuna hizalar.  Örneğin, varsayımında bir <xref:System.Windows.Controls.Primitives.Popup> sahip <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> kümesine <xref:System.Windows.Controls.Primitives.PlacementMode.Relative> ve <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> 100'e ayarlayın.  Ekranın alt kenarı bölümünü veya tümünü gizler <xref:System.Windows.Controls.Primitives.Popup>, <xref:System.Windows.Controls.Primitives.Popup> kendisini yeniden konumlandırır ekran ve dikey uzaklık hedef kaynağı ve açılan arasında kenar boyunca hizalama 100'den küçük noktasıdır. Aşağıdaki çizim bu gösterir.  
  
 ![Ekran ucuna hizalar açılan](../../../../docs/framework/wpf/controls/media/popupplacementrelativescreenedge.png "PopupPlacementRelativeScreenEdge")  
Açılan ekranda ucuna hizalar  
  
### <a name="changing-the-popup-alignment-point"></a>Açılan kutu hizalama noktası değiştirme  
 Varsa <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> olan <xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>, <xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>, veya <xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>, açılan hizalama noktası açılan Alttan veya sağ ekran kenarına karşılaştığında değiştirir.  
  
 Ekran kenar bölümünü veya tümünü gizler olduğunda, aşağıdaki çizimde gösterilmektedir <xref:System.Windows.Controls.Primitives.Popup>, sol alt köşesindeki açılır hizalama noktasıdır <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Ekran kenar nedeniyle yeni hizalama noktası](../../../../docs/framework/wpf/controls/media/popupplacementrelativepointscreenedge.png "PopupPlacementRelativePointScreenEdge")  
Açılan ekran kenar karşılaşır ve açılan kutu hizalama noktası değiştirir  
  
 Aşağıdaki çizimde olduğunda gösterilmektedir <xref:System.Windows.Controls.Primitives.Popup> gizli ekranın sağ kenarından açılan hizalama sağ üst köşesindeki noktasıdır <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Ekran kenarına nedeniyle yeni açılan hizalama noktası](../../../../docs/framework/wpf/controls/media/popupplacementrelativepointrightscreenedge.png "PopupPlacementRelativePointRightScreenEdge")  
Açılan ekranın sağ kenarından karşılaşır ve açılan kutu hizalama noktası değiştirir  
  
 Varsa <xref:System.Windows.Controls.Primitives.Popup> alt ve sağ ekran kenarlar karşılaştığında sağ alt köşesindeki açılır hizalama noktasıdır <xref:System.Windows.Controls.Primitives.Popup>.  
  
### <a name="changing-the-target-origin-and-popup-alignment-point"></a>Açılan kutu hizalama noktası ve hedef kaynak değiştirme  
 Zaman <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> olan <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>, <xref:System.Windows.Controls.Primitives.PlacementMode.Left>, <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>, <xref:System.Windows.Controls.Primitives.PlacementMode.Right>, veya <xref:System.Windows.Controls.Primitives.PlacementMode.Top>, belirli bir ekran kenar karşılaştıysanız hedef kaynağı ve açılan hizalama noktası değişiklik.  Konumu değiştirmek neden olan ekran kenarına bağlıdır <xref:System.Windows.Controls.Primitives.PlacementMode> değeri.  
  
 Olduğunda aşağıdaki çizimde gösterilmektedir <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> olan <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom> ve <xref:System.Windows.Controls.Primitives.Popup> alt ekran kenarına karşılaştığında hedef kaynak hedef alan sol üst köşesindeki ve açılan kutu hizalama noktası sol alt köşesindeki <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Ekran kenar nedeniyle yeni hizalama noktası](../../../../docs/framework/wpf/controls/media/popupplacementbottomscreenedge.png "PopupPlacementBottomScreenEdge")  
Alt yerleştirme vardır ve açılan ekran kenar karşılaşırsa  
  
 Olduğunda aşağıdaki çizimde gösterilmektedir <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> olan <xref:System.Windows.Controls.Primitives.PlacementMode.Left> ve <xref:System.Windows.Controls.Primitives.Popup> sol ekran kenarına karşılaştığında hedef kaynak hedef alana sağ üst köşesindeki ve açılan kutu hizalama noktası solüstköşesindeki<xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Sol ekran kenarına nedeniyle yeni hizalama noktası](../../../../docs/framework/wpf/controls/media/popupplacementleftscreenedge.png "PopupPlacementLeftScreenEdge")  
Sol yerleştirme olduğu ve açılan ekranın sol kenarından karşılaşırsa  
  
 Olduğunda aşağıdaki çizimde gösterilmektedir <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> olan <xref:System.Windows.Controls.Primitives.PlacementMode.Right> ve <xref:System.Windows.Controls.Primitives.Popup> sağ ekran kenarına karşılaştığında hedef kaynak hedef alan sol üst köşesindeki ve açılan kutu hizalama noktası sağ üst köşesindeki <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Sağ ekran kenarına nedeniyle yeni hizalama noktası](../../../../docs/framework/wpf/controls/media/popupplacementrightscreenedge.png "PopupPlacementRightScreenEdge")  
Yerleştirme hangisi ve açılan ekranın sağ kenarından karşılaşırsa  
  
 Olduğunda aşağıdaki çizimde gösterilmektedir <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> olan <xref:System.Windows.Controls.Primitives.PlacementMode.Top> ve <xref:System.Windows.Controls.Primitives.Popup> üst ekran kenarına karşılaştığında hedef kaynak hedef alanın sol alt köşesine ve açılan kutu hizalama noktası sol üst köşesindeki <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Üst ekran kenarına nedeniyle yeni hizalama noktası](../../../../docs/framework/wpf/controls/media/popupplacementtopscreenedge.png "PopupPlacementTopScreenEdge")  
Üst yerleştirme bulunur ve açılan ekran üst kenarı karşılaşırsa  
  
 Olduğunda aşağıdaki çizimde gösterilmektedir <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> olan <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse> ve <xref:System.Windows.Controls.Primitives.Popup> alt ekran kenarına karşılaştığında hedef alan (fare işaretçisi sınırları) ve açılan hizalama sol üst köşesindeki hedef kaynak değil sol alt köşesindeki noktasıdır <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![ekran kenarına yakın fareye nedeniyle yeni hizalama noktası](../../../../docs/framework/wpf/controls/media/popupplacementmousescreenedge.png "PopupPlacementMouseScreenEdge")  
Fare yerleştirme olduğu ve açılan ekran kenar karşılaşırsa  
  
### <a name="customizing-popup-placement"></a>Açılan yerleştirme özelleştirme  
 Hedef kaynak ve açılan hizalama noktası ayarlayarak özelleştirebileceğiniz <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> özelliğine <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>. Ardından tanımlayan bir <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> için olası yerleştirme noktaları ve birincil eksenler (tercih sırasına göre) kümesini döndürür temsilci <xref:System.Windows.Controls.Primitives.Popup>. En büyük bölümünü gösterir noktası <xref:System.Windows.Controls.Primitives.Popup> seçilir.  Konumunu <xref:System.Windows.Controls.Primitives.Popup> varsa otomatik olarak düzeltilir <xref:System.Windows.Controls.Primitives.Popup> ekranın kenarına tarafından gizlenir. Bir örnek için bkz: [özel açılan konumunu belirtin](../../../../docs/framework/wpf/controls/how-to-specify-a-custom-popup-position.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Açılan yerleştirme örnek](http://go.microsoft.com/fwlink/?LinkID=160032)
